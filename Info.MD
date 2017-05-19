Info格式
------
### Surge
```
    "Info": {
        "SERVER": [
            "[Surge]|SERVERA,http,1.2.3.1,8081,User,Password1",
            "[Surge]|SERVERB,https,1.2.3.2,8082,User,Password2,skip-cert-verify=true",
            "[Surge]|SERVERC,socks5,1.2.3.3,8083,User,Password3",
            "[Surge]|SERVERD,socks5-tls,1.2.3.4,8084,User,Password4,skip-cert-verify=true",
            "[Surge]|SERVERE,custom,1.2.3.5,8085,chacha20,Password5,[Module]",
            "[Surge]|SERVERF,custom,example.com,8085,aes-256-cfb,Password,[Module]",
            "[Surge]|SERVERG,custom,1.2.3.6,8086,chacha20,Password5,[Module],obfs=http,obfs-host=www.google.com",
            "[Surge]|SERVERH,custom,1.2.3.6,8086,chacha20,Password5,[Module],tfo=true"
        ],
        "Group": [
            "[Surge]|ProxyA = select,SERVERA,SERVERB,SERVERC,SERVERD,SERVERE",
            "[Surge]|ProxyB = select,SERVERA,SERVERB,SERVERC,SERVERD",
            "[Surge]|ProxyC = select,SERVERA,SERVERB,SERVERE",
            "[Surge]|ProxyD = select,SERVERD,SERVERE",
            "[Surge]|Autoxy = url-test,SERVERA,SERVERB,url = http://www.gstatic.com/generate_204, interval = 600, tolerance = 200, timeout = 5"
        ]
    }
```
### Potatso
```
    "Info": {
        "SERVER": [
            "[Potatso]|SERVERA,SS,1.2.3.5,8085,chacha20,Password",
            "[Potatso]|SERVERB,SS,example.com,8085,aes-256-cfb,Password",
        ],
        "Group": [
        ]
    }
```
### Shadowrocket
```
不需要配置
```
### Potatso2
```
    "Info": {
        "SERVER": [
            [Potatso2]|[PROXY.hk],type = \"SHADOWSOCKS\",host = \"ss.example.com\",port = 8388,encryption = \"aes-256-cfb\",password = \"DO NOT EXPOSE IT TO OTHERS\",remark = \"HK Proxy\",
            [Potatso2]|[PROXY.us_ssr],type = \"SHADOWSOCKSR\",host = \"ssr.example.com\",port = 8388,encryption = \"aes-256-cfb\",password = \"DO NOT EXPOSE IT TO OTHERS\",protocol = \"auth_aes128_md5\",protocolParam = \"64#123:user\",obfs = \"tls1.2_ticket_auth\",obfsParam = \"cloudflare.com\",remark = \"HK Proxy\",
            [Potatso2]|[PROXY.jp],type = \"SOCKS5\",host = \"socks5.example.com\",port = 8888,user = \"testuser\",password = \"DO NOT EXPOSE IT TO OTHERS\",remark = \"HK Proxy\"
        ],
        "Group": [
        ]
    }
```
### A.BIG.T
```
    "Info": {
        "SERVER": [
            "[A.BIG.T]|SERVERA,http,1.2.3.1,8081,User,Password1",
            "[A.BIG.T]|SERVERB,https,1.2.3.2,8082,User,Password2,skip-cert-verify=true",
            "[A.BIG.T]|SERVERC,socks5,1.2.3.3,8083,User,Password3",
            "[A.BIG.T]|SERVERD,socks5-tls,1.2.3.4,8084,User,Password4,skip-cert-verify=true",
            "[A.BIG.T]|SERVERE,custom,1.2.3.5,8085,chacha20,Password5",
            "[A.BIG.T]|SERVERF,custom,example.com,8085,aes-256-cfb,Password",
            "[A.BIG.T]|SERVERG,custom,1.2.3.6,8086,chacha20,Password5",
            "[A.BIG.T]|SERVERH,custom,1.2.3.6,8086,chacha20,Password5"
        ],
        "Group": [
            "[Surge]|ProxyA = select,SERVERA,SERVERB,SERVERC,SERVERD,SERVERE",
            "[Surge]|ProxyB = select,SERVERA,SERVERB,SERVERC,SERVERD",
            "[Surge]|ProxyC = select,SERVERA,SERVERB,SERVERE",
            "[Surge]|ProxyD = select,SERVERD,SERVERE",
            "[Surge]|Autoxy = url-test,SERVERA,SERVERB,url = http://www.gstatic.com/generate_204, interval = 600, tolerance = 200, timeout = 5"
        ]
    }
```
### Cross
```
    "Info": {
        "SERVER": [
            "[Cross]|SERVER,172.0.0.1,80, aes-256-cfb,\"Password\",upstream-proxy=false,upstream-proxy-auth=false,obfs-http=false"
        ],
        "Group": [
            "[Cross]|Proxy = ssid, default = SERVER, cellular = SERVER, \"WiFi_HOME\" = DIRECT, \"WiFi_WORK\" = SERVER, \"WiFi_Restaurant\" = SERVER"
        ]
    }
```
