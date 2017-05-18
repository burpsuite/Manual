高级规则
===========================
CloudGate高级规则可以直接导入使用,非常方便!

规则列表
------
|规则名称|下载地址|
|----|-----|
|Surge|`https://async.be/Rule/JSON/Surge`|
|Shadowrocket|`https://async.be/Rule/JSON/Shadowrocket`|
|A.BIG.T|`https://async.be/Rule/JSON/A.BIG.T`|
|Potatso|`https://async.be/Rule/JSON/Potatso`|
|Cross|`https://async.be/Rule/JSON/Cross`|

配置信息格式
------
使用规则需要知道[配置信息格式](https://github.com/BurpSuite/RuleManual/blob/master/Manual/JSON.MD)<br>
简要概括:通过简单的格式编写配置信息,然后就可以直接导入使用了!<br>

规则列表
------
使用规则需要知道[规则列表](https://github.com/BurpSuite/RuleList/blob/master/README.MD)<br>
简要概括:通过固定语法编写规则列表文件生成不同规则,可以改变规则全部部分所有参数,非常方便<br>
CloudGate支持通过`URL`参数形式切换第三方规则列表,第三方列表不作安全保证!<br>
在`Advanced`规则末尾找到`List`键名对应键值,填入规则列表URL地址即可!<br>
`"Other":{"List":"https://raw.githubusercontent.com/BurpSuite/RuleList/master/Default.json"}`<br>

鉴权令牌
------
使用规则需要知道[TOKEN](https://github.com/BurpSuite/RuleManual/blob/master/Manual/Token.MD)<br>
简要概括:每个下载的规则都包含唯一标识符,目的是为了检测下载规则与请求接口信息是否一致,如果不一致将导致失败!<br>
接口包括:`虾米音乐/优酷视频/百度翻译/Flex3`等,如果不使用上述应用,那么可以忽略这一部分!<br>
当然包含的信息仅用于接口自动鉴权使用,不会用在其他地方也不会收集任何信息!

规则说明
------
CloudGate规则地址可以使用`URL`方式导入,导入时请区分大小写!<br>
CloudGate规则导入地址无需更新!

获取帮助
------
|联系方式|内容信息|
|----|----|
|Twitter|https://twitter.com/@OAuth4|
|Github|https://github.com/BurpSuite|
|Email|service@async.be|
