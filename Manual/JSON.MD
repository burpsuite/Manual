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
|`EnhancedMode`|等价`enhanced-mode-by-rule`参数,TUN增强模式|
|`ExcludeHost`|等价`exclude-simple-hostnames`参数|
|`WIFIAccess`|等价`allow-wifi-access`参数,允许WIFI访问|
|`Replica`|等价`replica`参数,抓取流量`默认关闭`|
|`URLREGEX`|等价`URL-REGEX`参数,2.x版本以上支持,以下会报错`可以关闭`|
|`IPCIDR6`|等价`IP-CIDR6`参数,2.x版本以上支持,以下会报错`可以关闭`|
|`USERAGENT`|等价`USER-AGENT`参数,2.x版本以上支持,以下会报错`可以关闭`|
|`IPV6`|IPV6支持|
|`Rule`|选择代理列表高级或基本,开启选择基本规则,不开启选择高级规则`规则数量变化`|
|`SERVER`|第一个参数为代理名称,第二个为类型,第三个为地址,第四个为加密方式或用户名,第五个为密码|
|`Module`|`custom`模块,`shadowsocks`必须添加,只有填写了`[Module]`才会输出`Other->Module`信息|
|`Group`|等价与规则组,规则组包含代理名称,可以放置无限个代理,可以为AutoGroup|
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
        "Rule": true
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
        "Apple": "Proxyd",
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
        "List": "https://raw.githubusercontent.com/BurpSuite/RuleList/master/Default.json"
    }
}
</pre>

配置信息压缩示例
------
<pre>
{"Configuration":{"Author":"BurpSuite","Version":"6.0"},"Arguments":{"MITM":"true,15F5092B,https://raw.githubusercontent.com/BurpSuite/RuleList/master/Example/MITM","External":"true,BurpSuite@0.0.0.0:6170","MacOS":"true,1.2.3.4,5.6.7.8,3040,5030","DNS":"true,8.8.8.8,8.8.4.4"},"General":{"EnhancedMode":true,"ExcludeHost":true,"WIFIAccess":true,"Replica":false,"URLREGEX":true,"IPCIDR6":true,"USERAGENT":true,"IPV6":false,"Rule":true},"Info":{"SERVER":["[Surge]|SERVERNama = http,1.2.3.1,8081,User,Password1","[Surge]|SERVERNamb = https,1.2.3.2,8082,User,Password2,skip-cert-verify=true","[Surge]|SERVERNamc = socks5,1.2.3.3,8083,User,Password3","[Surge]|SERVERNamd = socks5-tls,1.2.3.4,8084,User,Password4,skip-cert-verify=true","[Surge]|SERVERName = custom,1.2.3.5,8085,chacha20,Password5,[Module]","[Surge]|SERVERNamf = custom,1.2.3.6,8086,chacha20,Password5,[Module],obfs=http,obfs-host=www.google.com","[Surge]|SERVERNamg = custom,1.2.3.6,8086,chacha20,Password5,[Module],tfo=true"],"Group":["[Surge]|Proxya = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd,SERVERName","[Surge]|Proxyb = select,SERVERNama,SERVERNamb,SERVERNamc,SERVERNamd","[Surge]|Proxyc = select,SERVERNama,SERVERNamb,SERVERName","[Surge]|Proxyd = select,SERVERNamd,SERVERName","[Surge]|Autoxy = url-test,SERVERNama, SERVERNamb, url = http://www.gstatic.com/generate_204, interval = 600, tolerance = 200, timeout = 5"]},"SUFFIX":{"Apple":"Proxyd","Proxy":"Autoxy","KEYWORD":"Proxyb","URLREGEX":"Proxyb","USERAGENT":"Proxya","IPCIDR6":"Proxyc","IPCIDR":"Proxyc","Other":"Autoxy"},"Other":{"Module":"https://raw.githubusercontent.com/BurpSuite/RuleList/master/Module/Module","List":"https://raw.githubusercontent.com/BurpSuite/RuleList/master/Default.json"}}
</pre>

配置信息编码示例
------
<pre>
eyJDb25maWd1cmF0aW9uIjp7IkF1dGhvciI6IkJ1cnBTdWl0ZSIsIlZlcnNpb24iOiI1LjAifSwiQXJndW1lbnRzIjp7Ik1JVE0iOiJ0cnVlLDE1RjUwOTJCLGh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL0V4YW1wbGUvTUlUTSIsIkV4dGVybmFsIjoidHJ1ZSxCdXJwU3VpdGVAMC4wLjAuMDo2MTcwIiwiTWFjT1MiOiJ0cnVlLDEuMi4zLjQsNS42LjcuOCwzMDQwLDUwMzAiLCJETlMiOiJ0cnVlLDguOC44LjgsOC44LjQuNCJ9LCJHZW5lcmFsIjp7IkVuaGFuY2VkTW9kZSI6dHJ1ZSwiRXhjbHVkZUhvc3QiOnRydWUsIldJRklBY2Nlc3MiOnRydWUsIlJlcGxpY2EiOmZhbHNlLCJVUkxSRUdFWCI6dHJ1ZSwiSVBDSURSNiI6dHJ1ZSwiVVNFUkFHRU5UIjp0cnVlLCJJUFY2IjpmYWxzZSwiUnVsZSI6dHJ1ZX0sIkluZm8iOnsiU0VSVkVSIjpbIltTdXJnZV18U0VSVkVSTmFtYSxodHRwLDEuMi4zLjEsODA4MSxVc2VyLFBhc3N3b3JkMSIsIltTdXJnZV18U0VSVkVSTmFtYixodHRwcywxLjIuMy4yLDgwODIsVXNlcixQYXNzd29yZDIsc2tpcC1jZXJ0LXZlcmlmeT10cnVlIiwiW1N1cmdlXXxTRVJWRVJOYW1jLHNvY2tzNSwxLjIuMy4zLDgwODMsVXNlcixQYXNzd29yZDMiLCJbU3VyZ2VdfFNFUlZFUk5hbWQsc29ja3M1LXRscywxLjIuMy40LDgwODQsVXNlcixQYXNzd29yZDQsc2tpcC1jZXJ0LXZlcmlmeT10cnVlIiwiW1N1cmdlXXxTRVJWRVJOYW1lLGN1c3RvbSwxLjIuMy41LDgwODUsY2hhY2hhMjAsUGFzc3dvcmQ1LFtNb2R1bGVdIiwiW1N1cmdlXXxTRVJWRVJOYW1mLGN1c3RvbSwxLjIuMy42LDgwODYsY2hhY2hhMjAsUGFzc3dvcmQ1LFtNb2R1bGVdLG9iZnM9aHR0cCxvYmZzLWhvc3Q9d3d3Lmdvb2dsZS5jb20iLCJbU3VyZ2VdfFNFUlZFUk5hbWcsY3VzdG9tLDEuMi4zLjYsODA4NixjaGFjaGEyMCxQYXNzd29yZDUsW01vZHVsZV0sdGZvPXRydWUiXSwiR3JvdXAiOlsiW1N1cmdlXXxQcm94eWEgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWIgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWMsU0VSVkVSTmFtZCIsIltTdXJnZV18UHJveHljID0gc2VsZWN0LFNFUlZFUk5hbWEsU0VSVkVSTmFtYixTRVJWRVJOYW1lIiwiW1N1cmdlXXxQcm94eWQgPSBzZWxlY3QsU0VSVkVSTmFtZCxTRVJWRVJOYW1lIiwiW1N1cmdlXXxBdXRveHkgPSB1cmwtdGVzdCxTRVJWRVJOYW1hLCBTRVJWRVJOYW1iLCB1cmwgPSBodHRwOi8vd3d3LmdzdGF0aWMuY29tL2dlbmVyYXRlXzIwNCwgaW50ZXJ2YWwgPSA2MDAsIHRvbGVyYW5jZSA9IDIwMCwgdGltZW91dCA9IDUiXX0sIlNVRkZJWCI6eyJBcHBsZSI6IlByb3h5ZCIsIlByb3h5IjoiQXV0b3h5IiwiS0VZV09SRCI6IlByb3h5YiIsIlVSTFJFR0VYIjoiUHJveHliIiwiVVNFUkFHRU5UIjoiUHJveHlhIiwiSVBDSURSNiI6IlByb3h5YyIsIklQQ0lEUiI6IlByb3h5YyIsIk90aGVyIjoiQXV0b3h5In0sIk90aGVyIjp7Ik1vZHVsZSI6Imh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL01vZHVsZS9Nb2R1bGUiLCJMaXN0IjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL0J1cnBTdWl0ZS9SdWxlTGlzdC9tYXN0ZXIvRGVmYXVsdC5qc29uIn19
</pre>

参数配置示例
------
<pre>
https://async.be/Rule/JSON/Surge?JSON=eyJDb25maWd1cmF0aW9uIjp7IkF1dGhvciI6IkJ1cnBTdWl0ZSIsIlZlcnNpb24iOiI2LjAifSwiQXJndW1lbnRzIjp7Ik1JVE0iOiJ0cnVlLDE1RjUwOTJCLGh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9CdXJwU3VpdGUvUnVsZUxpc3QvbWFzdGVyL0V4YW1wbGUvTUlUTSIsIkV4dGVybmFsIjoidHJ1ZSxCdXJwU3VpdGVAMC4wLjAuMDo2MTcwIiwiTWFjT1MiOiJ0cnVlLDEuMi4zLjQsNS42LjcuOCwzMDQwLDUwMzAiLCJETlMiOiJ0cnVlLDguOC44LjgsOC44LjQuNCJ9LCJHZW5lcmFsIjp7IkVuaGFuY2VkTW9kZSI6dHJ1ZSwiRXhjbHVkZUhvc3QiOnRydWUsIldJRklBY2Nlc3MiOnRydWUsIlJlcGxpY2EiOmZhbHNlLCJVUkxSRUdFWCI6dHJ1ZSwiSVBDSURSNiI6dHJ1ZSwiVVNFUkFHRU5UIjp0cnVlLCJJUFY2IjpmYWxzZSwiUnVsZSI6dHJ1ZX0sIkluZm8iOnsiU0VSVkVSIjpbIltTdXJnZV18U0VSVkVSTmFtYSA9IGh0dHAsMS4yLjMuMSw4MDgxLFVzZXIsUGFzc3dvcmQxIiwiW1N1cmdlXXxTRVJWRVJOYW1iID0gaHR0cHMsMS4yLjMuMiw4MDgyLFVzZXIsUGFzc3dvcmQyLHNraXAtY2VydC12ZXJpZnk9dHJ1ZSIsIltTdXJnZV18U0VSVkVSTmFtYyA9IHNvY2tzNSwxLjIuMy4zLDgwODMsVXNlcixQYXNzd29yZDMiLCJbU3VyZ2VdfFNFUlZFUk5hbWQgPSBzb2NrczUtdGxzLDEuMi4zLjQsODA4NCxVc2VyLFBhc3N3b3JkNCxza2lwLWNlcnQtdmVyaWZ5PXRydWUiLCJbU3VyZ2VdfFNFUlZFUk5hbWUgPSBjdXN0b20sMS4yLjMuNSw4MDg1LGNoYWNoYTIwLFBhc3N3b3JkNSxbTW9kdWxlXSIsIltTdXJnZV18U0VSVkVSTmFtZiA9IGN1c3RvbSwxLjIuMy42LDgwODYsY2hhY2hhMjAsUGFzc3dvcmQ1LFtNb2R1bGVdLG9iZnM9aHR0cCxvYmZzLWhvc3Q9d3d3Lmdvb2dsZS5jb20iLCJbU3VyZ2VdfFNFUlZFUk5hbWcgPSBjdXN0b20sMS4yLjMuNiw4MDg2LGNoYWNoYTIwLFBhc3N3b3JkNSxbTW9kdWxlXSx0Zm89dHJ1ZSJdLCJHcm91cCI6WyJbU3VyZ2VdfFByb3h5YSA9IHNlbGVjdCxTRVJWRVJOYW1hLFNFUlZFUk5hbWIsU0VSVkVSTmFtYyxTRVJWRVJOYW1kLFNFUlZFUk5hbWUiLCJbU3VyZ2VdfFByb3h5YiA9IHNlbGVjdCxTRVJWRVJOYW1hLFNFUlZFUk5hbWIsU0VSVkVSTmFtYyxTRVJWRVJOYW1kIiwiW1N1cmdlXXxQcm94eWMgPSBzZWxlY3QsU0VSVkVSTmFtYSxTRVJWRVJOYW1iLFNFUlZFUk5hbWUiLCJbU3VyZ2VdfFByb3h5ZCA9IHNlbGVjdCxTRVJWRVJOYW1kLFNFUlZFUk5hbWUiLCJbU3VyZ2VdfEF1dG94eSA9IHVybC10ZXN0LFNFUlZFUk5hbWEsIFNFUlZFUk5hbWIsIHVybCA9IGh0dHA6Ly93d3cuZ3N0YXRpYy5jb20vZ2VuZXJhdGVfMjA0LCBpbnRlcnZhbCA9IDYwMCwgdG9sZXJhbmNlID0gMjAwLCB0aW1lb3V0ID0gNSJdfSwiU1VGRklYIjp7IkFwcGxlIjoiUHJveHlkIiwiUHJveHkiOiJBdXRveHkiLCJLRVlXT1JEIjoiUHJveHliIiwiVVJMUkVHRVgiOiJQcm94eWIiLCJVU0VSQUdFTlQiOiJQcm94eWEiLCJJUENJRFI2IjoiUHJveHljIiwiSVBDSURSIjoiUHJveHljIiwiT3RoZXIiOiJBdXRveHkifSwiT3RoZXIiOnsiTW9kdWxlIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL0J1cnBTdWl0ZS9SdWxlTGlzdC9tYXN0ZXIvTW9kdWxlL01vZHVsZSIsIkxpc3QiOiJodHRwczovL3Jhdy5naXRodWJ1c2VyY29udGVudC5jb20vQnVycFN1aXRlL1J1bGVMaXN0L21hc3Rlci9EZWZhdWx0Lmpzb24ifX0=
</pre>

网址配置示例
------
<pre>
https://async.be/Rule/JSON/Surge?JSON=https://raw.githubusercontent.com/BurpSuite/RuleList/master/Example/Example.json
</pre>
