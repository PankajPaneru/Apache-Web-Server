# **Change Apache's Port to 5000: A Simple Guide**

## **Step 1: Install Apache Web Server**

Install Apache on your system. For Ubuntu, run:

```bash
sudo apt update
sudo apt install apache2
```

For CentOS 7, use:

```bash
sudo yum install httpd
```

## **Step 2: Disable the Firewall (Lab Use Only)**

Temporarily disable the firewall:

For Ubuntu:

```bash
sudo systemctl stop ufw
```

For CentOS 7:

```bash
sudo systemctl stop firewalld
```

## **Step 3: Create a Unique Website**

Create a directory for your website and add a simple HTML page:

```bash
sudo mkdir mywebsite
sudo vi mywebsite/index.html
```

Add your content:

```html
<html>
<title>My Unique Website</title>
</head>
<body>
<h1>Welcome to My Unique Website</h1>
</body>
</html>
```

## **Step 4: Configure Apache for Port 5000**

Create a configuration file:

For Ubuntu:

```bash
sudo vi /etc/apache2/sites-available/mywebsite.conf
```

For CentOS 7:

```bash
sudo vi /etc/httpd/conf.d/mywebsite.conf
```

Add:

```apache
<VirtualHost *:5000>
	ServerName your-server-ip
	DocumentRoot /var/www/html/mywebsite
</VirtualHost>
```

Replace `your-server-ip` with your server's IP or domain.

## **Step 5: Update Hosts File**

Add your domain to `/etc/hosts`:

```bash
sudo vi /etc/hosts
your-server-ip    website.com
```

## **Step 6: Restart Apache**

For Ubuntu:

```bash
sudo a2ensite mywebsite.conf
sudo systemctl restart apache2
```

For CentOS 7:

```bash
sudo systemctl restart httpd
```

## **Step 7: Test Your Unique Website**

Visit your website on port 5000:

```bash
curl website.com:5000
```

## **Experience the Change**

Congratulations! Your website now stands out on port 5000. Enjoy the freedom of this unconventional hosting journey on Ubuntu and CentOS 7. Stand out in the digital crowd!

## **Embrace the Unconventional Power of Apache!**
