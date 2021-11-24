# portfolio2sitesingledomain

First Create two Ec2 Nano Instances
install Nginx webserver
copy your diffrent two portfolio contents to separte servers webroot.
Change the Nginx conf like below.

Server 1 Config file

```

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
}

```

Server 2 config file

```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
}

```


The content are same.

Create Classic loadbalancer and add two instances to that.
in Classic loadbalancer > Description > Port Configuration

change the stickness settings
![image](https://user-images.githubusercontent.com/38104778/143082298-8009c4d0-94f2-468c-9acf-81eefbfa141a.png)

Next create application load balancer .

![image](https://user-images.githubusercontent.com/38104778/143081183-024e6bd6-5740-4d5d-9b35-c5a282e9763b.png)

create target group and add two instance to that.

![image](https://user-images.githubusercontent.com/38104778/143081034-11964fe6-fc0b-407d-8837-21adf5d7c880.png)
![image](https://user-images.githubusercontent.com/38104778/143081096-8a5c5795-ec72-4d41-b40f-a57f9b3f4e2e.png)


Map the target group to the application loadbalancer.

Now check the apllication loadbalanncer url in browser.

Thas all guys.

