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

## <span style="font-variant: small-caps;">Setup</span>

### STEP 1 CREATE A BOOTABLE USB (USING RUFUS)

#### I would recommend you keep all the default the same. You can change the name of the flash drive by changing the text under 'VOLUME LABLE'.

#### Process for windows:
1. Run the Rufus exe
2. Under 'DEVICE' select your flash drive
3. Under 'BOOT SELECTION' keep it on 'ISO IMAGE'
4. Click on 'SELECT' next to 'Boot selection'
5. Select the OS you want to use and click 'OPEN' **YOU NEED TO HAVE AN ISO COPY OF THE SOFTWARE ON YOUR MACHINE**
7. 'PARTITION SCHEME' depends on the scheme of your hard drive you are going to install it on. I recommend leaving it as default.
8. 'TARGET SYSTEM' depends on your motherboard if you have an old motherboard I recommend leaving it as default.
9. Click on 'START' to start the process.
10. If you get the POPUP 'ISO HYBRID IMAGE DETECTED' just use the recommened option.
<div style="text-align:center">
<img src="./image/ISOHybrid image detected.png" alt="Image of ISO HYBRID IMAGE DETECTED popup" width="100%"/>
</div>

<div style="text-align:center">
  <img src="./image/Rufus.png" alt="Image of Completed Rufus Setup" width="100%"/>
</div>

