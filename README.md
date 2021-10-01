# ssl-automation
A repo to deploy and secure single server node applications/websites
This is made under the assumption that you have a working ip/domain for your website. 
You are able to run and test these commands local as well as in an ec2 shell. 

## Step 1. run the following commands to install Docker && docker-compose

## Step 2. Place working application in the app folder. 
* the Dockerfile is preset to install the latest version of node and for the app to start with the command ```npm start```
* You will also need to add this code in your server *assuming it is an express server* 
```
app.use(express.static(".well-known/acme-challenge/"));

```
## Step 3. Replace <*domain*> with your ip address or domain for your website in the ```data/nginx/app.conf``` file
![init_file](images/domain_1.png)
![init_file](images/domain_2.png)
![init_file](images/domain_3.png)

## Step 4. Run the following command  
```
curl -L https://raw.githubusercontent.com/wmnnd/nginx-certbot/master/init-letsencrypt.sh > init-letsencrypt.sh
``` 
followed by 
```
chmod +x init-letsencrypt.sh
```
* this command will download a file that will produce the certificate.
* Make sure to review the file so that you can stage your attempts before hitting a rate limit and that it hits the proper domain/ip
![init_file](images/init_file_1.png)

## Step 5 Run the following command 
```
sudo ./init-letsencrypt.sh
```
* You should see *Succesfully received certificate* in the console. Once you see that message change the staging value in the init-letsencrypt.sh file back to 0 and repeat this step again. 

![post_staging](images/post_staging.png)
