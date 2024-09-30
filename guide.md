<!-- Start of the project -->
# Assignment 1
## Heading 2
## Today we will be going through the steps necessary to host a droplet (virtual private server) on your Digital Ocean account, securely access it using ssh keys, and using your droplet to create a second droplet with a set configuration.

## Step 1: Create SSH Keys
- SSH keys are used to securely authenticate the identity of of a client when accessing a host. We will be creating two keys, one public key for the host, and one private key which will unlock access to the host.
1. Navigate to your home directory. 
- In windows this will generally be `C:\Users\username`, with username replaced by your windows username.
2. Check for the existence of a directory titled `.ssh`
3. If this directory does not exist please create it now.
- The .ssh directory will be used to store the SSH keys you create.

4. Open a terminal and run the following command:
- Note: Replace username with your windows username. Replace email@gmail.com with your email.
```
ssh-keygen -t ed25519 -f C:\Users\username\.ssh\one_key -C 
```
- Note: The -t flag defines the type of encryption the keys will use. In this case we'll be using the ed25519 standard.
- Note: The -f flag defines where on your computer we want to store the newly created keys. In this case the keys will use "one_key" as the name. email@gmail.com
- Note: The -C flag allows us to create a comment for the keys. You can use this comment to help you differentiate between keys that you create, or add an identifier such as your email to mark it as one you created. In this case the keys will simply use the email address you enter.

* You should now have two new files in your .ssh directory. The file called one_key is your private key, do not share this with anyone. The file called one_key.pub is your public key, and in the next step we will add it to your Digital Ocean account. 

## Step 2: Add Public SSH Key to Digital Ocean Account
1. Navigate to your .ssh directory and open one_key.pub with Visual Studio Code.
2. Copy the text string inside one_key.pub.

3. Navigate to the Digital Ocean website and log in to your account.

4. Click Settings on the left of the browser window.

5. Click the Security tab beneath the Settings heading.

6. Click Add SSH Key.

7. Paste the text string you copied from one_key.pub into the Public Key field.

8. Type in a name for your key in the Key Name field.
- Note: The key name can be used to help differentiate between keys that you add to your Digital Ocean account. 


## Step 3: Download Arch Linux Image
1. Navigate to https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/ .
2. Click images in the most recently uploaded row.
3. Click the image name that contains "cloudimg" and ends in ".qcow2".
- The download should start automatically and is roughly 500MB in size.

## Step 4: Upload Arch Linux Image to Digital Ocean
1. Navigate to the Digital Ocean website and log in to your account.
2. Click Backups & Snapshots on the menu on the left side of the screen.
3. Click Custom Images.
4. Click Upload Image.
5. Browse your computer to find the image you downloaded and press Open.
6. Click Choose a Distribution.
7. Click Arch Linux.
8. Click the Datacenter Region closest geographically to your location.
- Note: This is the server your image will be uploaded to, using the datacenter closest to your location will provide the lowest latency when accessing it.
9. Click Upload Image.
- Note: There will be a charge of $.06 per GB per month to store this image.


## Create Droplent Running Arch Linux

## Create Digital Ocean API Key

## Install Doctl On Droplet

## Create Config File On Droplet

## Create New Droplet 