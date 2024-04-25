# Ubuntu  Server Setup

## <span style="font-variant: small-caps;">Introduction</span>

The following project focuses on repurposing an old computer into a network storage device using Ubuntu Server and Samba, while also transforming it into a downloading box with software like JDownloader 2 for direct downloads and QBittorrent for torrent downloads.

There are many reasons to want your own server. My primary reason is storage; I constantly run out of storage on my main device so instead of formatting my device every few months, I plan to download everything I need onto my server and use it as I please.

## <span style="font-variant: small-caps;">Preparation</span>


#### What you will be needing:
    
HARDWARE
- An old PC or Laptop
- Another PC or Laptop you will be sshing into the server from
- An ethernet cable for your old device (This is recommend to keep a stable internet connection for your server) 
- A flash drive (If you want to use a flash drive as your bootdrive you will need two flash drives)

SOFTWARE

#### Use the software you are comfortable with. Since this document covers Ubuntu Server that is the OS we will be using. For USB boot software I have only used Rufus, but a quick Google search recommended me these alternatives. You don't have to use the same software as me but expect my setup to be different from yours if you do.

- A copy of Ubuntu Server or you choice of OS. [LINK](https://ubuntu.com/download/server)
- A copy of utility software to create bootable USB drives. 
  - For WINDOWS I recommend Rufus. [LINK](https://rufus.ie/en/)
  - For LINUX it is recommend that you use VENTOY. [LINK](https://www.ventoy.net/en/download.html)
  - For MAC OS it is recommend that you use ETCHER. [LINK](https://etcher.balena.io/#download-etcher)

NETWORK

#### You need to reserve an IP address (DCHP) for your server. To do that you need to have the mac address.

#### The follwing instructions are for the ZYXEL Router. 

FINDING THE MAC ADDRESS:
1. Open a brower and enter your IP address. 
   1. To find your IP address on a window machine open command promt and type "ipconfig".
   2. You are looking for the "Default Gateway". It is generally 192.168.1.1
2. Login to your router. (the password and username on the back of the router) 
3. Click on "CONNECTIVITY", find the server MAC address. **NOTE: For this to work the device you are planning on turning into your sever needs to be connected to the network** 
4. If the device is on and connected to the network it should appear here. If it is connected via WiFi check the "WiFi" Page, if it is wired check the "Wired" Page.

SETTING THE STATIC IP:

5. Click on the 3 horizontal lines in the corner.
5. Click on "NETWORK SETTING" > "HOME NETWORK" > "STATIC DHCP".
6. Click on "+ STATIC DHCP CONFIGURATION". 
7. The only things you are chaning are:
   1. Add the MAC Address to the inputbox next to "MAC ADDRESS".
   2. Add your chosen IP address to the inputbox next to "IP ADDRESS". **NOTE: Only change the last 3 digits of the IP leave the rest as is**

### USE THE FOLLOWING IMAGES AS A VISUAL GUIDE
#### GETTING YOUR IP ADDRESS
<img src="./images/Setting Static IP/IP ADDRESS.png" alt="Image of finding IP address" width="200"/>

#### FINDING DEVICE MAC ADDRESS
<img src="./images/Setting Static IP/CONNECTION.png" alt="Image of path to Device" width="300"/>

<img src="./images/Setting Static IP/FIND MAC ADDRESS.png" alt="Image of devices connected to network" width="350"/>

#### GETTING TO STATIC DHCP
<img src="./images/Setting Static IP/TRIPLE LINE.png" alt="Image of path to DHCP" width="300"/>

<img src="./images/Setting Static IP/NETWORK SETTINGS.png" alt="Image of path to DHCP" width="100"/>

<img src="./images/Setting Static IP/GETTING TO DHCP.png" alt="Image of path to DHCP" width="300"/>

<img src="./images/Setting Static IP/CREATING NEW STATIC DHCP.png" alt="Image of DHCP Page" width="300"/>

#### ADDING STATIC DHCP
<img src="./images/Setting Static IP/ADDING IP AND MAC ADDRESS.png" alt="Image of adding new Static DHCP" width="300"/>




## <span style="font-variant: small-caps;">Setup</span>

### Overview of Steps

#### - Step 1: Create a Bootable USB Drive
#### - Step 2: Installing and Configuring Ubuntu Server
#### - Step 3: Setting up and Configuring Samba

### STEP 1: CREATE A BOOTABLE USB (USING RUFUS)

#### I would recommend you keep all the default the same. You can change the name of the flash drive by changing the text under 'VOLUME LABLE'.

#### Process for windows:
1. Run the Rufus exe
2. Under 'DEVICE' select your flash drive
3. Under 'BOOT SELECTION' keep it on 'ISO IMAGE'
4. Click on 'SELECT' next to 'Boot selection'
5. Select the OS you want to use and click 'OPEN' **YOU NEED TO HAVE AN ISO COPY OF THE SOFTWARE ON YOUR MACHINE**
6. 'PARTITION SCHEME' depends on the scheme of your hard drive you are going to install it on. I recommend leaving it as default.
7. 'TARGET SYSTEM' depends on your motherboard if you have an old motherboard I recommend leaving it as default.
8. Click on 'START' to start the process.
9. If you get the POPUP 'ISO HYBRID IMAGE DETECTED' just use the recommened option.

</br>
<span style="font-size: 18px; font-weight: bold;">ISO HYBRID POP UP</span>
</br>
<img src="./images/Creating Bootdrive/ISOHybrid image detected.png" alt="Image of ISO HYBRID IMAGE DETECTED popup" width="50%"/>
</br>
</br>

<span style="font-size: 18px; font-weight: bold;">Completed Rufus Setup</span>
</br>
<img src="./images/Creating Bootdrive/Rufus.png" alt="Image of Completed Rufus Setup" width="50%"/>


### STEP 2: Install Ubuntu Server on your chosen device

**Note: The installation process will wipe the device you choose to install the OS on.**
**BACKUP ANY DATA BEFORE CONTINUING**

1. Plug the flash drive with the chosen OS on it into your old device. If you are planing on installing your chosen OS on a flash drive plug in the other flash drive as well. 
   
2. Start Up the device and boot into the BIOS.
   
3. Set the boot device to your flash drive with the OS on it (Some BIOS's will allow you to select the boot device without going futher into the BIOS by pressing F12. Check if your BIOS allows this.). Continue the Start Up process.
   

**All the steps below this is for Ubuntu Server 22.04.4**

*Things to note: To select something press on the spacebar. To move around use the arrow keys. When you are done configuring on a page move to the bottom and select done*

**If you cannot make out an image, click on it to enlarge it.**

1. When it fully boots up you should see the following screen. Select "Try or Install Ubuntu Server".
   
2. Welcome Page:
   
   Select your prefered language and press "ENTER" or "SPACEBAR". *If your welcome message is in a languege you dont understand dont worry by select your chosen language the rest of the setup changes to that language.*

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/4. Select Language.PNG" alt="Select Language" width="20%"/> 
</div> 
</br>
</br>

3. Keyboard Configuration:
   
   Select your prefered keyboard configuration.  

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/6. Keyboard Config.PNG" alt="Keyboard Config" width="20%"/>  
</div>
</br>
</br>


4. Choose Type of Install:
   
   Select the type of installtion, I will be using "Ubuntu Server", if you don't need/want the extra features you can choose Ubuntu Server minimized (This guide will not be doing the minimized version). 

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/6. Keyboard Config.PNG" alt="Keyboard Config" width="20%"/>  
</div>
</br>
</br>

5. Network Connections:
   
   Check the IP address that is displayed is the same as what you made it. 

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/8. Network connection.PNG" alt="Network Connection" width="20%"/>  
</div>
</br>
</br>

6.  Configure Proxy:
    
    If you have a prooxy address this is where you fill it in. 

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/9. Configure proxy.PNG" alt="Configure Proxy" width="20%"/>  
</div>
</br>
</br>

7.  Configure Ubuntu Archive Mirror:
    
    You'll see that Ubuntu is trying to load something. What it is doing is testing the mirror location, it is advized that you let this finish as it only takes a minute max. You'll know it completed by it telling you "This mirror location passed tests". 

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/10. Configure Ubuntu Archive mirror.PNG" alt="Configure Ubuntu Archive Mirror" width="20%"/>  
</div>
</br>
</br>    
    
8.  Guided Storage Configuration:
    
    This is where you decide where you want to install Ubuntu Server. To select a hard drive navigate to below "USE AN ENTIRE DISK" and click spacebar this will bring up all your different harddrive option, select the one you want to use.
    
    It is recommended that you deselect "SET UP THIS DISK AS AN LVM GROUP", if it is enable it will split your drive into multiple volumes and not use the entire space.

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/11. Guided Storage configuration.PNG" alt="Guided Storage Configuration" width="20%"/>  
</div>
</br>
</br>

9.  Storage Configuration:
    
    This part show you the option you have selected as an install drive and other drives you have available. Double check your work before continueing as this is the final step.  You will receive a popup asking to confirm this action. Select continue and click "ENTER" or "SPACEBAR".

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/12. Storage Configuration.PNG" alt="Storage Configuration" width="20%"/>  
</div>
</br>
</br>

10. Profile Setup:

    Fill in the details.
    
    *Note: "Your servers name is the name that will be displayed on the network, "Pick a username" is the username you will be using to login into this machine from another machine same goes for the password.*

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/13. Profile Setup.PNG" alt="Profile Setup" width="20%"/>  
</div>
</br>
</br>

11. Upgrade to Ubuntu Pro:

    If you want Ubuntu Pro, select enable. *I have not used Ubuntu Pro before so I cannot speak on the benifits or negatives.*

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/14. Upgrade to Ubuntu Pro.PNG" alt="Upgrade to Ubuntu Pro" width="20%"/>  
</div>
</br>
</br>

12. SSH Setup:

    Select Install OpenSSH server. *This will allow you to ssh into your server later on.*

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/15. SSH Setup.PNG" alt="SSH Setup" width="20%"/>  
</div>
</br>
</br>

13. Featured Server Snaps:
    
    This page list various programs that you can install on your server immedietly. *Don't worry about picking a program as you can always install it later.*

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/16. Feature Server Snaps.PNG" alt="Featured Server Snaps" width="20%"/> 
</div> 
</br>
</br>

14. Installing System:

    WELLDONE, this is the final part. Wait for Ubuntu Server to install onto your old hardware. This process could take someone time so come back in like a half an hour.

    When the process is done select "REBOOT NOW" and remove the Bootdrive USB.

</br>
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/17. Installing System.PNG" alt="Installing System" width="20%"/> 
</div>
</br>
</br>

15.  What SUCCESS looks like:
<div style="text-align:center">
<img src="./images/Ubuntu Server Install/18. What success looks like.PNG" alt="Installing System" width="50%"/> 
</div>