<h3>osTicket - Post-Install Configuration</h3>
<p>After successfully installing osTicket, you need to complete the post-install configuration to ensure the system is fully operational and optimized. Below are the essential steps:</p>
<hr />
<h3><strong>1. Delete the Setup Directory</strong></h3>
<p>For security reasons, you must remove the setup directory to prevent unauthorized reinstallation.</p>
<ul>
<li>Navigate to your osTicket installation directory:
<div>
<div>makefile</div>
<div>
<div>
<div><span data-state="closed"><button>Copier</button></span><span data-state="closed"><button>Modifier</button></span></div>
</div>
</div>
<div dir="ltr"><code>C:\inetpub\wwwroot\osticket</code></div>
</div>
</li>
<li>Delete the <code>setup</code> folder using the command:
<div>
<div>bash</div>
<div>
<div>
<div><span data-state="closed"><button>Copier</button></span><span data-state="closed"><button>Modifier</button></span></div>
</div>
</div>
<div dir="ltr"><code>rd /s /q C:\inetpub\wwwroot\osticket\setup </code></div>
</div>
</li>
<li>Restart IIS:
<div>
<div>nginx</div>
<div>
<div>
<div><span data-state="closed"><button>Copier</button></span><span data-state="closed"><button>Modifier</button></span></div>
</div>
</div>
<div dir="ltr"><code>iisreset</code></div>
</div>
</li>
</ul>
<hr />
<h3><strong>2. Configure Email Settings</strong></h3>
<p>osTicket can send and receive emails using SMTP and IMAP/POP.</p>
<ol>
<li><strong>Navigate to Admin Panel</strong>:
<div>
<div>perl</div>
<div>
<div>
<div><span data-state="closed"><button>Copier</button></span><span data-state="closed"><button>Modifier</button></span></div>
</div>
</div>
<div dir="ltr"><code>http://&lt;your-azure-vm-public-ip&gt;/osticket/scp </code></div>
</div>
</li>
<li><strong>Go to "Emails" &rarr; "Email Settings"</strong>:
<ul>
<li>Set the <strong>Default System Email</strong> for notifications.</li>
<li>Enable <strong>Incoming Email Fetching</strong> for IMAP or POP.</li>
<li>Configure <strong>SMTP Settings</strong> for outgoing emails.</li>
<li>Save changes and test email sending/receiving.</li>
</ul>
</li>
</ol>
<hr />
<h3><strong>3. Configure Departments and Agents</strong></h3>
<ol>
<li>
<p><strong>Set Up Departments</strong>:</p>
<ul>
<li>Go to <strong>Admin Panel &rarr; Agents &rarr; Departments</strong>.</li>
<li>Create departments like IT Support, Customer Service, etc.</li>
<li>Assign department managers and auto-responders.</li>
</ul>
</li>
<li>
<p><strong>Create Agents (Support Staff)</strong>:</p>
<ul>
<li>Go to <strong>Admin Panel &rarr; Agents &rarr; Add New Agent</strong>.</li>
<li>Assign them to a department with proper access roles.</li>
<li>Set permissions for ticket handling.</li>
</ul>
</li>
</ol>
<hr />
<h3><strong>4. Customize Ticket Settings</strong></h3>
<ol>
<li>
<p><strong>Navigate to "Admin Panel" &rarr; "Settings" &rarr; "Tickets"</strong>:</p>
<ul>
<li>Enable <strong>Ticket Auto-Response</strong>.</li>
<li>Set ticket priority levels.</li>
<li>Configure ticket assignment and SLA (Service Level Agreements).</li>
</ul>
</li>
<li>
<p><strong>Create Custom Forms and Fields</strong>:</p>
<ul>
<li>Go to <strong>Admin Panel &rarr; Manage &rarr; Forms</strong>.</li>
<li>Add new fields like Order Number, Product Type, etc.</li>
</ul>
</li>
</ol>
<hr />
<h3><strong>5. Configure Help Topics</strong></h3>
<ul>
<li>Go to <strong>Admin Panel &rarr; Manage &rarr; Help Topics</strong>.</li>
<li>Define various ticket categories like "Technical Support," "Billing Issue," etc.</li>
<li>Assign default departments to specific topics.</li>
</ul>
<hr />
<h3><strong>6. Enable User Authentication</strong></h3>
<ul>
<li>Navigate to <strong>Admin Panel &rarr; Users &rarr; Authentication</strong>.</li>
<li>Enable <strong>LDAP or OAuth authentication</strong> (if required).</li>
<li>Configure Google/Microsoft authentication if needed.</li>
</ul>
<hr />
<h3><strong>7. Set Up Alerts and Notifications</strong></h3>
<ul>
<li>Navigate to <strong>Admin Panel &rarr; Settings &rarr; Alerts &amp; Notices</strong>.</li>
<li>Enable alerts for <strong>New Tickets, Ticket Assignments, Responses, and Overdue Tickets</strong>.</li>
<li>Customize email templates under <strong>Emails &rarr; Templates</strong>.</li>
</ul>
<hr />
<h3><strong>8. Secure Your Installation</strong></h3>
<ol>
<li>
<p><strong>Restrict Access to the Admin Panel</strong>:</p>
<ul>
<li>Use Azure&rsquo;s <strong>Network Security Groups (NSG)</strong> to limit access.</li>
<li>Allow only trusted IPs to access <code>/scp</code>.</li>
</ul>
</li>
<li>
<p><strong>Enable HTTPS (SSL)</strong>:</p>
<ul>
<li>Use <strong>Let's Encrypt</strong> or an Azure-provided SSL certificate.</li>
<li>Configure IIS to force HTTPS for all connections.</li>
</ul>
</li>
<li>
<p><strong>Regularly Backup the Database</strong>:</p>
<ul>
<li>Set up <strong>Azure SQL backups</strong> or schedule MySQL dumps:
<div>
<div>css</div>
<div>
<div>
<div><span data-state="closed"><button>Copier</button></span><span data-state="closed"><button>Modifier</button></span></div>
</div>
</div>
<div dir="ltr"><code>mysqldump -u ostuser -p osticket &gt; osticket_backup.sql</code></div>
</div>
</li>
</ul>
</li>
</ol>
<hr />
<h3><strong>9. Test the System</strong></h3>
<ul>
<li>Create a <strong>test ticket</strong> to ensure emails, notifications, and agent assignments are working correctly.</li>
<li>Check logs in <strong>Admin Panel &rarr; Dashboard &rarr; Logs</strong> for errors.</li>
</ul>
