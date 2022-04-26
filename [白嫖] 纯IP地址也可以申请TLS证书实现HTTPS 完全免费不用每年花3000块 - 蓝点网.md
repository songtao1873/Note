# [白嫖] 纯IP地址也可以申请TLS证书实现HTTPS 完全免费不用每年花3000块 - 蓝点网
# \[白嫖] 纯 IP 地址也可以申请 TLS 证书实现 HTTPS 完全免费不用每年花 3000 块

 [![](https://www.landian.vip/wp-content/uploads/2022/03/avatar-1-2022-03-30-01-00-57-75.png)
 **山外的鸭子哥**](https://www.landian.vip/archives/user/1 "山外的鸭子哥")[开发运维](https://www.landian.vip/tutorials/dev), [技术教程](https://www.landian.vip/tutorials)2022 年 4 月 25 日 14:4185.70K

[![](https://img.lancdn.com/0x87009/Windows-11-SingleTop.png)
](https://ourl.co/91375)

目前免费 TLS 证书已经非常容易获取，Let's Encrypt 提供 90 天的单域名、多域名、乃至通配符证书。不过纯 IP 地址 TLS 证书多数都是收费的，Let's Encrypt 也不支持纯 IP 地址证书，想要从商业 CA 那里申请纯 IP 地址 TLS 证书价格并不便宜，有的需要人民币 3000 元 / 年。

不过如果想要白嫖的话也不是不行，国外数字证书提供商 zeroSSL 就提供基于 IP 地址的 TLS 证书，可以实现 IP 地址 HTTPS 加密访问。

当然对多数个人用户和开发者来说估计完全用不到 IP 证书，或许只有某些企业在特定场景下才可能用得上纯 IP 地址证书吧。下面是 zeroSSL 纯 IP 地址证书的申请方法。

**完整申请步骤如下：3 分钟搞定**

1\. 点击这里注册 zeroSSL 账号：[https://ourl.co/zerossl](https://ourl.co/zerossl) 邮箱验证即可

2\. 转到控制面板点击创建新证书：

[![](https://img.lancdn.com/landian/2022/04/93605-1.png)
](https://img.lancdn.com/landian/2022/04/93605-1.png)

3\. 在域名里输入 ip 地址即可

[![](https://img.lancdn.com/landian/2022/04/93605-2.png)
](https://img.lancdn.com/landian/2022/04/93605-2.png)

4\. 免费版是 90 天的：

[![](https://img.lancdn.com/landian/2022/04/93605-3.png)
](https://img.lancdn.com/landian/2022/04/93605-3.png)

5\. 选择自动生成 CSR 即可，如果你有需要的话，也可以自己生成 CSR 提交

[![](https://img.lancdn.com/landian/2022/04/93605-4.png)
](https://img.lancdn.com/landian/2022/04/93605-4.png)

6\. 白嫖党当然选 90 天免费的，1 年的都需要收费了

[![](https://img.lancdn.com/landian/2022/04/93605-5.png)
](https://img.lancdn.com/landian/2022/04/93605-5.png)

7\. 这里我们选择文件验证，因为 DNS 验证要域名的解析权限这个估计大家都没吧

[![](https://img.lancdn.com/landian/2022/04/93605-6.png)
](https://img.lancdn.com/landian/2022/04/93605-6.png)

9\. 下载验证文件并在服务器上创建对应文件夹，要确保 IP 地址 + 文件夹 + 文件能够正常访问。宝塔用户可以在网站里创建新网站，域名就直接输入 ip 地址即可。

[![](https://img.lancdn.com/landian/2022/04/93605-7.png)
](https://img.lancdn.com/landian/2022/04/93605-7.png)

10\. 点击验证：

[![](https://img.lancdn.com/landian/2022/04/93605-8.png)
](https://img.lancdn.com/landian/2022/04/93605-8.png)

11\. 验证完成等待签发证书：

[![](https://img.lancdn.com/landian/2022/04/93605-9.png)
](https://img.lancdn.com/landian/2022/04/93605-9.png)

12\. 证书签发完成可以下载了：

[![](https://img.lancdn.com/landian/2022/04/93605-11.png)
](https://img.lancdn.com/landian/2022/04/93605-11.png)

13\. 下载的证书有 ca_bundle.crt 和 certificate.crt 以及私钥 key，NGINX 里使用 certificate.crt+key 即可，有的环境可能要两个 crt 拼接下，具体得各位自己按使用环境测试。

14\. 在服务器上部署 TLS 证书后即可访问：

[![](https://img.lancdn.com/landian/2022/04/93605-12.png)
](https://img.lancdn.com/landian/2022/04/93605-12.png)

15\. 证书有效：

[![](https://img.lancdn.com/landian/2022/04/93605-13.png)
](https://img.lancdn.com/landian/2022/04/93605-13.png)

**到期后怎么续期：** 

zeroSSL 也提供 API 能够实现自动需求但需要各位自己动手实现证书自动化申请和续期，如果没有开发能力的话只能 90 天一次手动申请新证书来实现人肉需求。

也有开发者使用 golang 写了个工具可以实现更新：[https://github.com/tinkernels/zerossl-ip-cert](https://github.com/tinkernels/zerossl-ip-cert)

更多请参考 zeroSSL API 文档：[https://zerossl.com/documentation/api/](https://zerossl.com/documentation/api/)

[HTTPS**(133)**](https://www.landian.vip/archives/tag/https "HTTPS")[IP**(20)**](https://www.landian.vip/archives/tag/ip "IP")[SSL**(74)**](https://www.landian.vip/archives/tag/ssl "SSL")[TLS**(29)**](https://www.landian.vip/archives/tag/tls "TLS")[zeroSSL**(1)**](https://www.landian.vip/archives/tag/zerossl "zeroSSL")[数字证书**(53)**](https://www.landian.vip/archives/tag/%e6%95%b0%e5%ad%97%e8%af%81%e4%b9%a6 "数字证书")

### 分享海报

下载海报

![](https://img.lancdn.com/landian/2022/04/93605.png)

252022/04

## \[白嫖] 纯 IP 地址也可以申请 TLS 证书实现 HTTPS 完全免费不用每年花 3000 块

目前免费 TLS 证书已经非常容易获取，Let's Encrypt 提供 90 天的单域名、多域名、乃至通配符证书。不过纯 IP 地址 TLS 证书多数都是收费的，Let's Encrypt 也不支持纯 IP 地址证书，想要...

#### 蓝点网

给你感兴趣的内容！

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAAAXNSR0IArs4c6QAAA/5JREFUaEPtWtmO4jAQhP//aFagddTU1GWGlVaEeZojcdzt6joyXC+Xy+1SfN1u/LLr9Xrcfb/m/vO6Vn1/v2Hdt+65/24+Y967HqDumXtIpdx3e1PFqI3NzWFR7oGzEeu6WTAWjWthc1kj1PPXvUfBrEtN99kpzpNIHXenrZqJ+2InP587r/8WrDqDsHczmOZTQZXNsILxXOOfn/CEIc4zI5/1u0QuOM/Y/FSkuv/XkP6IghO7KaJwzKpONMnPaqi6jklhy/AP0mqYtGHGVocbrV7XJO11Y8DqOl/B1nVAi5JWY0cbHXfmQiHPGaWE1isruJ296ZYofIbtZGzOGqTcU2NT1Rw/3XvagpnAN9aOGRUGOcesyTg4JKl1EVGHj8fwkMwBgw3eg3KCxkO5Njd/ThZ3RutHWjpFwUm0GZE0MHQZus3MLFKyMWLoYEizOty6K1W8kiXn6lyBalSSFD15cOe0PrLgJUs7kc6xNwaLSShKCRLpsDXZSMzr1GH9gHQb0ZTreoKPeL+lNoZcMhuLRTezjXt5rLEgrTrGbnK5081nIhb8u5I791Ig+olTFuzy6ZztKU9phvC0HGOnU1lwTqGhip3LabHCGJwZwTSB3G2GEVvikmSQLGk1etnYR2ch/6uCJzs6M64IiRmCVyDNTmXHbDQR8sjDDaTTw3ENJStpFhlXtO4sWdZvwQ62O26MaSozC+60ESE7KqHGjBoPxcRqw214aMbGWVElkbO5LqFJp3WKght9nZBS0EfGZx1PGjrlTRFlWuOl8KAcmEtLThpYk9RaqOkNbJcjY5J4HBbmYWVCdoxDE0QUAWFhTSpzjnAi7tGQex5uzYbSOCSaRq+TXjqWnyfpUMgI8Cg4SYaLau5EFYM7NmbQRC5QJ5+k83wFs7QUuwT/QnGEkmbQIceSz989qJOXepwKVsz6G1lCkmnm2cmQclV03fTGAwkNtZh1OKWnqQSKldc1ifHV/hRzx3daH1twK+zIoIk91QmxRrJ5Ttc5NDHlofEwkZaCiys+pSLmrBD6aVYVN8xD+hY8rViTR1lXG2PPUJJQoILIDsvTf6Y11pDNvNNc1QSpl6CzLmQoiWR1nK/gd36KZ0eTd/QVE48KD8yDIxm+/DmtaUBw8+lVzGRfZw0b24lrpVBxzoITOyqNTJmV/X3GwgVBxbKoGCxStuFhnfzWB8RVtlWQVu6thaprmAsv2NQnCcS0lMy8O+0lHe+IhEpzm0LfVrAjKrUR5YWTTVQowDFQdlK9ttqC9CxYwRUlo/HliVkbVDk+meuft+AESWcBU+DHtR2cFRQbbpmsjlA/0LnzifhmhtHzOslhjWCmZY4JwhsjJJOuJ3k7W8F/AAuJ4yvjyEfnAAAAAElFTkSuQmCC)

感谢您的阅读，本文为蓝点网原创内容，转载时请标注来源于蓝点网和[本文链接](https://www.landian.vip/archives/93605.html)

#### "给作者加个鸭腿~ 感谢支持~"

打赏还没有人赞赏，支持一下

分享海报收藏**(0)**

**1\*\***0\*\*

分享：

![](data:image/png;base64,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)

打开微信 “扫一扫”，打开网页后点击屏幕右上角分享按钮 
 [https://www.landian.vip/archives/93605.html](https://www.landian.vip/archives/93605.html)
