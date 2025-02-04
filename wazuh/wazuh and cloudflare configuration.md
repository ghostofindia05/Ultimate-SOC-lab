<configuration>
    <step id="1" title="Configure your domain with Cloudflare" />
    
    <step id="2" title="Wazuh Server installation, configuration & connecting to Cloudflare">
        <task title="Install Wazuh in Ubuntu Server">
            <link>Quickstart · Wazuh documentation</link>
        </task>
        
        <task title="Configure the Wazuh Manager">
            <description>Before proceeding with the Windows agent, make sure the Wazuh Manager is configured to use a password.</description>
            <subtask title="Modify the <auth> Section">
                <file path="/var/ossec/etc/ossec.conf">
                    <content format="xml">
                        &lt;auth&gt;
                        &lt;disabled&gt;no&lt;/disabled&gt;
                        &lt;port&gt;1515&lt;/port&gt;
                        &lt;use_source_ip&gt;no&lt;/use_source_ip&gt;
                        &lt;purge&gt;yes&lt;/purge&gt;
                        &lt;use_password&gt;yes&lt;/use_password&gt;
                        &lt;ciphers&gt;HIGH:!ADH:!EXP:!MD5:!RC4:!3DES:!CAMELLIA:@STRENGTH&lt;/ciphers&gt;
                        &lt;!-- &lt;ssl_agent_ca&gt;&lt;/ssl_agent_ca&gt; --&gt;
                        &lt;ssl_verify_host&gt;no&lt;/ssl_verify_host&gt;
                        &lt;ssl_manager_cert&gt;etc/sslmanager.cert&lt;/ssl_manager_cert&gt;
                        &lt;ssl_manager_key&gt;etc/sslmanager.key&lt;/ssl_manager_key&gt;
                        &lt;ssl_auto_negotiate&gt;no&lt;/ssl_auto_negotiate&gt;
                        &lt;/auth&gt;
                    </content>
                </file>
                <command>sudo systemctl restart wazuh-manager</command>
            </subtask>
            
            <subtask title="Set a Password for Enrollment">
                <file path="/var/ossec/etc/authd.pass">
                    <content>MySecurePassword123</content>
                </file>
                <command>sudo chmod 600 /var/ossec/etc/authd.pass</command>
            </subtask>
        </task>
    </step>
    
    <step id="3" title="Configuration of Wazuh in Windows Endpoint">
        <task title="Install Wazuh Agent in Windows Endpoint">
            <link>Installing Wazuh agents on Windows endpoints - Wazuh agent</link>
        </task>
        
        <task title="Configure the Windows Agent">
            <file path="C:\\Program Files (x86)\\ossec-agent\\ossec.conf">
                <content format="xml">
                    &lt;server&gt;
                    &lt;address&gt;127.0.0.1&lt;/address&gt;
                    &lt;port&gt;4544&lt;/port&gt;
                    &lt;/server&gt;
                </content>
            </file>
        </task>
    </step>
    
    <step id="4" title="Creating Scheduled Task">
        <task title="Install Cloudflared in Windows">
            <link>Downloads · Cloudflare Zero Trust docs</link>
        </task>
        
        <task title="Add Task Arguments">
            <command format="powershell">-NoProfile -WindowStyle Hidden -Command "Start-Process -FilePath 'cloudflared' -ArgumentList 'access tcp --hostname agent-register.bkrishna.site --url 127.0.0.1:4545' -NoNewWindow; Start-Process -FilePath 'cloudflared' -ArgumentList 'access tcp --hostname agent.bkrishna.site --url 127.0.0.1:4544' -NoNewWindow"</command>
        </task>
        
        <task title="Modify Task Conditions">
            <setting name="Start only if on AC Power" value="false" />
            <setting name="Allow task to be run on demand" value="true" />
            <setting name="Retry attempts" value="3 times every 1 minute" />
        </task>
        
        <task title="Enable Task to Run Without User Login">
            <subtask title="Use a System-Wide Account">
                <description>The task account should ideally be a system account or a service account with sufficient privileges.</description>
            </subtask>
            <subtask title="Modify Group Policy">
                <path>Computer Configuration &gt; Windows Settings &gt; Security Settings &gt; Local Policies &gt; User Rights Assignment</path>
                <setting name="Log on as a service" value="Ensure the account is listed" />
            </subtask>
        </task>
        
        <task title="Test the Task">
            <command>Reboot the system to confirm the commands run at startup.</command>
        </task>
    </step>
</configuration>
