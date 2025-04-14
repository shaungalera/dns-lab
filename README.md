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
.Log into Client-1 as an admin: mydomain\jane_admin.
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


