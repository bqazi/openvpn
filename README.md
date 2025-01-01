![openvpm image](https://github.com/bqazi/openvpn/blob/main/openvpn_azure.png) <br><br>

## Overview
In this tutorial, we will set up an OpenVPN server on an Azure virtual machine. 
We can choose any region of the world that’s available on Azure to connect to around the world. 
VPNs are the primary way to hide our internet traffic from our ISP or other spies. We will confirm the VPN is 
working at the end with an ip address and location checker tool. 

### Part 1/5
On the Azure portal, navigate to the `Create a resource` > search for `Open VPN` > 
select `OpenVPN Access Server` > `Create new` resource group > name your virtual machine > 
Change `Authentication type` to `Password` and set your login credentials > `Standard_D2s_v3 - 2 vcpus, 8 GiB memory` for `Size` > 
`Next : Disks` > `128 GiB (P10)` for `OS disk size` > `Next : Networking` > leave the default network settings and click `Review + create` > 
`Create` > deployment will be complete within a few minutes.

### Part 2/5
Navigate to `openvpn.net` and create a free access server account > 
use the free services that provides 2 connections or use a subscription if you’d like more connections.

### Part 3/5
Using command line*, you will now ssh into the OpenVPN server using the following command: `ssh <azure vm admin username>@<azure public ip address>` <br><br>
E.g. `ssh myopenvpnserver@172.111.22.333`<br><br>
Next, type `yes` > enter password > once the connection is established, proceed with the default yes/allow until you reach the following prompt 
`Do you wish to login to the Admin UI as openvpn` and type `no` > set a new username and password to access the server > continue selecting the 
default yes/allow until the configuration is complete. <br><br>
*Note: you can also use applications such as PuTTY or MobaXterm if you’d like a GUI

### Part 4/5
Next, type the following onto your web browser to access the server `https://<your azure public ip>/admin` > proceed anyway > 
use your credentials made on the command line > Navigate to your original openVPN account you made on the browser, copy the activation key, 
paste it into the the server site, and activate > `Configuration` > `Network Settings` > 
type your azure public ip address > save settings.

### Part 5/5
Download and install the client for your operating system using openvpn.net/client/ > Connect via URL by typing `https://<azure public ip address>` > 
type your credentials made on the command line, select `connect after import`, enter password, and you are now connected. <br>

To test your connection, you can check your location on Google by turning off your vpn and turning it back on. 
You can also do the same with your ip address using a site such as whatsmyip.org You should have two 
different locations when the VPN is on and when it’s off. <br>

Once your connection is complete, you can add other virtual machines to your virtual networks using OpenVPN client, add MFA to user accounts, and more. <br>

## Licensing
Note that Microsoft Azure and OpenVPN client require a subscription if you would like to use the platforms at scale or for commercial use.
	
