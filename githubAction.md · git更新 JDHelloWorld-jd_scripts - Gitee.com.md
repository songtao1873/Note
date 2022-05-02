# githubAction.md · git更新/JDHelloWorld-jd_scripts - Gitee.com
## [](#%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E8%AF%B4%E6%98%8E)环境变量说明

##### [](#%E4%BA%AC%E4%B8%9C%E5%BF%85%E9%A1%BB)京东 (必须)

| Name        | 归属  | 属性  | 说明                                                                                                                                                                                                                                                                                                                                      |
| ----------- | --- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `JD_COOKIE` | 京东  | 必须  | 京东 cookie, 多个账号的 cookie 使用`&`隔开，例：`pt_key=XXX;pt_pin=XXX;&pt_key=XXX;pt_pin=XXX;&pt_key=XXX;pt_pin=XXX;`。具体获取参考[浏览器获取京东 cookie 教程](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/backUp/GetJdCookie.md) 或者 [插件获取京东 cookie 教程](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/backUp/GetJdCookie2.md) |

##### [](#%E4%BA%AC%E4%B8%9C%E9%9A%90%E7%A7%81%E5%AE%89%E5%85%A8-%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)京东隐私安全 环境变量

| Name            | 归属       | 属性  | 默认值  | 说明                                                                         |
| --------------- | -------- | --- | ---- | -------------------------------------------------------------------------- |
| `JD_DEBUG`      | 脚本打印 log | 非必须 | true | 运行脚本时，是否显示 log, 默认显示。改成 false 表示不显示，注重隐私的人可以设置 JD_DEBUG 为 false            |
| `JD_USER_AGENT` | 京东       | 非必须 |      | 自定义此库里京东系列脚本的 UserAgent，不懂不知不会 UserAgent 的请不要随意填写内容。如需使用此功能建议填写京东 APP 的 UA |

##### [](#%E6%8E%A8%E9%80%81%E9%80%9A%E7%9F%A5%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E7%9B%AE%E5%89%8D%E6%8F%90%E4%BE%9B%E5%BE%AE%E4%BF%A1server%E9%85%B1pushplus%E6%8E%A8%E9%80%81%E5%8A%A0ios-bark-apptelegram%E6%9C%BA%E5%99%A8%E4%BA%BA%E9%92%89%E9%92%89%E6%9C%BA%E5%99%A8%E4%BA%BA%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%9C%BA%E5%99%A8%E4%BA%BAigot%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E5%BA%94%E7%94%A8%E6%B6%88%E6%81%AF%E7%AD%89%E9%80%9A%E7%9F%A5%E6%96%B9%E5%BC%8F)推送通知环境变量 (目前提供`微信 server 酱`、`pushplus(推送加)`、`iOS Bark APP`、`telegram 机器人`、`钉钉机器人`、`企业微信机器人`、`iGot`、`企业微信应用消息`等通知方式)

| Name                       | 归属                                                                                                                            | 属性  | 说明                                                                                                                                                                                                                                                               |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `PUSH_KEY`                 | 微信 server 酱推送                                                                                                                 | 非必须 | server 酱的微信通知[官方文档](https://gitee.com/link?target=http%3A%2F%2Fsc.ftqq.com%2F3.version)，已兼容 [Server 酱 ·Turbo 版](https://gitee.com/link?target=https%3A%2F%2Fsct.ftqq.com%2F)                                                                                     |
| `BARK_PUSH`                | [BARK 推送](https://gitee.com/link?target=https%3A%2F%2Fapps.apple.com%2Fus%2Fapp%2Fbark-customed-notifications%2Fid1403753865) | 非必须 | IOS 用户下载 BARK 这个 APP, 填写内容是 app 提供的`设备码`，例如：[https://api.day.app/123](https://gitee.com/link?target=https%3A%2F%2Fapi.day.app%2F123) ，那么此处的设备码就是`123`，再不懂看 [这个图](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/icon/bark.jpg)（注：支持自建填完整链接即可）   |
| `BARK_SOUND`               | [BARK 推送](https://gitee.com/link?target=https%3A%2F%2Fapps.apple.com%2Fus%2Fapp%2Fbark-customed-notifications%2Fid1403753865) | 非必须 | bark 推送声音设置，例如`choo`, 具体值请在`bark`-`推送铃声`-`查看所有铃声`                                                                                                                                                                                                                |
| `BARK_GROUP`               | [BARK 推送](https://gitee.com/link?target=https%3A%2F%2Fapps.apple.com%2Fus%2Fapp%2Fbark-customed-notifications%2Fid1403753865) | 非必须 | bark 推送消息分组，默认`JDHelloWorld`, 推送成功后可以在`bark`-`历史消息`-`右上角文件夹图标查看`                                                                                                                                                                                                 |
| `TG_BOT_TOKEN`             | telegram 推送                                                                                                                   | 非必须 | tg 推送 (需设备可连接外网),`TG_BOT_TOKEN`和`TG_USER_ID`两者必需, 填写自己申请[@BotFather](https://gitee.com/link?target=https%3A%2F%2Ft.me%2FBotFather)的 Token, 如`10xxx4:AAFcqxxxxgER5uw` , [具体教程](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/backUp/TG_PUSH.md) |
| `TG_USER_ID`               | telegram 推送                                                                                                                   | 非必须 | tg 推送 (需设备可连接外网),`TG_BOT_TOKEN`和`TG_USER_ID`两者必需, 填写[@getuseridbot](https://gitee.com/link?target=https%3A%2F%2Ft.me%2Fgetuseridbot)中获取到的纯数字 ID, [具体教程](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/backUp/TG_PUSH.md)                       |
| `DD_BOT_TOKEN`             | 钉钉推送                                                                                                                          | 非必须 | 钉钉推送 (`DD_BOT_TOKEN`和`DD_BOT_SECRET`两者必需)[官方文档](https://gitee.com/link?target=https%3A%2F%2Fdevelopers.dingtalk.com%2Fdocument%2Fapp%2Fcustom-robot-access) , 只需`https://oapi.dingtalk.com/robot/send?access_token=XXX` 等于`=`符号后面的 XXX 即可                        |
| `DD_BOT_SECRET`            | 钉钉推送                                                                                                                          | 非必须 | (`DD_BOT_TOKEN`和`DD_BOT_SECRET`两者必需) , 密钥，机器人安全设置页面，加签一栏下面显示的 SEC 开头的`SECXXXXXXXXXX`等字符 , 注: 钉钉机器人安全设置只需勾选`加签`即可，其他选项不要勾选, 再不懂看 [这个图](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/icon/DD_bot.png)                                           |
| `QYWX_KEY`                 | 企业微信机器人推送                                                                                                                     | 非必须 | 密钥，企业微信推送 webhook 后面的 key [详见官方说明文档](https://gitee.com/link?target=https%3A%2F%2Fwork.weixin.qq.com%2Fapi%2Fdoc%2F90000%2F90136%2F91770)                                                                                                                         |
| `QYWX_AM`                  | 企业微信应用消息推送                                                                                                                    | 非必须 | corpid,corpsecret,touser,agentid, 素材库图片 id [参考文档 1](https://gitee.com/link?target=http%3A%2F%2Fnote.youdao.com%2Fs%2FHMiudGkb) [参考文档 2](https://gitee.com/link?target=http%3A%2F%2Fnote.youdao.com%2Fnoteshare%3Fid%3D1a0c8aff284ad28cbd011b29b3ad0191)          |
| 素材库图片填 0 为图文消息, 填 1 为纯文本消息 |                                                                                                                               |     |                                                                                                                                                                                                                                                                  |
| `IGOT_PUSH_KEY`            | iGot 推送                                                                                                                       | 非必须 | iGot 聚合推送，支持多方式推送，确保消息可达。 [参考文档](https://gitee.com/link?target=https%3A%2F%2Fwahao.github.io%2FBark-MP-helper)                                                                                                                                                   |
| `PUSH_PLUS_TOKEN`          | pushplus 推送                                                                                                                   | 非必须 | 微信扫码登录后一对一推送或一对多推送下面的 token(您的 Token) [官方网站](https://gitee.com/link?target=http%3A%2F%2Fwww.pushplus.plus%2F)                                                                                                                                                    |
| `PUSH_PLUS_USER`           | pushplus 推送                                                                                                                   | 非必须 | 一对多推送的 “群组编码”（一对多推送下面 -> 您的群组 (如无则新建)-> 群组编码）注:(1、需订阅者扫描二维码 2、如果您是创建群组所属人，也需点击 “查看二维码” 扫描绑定，否则不能接受群组消息推送)，只填`PUSH_PLUS_TOKEN`默认为一对一推送                                                                                                                            |
| `TG_PROXY_HOST`            | Telegram 代理的 IP                                                                                                               | 非必须 | 代理类型为 http。例子：http 代理 [http://127.0.0.1:1080](https://gitee.com/link?target=http%3A%2F%2F127.0.0.1%3A1080) 则填写 127.0.0.1                                                                                                                                         |
| `TG_PROXY_PORT`            | Telegram 代理的端口                                                                                                                | 非必须 | 例子：http 代理 [http://127.0.0.1:1080](https://gitee.com/link?target=http%3A%2F%2F127.0.0.1%3A1080) 则填写 1080                                                                                                                                                         |
| `TG_PROXY_AUTH`            | Telegram 代理的认证参数                                                                                                              | 非必须 | 代理的认证参数                                                                                                                                                                                                                                                          |
| `TG_API_HOST`              | Telegram api 自建的反向代理地址                                                                                                        | 非必须 | 例子：反向代理地址 [http://aaa.bbb.ccc](https://gitee.com/link?target=http%3A%2F%2Faaa.bbb.ccc) 则填写 aaa.bbb.ccc [简略搭建教程](https://gitee.com/link?target=https%3A%2F%2Fshimo.im%2Fdocs%2FJD38CJDQtYy3yTd8%2Fread)                                                           |

##### [](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%B1%BB%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)互助码类环境变量

| Name                        | 归属      | 属性      | 需要助力次数 / 可提供助力次数                                                                                                                                                                                            | 说明  |
| --------------------------- | ------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| `FRUITSHARECODES`           | 东东农场    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 5/3     | 填写规则请看[jdFruitShareCodes.js](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/jdFruitShareCodes.js)或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99) |     |
| `PETSHARECODES`             | 东东萌宠    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 5/5     | 填写规则和上面类似或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                          |     |
| `PLANT_BEAN_SHARECODES`     | 种豆得豆    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 9/3     | 填写规则和上面类似或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                          |     |
| `DDFACTORY_SHARECODES`      | 东东工厂    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 5/3     | 填写规则和上面类似或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                          |     |
| `DREAM_FACTORY_SHARE_CODES` | 京喜工厂    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 不固定 / 3 | 填写规则和上面类似或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                          |     |
| `JDZZ_SHARECODES`           | 京东赚赚    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 5/2     | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `JDJOY_SHARECODES`          | 疯狂的 JOY |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 6/      | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `BOOKSHOP_SHARECODES`       | 京东书店    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 10/     | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `JD_CASH_SHARECODES`        | 签到领现金   |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 10/     | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `JDSGMH_SHARECODES`         | 闪购盲盒    |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 10/     | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `JDCFD_SHARECODES`          | 京喜财富岛   |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 未知 / 未知 | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `JDHEALTH_SHARECODES`       | 东东健康社区  |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 未知 / 未知 | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |
| `CITY_SHARECODES`           | 城城领现金   |         |                                                                                                                                                                                                             |     |
| 互助码                         | 非必须     | 未知 / 未知 | 填写规则和上面类似，或见下方[互助码的填写规则](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)                                                                                                         |     |

##### [](#%E6%8E%A7%E5%88%B6%E8%84%9A%E6%9C%AC%E5%8A%9F%E8%83%BD%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)控制脚本功能环境变量

| Name           | 归属      | 属性  | 说明                                         |
| -------------- | ------- | --- | ------------------------------------------ |
| `JD_BEAN_STOP` | 京东多合一签到 | 非必须 | `jd_bean_sign.js`自定义延迟签到, 单位毫秒. 默认分批并发无延迟， |

延迟作用于每个签到接口，如填入延迟则切换顺序签到 (耗时较长)，  
如需填写建议输入数字`1`，详见[此处说明](https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2FNobyDa%2FScript%2Fblob%2Fmaster%2FJD-DailyBonus%2FJD_DailyBonus.js%23L93) \|
\| `JD_BEAN_SIGN_STOP_NOTIFY` | 京东多合一签到 | 非必须 | `jd_bean_sign.js`脚本运行后不推送签到结果通知，默认推送，填`true`表示不发送通知 |
\| `JD_BEAN_SIGN_NOTIFY_SIMPLE` | 京东多合一签到 | 非必须 | `jd_bean_sign.js`脚本运行后推送签到结果简洁版通知，  
默认推送签到简洁结果，填`true`表示推送简洁通知，[效果图](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/icon/bean_sign_simple.jpg) \|
\| `PET_NOTIFY_CONTROL` | 东东萌宠  
推送开关 | 非必须 | 控制京东萌宠是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `FRUIT_NOTIFY_CONTROL` | 东东农场  
推送开关 | 非必须 | 控制京东农场是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `CASH_NOTIFY_CONTROL` | 京东领现金  
推送开关 | 非必须 | 控制京东领现金是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `CASH_EXCHANGE` | 京东领现金  
红包兑换京豆开关 | 非必须 | 控制京东领现金是否把红包兑换成京豆,  
`false`为否,`true`为是 (即：花费 2 元红包兑换 200 京豆，一周可换四次)，默认为`false` \|
\| `DDQ_NOTIFY_CONTROL` | 点点券  
推送开关 | 非必须 | 控制点点券是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `JDZZ_NOTIFY_CONTROL` | 京东赚赚小程序  
推送开关 | 非必须 | 控制京东赚赚小程序是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `MONEYTREE_NOTIFY_CONTROL` | 京东摇钱树  
推送开关 | 非必须 | 控制京东摇钱树兑换 0.07 金贴后是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `JD_JOY_REWARD_NOTIFY` | 宠汪汪  
兑换京豆推送开关 | 非必须 | 控制`jd_joy_reward.js`脚本是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `JOY_FEED_COUNT` | 宠汪汪喂食数量 | 非必须 | 控制`jd_joy_feedPets.js`脚本喂食数量, 可以填的数字 0,10,20,40,80, 其他数字不可. |
\| `JOY_HELP_FEED` | 宠汪汪帮好友喂食 | 非必须 | 控制`jd_joy_steal.js`脚本是否给好友喂食,`false`为否,`true`为是 (给好友喂食) |
\| `JOY_RUN_FLAG` | 宠汪汪是否赛跑 | 非必须 | 控制`jd_joy.js`脚本是否参加赛跑 (默认参加双人赛跑),  
`false`为否,`true`为是，脚本默认是`true` \|
\| `JOY_TEAM_LEVEL` | 宠汪汪  
参加什么级别的赛跑 | 非必须 | 控制`jd_joy.js`脚本参加几人的赛跑, 可选数字为`2`,`10`,`50`，  
其中 2 代表参加双人 PK 赛，10 代表参加 10 人突围赛，  
50 代表参加 50 人挑战赛 (注：此项功能在`JOY_RUN_FLAG`为 true 的时候才生效)，  
如若想设置不同账号参加不同类别的比赛则用 & 区分即可 (如下三个账号：`2&10&50`) |
\| `JOY_RUN_NOTIFY` | 宠汪汪  
宠汪汪赛跑获胜后是否推送通知 | 非必须 | 控制`jd_joy.js`脚本宠汪汪赛跑获胜后是否推送通知，  
`false`为否 (不推送通知消息),`true`为是 (即：发送推送通知消息)  
 \|
\| `JOY_RUN_HELP_MYSELF` | 宠汪汪  
赛跑自己账号内部互助 | 非必须 | 输入`true`为开启内部互助 |
\| `JD_JOY_REWARD_NAME` | 宠汪汪  
积分兑换多少京豆 | 非必须 | 目前可填值为`20`或者`500`, 脚本默认`0`,`0`表示不兑换京豆 |
\| `JOY_RUN_TOKEN` | 宠汪汪  
赛跑 token | 非必须 | 需自行抓包，宠汪汪小程序获取 token，点击`发现`或`我的`，寻找`^https:\/\/draw\.jdfcloud\.com(\/mirror)?\/\/api\/user\/user\/detail\?openId=`获取 token |
\| `MARKET_COIN_TO_BEANS` | 东东超市  
兑换京豆数量 | 非必须 | 控制`jd_blueCoin.js`兑换京豆数量,  
可输入值为`20`或者`1000`的数字或者其他商品的名称, 例如`碧浪洗衣凝珠` \|
\| `MARKET_REWARD_NOTIFY` | 东东超市  
兑换奖品推送开关 | 非必须 | 控制`jd_blueCoin.js`兑换奖品成功后是否静默运行,  
`false`为否 (发送推送通知消息),`true`为是 (即：不发送推送通知消息) |
\| `JOIN_PK_TEAM` | 东东超市  
自动参加 PK 队伍 | 非必须 | 每次 pk 活动参加作者创建的 pk 队伍,`true`表示参加,`false`表示不参加 |
\| `SUPERMARKET_LOTTERY` | 东东超市抽奖 | 非必须 | 每天运行脚本是否使用金币去抽奖,`true`表示抽奖,`false`表示不抽奖 |
\| `FRUIT_BEAN_CARD` | 东东农场  
使用水滴换豆卡 | 非必须 | 东东农场使用水滴换豆卡 (如果出现限时活动时 100g 水换 20 豆, 此时比浇水划算, 推荐换豆),  
`true`表示换豆 (不浇水),`false`表示不换豆 (继续浇水), 脚本默认是浇水 |
\| `UN_SUBSCRIBES` | jd_unsubscribe.js | 非必须 | 共四个参数, 换行隔开. 四个参数分别表示  
`是否取关全部商品 (0 表示一个都不)`,`是否取关全部店铺数 (0 表示一个都不)`,`遇到此商品不再进行取关`,`遇到此店铺不再进行取关`，[具体使用往下看](#%E5%8F%96%E5%85%B3%E5%BA%97%E9%93%BA%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E7%9A%84%E8%AF%B4%E6%98%8E) \|
\| `JDJOY_HELPSELF` | 疯狂的 JOY  
循环助力 | 非必须 | 疯狂的 JOY 循环助力，`true`表示循环助力,`false`表示不循环助力，默认不开启循环助力。 |
\| `JDJOY_APPLYJDBEAN` | 疯狂的 JOY  
京豆兑换 | 非必须 | 疯狂的 JOY 京豆兑换，目前最小值为 2000 京豆 (详情请查看活动页面 - 提现京豆)，  
默认数字`0`不开启京豆兑换。 |
\| `BUY_JOY_LEVEL` | 疯狂的 JOY  
购买 joy 等级 | 非必须 | 疯狂的 JOY 自动购买什么等级的 JOY |
\| `MONEY_TREE_SELL_FRUIT` | 摇钱树  
是否卖出金果 | 非必须 | 控制摇钱树脚本是否自动卖出金果兑换成金币，`true`卖出，`false`不卖出，默认`false` \|
\| `FACTORAY_WANTPRODUCT_NAME` | 东东工厂  
心仪商品 | 非必须 | 提供心仪商品名称 (请尽量填写完整和别的商品有区分度)，达到条件后兑换，  
如不提供则会兑换当前所选商品 |
\| `DREAMFACTORY_FORBID_ACCOUNT` | 京喜工厂  
控制哪个京东账号不运行此脚本 | 非必须 | 输入`1`代表第一个京东账号不运行，多个使用`&`连接，例：`1&3`代表账号 1 和账号 3 不运行京喜工厂脚本，注：输入`0`，代表全部账号不运行京喜工厂脚本 |
\| `JDFACTORY_FORBID_ACCOUNT` | 东东工厂  
控制哪个京东账号不运行此脚本 | 非必须 | 输入`1`代表第一个京东账号不运行，多个使用`&`连接，例：`1&3`代表账号 1 和账号 3 不运行东东工厂脚本，注：输入`0`，代表全部账号不运行东东工厂脚本 |
\| `CFD_NOTIFY_CONTROL` | 京喜财富岛  
控制是否运行脚本后通知 | 非必须 | 输入`true`为通知, 不填则为不通知 |
\| `JXNC_NOTIFY_LEVEL` | 京喜农场通知控制  
推送开关, 默认 1 | 非必须 | 通知级别 0 = 只通知成熟; 1 = 本次获得水滴 > 0;2 = 任务执行; 3 = 任务执行 + 未种植种子 |
\| `PURCHASE_SHOPS` | 执行`jd_scripts`仓库的脚本是否做加物品至购物车任务。默认关闭不做加购物车任务 | 非必须 | 如需做此类型任务。请设置`true`，目前东东小窝 (jd_small_home.js) 脚本会有加购任务 |
\| `TUAN_ACTIVEID` | 京喜工厂拼团瓜分电力活动的`activeId`  
默认读取作者设置的 | 非必须 | 如出现脚本开团提示失败：`活动已结束，请稍后再试~`，可自行抓包替换 (开启抓包，进入拼团瓜分电力页面，寻找带有`tuan`的链接里面的`activeId=`) |
\| `HELP_AUTHOR` | 是否给作者助力 免费拿, 极速版拆红包, 省钱大赢家等活动.  
默认是 | 非必须 | 填`false`可关闭此助力 |

##### [](#%E4%BA%92%E5%8A%A9%E7%A0%81%E7%9A%84%E5%A1%AB%E5%86%99%E8%A7%84%E5%88%99)互助码的填写规则

> 互助码如何获取：长期活动可在 jd_get_share_code.js 里面查找，短期活动需运行相应脚本后，在日志里面可以找到。

同一个京东账号的好友互助码用 @隔开, 不同京东账号互助码用 & 或者换行隔开, 下面给一个文字示例和具体互助码示例说明

两个账号各两个互助码的文字示例：

京东账号 1 的 shareCode1@京东账号 1 的 shareCode2 & 京东账号 2 的 shareCode1@京东账号 2 的 shareCode2

两个账号各两个互助码的真实示例：

0a74407df5df4fa99672a037eec61f7e@dbb21614667246fabcfd9685b6f448f3&6fbd26cc27ac44d6a7fed34092453f77@61ff5c624949454aa88561f2cd721bf6&6fbd26cc27ac44d6a7fed34092453f77@61ff5c624949454aa88561f2cd721bf6

#### [](#%E5%8F%96%E5%85%B3%E5%BA%97%E9%93%BA%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E7%9A%84%E8%AF%B4%E6%98%8E)取关店铺环境变量的说明

> 环境变量内容的意思依次是`是否取关全部商品 (0 表示一个都不)`,`是否取关全部店铺数 (0 表示一个都不)`,`遇到此商品不再进行取关`,`遇到此店铺不再进行取关`

例如 1：不要取关任何商品和店铺，则输入`0&0` 例如 2：我想商品遇到关键字 `iPhone12` 停止取关，店铺遇到 `Apple 京东自营旗舰店` 不再取关，则输入`10&10&iPhone12&Apple 京东自营旗舰店`(前面两个参数非 0 即可)

#### [](#%E5%85%B3%E4%BA%8E%E8%84%9A%E6%9C%AC%E6%8E%A8%E9%80%81%E9%80%9A%E7%9F%A5%E9%A2%91%E7%8E%87)关于脚本推送通知频率

> 如果你填写了推送通知方式中的某一种通知所需环境变量，那么脚本通知情况如下：

> 目前默认只有 jd_fruit.js,jd_pet.js,jd_bean_sign.js,jd_bean_change.js,jd_jxnc.js 这些脚本 (默认) 每次运行后都通知

其余的脚本平常运行都是不通知，只有在京东 cookie 失效以及达到部分条件后，才会推送通知 
 [https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/githubAction.md#%E5%85%B3%E4%BA%8E%E8%84%9A%E6%9C%AC%E6%8E%A8%E9%80%81%E9%80%9A%E7%9F%A5%E9%A2%91%E7%8E%87](https://gitee.com/git-update/jdhello-world-jd_scripts/blob/main/githubAction.md#%E5%85%B3%E4%BA%8E%E8%84%9A%E6%9C%AC%E6%8E%A8%E9%80%81%E9%80%9A%E7%9F%A5%E9%A2%91%E7%8E%87)
