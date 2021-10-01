# ssl-automation
A repo to deploy and secure single server node applications/websites
This is made under the assumption that you have a working ip/domain for your website. 

Step 1. run the following commands to install Docker && docker-compose

Step 2. Place working application in the app folder. 
* the Dockerfile is preset to install the latest version of node and for the app to start with the command ```npm start```

Step 3. Replace <domain> with your ip address or domain for your website

Step 4. run this command ```curl -L https://raw.githubusercontent.com/wmnnd/nginx-certbot/master/init-letsencrypt.sh > init-letsencrypt.sh``` followed by ```chmod +x init-letsencrypt.sh```
* this command will download a file that will produce the certificate.
* Make sure to review the file so that you can stage your attempts before hitting a rate limit and that it hits the proper domain/ip

Step 5. Run ```sudo ./init-letsencrypt.sh```
