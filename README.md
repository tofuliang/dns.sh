# dns.sh

基于DNSPod用户API实现的纯Shell动态域名客户端，适配多个IP地址。

# Config

复制`dns.json.example`到同一目录下的`dns.json`并根据你的配置修改即可。

执行时直接运行`dns.sh`，支持cron任务。

配置文件格式：
```json
{
	"token":"yourApiToken",
	"domains":{
		"xxxx.xx":[
		    "\@",
			"www",
			"aaa"
		]
	},
	"ips":{
		"ip-chinanet":"ifconfig |grep inet|grep netmask|grep 192|awk '{print $2}'",
		"ip-chinamobile":"ifconfig |grep inet|grep netmask|grep 10|awk '{print $2}'",
		"ip-chinaunicom":"ifconfig |grep inet|grep netmask|grep 12|awk '{print $2}'"
	}
}
```

`token` 为Dnspod生成的APIToken.

`domians` 可以配置多个域名及子域名.

`ips` 可以配置多个,键为ip的备注(对应dnspod上的记录备注),值为获取ip的命令.


# Credit

[jq](https://stedolan.github.io/jq/)

[filedb](https://github.com/josegonzalez/bash-filedb)

Inspired by [ArDNSPod](https://github.com/anrip/ArDNSPod)
