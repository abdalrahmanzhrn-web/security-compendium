# curl usage (full output or response and request)

```html
zahranSatosh@htb[/htb]$ curl inlanefreight.com -v

 * Trying SERVER_IP:80... * TCP_NODELAY set * Connected to inlanefreight.com (SERVER_IP) port 80 (#0) >
    GET / HTTP/1.1 > Host: inlanefreight.com >
    User-Agent: curl/7.65.3 > Accept: */* >
     Connection: close >

* Mark bundle as not supporting multiuse < HTTP/1.1 401 Unauthorized < Date: Tue, 21 Jul 2020 05:20:15 GMT < Server: Apache/X.Y.ZZ (Ubuntu) < WWW-Authenticate: Basic realm="Restricted Content" < Content-Length: 464 < Content-Type: text/html; charset=iso-8859-1 < <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN"> <html><head> ...SNIP...
```

```bash
curl -s "https://empresa.bancoplata.mx/envs/env.json" | jq .  (map)

curl -s "https://empresa.bancoplata.mx/envs/env.json" | jq .

curl -s "https://prime.bancoplata.mx/file-service/static/" | jq .
```

https://prime.bancoplata.mx/file-service/static/

```bash
curl -s "https://prime.bancoplata.mx/file-service/static/." | jq .
```

https://prime.bancoplata.mx/file-service/static/.
