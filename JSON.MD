配置信息格式
===========================
高级规则的配置信息格式,快速使用方法!

配置信息格式说明
------
通过配置信息快速生成含有配置信息规则,配置信息格式包含几乎所有参数,不需要的参数可以选择删除!<br>
注意:通过原始数据导入方式建议不要超过5000个字符,否则可能无法导入,如果过长推荐使用URL方式导入!<br>
支持全部`http/https/socks5/socks5-tls/custom`服务器类型,支持全新`tfo/obfs`特性!<br>
整个配置需要使用JSON格式编写,请按照[JSON标准](http://www.json.cn/wiki.html)编写!<br>
为了确保配置正确性,可以使用[JSON校验](http://www.bejson.com)进行检查正确性!<br>
为了降低字符串数量,可以使用[JSON压缩](http://www.bejson.com/zhuanyi/)进行压缩字符串!<br>
最后使用[Base64编码](http://www1.tc711.com/tool/BASE64.htm)进行编码配置数据!<br>
进行这些步骤之后你会得到Base64数据,你可以将数据放置在`{规则名称}?JSON=`后面导入使用!<br>
或者你可以直接将JSON数据存储为一个文件,然后通过`{规则名称}?JSON={文件URL}`方式导入!<br>


关于配置信息格式
------
|高级规则语法|功能描述|
|----|-----|
|`Author`|使用该配置用户的名字`非必要`|
|`Version`|用于区分不同版本的重要信息`必要`|
|`MITM`|MITM信息,`true`为开启\|`15F5092B`为ca-passphrase信息\|`URL`为ca-p12信息|
|`External`|外部控制器,`true`开启\|`BurpSuite`密码\|`0.0.0.0`默认信息\|`6170`端口|
|`MacOS`|MacOS参数,`true`开启\|`1.2.3.4`监听地址\|`5.6.7.8`socks监听地址\|`3040`服务端口\|`5030`socks服务端口|
|`DNS`|DNS参数,`true`开启\|`8.8.8.8`主DNS\|`8.8.4.4`副DNS,还可以继续无限增加|
|`EnhancedMode`|等价`enhanced-mode-by-rule`参数,`TUN`增强模式|
|`ExcludeHost`|等价`exclude-simple-hostnames`参数|
|`WIFIAccess`|等价`allow-wifi-access`参数,允许`WIFI`访问|
|`Replica`|等价`replica`参数,抓取流量`默认关闭`|
|`URLREGEX`|等价`URL-REGEX`参数,`2.x`版本以上支持,以下会报错`可以关闭`|
|`IPCIDR6`|等价`IP-CIDR6`参数,`2.x`版本以上支持,以下会报错`可以关闭`|
|`USERAGENT`|等价`USER-AGENT`参数,`2.x`版本以上支持,以下会报错`可以关闭`|
|`IPV6`|IPV6支持|
|`Rule`|选择代理列表高级或基本,开启选择基本规则,不开启选择高级规则`规则数量变化`|
|`SERVER`|不同的应用格式不同,请参考Info格式示例,Surge需要将模块地址替换为[Module]|
|`Module`|`custom`模块,`shadowsocks`必须添加,只有填写了`[Module]`才会输出`Other->Module`信息|
|`Group`|等价与规则组,规则组包含代理名称,可以放置无限个代理,可以为`AutoGroup`|
|`Apple`|Apple规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`Apple`|`Apple`规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`Proxy`|`Proxy`规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`KEYWORD`|`KEYWORD`规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`URLREGEX`|`URLREGEX`规则块的后缀,可以填写`Group`组的名称,可以随意自定义`只有启用才会生效`|
|`USERAGENT`|`USERAGENT`规则块的后缀,可以填写`Group`组的名称,可以随意自定义`只有启用才会生效`|
|`IPCIDR6`|`IPCIDR6`规则块的后缀,可以填写`Group`组的名称,可以随意自定义`只有启用才会生效`|
|`IPCIDR`|`IPCIDR`规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`Other`|`Other`规则块的后缀,可以填写`Group`组的名称,可以随意自定义|
|`Module`|就是上面提到的`Module`|
|`List`|规则列表参数,规则列表参数必须存在缺少无法生成规则|
|`Merge`|规则合并参数,可有可无,如果你需要除了规则列表外自定义一些规则则需要填写|

Merge介绍
------
如果你需要增加使用规则列表,以往都需要你去副本一下规则列表,添加Merge功能后你可以<br>
很简单的增加你需要的规则,Merge编写格式同规则列表格式,非常简单,同时也是实时同步<br>
使用递归方式将Merge信息追加在规则列表后面,所以优先级低于规则列表,不支持移除规则列表规则

Info格式示例
------
如果你需要使用除`Surge`之外的`Advanced`规则,那么你需要了解[Info格式](Info.MD)!<br>
简要概括:通过[规则名称]|标记符进行区分规则所属服务器信息,非当前规则服务器将会跳过!

配置信息格式示例
------
<pre>
{
    "Configuration": {
        "Author": "BurpSuite",
        "Version": "6.0"
    },
    "Arguments": {
        "MITM": "true,15F5092B,https://raw.githubusercontent.com/BurpSuite/RuleList/master/Example/MITM",
        "External": "true,BurpSuite@0.0.0.0:6170",
        "MacOS": "true,1.2.3.4,5.6.7.8,3040,5030",
        "DNS": "true,8.8.8.8,8.8.4.4"
    },
    "General": {
        "EnhancedMode": true,
        "ExcludeHost": true,
        "WIFIAccess": true,
        "Replica": false,
        "URLREGEX": true,
        "IPCIDR6": true,
        "USERAGENT": true,
        "IPV6": false,
        "Rule": false
    },
    "Info": {
        "SERVER": [
            "[Surge]|SERVERNama = http,1.2.3.1,8081,User,Password1",
            "[Surge]|SERVERNamb = https,1.2.3.2,8082,User,Password2,skip-cert-verify=true",
            "[Surge]|SERVERNamc = socks5,1.2.3.3,8083,User,Password3",
            "[Surge]|SERVERNamd = socks5-tls,1.2.3.4,8084,User,Password4,skip-cert-verify=true",
            "[Surge]|SERVERName = custom,1.2.3.5,8085,chacha20,Password5,[Module]",
            "[Surge]|SERVERNamf = custom,1.2.3.6,8086,chacha20,Password5,[Module],obfs=http,obfs-host=www.google.com",
            "[Surge]|SERVERNamg = custom,1.2.3.6,8086,chacha20,Password5,[Module],tfo=true"
        ],
        "Group": [
            "[Surge]|Proxya = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd,SERVERName",
            "[Surge]|Proxyb = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd",
            "[Surge]|Proxyc = select,SERVERNama,SERVERNamb,SERVERName",
            "[Surge]|Proxyd = select,SERVERNamd,SERVERName",
            "[Surge]|Autoxy = url-test,SERVERNama, SERVERNamb, url = http://www.gstatic.com/generate_204, interval = 600, tolerance = 200, timeout = 5"
        ]
    },
    "SUFFIX": {
        "Apple": "DIRECT",
        "Proxy": "Autoxy",
        "KEYWORD": "Proxyb",
        "URLREGEX": "Proxyb",
        "USERAGENT": "Proxya",
        "IPCIDR6": "Proxyc",
        "IPCIDR": "Proxyc",
        "Other": "Autoxy"
    },
    "Other": {
        "Module": "https://raw.githubusercontent.com/BurpSuite/RuleList/master/Module/Module",
        "List": "https://raw.githubusercontent.com/BurpSuite/RuleList/master/Default.json",
        "Merge": "https://raw.githubusercontent.com/CloudGateRules/RuleList/master/Example/Merge.json"
    }
}
</pre>

配置信息压缩示例
------
<pre>
{"Configuration":{"Author":"BurpSuite","Version":"6.0"},"Arguments":{"MITM":"true,15F5092B,https://raw.githubusercontent.com/BurpSuite/RuleList/master/Example/MITM","External":"true,BurpSuite@0.0.0.0:6170","MacOS":"true,1.2.3.4,5.6.7.8,3040,5030","DNS":"true,8.8.8.8,8.8.4.4"},"General":{"EnhancedMode":true,"ExcludeHost":true,"WIFIAccess":true,"Replica":false,"URLREGEX":true,"IPCIDR6":true,"USERAGENT":true,"IPV6":false,"Rule":false},"Info":{"SERVER":["[Surge]|SERVERNama = http,1.2.3.1,8081,User,Password1","[Surge]|SERVERNamb = https,1.2.3.2,8082,User,Password2,skip-cert-verify=true","[Surge]|SERVERNamc = socks5,1.2.3.3,8083,User,Password3","[Surge]|SERVERNamd = socks5-tls,1.2.3.4,8084,User,Password4,skip-cert-verify=true","[Surge]|SERVERName = custom,1.2.3.5,8085,chacha20,Password5,[Module]","[Surge]|SERVERNamf = custom,1.2.3.6,8086,chacha20,Password5,[Module],obfs=http,obfs-host=www.google.com","[Surge]|SERVERNamg = custom,1.2.3.6,8086,chacha20,Password5,[Module],tfo=true"],"Group":["[Surge]|Proxya = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd,SERVERName","[Surge]|Proxyb = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd","[Surge]|Proxyc = select,SERVERNama,SERVERNamb,SERVERName","[Surge]|Proxyd = select,SERVERNamd,SERVERName","[Surge]|Autoxy = url-test,SERVERNama, SERVERNamb, url = http://www.gstatic.com/generate_204, interval = 600, tolerance = 200, timeout = 5"]},"SUFFIX":{"Apple":"DIRECT","Proxy":"Autoxy","KEYWORD":"Proxyb","URLREGEX":"Proxyb","USERAGENT":"Proxya","IPCIDR6":"Proxyc","IPCIDR":"Proxyc","Other":"Autoxy"},"Other":{"Module":"https://raw.githubusercontent.com/BurpSuite/RuleList/master/Module/Module","List":"https://raw.githubusercontent.com/BurpSuite/RuleList/master/Default.json","Merge":"https://raw.githubusercontent.com/CloudGateRules/RuleList/master/Example/Merge.json"}}
</pre>

配置信息编码示例
------
<pre>
eyJDb25maWd1cmF0aW9uIjp7IkF1dGhvciI6IkJ1cnBTdWl0ZSIsIlZlcnNpb24iOiI2LjAifSwiQXJndW1lbnRzIjp7Ik1JVE0iOiJ0cnVlLDE1RjUwOTJCLGh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL0V4YW1wbGUvTUlUTSIsIkV4dGVybmFsIjoidHJ1ZSxCdXJwU3VpdGVAMC4wLjAuMDo2MTcwIiwiTWFjT1MiOiJ0cnVlLDEuMi4zLjQsNS42LjcuOCwzMDQwLDUwMzAiLCJETlMiOiJ0cnVlLDguOC44LjgsOC44LjQuNCJ9LCJHZW5lcmFsIjp7IkVuaGFuY2VkTW9kZSI6dHJ1ZSwiRXhjbHVkZUhvc3QiOnRydWUsIldJRklBY2Nlc3MiOnRydWUsIlJlcGxpY2EiOmZhbHNlLCJVUkxSRUdFWCI6dHJ1ZSwiSVBDSURSNiI6dHJ1ZSwiVVNFUkFHRU5UIjp0cnVlLCJJUFY2IjpmYWxzZSwiUnVsZSI6ZmFsc2V9LCJJbmZvIjp7IlNFUlZFUiI6WyJbU3VyZ2VdfFNFUlZFUk5hbWEgPSBodHRwLDEuMi4zLjEsODA4MSxVc2VyLFBhc3N3b3JkMSIsIltTdXJnZV18U0VSVkVSTmFtYiA9IGh0dHBzLDEuMi4zLjIsODA4MixVc2VyLFBhc3N3b3JkMixza2lwLWNlcnQtdmVyaWZ5PXRydWUiLCJbU3VyZ2VdfFNFUlZFUk5hbWMgPSBzb2NrczUsMS4yLjMuMyw4MDgzLFVzZXIsUGFzc3dvcmQzIiwiW1N1cmdlXXxTRVJWRVJOYW1kID0gc29ja3M1LXRscywxLjIuMy40LDgwODQsVXNlcixQYXNzd29yZDQsc2tpcC1jZXJ0LXZlcmlmeT10cnVlIiwiW1N1cmdlXXxTRVJWRVJOYW1lID0gY3VzdG9tLDEuMi4zLjUsODA4NSxjaGFjaGEyMCxQYXNzd29yZDUsW01vZHVsZV0iLCJbU3VyZ2VdfFNFUlZFUk5hbWYgPSBjdXN0b20sMS4yLjMuNiw4MDg2LGNoYWNoYTIwLFBhc3N3b3JkNSxbTW9kdWxlXSxvYmZzPWh0dHAsb2Jmcy1ob3N0PXd3dy5nb29nbGUuY29tIiwiW1N1cmdlXXxTRVJWRVJOYW1nID0gY3VzdG9tLDEuMi4zLjYsODA4NixjaGFjaGEyMCxQYXNzd29yZDUsW01vZHVsZV0sdGZvPXRydWUiXSwiR3JvdXAiOlsiW1N1cmdlXXxQcm94eWEgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWIgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCIsIltTdXJnZV18UHJveHljID0gc2VsZWN0LFNFUlZFUk5hbWEsU0VSVkVSTmFtYixTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWQgPSBzZWxlY3QsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxBdXRveHkgPSB1cmwtdGVzdCxTRVJWRVJOYW1hLCBTRVJWRVJOYW1iLCB1cmwgPSBodHRwOi8vd3d3LmdzdGF0aWMuY29tL2dlbmVyYXRlXzIwNCwgaW50ZXJ2YWwgPSA2MDAsIHRvbGVyYW5jZSA9IDIwMCwgdGltZW91dCA9IDUiXX0sIlNVRkZJWCI6eyJBcHBsZSI6IkRJUkVDVCIsIlByb3h5IjoiQXV0b3h5IiwiS0VZV09SRCI6IlByb3h5YiIsIlVSTFJFR0VYIjoiUHJveHliIiwiVVNFUkFHRU5UIjoiUHJveHlhIiwiSVBDSURSNiI6IlByb3h5YyIsIklQQ0lEUiI6IlByb3h5YyIsIk90aGVyIjoiQXV0b3h5In0sIk90aGVyIjp7Ik1vZHVsZSI6Imh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL01vZHVsZS9Nb2R1bGUiLCJMaXN0IjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL0J1cnBTdWl0ZS9SdWxlTGlzdC9tYXN0ZXIvRGVmYXVsdC5qc29uIn19
</pre>

参数配置示例
------
<pre>
https://async.be/Rule/JSON/Surge?JSON=eyJDb25maWd1cmF0aW9uIjp7IkF1dGhvciI6IkJ1cnBTdWl0ZSIsIlZlcnNpb24iOiI2LjAifSwiQXJndW1lbnRzIjp7Ik1JVE0iOiJ0cnVlLDE1RjUwOTJCLGh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL0V4YW1wbGUvTUlUTSIsIkV4dGVybmFsIjoidHJ1ZSxCdXJwU3VpdGVAMC4wLjAuMDo2MTcwIiwiTWFjT1MiOiJ0cnVlLDEuMi4zLjQsNS42LjcuOCwzMDQwLDUwMzAiLCJETlMiOiJ0cnVlLDguOC44LjgsOC44LjQuNCJ9LCJHZW5lcmFsIjp7IkVuaGFuY2VkTW9kZSI6dHJ1ZSwiRXhjbHVkZUhvc3QiOnRydWUsIldJRklBY2Nlc3MiOnRydWUsIlJlcGxpY2EiOmZhbHNlLCJVUkxSRUdFWCI6dHJ1ZSwiSVBDSURSNiI6dHJ1ZSwiVVNFUkFHRU5UIjp0cnVlLCJJUFY2IjpmYWxzZSwiUnVsZSI6ZmFsc2V9LCJJbmZvIjp7IlNFUlZFUiI6WyJbU3VyZ2VdfFNFUlZFUk5hbWEgPSBodHRwLDEuMi4zLjEsODA4MSxVc2VyLFBhc3N3b3JkMSIsIltTdXJnZV18U0VSVkVSTmFtYiA9IGh0dHBzLDEuMi4zLjIsODA4MixVc2VyLFBhc3N3b3JkMixza2lwLWNlcnQtdmVyaWZ5PXRydWUiLCJbU3VyZ2VdfFNFUlZFUk5hbWMgPSBzb2NrczUsMS4yLjMuMyw4MDgzLFVzZXIsUGFzc3dvcmQzIiwiW1N1cmdlXXxTRVJWRVJOYW1kID0gc29ja3M1LXRscywxLjIuMy40LDgwODQsVXNlcixQYXNzd29yZDQsc2tpcC1jZXJ0LXZlcmlmeT10cnVlIiwiW1N1cmdlXXxTRVJWRVJOYW1lID0gY3VzdG9tLDEuMi4zLjUsODA4NSxjaGFjaGEyMCxQYXNzd29yZDUsW01vZHVsZV0iLCJbU3VyZ2VdfFNFUlZFUk5hbWYgPSBjdXN0b20sMS4yLjMuNiw4MDg2LGNoYWNoYTIwLFBhc3N3b3JkNSxbTW9kdWxlXSxvYmZzPWh0dHAsb2Jmcy1ob3N0PXd3dy5nb29nbGUuY29tIiwiW1N1cmdlXXxTRVJWRVJOYW1nID0gY3VzdG9tLDEuMi4zLjYsODA4NixjaGFjaGEyMCxQYXNzd29yZDUsW01vZHVsZV0sdGZvPXRydWUiXSwiR3JvdXAiOlsiW1N1cmdlXXxQcm94eWEgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWIgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCIsIltTdXJnZV18UHJveHljID0gc2VsZWN0LFNFUlZFUk5hbWEsU0VSVkVSTmFtYixTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWQgPSBzZWxlY3QsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxBdXRveHkgPSB1cmwtdGVzdCxTRVJWRVJOYW1hLCBTRVJWRVJOYW1iLCB1cmwgPSBodHRwOi8vd3d3LmdzdGF0aWMuY29tL2dlbmVyYXRlXzIwNCwgaW50ZXJ2YWwgPSA2MDAsIHRvbGVyYW5jZSA9IDIwMCwgdGltZW91dCA9IDUiXX0sIlNVRkZJWCI6eyJBcHBsZSI6IkRJUkVDVCIsIlByb3h5IjoiQXV0b3h5IiwiS0VZV09SRCI6IlByb3h5YiIsIlVSTFJFR0VYIjoiUHJveHliIiwiVVNFUkFHRU5UIjoiUHJveHlhIiwiSVBDSURSNiI6IlByb3h5YyIsIklQQ0lEUiI6IlByb3h5YyIsIk90aGVyIjoiQXV0b3h5In0sIk90aGVyIjp7Ik1vZHVsZSI6Imh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL01vZHVsZS9Nb2R1bGUiLCJMaXN0IjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL0J1cnBTdWl0ZS9SdWxlTGlzdC9tYXN0ZXIvRGVmYXVsdC5qc29uIiwiTWVyZ2UiOiJodHRwczovL3Jhdy5naXRodWJ1c2VyY29udGVudC5jb20vQ2xvdWRHYXRlUnVsZXMvUnVsZUxpc3QvbWFzdGVyL0V4YW1wbGUvTWVyZ2UuanNvbiJ9fQ==
</pre>

网址配置示例
------
<pre>
https://async.be/Rule/JSON/Surge?JSON=https://raw.githubusercontent.com/BurpSuite/RuleList/master/Example/Example.json
</pre>
