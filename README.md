# Free-SSL-certificate-Installation-on-server-using-chatbot

What is SSL?

SSL is standard technology for securing an internet connection by encrypting data sent between a website and a browser (or between two servers). It prevents hackers from seeing or stealing any information transferred, including personal or financial data.

Steps to Install a Free SSL Certificate with Let’s Encrypt and Certbot

Step 1: Update the Package Repository

sudo apt-get update
Step 2: Install Certbot and Nginx Plugin

sudo apt-get install certbot -y
sudo apt-get install python3-certbot-nginx -y
Step 3: Install the Nginx webserver

sudo apt install nginx -y
Step 4: Configure Your Domain

Make sure your domain or subdomain is pointing to your server’s public IP. This is done by creating an A record in your DNS settings.

Zoom image will be displayed

Wait a few minutes for the DNS propagation before moving forward.

Step 5: Update the nginx configuration file

sudo tee /etc/nginx/sites-available/react-app > /dev/null <<EOF
server {
    listen 80;
    server_name demo-lubbock.powerconnect.ai;
    return 301 https://\$host\$request_uri;
}
EOF
Enable the site:

sudo ln -s /etc/nginx/sites-available/react-app /etc/nginx/sites-enabled/
Test NGINX config:

sudo nginx -t
Reload NGINX:

sudo systemctl reload nginx
Step 6: Generate the SSL Certificate

sudo certbot --nginx -d development.mgyk.shop
Zoom image will be displayed

Certbot will verify your domain, fetch the certificate from Let’s Encrypt, and automatically configure your Nginx virtual host with SSL. The certificate will be valid for 90 days from the date of issuance.
