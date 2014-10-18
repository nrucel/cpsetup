cpsetup
=======

<table border="0">
<tr>
<td width="60%"><h3>cpsetup</h3> is a custom bash/shell script to setup and harden cPanel CentOS/RHEL server with ConfigServer Firewall, MailManage, MailQueue, Malware Detect, and many security tweaks.

<br />
<h4>Features Include:</h4>
<ul>
<li>Install ClamAV from Source</li>
<li>Install <a href="http://configserver.com/cp/cmm.html" target="_blank">ConfigServer MailManage</a></li>
<li>Install <a href="http://configserver.com/cp/cmq.html" target="_blank">ConfigServer MailQueues</a></li>
<li>Install <a href="http://configserver.com/cp/csf.html" target="_blank">ConfigServer Firewall</a></li>
<li>Install <a href="https://www.rfxn.com/projects/linux-malware-detect/" target="_blank">R-fx Malware Detect</a></li>
<li>Install yum terminal colors</li>
<li>Update Firewall Configuration</li>
<li>Update SSH Configuration ( Port, and UseDNS )</li>
<li>Update cPanel Configurations</li>
<li>Update Pure FTP Configurations</li>
<li>Update cPanel Tweak Settings</li>
<li>Update MySQL Settings</li>
<li>Update PHP Settings</li>
</ul>
<h4>Future Enhancements:</h4>
<ul>
<li>Update Apache Global Configuration</li>
<li>Update EasyApache conf and Rebuild</li>
<li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/accountdnscheck/" target="_blank">Account DNS Check</a></li>
<li>Install <a href="https://waf.comodo.com/" target="_blank">Comodo WAF</a></li>
<li>Install <a href="http://www.softaculous.com/" target="_blank">Softaculous</a></li>
<li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/watchmysql/" target="_blank">WatchMySQL</a></li>
<li>Install <a href="http://how2.be/en/community/phpinimgr/" target="_blank">PHP.ini Manager</a></li>
<li>Install <a href="https://www.ndchost.com/cpanel-whm/addons/cleanbackups/" target="_blank">Clean Backups</a></li>
</ul>
</td>
<td width="40%">
<p align="center"><img src="screenshot.png"></p>
</td>
</tr>
</table>

Available Arguments
-------------------

```
cpsetup - cPanel setup script
Usage example:
cpsetup [(-h|--help)] [(-v|--verbose)] [(-V|--version)] [(-u|--unattended)]
Options:
-h or --help: Displays this information.
-v or --verbose: Verbose mode on.
-V or --version: Displays the current version number.
-u or --unattended: Unattended installation ( bypasses all prompts ).
```


Firewall Updates
----------------

Option | Original Value | New Value
--- | --- | ---
`RESTRICT_SYSLOG` | 0 | 3
`SMTP_BLOCK` | 0 | 1
`LF_SCRIPT_ALERT` | 0 | 1
`SYSLOG_CHECK` | 0 | 1800
`PT_ALL_USERS` | 0 | 1

SSH Updates
----------------
Any options that have `(prompt)` means you will be prompted to specify your own custom value if `-u` was not used as an argument.

Option | Original Value | New Value
--- | --- | ---
`Port` | 22 | 222 (prompt)
`UseDNS` | yes | no


cPanel Config Updates
----------------

Option | Original Value | New Value
--- | --- | ---
Shell Fork Bomb Protection | Disabled | Enabled
Compiler Access | Enabled | Disabled
Root Forwarder Email | None | User Specified (prompt)


Pure FTP Updates
----------------

Option | Original Value | New Value | Result
--- | --- | --- | ---
`RootPassLogins` | yes | no | Can't login with root pw
`AnonymousCantUpload` | no | yes | Anonymous can't upload
`NoAnonymous` | no | yes | Anonymous can't login


cPanel Tweak Settings Updates
-----------------------------

Option | Original Value | New Value
--- | --- | ---
BoxTrapper | Enabled | Disabled
Referrer Blank Sanity Check | Disabled | Enabled
Referrer Safety Check | Disabled | Enabled
Hide Login PW from CGI Scripts | Disabled | Enabled
Max Emails Account Can Send Per Hour | Unlimited | 199


MySQL Settings Updates
-----------------------

Option | Original Value | New Value
--- | --- | ---
local-infile | 1 | 0


PHP Configuration Updates
--------------------------

Option | Original Value | New Value
--- | --- | ---
enable_dl | On | Off
disable_functions | None | show_source, system, shell_exec, passthru, exec, phpinfo, popen, proc_open, allow_url_fopen, ini_set