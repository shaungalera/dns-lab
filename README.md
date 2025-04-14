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


