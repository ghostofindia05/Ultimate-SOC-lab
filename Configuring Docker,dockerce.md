<h1>Configuring Ngnix proxymanager,Authentik,Netbird</h1>
<h2>Installation of Docker and Docker Compose via a Simple Script</h2>

<h1>Docker, Docker-Compose, Portainer-CE, and Nginx Proxy Manager Installation Guide Method-1</h1>
<p>You can easily install Docker-CE, Docker-Compose, Portainer-CE, and Nginx Proxy Manager by using this quick install script I created and maintain on GitHub. Just use the following command:</p>
<pre><code>wget https://gitlab.com/bmcgonag/docker_installs/-/raw/main/install_docker_nproxyman.sh -O install-docker.sh</code></pre>
<p>This will download the script to your desired host. Once downloaded, follow these steps:</p>
<ol>
  <li>Change the permissions to make the script executable:
    <pre><code>chmod +x ./install-docker.sh</code></pre>
  </li>
  <li>Run the script with the following command:
    <pre><code>./install-docker.sh</code></pre>
  </li>
</ol>
<p>When you run the script, it will prompt you to select your host operating system and ask which software you want to install. Simply enter 'y' for each component you want to install. During the installation process, you might be asked for your superuser (sudo) password.</p>
<p>Allow the script to complete the installation. At this point, you might want to log out and log back in. This will allow you to use the <code>docker-compose</code> commands without needing to prepend <code>sudo</code> to them.</p>

<h1>Docker, Docker-Compose, Portainer-CE, and Nginx Proxy Manager Installation Guide Method-2</h1>
## Install Using Root

To install the newest versions of sudo (optional depending on which script you use), curl, Docker, and docker compose, simply ssh into your server, then clone this repository with: 

```
git clone https://github.com/dnburgess/dockerinstall.git
```
If you don't have git installed, you can run:
```
apt install git
```

Change into the new directory:
```
cd dockerinstall
```

Make the file executable:
```
chmod +x dockerinstall.sh
```

Execute the file:
```
./dockerinstall.sh
```
<p>After installing we will create user and add it to docker group</p>
Adding user ghost and confirm your pasword
```
adduser ghost
```
Adding user ghost to docker group
```
usermod -aG docker ghost
```
If u want to login to ghost user using ssh
```
cp -r .ssh /home/ghsot
```
Changes the ownership of the /home/ghost directory and all its contents (files and subdirectories) to the user ghost

```
chown -R auth /home/ghost ghost
```
Now reboot
```
reboot
```



