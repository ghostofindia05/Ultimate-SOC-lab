<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wazuh Configuration Guide</title>
</head>
<body>
    <h1>Wazuh Configuration Guide</h1>
    <h2>Overview</h2>
    <p>Wazuh is an open-source security monitoring tool that helps in threat detection, integrity monitoring, and compliance auditing.</p>

    <h2>Installation</h2>
    <h3>1. Update the System</h3>
    <pre><code>sudo apt-get update</code></pre>

    <h3>2. Install Wazuh Manager</h3>
    <pre><code>sudo apt-get install wazuh-manager</code></pre>

    <h2>Configuration</h2>
    <h3>1. Configure Wazuh Agents</h3>
    <pre><code>sudo nano /var/ossec/etc/ossec.conf</code></pre>
    <ul>
        <li>Set the manager IP and port.</li>
    </ul>

    <h3>2. Start Wazuh Service</h3>
    <pre><code>sudo systemctl start wazuh-manager
sudo systemctl enable wazuh-manager</code></pre>
</body>
</html>
