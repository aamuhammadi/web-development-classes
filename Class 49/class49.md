Today we have discussed the following topic:

Deploying Multiple Websites on One DigitalOcean Droplet

Kindly find the video link below:
https://drive.google.com/file/d/1rhFLF2s0rt-lAZWakxmYkGfsqpIDo9GS/view?usp=sharing

Helpers code:

Create a Website Directory:

Run the following command to create a website directory:
mkdir /var/www/<website2>

Upload or Create Website Files:

Ensure that you upload or create all the necessary files from your local environment, including the .env file.

Create a Database on the Droplet

Test Your Website:

Check if your website is functioning correctly by accessing it via your IP address and specifying the appropriate port.

Ensure that your chosen ports are unique.

Move to the following folder: /etc/nginx/sites-available

Then, create and configure your website2 file as follows:

server {
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

Next, run the following commands:

sudo nginx -t

sudo systemctl reload nginx

Create a symbolic link to enable your website2 configuration:

ln -s /etc/nginx/sites-available/<website2> /etc/nginx/sites-enabled/

Secure Your Domain or Sub-domain Using SSL

Start Your Project with PM2
