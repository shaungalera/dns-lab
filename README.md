<p a href="center">

![image](https://github.com/user-attachments/assets/2fe7465c-256e-48a1-a8ad-cdd2d874dae4)

</P>

<h1>Microsoft Azure DNS Lab Tutorial</h1>

<h2>Introduction</h2>

This lab focuses on DNS configuration and testing using A-Records, Local DNS Cache, and CNAME Records. We will be utilizing the DC-1 and Client-1 virtual machines (VMs) that were set up in the previous Active Directory lab. Ensure that these VMs are properly configured and running before proceeding with the exercises.

<h2>Prerequisites</h2>

.Access to **DC-1** and **Client-1** VMs.<br />
.Administrator credentials for the domain: mydomain.com\jane_admin (from the AD lab).<br>
.Working knowledge of DNS records.<br>

<h2>A-Record Exercise</h2>

**1.) Connect to DC-1**:<br />
.Log into DC-1 using the domain admin account: mydomain.com\jane_admin.<br>
**2.) Connect to Client-1**:<br />
.Log into Client-1 as an admin: mydomain\jane_admin.<br>
**3.) Verify that "mainframe" is Unreachable**:<br />
.On Client-1, open the Command Prompt and run:<br>
 "ping mainframe"<br>
.Observe that the ping fails<br>
.Run the following command to check for the DNS record: 'nslookup mainframe' Observe that it fails (no DNS record exists).<br>

![image](https://github.com/user-attachments/assets/f971a99c-8eab-4fe4-abfc-210e6ba1b7f3)

**4.) Create a DNS A-Record**:<br />
.Switch to DC-1.<br>
.Open the DNS Manager.<br>
.Navigate to the appropriate forward lookup zone.<br>
.Add an A-Record for mainframe and point it to DC-1's Private IP address.<br>

**.Right click in open space**<br>

![image](https://github.com/user-attachments/assets/a19c84e3-7aee-4854-a49c-5ef9f72e45b9)
![image](https://github.com/user-attachments/assets/e177db3f-dac3-4d4b-9b19-1400878cd326)

**5.) Verify Connectivity to "mainframe"**:<br />
.Go back to Client-1.<br>
.Run: ping mainframe<br>
.Observe that the ping is now successful.<br>

![image](https://github.com/user-attachments/assets/d8e61c9b-30a6-40f3-99e6-0619363cd9a7)

<h2>Local DNS Cache Exercise</h2>

**1.) Modify the A-Record**<br>
.On DC-1, change the mainframe A-Record to point to 8.8.8.8.<br>

![image](https://github.com/user-attachments/assets/358d57c6-9719-4eb5-aebe-fba6404ed81a)

**2.) Ping "mainframe" from Client-1**:<br />

.On Client-1, run: ping mainframe<br>
.Observe that the ping still resolves to the old address (cached locally).<br>

**3.) Check the Local DNS Cache**:<br />

.On Client-1, display the DNS cache using: ipconfig /displaydns<br>
.Observe the cached record for mainframe.<br>

**4.) Flush the DNS Cache**:<br />

.Clear the local DNS cache using (you may need to run powershell as administrator): ipconfig /flushdns<br>

**5.) Verify Cache Clearing**:<br />

.Confirm the cache is empty by running: ipconfig /displaydns<br>

**6.) Verify the Updated A-Record**:<br />

.Attempt to ping mainframe again: ping mainframe<br>
.Observe that it now resolves to the updated address (8.8.8.8).<br>

![image](https://github.com/user-attachments/assets/275d0899-fda2-4348-b396-d1eeaed46232)

<h2>CNAME Record Exercise</h2>

**1.) Create a CNAME Record**:</br>
.On DC-1, open the DNS Manager.<br>
.Navigate to the appropriate forward lookup zone.<br>
.**Add a CNAME Record**:<br>
*Alias*: bubble.<br>
*Points to*: www.google.com.<br>

![image](https://github.com/user-attachments/assets/e508c921-d71c-411f-b220-f34fd22095d5)

**2.) Test the CNAME Record**:<br />

.On Client-1, ping search: ping search<br>
.Observe the results of the CNAME record resolution.<br>

**3.) Verify Using nslookup**:<br />

.On Client-1, run: nslookup search<br>
.Observe the results, ensuring the alias resolves to www.google.com.<br>


![image](https://github.com/user-attachments/assets/f86bed4f-9ebd-48b1-83cd-1a2c77b40faf)

<h2>Conclusion</h2>

Congratulations! You have successfully completed the DNS exercises for A-Records, Local DNS Cache, and CNAME Records.
