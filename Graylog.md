    <h1>Graylog Configuration Guide</h1>
    <h2>Overview</h2>
    <p>Graylog is a powerful log management and analysis tool that allows for real-time analysis and storage of log data.</p>

    <h2>Installation</h2>
    <h3>1. Update the System</h3>
    <pre><code>sudo apt-get update</code></pre>

    <h3>2. Install Graylog Server</h3>
    <pre><code>sudo apt-get install graylog-server</code></pre>

    <h2>Configuration</h2>
    <h3>1. Configure Graylog Server</h3>
    <pre><code>sudo nano /etc/graylog/server/server.conf</code></pre>
    <ul>
        <li>Set parameters like <code>node_id_file</code>, <code>rest_listen_uri</code>, and <code>web_listen_uri</code>.</li>
    </ul>

    <h3>2. Start Graylog Service</h3>
    <pre><code>sudo systemctl start graylog-server
    <pre><code>sudo systemctl enable graylog-server</code></pre>
