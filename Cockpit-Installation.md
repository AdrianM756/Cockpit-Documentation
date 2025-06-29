## Cockpit

[Cockpit](https://cockpit-project.org/) is a web-based graphical interface for servers, intended for everyone, especially those who are:

* New to linux
* Familiar with Linux and want an easy, graphical way to administer servers
* Linux administrators who mainly use other tools but want an overview on individual systems

## Cockpit Installation

In This demo, we will be installing cockpit on a ubuntu machine. First, let's update our package.
```
apt update -y
```
<br>

After updating, let's install cockpit.
```
apt install cockpit -y
```
<br>

Next, Let's nable the Cockpit service to automatically start at boot.
```
systemctl enable cockpit.socket
```
<br>

We then need to start the cockpit service.
```
systemctl start cockpit
```
<br>

We can view the cockpit status and verify that it's running.
```
systemctl status cockpit
```
<br>

![image](https://github.com/user-attachments/assets/a6e825c5-49ce-4a53-955c-052fb1d584a6)
<br>

By default, Cockpit listens for connection requests on the TCP port 9090 without encryption. To access it via HTTP, we need to add the following:

navigate to and edit the ```cockpit.conf```
```
nano /etc/cockpit/cockpit.conf
```
<br>

Add the following on the ```cockpit.conf``` file.
```
[WebService]
AllowUnencrypted=true
```
<br>

Restart the cockpit service.
```
systemctl restart cockpit
```
<br>

## Creating users

***NOTE:*** Cockpit does not support ```root``` user account logins directly through the web interface. Ensure to use non-root user accounts to access Cockpit and manage the server.

Once you've created a user, you can now access it via port ```9090```.
```
http://ip_address_of_your_machine:9090
```
<br>

![image](https://github.com/user-attachments/assets/8bf83aa5-9b25-476b-aeff-4e6f44a21b11)
<br>


