# Nginx
Un [[proxy reverso]] para Linux, utilizado en todo lado.

## Como hacer una redirección a otra ip
Esto aplica para contenedores de Docker también:
```nginx
server{
        listen 80;
        server_name magi.imyr.local;
        location / {
				proxy_set_header Host $host;
                proxy_pass http://172.17.0.2$request_uri;
        }
}
```
