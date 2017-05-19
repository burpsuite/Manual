鉴权令牌
===========================
`<TOKEN>`字段为接口加密随机值替换定位符,使用OpenSSL RSA4096加密生成的下载用户唯一鉴权标识符<br>
无TOKEN将导致无法请求接口返回400错误,TOKEN包含唯一信息,请求过多将导致TOKEN与IP加入黑名单<br>
由于加入`TOKEN`保护,用户下载的分享规则文件除自己外其他人将无法使用,极大程度抑制再分发和盗取接口行为<br>
由于TOKEN与IP等信息绑定,所以使用`AutoGroup`将导致无法使用,在网络请求`Debugging Cookie`里可以看到IP及时间戳<br>
或者可以尝试将`async.be`和`burpsuite.applinzi.com`鉴权服务器加入代理列表<br>
`TOKEN`由下载服务器`async.be`生成,`TOKEN`由接口服务器`burpsuite.applinzi.com`检测,所以请务必保证IP一致!
