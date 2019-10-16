```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

```
make build run

```

```
docker exec nodejs_master cat /var/log/nodejs_log

```

Creating a self signed SSL certificate

You will have to fill in the following questions;

* Country Name (2 letter code)
* State or Province Name (full name)
* Locality Name (eg, city)
* Organization Name (eg, company)
* Organizational Unit Name (eg, section)
* Common Name (eg, fully qualified host name)
* Email Address
* Once that is done you will have two new files in your nginx dir

```
openssl req -newkey rsa:2048 -nodes -keyout nginx/my-site.com.key -x509 -days 365 -out nginx/my-site.com.crt

```