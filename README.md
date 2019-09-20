# quicly start a webrtc video Call session 

## get npm modules

install npm module for webrtc development 
```
npm install webrtcdevelopment
```
include the css and js header files into project 
```
<link rel=stylesheet href="node_modules/webrtcdevelopment/client/build/webrtcdevelopment_header.css">
<script src="node_modules/webrtcdevelopment/client/build/webrtcdevelopment_header.js"> </script>
```
indlude the main scripts 
```
<link rel=stylesheet href="node_modules/webrtcdevelopment/client/build/webrtcdevelopment.css">
<script src="node_modules/webrtcdevelopment/client/build/webrtcdevelopment.js"></script>
```

## Secure HTTP server to mount the website 

**Create CA**
openssl req -batch -new -newkey ec:<(openssl ecparam -name prime256v1) -nodes -keyout ca-key.pem -x509 -out ca.pem -days 3650 -subj "/CN=A localhost CA"

**Create a CSR for localhost, then sign it by CA**
openssl req -batch -new -newkey ec:<(openssl ecparam -name prime256v1) -nodes  -keyout key.pem -subj /CN=localhost | openssl x509 -req -CAkey ca-key.pem -CA ca.pem -CAcreateserial -out cert.pem -days 365 -extfile <(echo subjectAltName=DNS:localhost)

$ http-server -S -C cert.pem -o
Starting up http-server, serving ./ through https
Available on:
  https:127.0.0.1:8080
  https:192.168.1.101:8080
  https:192.168.1.104:8080
Hit CTRL-C to stop the server

or use directly the fake keys supplied in project 
```
$ http-server --ssl  -C fake-keys/certificate.pem -K fake-keys/privatekey.pem -o 
Starting up http-server, serving ./ through https
Available on:
  https://127.0.0.1:8080
  https://192.168.0.3:8080
Hit CTRL-C to stop the server

```

## Secure nodejs socket.io server to mount the signaller 

// tbd 

## Loading widgets 

Refer to https://github.com/altanai/webrtc/blob/master/README.md

## References 

webrtcdevelopment npm module - https://npmjs.com/package/webrtcdevelopment

## License 
----
MIT

## Author 
----
Altanai 