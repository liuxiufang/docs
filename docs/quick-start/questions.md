---
title: 常见问题
---

# 常见问题
* 在出现各种问题前（如注解失效...），我们推荐您先阅读 [hyperf.常见问题](https://hyperf.wiki/2.0/#/zh-cn/quick-start/questions)
* 下面列出的常见问题未能解决您的问题，您可以搜索我们`git仓库`的`issue`，或者提交`issue`。
* 如果您是我们的商业授权客户，请您通过[交流方式](/introduction/communication)联系我们，我们将拉您进入技术讨论群，以优先解决您的棘手问题

## 会话内容未拉取
* 请检查当时聊天对象是否购买并设置了微信`会话内容`存档服务
* 请检查微信后台的`会话内容`的`版本号`是否与`mochat`后台配置的`版本号`一致。(微信后台每重置一次公钥，都会自动升级一个版本)
* 请检查服务器的IP地址，是否在微信后台`会话内容`配置页面的白名单内。查看服务实例的IP地址可用`curl https://www.cip.cc`命令