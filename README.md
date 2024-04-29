<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
  Create a VM for Windows and create a VM for Linux
- Step 2
  Remote Desktop into your windows VM
- Step 3
  Download, install and run Wireshark
- Step 4
  Open Microsoft Powershell
- Step 5
  Entering commands for pinging VM2 from VM1

  
<h2>Actions and Observations</h2>

<p>
  
![VM window and Linux](https://github.com/Onstarva/azure-network-protocols/assets/166679644/7f11c016-61e3-47cf-8020-899618b2b9ef)
![Wireshark](https://github.com/Onstarva/azure-network-protocols/assets/166679644/7598d104-cd19-4292-93ea-54dc6a0a7c70)
![Capturing packets via Wireshark](https://github.com/Onstarva/azure-network-protocols/assets/166679644/906fe341-7a3e-4bd6-b082-a3d2396d51e4)
![live traffic](https://github.com/Onstarva/azure-network-protocols/assets/166679644/f0b71cf2-d949-414c-8cbd-dd6259a0f828)



</p>
<p>
You want to create a VM and resourse group using Windows 10 using 2vcpus. Make another VM with linux connected in the same resource group, region and 2vcpus. Now connect to Windows VM via remote desktop and login. Once the VM windows is done starting up, go to your internet browser and search for Wireshark. Download Wireshark for windows and install it. Once installed, open Wireshark and click Ethernet and click the Blue Sharkfin at the top left of your screen to start capturing packets. You'll now see the live IP traffic that is happening on your VM. Click the top tect line and filter traffic by typing icmp(Internet Control Messaging Protocal) and hit enter. 
</p>
<br />

<p>
  
![VM Ip address](https://github.com/Onstarva/azure-network-protocols/assets/166679644/72dd0933-e37e-47ed-afef-298a3dd8f613)
![Pinging VM2](https://github.com/Onstarva/azure-network-protocols/assets/166679644/72e3b77b-38dc-4583-90c4-d55e7d740a4f)
![IPV4](https://github.com/Onstarva/azure-network-protocols/assets/166679644/25dd90ba-c083-4439-9a4a-846915df6f56)
![-t pings](https://github.com/Onstarva/azure-network-protocols/assets/166679644/b69c5a78-153d-4673-8a38-05c4f5f0693f)




</p>
<p>
Now to ping VM2 from VM1. Go back to Azure Portal and find VM2's Private IP address, copy it and back into VM1. Open Windows Powershell while in VM1 and use the command ping # (paste ip address for #) and hit enter. You will see it pinging VM2 from VM1 along with it's packets. You can use the same command to ping sites like google.com and get different ping replys back. The variety ping commands do the following.
  
- Forcing connections to Ipv4: -4
- Infinite Pings: -t
- Hold and hit Cntl - c to stop infinite Pings
  
</p>
<br />

<p>
  
![SSH](https://github.com/Onstarva/azure-network-protocols/assets/166679644/a4f8d374-9912-4a31-b977-0443f6d5b35d)
![SSH connected to VM2](https://github.com/Onstarva/azure-network-protocols/assets/166679644/718bec77-a7b4-499d-b140-7ede0fd911cf)


</p>
<p>
Now to Filter SSH (shell) go back to the top text box and type SSH and hit enter. Go back into Powershell the following commands. You will be asked if you wish to continue, type yes and enter. Now enter the usernames password, do note when you type you will not see any text typing when you type. Enter said usernames password and hit enter and if a connection is established you will get a comfirmation from Powershell saying your connected to VM2 in green text. If you wish to disconnect from VM2 to VM1. Type exit and hit enter.
  
- ssh username@ # (Example: ssh labsuser@10.0.0.5).
  
</p>
<br />

<p>
  
![DHCP traffic](https://github.com/Onstarva/azure-network-protocols/assets/166679644/b352a1db-6b50-4231-b524-c4d65eb64f89)


</p>
<p>
To observing DHCP traffic. Go back to the top text section and type DHCP and hit enter. If you wish to renew your IP address, type ipconfig /renew and you will be re-assigned an IP address.
  
- Re-issues IP address: ipconfig /renew
  
</p>
<br />

<p>
  
![DNS traffic](https://github.com/Onstarva/azure-network-protocols/assets/166679644/6108db23-5c06-4e3c-98e8-4d46ed291470)


</p>
<p>
To view DNS traffic. Go back to the top text section and type DNS. In Powershell type nslookup followed by the site name and hit enter to ask what the IP address is of a site.
  
- Ask what IP a site is using: nslookup www.google.com

</p>
<br />

<p>
  
![RDP traffic spam](https://github.com/Onstarva/azure-network-protocols/assets/166679644/36371372-c4ba-40f3-95f0-dc03d93be56e)


</p>
<p>
To observe RDP traffic. Go back to the top text section and type RDP. Do note it will be spamming traffic since you're connecting your computer to a Virtual Machine. Whenever you do anything it will send traffic, typing included.


</p>
