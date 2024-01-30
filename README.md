# Sub-task #1 Linux Server Simulation:

&nbsp;

### using dnf package manager for fedora linux to install Apache, MySQL and PHP:

- `sudo dnf update`
- `sudo dnf install httpd mysql-server php php-mysqlnd`

&nbsp;

### starting and enabling Apache and MySQL-service:

- `sudo systemctl start httpd`
- `sudo systemctl enable httpd`
- `sudo systemctl start mariadb`
- `sudo systemctl enable mariadb`

&nbsp;

### Configuring Apache to serve the website:

- `sudo nano /etc/httpd/conf/httpd.conf`

edit the apache configuration file:

- update the DocumentRoot to '/var/www/html/'

&nbsp;

### Create a simple Website:

create a file names 'index.php' in '/var/www/html/' with the following content:

```php
<?php
echo "Hello World!";
?>
```

### Configue MySQL:

- `sudo mysql_secure_installation`
- `sudo systemctl start mysqld`
- `sudo systemctl enable mysqld`
- `sudo mysql`

Inside MySQL, create a new database, user, and password:

```sql
CREATE DATABASE database_name;
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON your_database_name.* TO 'username'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

&nbsp;edit 'index.php' to include database connection and display IP address and current time:

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "database_name";

$conn = new mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$ip_address = $_SERVER['REMOTE_ADDR'];
$current_time = date("Y-m-d H:i:s");

echo "Hello World! Your IP address is $ip_address and the current time is $current_time";

$conn->close();
?>
```

### Additionally for connection from another machine on the same network we can allow incoming connection in the firewall as following:

- `sudo firewall-cmd --add-service=http --permanent`
- `sudo firewall-cmd --reload`

&nbsp;

# Sub-task #2 Git & GitHub:

Initializing a new Git repo on local machine:

open a terminal and navigate to the root directory of the project. then run:

`git init`

create a file named '.gitignore' in the root of the project.

nano .gitignore

# Networking and Cloud Instance Connectivity Documentation

## IP Address:

An IP (Internet Protocol) address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves two main purposes: host or network interface identification and location addressing.

## MAC Address:

A MAC (Media Access Control) address is a unique identifier assigned to network interfaces for communications on a network. It is a hardware address embedded into the network interface card (NIC) during manufacturing.

## Switches:

A switch is a networking device that operates at Layer 2 (Data Link Layer) of the OSI model. It connects devices within a local area network (LAN) and uses MAC addresses to forward data only to the specific device it is intended for, improving network efficiency.

## Routers:

A router is a networking device that operates at Layer 3 (Network Layer) of the OSI model. It connects different networks and routes data between them based on IP addresses. Routers are essential for directing traffic on the internet.

## Routing Protocols:

Routing protocols are sets of rules used by routers to determine the optimal path for data to travel from the source to the destination across a network. Examples include RIP (Routing Information Protocol), OSPF (Open Shortest Path First), and BGP (Border Gateway Protocol).

## Connecting to a Cloud Instance from a Remote Machine (SSH Process):

### Steps:

1.  **Obtain the Public IP Address of the Cloud Instance:**
    
    Log in to your cloud platform dashboard and retrieve the public IP address assigned to your cloud instance.
    
2.  **Open a Terminal on the Remote Machine:**
    
    On your local machine, open a terminal. You can use the terminal on Linux or macOS, or tools like PuTTY on Windows.
    
3.  **Use SSH to Connect:**
    
    In the terminal, use the following command to initiate an SSH connection:
    
    ```bash
    ssh username@public_ip_address
    
    
    ```
    

Enter password or Use SSH keys:

if prompted, enter the password associated with the username. alternatively, you can set up SSH key-based authentication for a more secure and password-less connection.

GitHub Repository Link:https://github.com/ahmednasret7/ATW-Ltd-task

&nbsp;