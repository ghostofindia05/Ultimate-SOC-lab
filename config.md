<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Configuration Guide</title>
</head>
<body>

<h1>Configuration Guide</h1>
<p>This guide provides step-by-step instructions to configure Wazuh, IRIS, Graylog, SOC Fortress Copilot, Windows Server, Ubuntu, and Windows.</p>

<h2>Table of Contents</h2>
<ul>
    <li><a href="#wazuh">Wazuh</a></li>
    <li><a href="#iris">IRIS</a></li>
    <li><a href="#graylog">Graylog</a></li>
    <li><a href="#soc-fortress-copilot">SOC Fortress Copilot</a></li>
    <li><a href="#windows-server">Windows Server</a></li>
    <li><a href="#ubuntu">Ubuntu</a></li>
    <li><a href="#windows">Windows</a></li>
</ul>

<hr>

<h2 id="wazuh">Wazuh</h2>
<h3>1. Install Wazuh Manager</h3>
<pre><code>sudo apt-get update
sudo apt-get install wazuh-manager
</code></pre>

<h3>2. Configure Wazuh Agents</h3>
<pre><code>sudo nano /var/ossec/etc/ossec.conf
</code></pre>
<p>- Set up the manager IP and port.</p>
<p>- Configure agents to report to the Wazuh manager.</p>

<h3>3. Start Wazuh Service</h3>
<pre><code>sudo systemctl start wazuh-manager
sudo systemctl enable wazuh-manager
</code></pre>

<hr>

<h2 id="iris">IRIS</h2>
<h3>1. Install IRIS</h3>
<pre><code># Clone the repository
git clone https://your-iris-repo-url
</code></pre>
<p>Follow the documentation provided in the repository to complete the setup.</p>

<hr>

<h2 id="graylog">Graylog</h2>
<h3>1. Install Graylog</h3>
<pre><code>sudo apt-get update
sudo apt-get install graylog-server
</code></pre>

<h3>2. Configure Graylog</h3>
<pre><code>sudo nano /etc/graylog/server/server.conf
</code></pre>
<p>- Set up the appropriate settings like node_id_file, rest_listen_uri, and web_listen_uri.</p>

<h3>3. Start Graylog Service</h3>
<pre><code>sudo systemctl start graylog-server
sudo systemctl enable graylog-server
</code></pre>

<hr>

<h2 id="soc-fortress-copilot">SOC Fortress Copilot</h2>
<p>Instructions for configuring SOC Fortress Copilot will go here.</p>

<hr>

<h2 id="windows-server">Windows Server</h2>
<p>Instructions for configuring Windows Server will go here.</p>

<hr>

<h2 id="ubuntu">Ubuntu</h2>
<p>Instructions for configuring Ubuntu will go here.</p>

<hr>

<h2 id="windows">Windows</h2>
<p>Instructions for configuring Windows will go here.</p>

</body>
</html>
