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

creating nodejs application
```
cd nodejs
docker build -t my-nodejs .
docker run -itd --name nodejs_application -p 3000:3000 my-nodejs:latest

```

creating nginx application 
```
cd nginx
docker build -t my-nginx .
docker run -itd --name my-nginx -p 80:80 -p 443:443 --link nodejs_application:nodejs_application my-nginx:latest
```

