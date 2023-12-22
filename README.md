# Hosting Multiple Websites on a Single Server <br>with Apache Virtual Hosts
![mutiplewebs](https://github.com/PankajPaneru/Apache-Web-Server/assets/132757802/bf7bc31c-0d9a-4a0a-a7c1-595272f18be8)

Are you wondering if it's possible to host multiple websites on a single server? The answer is a resounding yes! In the world of Apache web servers, this can be achieved through the concept of Virtual Hosts or Vhosts.

## Two Ways to Achieve Multiple Website Hosting

### A. Name-Based Virtual Hosts

**Step 1: Install Apache Web Server**

```bash
yum install httpd  # For CentOS
sudo apt install apache2  # For Ubuntu
```

**Step 2: Stop the Internal Firewall (For Lab Purposes Only)**


```bash
systemctl stop firewalld  # For CentOS
systemctl stop ufw  # For Ubuntu
```

**Step 3: Create Different Websites**

Create two separate directories, `site1` and `site2`, along with their respective `index.html` files in the default location for webpage files.

```bash
cd /var/www/html/
mkdir site1 site2
vi site1/index.html
```
```bash
<html>
<title>Site 1</title>
</head>
<body>
<h1>Welcome to Site 1</h1>
</body>
</html>
```
Similarly,

```bash
vi site2/index.html
```
```bash
<html>
<title>Site 2</title>
</head>
<body>
<h1>Welcome to Site 2</h1>
</body>
</html>
```

**Step 4: Configure Apache**

Create a file named `mywebsites.conf` in the `/etc/httpd/conf.d` directory (on Ubuntu ‘/etc/apache2/sites-available’).
```bash
vi /etc/httpd/conf.d/mywebsites.conf
```

Add the following lines:
```bash
<VirtualHost *:80>
	ServerName website1.com
	DocumentRoot /var/www/html/site1
</VirtualHost>

<VirtualHost *:80>
	ServerName website2.com
	DocumentRoot /var/www/html/site2
</VirtualHost>
```
**Step 5: Update DNS Files or Host File**
Ensure the domain names are mentioned in the `/etc/hosts` section.

```bash
vi /etc/hosts
```
```bash
192.168.0.103    website1.com website2.com
```

**Step 6: Restart the HTTP service:**

```bash
systemctl restart httpd
systemctl restart apache2
```

**Step 7: Check the websites:**

```bash
curl website1.com
curl website2.com
```

### B. IP Address-Based Virtual Hosts


If you have multiple interfaces on your server, you can also host multiple websites.

Follow similar steps as above, with the following modifications:

**Step 1: Modify `mywebsites.conf`**
```bash
vi /etc/httpd/conf.d/mywebsites.conf
```
```bash
<VirtualHost 192.168.0.103:80>
	ServerName website1.com
	DocumentRoot /var/www/html/site1
</VirtualHost>

<VirtualHost 192.168.0.104:80>
	ServerName website2.com
	DocumentRoot /var/www/html/site2
</VirtualHost>
```
**Step 2: Update DNS Files or Host File**
```bash
vi etc/hosts
```
```bash
192.168.0.103    website1.com
192.168.0.104    website2.com
```

**Step 3: Restart Apache**
```bash
systemctl restart httpd
systemctl restart apache2
```
Test the websites:
```bash
curl website1.com
curl website2.com
```
And there you have it! Hosting multiple websites on a single server using Apache Virtual Hosts. Have fun exploring the vast possibilities of web hosting.


