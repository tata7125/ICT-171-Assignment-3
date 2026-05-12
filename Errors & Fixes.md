## ERROR 403 
- Ocurred when trying to install wordpress on my IP address.
<img width="515" height="214" alt="25a06b6cff9c83ba34170398d457309135740ad6" src="https://github.com/user-attachments/assets/d57d9bcc-bf8f-4304-996e-e69d4ad105cc" />  

## FIX   
**Try**   
```
sudo nano /etc/nginx/sites-available/default
```
You should see something like this:  
<img width="897" height="811" alt="image" src="https://github.com/user-attachments/assets/b06472cb-2268-4de1-9f87-2ffbd99ccb44" />

Delete all the content and change it to this: 
```
root /var/www/html;

index index.php index.html index.htm;

server_name www.countryhopper.life;

location / {
    try_files $uri $uri/ /index.php?$args;
}

location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
}

location ~ /\.ht {
    deny all;
}
```
If it still does not work, check that your php version is 8.3 by typing this commands:
```
php -v
```
If its not then type this command to install: 
```
sudo apt install php8.3-fpm php8.3-mysql php8.3-cli php8.3-curl php8.3-xml php8.3-mbstring php8.3-zip php8.3-gd -y
```

## Second Error 403 
This occured after finishing my website using WordPress and trying to make it HTTPS. 


