<!-- ABOUT THE PROJECT -->
## 1.) About the project Details
<div id="About_the_project_Details"></div>

This will document how to use Windows 11 Native IPSec IKEv2 VPN, as well as StrongSwan on Andriod with a Fortigate using the maximum security settings both Windows and FortiOS support as of 2026. We will be using Machine Certifiacte Based User Authentication for this setup which means we need to create our own certificates, install them into FortiOS, install them on our Andriod Phone and install them on Windows. 


## 2.) Create Certificate Signing Request
<ol>
<li>From Microsoft Windows, click **Start.**</li>
<li>In the Search programs and files field, type **mmc.**</li>
<li>Click  **File > Add/Remove Snap-in.**</li>
<li>From the list of available snap-ins, select **Certificates.**</li>
<li>Click **Add.**</li>
<li>Select **Computer account.** </li>
<li>Click **Next.**</li>
<li>Select **Local computer **(the computer this console is running on).</li>
<li>Click **Finish.**</li>
<li>In the Add/Remove Snap-in window, click **OK.**</li>
<li>Save these console settings for future use.</li>
<li>Access your MMC snap in > right click the **Personal** folder.</li>
<li>
  Select **All Tasks > Advanced Operations > Create Custom Request.**
  ![create-custom-request](https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/create-custom-request.png)
</li>
<li><a href="#Grafana">Grafana</a></li>
<li><a href="#influxDB">influxDB</a></li>
<li><a href="#jackett">jackett</a></li>
<li><a href="#plex">plex</a></li>
<li><a href="#radar">radar</a></li>
<li><a href="#sickchill">sickchill</a></li>
<li><a href="#nginx_reverse_proxy">nginx Reverse Proxy</a></li>
<li><a href="#jellyfin">jellyfin</a></li>
<li><a href="#tautulli">tautulli</a></li>
<li><a href="#Chromium">Chromium</a></li>
<li><a href="#Torrent_downloader_VPN">Torrent down-loader + VPN</a></li>
<li><a href="#ngninx_PHP_Maria_DB_Stack">ngninx + PHP + MySQL Stack + PHPMyAdmin</a></li>
<li><a href="#urbackup">UrBackup</a></li>
<li><a href="#Grey_log">Grey log</a></li>
<li><a href="#flaresolverr">flaresolverr</a></li>
<li><a href="#ytdlp">YT-DLP</a></li>
<li><a href="#dozzel">Dozzel</a></li>
<li><a href="#convertx">ConvertX</a></li>
</ul>
<li><a href="#Data_Logging_Exporting_to_Influx_DB_v2">Data Logging Exporting to Influx DB v2</a></li>
<li><a href="#Install_script_to_pull_TrueNAS_SNMP_data">Install script to pull TrueNAS SNMP data + Non-SNMP Data like GPU Details</a></li>
<li><a href="#Setup_Grafana_Dashboard_for_TrueNAS">Setup Grafana Dashboard for TrueNAS</a></li>   
<li><a href="#Setup_Custom_Logging_Scripts_and_Configure_CRON">Setup Custom Logging Scripts and Configure CRON</a></li> 
<li><a href="#Cloud_backups_to_BackBlaze_B2_Bucket">Cloud backups to BackBlaze B2 Bucket</a></li>
<li><a href="#Replace_DS_File_app_Android_Only">Replace “DS File” app – Android Only</a></li>
<li><a href="#Configure_Data_Scrubs">Configure Data Scrubs</a></li>
<li><a href="#Schedule_SMART_tests">Schedule SMART tests</a></li>
<li><a href="#Configiure_email_sending_from_CLI">Configure Email Sending From CLI</a></li>
<li><a href="#Configure_Remote_Access_using_Tail_Scale">Configure Remote Access using Pangolin</a></li>
<li><a href="#Mount_External_NFS_Shares_into_TrueNAS_Dataset">Mount External NFS Shares into TrueNAS Dataset</a></li>
<li><a href="#General_Little_Settings_Here_and_There">General Little Settings Here and There</a></li>
<li><a href="#Rsync_Files_From_Synology_to_TrueNAS">Rsync Files From Synology to TrueNAS</a></li>
<li><a href="#On_Systems_with_IPMI_supported_motherboards">On Systems with IPMI supported motherboards</a></li>
<li><a href="#File_Managers">File Managers</a></li>
<li><a href="#app_backups">Automated APP Backups</a></li>
  </ol>
