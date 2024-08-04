Nginx is a powerful, high-performance web server that can also be used as a reverse proxy, load balancer, and HTTP cache. In this tutorial, we'll walk you through the steps to install and configure **Nginx** on **Ubuntu**.

<br>
###Update Your Package List

Before installing Nginx, it's always a good idea to update your package list to ensure you have the latest information about available packages:

``` bash
sudo apt update && sudo apt upgrade -Y
```


<br>
###Install Nginx

Install Nginx using the following command:

```bash
sudo apt install nginx -y
```


<br>
###Start and Enable Nginx

Once the installation is complete, start the Nginx service and enable it to start on boot:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```


<br>
###Adjust the Firewall

If you have a firewall running, you'll need to allow traffic on HTTP (port 80) and HTTPS (port 443):


```bash
sudo ufw allow 'Nginx Full'
```


<br>
###Verify the Installation

You can verify that Nginx is running by visiting your server's IP address in your web browser. You should see the default Nginx welcome page.


<br>
###Configure Nginx

To configure Nginx, you need to edit the configuration files located in /etc/nginx/. The main configuration file is nginx.conf, and site-specific configurations are stored in the sites-available directory.

**For example**, to configure a new site, create a configuration file in sites-available:

```bash
sudo nano /etc/nginx/sites-available/my_site
```

<br>
Add your site configuration:

```nginx
server {
    listen 80;
    server_name my_site.com;
    root /var/www/my_site;

    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
<br>
Enable the site by creating a symlink to the sites-enabled directory:

```bash
sudo ln -s /etc/nginx/sites-available/my_site /etc/nginx/sites-enabled/
```



<br>
###Test and Restart Nginx

Test your configuration for syntax errors:

```bash
sudo nginx -t
```


<br>
If the test is successful, restart Nginx to apply the changes:

```bash
sudo systemctl restart nginx
```



<br>
###Conclusion

By following these steps, you have successfully installed and configured Nginx on your Ubuntu server. Nginx is now ready to serve your web content efficiently and securely.





