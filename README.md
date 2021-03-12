# V2Ray4Heroku

## 概述
用于在 [Heroku](https://www.heroku.com/) 上部署 [V2Ray](https://www.v2fly.org/)

## 部署
[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https%3A%2F%2Fgithub.com%2Flyz7805%2Fv2ray4heroku)

## 环境变量
### UUID
供用户连接的 UUID，可默认，也可通过 <http://www.uuid.online/> 或 <https://www.uuidgenerator.net/> 生成

## 客户端连接
* 协议（protocol） - vmess
* 地址（address） - [app].herokuapp.com
* 端口（port） - 443
* 用户ID（id） - [UUID]
* 额外ID（alterId） - 64
* 传输协议（network） - ws
* 底层传输安全（tls) - tls

```json
{
  "inbounds": [],
  "outbounds": [
    {
      "tag": "proxy",
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "[app].herokuapp.com",
            "port": 443,
            "users": [
              {
                "id": "[UUID]",
                "alterId": 64,
                "security": "auto"
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "tlsSettings": {
          "allowInsecure": true
        }
      }
    }
  ]
}
```

## 参考
* [v2fly docker](https://github.com/v2fly/docker)
* [V2Ray Heroku](https://github.com/bclswl0827/v2ray-heroku)
