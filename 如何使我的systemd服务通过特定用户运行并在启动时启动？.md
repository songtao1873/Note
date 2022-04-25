# 如何使我的systemd服务通过特定用户运行并在启动时启动？
   如何使我的 systemd 服务通过特定用户运行并在启动时启动？      

# 如何使我的 systemd 服务通过特定用户运行并在启动时启动？

* * *

132  

我刚从 Ubuntu 服务器 14 升级到版本 15。升级后，我的新贵脚本无法正常工作，并且读到 systemd 是新的默认值。我距离 Linux 专家还很远，所以请对我放轻松:-)

这是我之前的暴发户脚本：

```
description "NZBGet upstart script"

setuid robert
setgid robert

start on runlevel [2345]
stop on runlevel [016]

respawn

expect fork

script
    exec nzbget -D
end script

pre-stop script
    exec nzbget -Q
end script

```

基于[systemd wiki 页面](https://wiki.ubuntu.com/SystemdForUpstartUsers)的[新贵](https://wiki.ubuntu.com/SystemdForUpstartUsers)，我使用那里提供的表来尽可能紧密地映射新的 systemd 服务文件中的内容：

```
[Unit]
Description=NZBGet Service

[Service]
Type=forking
ExecStart=/usr/local/bin/nzbget -D
ExecStop=/usr/local/bin/nzbget -Q
Restart=on-failure

```

该文件位于`/home/robert/.config/systemd/user/nzbget.service`。要手动启动该服务，我一直在做：

```
$ systemctl --user start nzbget

```

这很好。但是，当我退出 SSH 会话时，该服务将关闭。此外，它不会在启动或用户登录时启动。我希望它的行为与作为新贵服务的行为相同：我希望它在引导时启动，持续运行并以特定用户身份运行。

我需要怎么做才能获得此配置？

[systemd](/ubuntu/tagged/systemd/) 

— [无效指针](https://askubuntu.com/users/332176/void-pointer)  
[source](https://askubuntu.com/questions/676007/how-do-i-make-my-systemd-service-run-via-specific-user-and-start-on-boot)

Answers:

* * *

163  

## 第一个问题

您可以指定指令`User=`，并`Group=`在`[Service]`该单位文件的部分。

## 第二个问题

要使服务在启动时运行，请勿将其放在主文件夹中。相反，将其放在下`/etc/systemd/system/`。这是系统管理员（即您）用来添加新的系统范围服务的文件夹。

其他文件夹包括：

-   `/usr/lib/systemd/system/`是用于想要安装单位文件的软件包，尽管在 Debian 和 Ubuntu 下，该文件夹实际上是`/lib/systemd/system/`因为这些文件夹`bin`和`lib`文件夹尚未合并到统一的`/usr/`前缀中。
-   `/usr/local/systemd/system/` 用于通过本地编译的软件包安装单元。

## 测试单元

单元文件放在适当的位置后，您可以尝试`systemctl start <UNIT_FILENAME>`照常键入立即尝试启动单元。它无需输入设备的完整路径即可工作。如果扩展名也不必指定`.service`。

## 启用设备

在启用您的单元之前，您需要添加一个`[Install]`部分，您应该在下面添加指令`WantedBy=multi-user.target`。该指令指定启动过程的阶段，在该阶段应启动服务（如果已启用）。`multi-user.target`适用于大多数服务。

添加该信息后，您可以使用`systemctl enable <UNIT_FILENAME>`，启用该单元，从现在开始使 systemd 在指定阶段的启动过程中自动启动。

— [山保](https://askubuntu.com/users/112426/yamaho)  
[source](https://askubuntu.com/questions/676007/how-do-i-make-my-systemd-service-run-via-specific-user-and-start-on-boot/676022#676022)

* * *

这工作了。虽然我必须在命令中指定服务文件名的绝对路径，`systemctl enable`但起初对我来说这并不明显。同时启用也给我一些关于缺少`[Install]`部分的警告。我忽略了它，但是我不确定它是否会影响它在启动时启动的能力。

— [void.pointer 2015 年](https://askubuntu.com/users/332176/void-pointer)

* * *

2  

该`Install`警告实际上非常重要。没有`WantedBy=multi-user.target`该`[Install]`部分的内容，它将无法在启动时启动。这增加的后`.service`文件，_那么_就可以`enable`了。

— [void.pointer 2015 年](https://askubuntu.com/users/332176/void-pointer)

* * *

4  

对于这么长的时间无人问津，我深表歉意。我固定了单元文件应存放的位置，并添加了有关该`[Install]`部分的缺失信息。希望它现在对任何寻找它的人都有帮助。

— [Yamaho](https://askubuntu.com/users/112426/yamaho)

* * *

5  

当使用用户名进行模板化时，这将变得更加容易，例如，使用文件名定义您的服务，`something@.service`然后使用以下格式：`enable`d 就像`something@username.service`该设置一样，`User=%i`意味着用户没有经过硬编码，并且多个用户可以使用相同的定义。[一个例子。](https://github.com/joeroback/dropbox)

— [沃尔夫'17](https://askubuntu.com/users/518847/walf)

* * *

1  

如果放下它会开始`/etc/systemd/user/`吗？

— [库尔希德 · 阿拉姆](https://askubuntu.com/users/11112/khurshid-alam)

* * *

46  

您可能对使用 systemd 的 “用户挥之不去” 功能感兴趣。通过启用`loginctl enable-linger USERNAME`。

这会导致在启动时为各个用户启动一个单独的服务管理器，因此`~/.config/systemd/user`将根据您的服务配置在启动和关闭时提取并处理用户定义的单元。

您还可以`systemctl --user`用于管理和配置服务，这些服务将在用户的服务管理器（而不是系统之一）上运行。

— [字节堡](https://askubuntu.com/users/175043/byteborg)  
[source](https://askubuntu.com/questions/676007/how-do-i-make-my-systemd-service-run-via-specific-user-and-start-on-boot/859583#859583)

* * *

6  

`systemctl --user`是一个了不起的发现。谢谢！

— [安瓦尔](https://askubuntu.com/users/61218/anwar)

* * *

@byteborg 也许您可以为[unix.stackexchange.com/questions/409900/…](https://unix.stackexchange.com/questions/409900/user-lingering-systemd-dependency-on-postgresql "用户对 PostgreSQL 的 systemd 依赖")做出贡献？我需要在用户延迟服务中依赖 PostgreSQL，但是数据库仍然是系统服务，而不是用户的服务。

— [米哈尔˚F](https://askubuntu.com/users/429116/micha%c5%82-f)

* * *

1  

服务运行后，是否有任何技术可以使用户查看服务日志？没有特权的用户将无法访问 / var / log / syslog。

— [mpr](https://askubuntu.com/users/583659/mpr)

* * *

2  

请注意，`systemctl --user`这似乎不适用于 SSH 会话。

— [Mark K Cowan '18](https://askubuntu.com/users/138999/mark-k-cowan)

* * *

2  

应该是公认的解决方案

— [德鲁](https://askubuntu.com/users/2595/drew) 
 [https://qastack.cn/ubuntu/676007/how-do-i-make-my-systemd-service-run-via-specific-user-and-start-on-boot](https://qastack.cn/ubuntu/676007/how-do-i-make-my-systemd-service-run-via-specific-user-and-start-on-boot)
