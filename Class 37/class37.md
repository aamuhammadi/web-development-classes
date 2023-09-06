Today we have learned Deploying App on DigitalOcean (VPS)

Kindly find the video link below:
https://drive.google.com/file/d/1zj039clKLQnbM2Cc9wodcbPLz3scrjmU/view?usp=sharing

A Step-by-Step Guide to Deploying a Website on DigitalOcean

1. Ensure that you've thoroughly tested, optimized, and uploaded your code to a GitHub repository.

2. Begin by creating a DigitalOcean account, you can sign up using this link (https://m.do.co/c/ac8ddb2ca45f) and get a $200 credit that is valid for 60 days and then proceed to create a droplet. Set either a password or an SSH key, along with a hostname for your droplet.

3. Log in to your droplet using a terminal by typing the following command:

ssh root@your-ip-address

4. Install Node.js and npm on Ubuntu. You can follow this guide to install them: https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04

5. Clone your repository to your droplet. Make sure you've created a personal access token to clone it.

6. After cloning, navigate to the folder where you've cloned the code and run the ‘npm install’ command.

7. Once you've installed the required packages, start the project to ensure it's functioning correctly on your IP address.

8. Install Nginx on your droplet to host your website on a domain, sub-domain, or your droplet's IP address. You can follow this guide to install Nginx: https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04

9. Link your domain or sub-domain and configure Nginx settings.

Move to this folder /etc/nginx/sites-available and configure file

server {
listen 80;
server_name domain-or-sub-domain-url-here;

    root /folder-path;
    index index.html;

location / {

        proxy_pass http://ip-address-here:port;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
       }

}

sudo nginx -t

sudo systemctl reload nginx

10. Enhance the security of your website by adding an SSH certificate. You can follow this guide to secure it: https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04

11. Create a production build using the command 'npm run build'.

12. Install PM2 and use it to keep your app running.

npm install pm2@latest -g
pm2 start npm --name "ams-aamax" -- run start
pm2 save

Additional useful commands:
pm2 logs
pm2 status
pm2 restart

Congratulations! Your app is now up and running smoothly. Alhamdulillah.

13. Consider enabling the backup for your droplet.

Note:
Why choose DigitalOcean over other hosting providers like Vercel and many others out there?

When uploading the backend code, you will require additional configurations for the backend and database, such as MongoDB and PostgreSQL.

Additionally, you can add multiple sites to your droplet.
