<!-- ABOUT THE PROJECT -->
## 1.) About the project Details
<div id="About_the_project_Details"></div>

This will document how to use Windows 11 Native IPSec IKEv2 VPN, as well as StrongSwan on Andriod with a Fortigate using the maximum security settings both Windows and FortiOS support as of 2026. We will be using Machine Certifiacte Based User Authentication for this setup which means we need to create our own certificates, install them into FortiOS, install them on our Andriod Phone and install them on Windows. 


## 2.) Create Certificate Signing Request
<ol>
<li>From Microsoft Windows, click <strong>Start.</strong></li>
<li>In the Search programs and files field, type <strong>mmc.</strong></li>
<li>Click  <strong>File > Add/Remove Snap-in.</strong></li>
<li>From the list of available snap-ins, select <strong>Certificates.</strong></li>
<li>Click <strong>Add.</strong></li>
<li>Select <strong>Computer account.</strong> </li>
<li>Click <strong>Next.</strong></li>
<li>Select <strong>Local computer </strong>(the computer this console is running on).</li>
<li>Click <strong>Finish.</strong></li>
<li>In the Add/Remove Snap-in window, click <strong>OK.</strong></li>
<li>Save these console settings for future use.</li>
<li>Access your MMC snap in > right click the <strong>Personal</strong> folder.</li>
<li>
  Select <strong>All Tasks > Advanced Operations > Create Custom Request.</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/create-custom-request.png" alt="create-custom-request" />
</li>
<li>
  The CSR generation wizard will open > Click <strong>Next.</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/before-you-begin.png" alt="before-you-begin" />
</li>
<li>
  Select the option to <strong>Proceed without enrollment policy</strong> > Click <strong>Next.</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/proceed-without-enrollment-policy.png" alt="proceed-without-enrollment-policy" />
</li>
<li>
  Click <strong>Next</strong> at the PKCS # 10 window.
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/select-pkcs-10.png" alt="select-pkcs-10" />
</li>
<li>
  From the <strong>Details</strong> drop-down menu > Click <strong>Properties.</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/certificate-enrollment-properties.png" alt="certificate-enrollment-properties" />
</li>
<li>
  Enter a <strong>Friendly Name</strong> and <strong>Description</strong> of your choosing. Suggest set to ipv4.mydomain.com
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/friendly-name.png" alt="friendly-name" />
</li>
<li>
  Access the <strong>Subject</strong> tab in the <strong>Subject name:</strong> Type: field add the following distinguish name values required for your CSR<br><br>
  <strong>Common Name</strong> set to the value of ipv4.mydomain.com<br><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/add-subjects.png" alt="add-subjects" />
</li>
<li>
  Access the <strong>Extensions</strong> tab<br><br>
  Under <strong>Key Usage</strong>, Ensure <strong>Data encipherment</strong> and <strong>Key encipherment</strong> are moved over to the right using the <strong>Add</strong> button<br><br>
  Under <strong>Extended Key Usage (application policies)</strong> ensure <strong>Server Authentication</strong> and <strong>Client Authentication</strong> are moved over to the right using the <strong>Add</strong> button<br><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/extensions1.png" alt="extensions1" /><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/extensions2.png" alt="extensions2" />
</li>
<li>
  Click the <strong>Private Key</strong> tab > click the drop-down for <strong>Key options</strong> and select <strong>Key size</strong> to be a value of <strong>2048</strong> and check the option to <strong>Make private key exportable</strong> anmd Click <strong>OK</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/make-private-key-exportable.png" alt="make-private-key-exportable" />
</li>
<li>
  Click the drop-down for <strong>Select Hash Algorithm</strong>, under Hash Algorithm select <strong>sha256</strong> and Click <strong>OK</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/select-hash-algorithm.png" alt="select-hash-algorithm" />
</li>
<li>
  Click <strong>Next</strong> and Click <strong>Browse</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/save-the-offiline-request.png" alt="save-the-offiline-request" />
</li>
<li>
  Select a location to save the CSR file. Enter <strong>request.csr</strong> for the file name and click <strong>Save</strong>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/name-csr-file-to-save.png" alt="name-csr-file-to-save" />
</li>
<li>
  Click <strong>Finish</strong> with the file format selected as <strong>Base 64</strong>
</ol>


## 3.) Export Certificate Signing Request Key
<ol>
<li>
  From within Windows Cert Manager, click <strong>Certificate Enrollment Requests --> Certificates</strong><br>
  <strong>Right Click</strong> on the requtest and select <strong>All Tasks --> Export...</strong><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export1.png" alt="export1" />
</li>
<li>
  Click <strong>Next</strong><br>
    <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export2.png" alt="export2" />
</li>
<li>
  Select <strong>Yes, export the private key</strong> and click <strong>Next</strong><br>
    <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export3.png" alt="export3" />
</li>
<li>
  Ensure all checkboxes are chosen <strong>EXCEPT</strong> for <strong>Delete the private key if export is sucessful</strong><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export4.png" alt="export4" />
</li>
<li>
  Create and Confirm a password. This password will be needed again laster when making our certificates. Ensure the <strong>Encryption</strong> is set to <strong>AES256-SHA256</strong> and click <strong>Next</strong><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export5.png" alt="export5" />
</li>
<li>
  Click <strong>Browse</strong> and save the key to the same place the signing request file was previously saved. Save the key file as file name <strong>requestkey.pfx</strong> and click <strong>Next</strong><br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export6.png" alt="export6" />
</li>
<li>
  Click <strong>Finish</strong><br>
    <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export7.png" alt="export7" />
  </li>
<li>
 From within Windows Cert Manager, click <strong>Certificate Enrollment Requests --> Certificates</strong><br>
  <strong>Right Click</strong> on the requtest and select <strong>Delete</strong> and confirm when the popup asks<br>
  <img src="https://raw.githubusercontent.com/wallacebrf/fortigate_windows_native_ikev2/refs/heads/main/images/export8.png" alt="export8" />
</li>
</ol>

