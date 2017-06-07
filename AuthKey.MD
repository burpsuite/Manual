认证密钥介绍
------
`[AUTHKEY]`字段为接口加密数据定位符,使用`OpenSSL RSA4096`加密生成的下载用户唯一权限标识符<br>
无`AUTHKEY`将导致无法请求接口返回`400`错误,`AUTHKEY`包含唯一信息,请求过多将导致`AUTHKEY`加入黑名单<br>
由于加入`AUTHKEY`保护,用户下载的规则文件除自己外其他人将无法使用,极大程度抑制再分发和盗取接口行为<br>
`AUTHKEY`与`IP`等信息绑定,使用`AutoGroup`将导致无法使用,网络请求`Header`可以看到`IP`及`TimeStamp`信息<br>
请将`async.be`认证服务器加入代理列表,所以请务必保证IP一致!
