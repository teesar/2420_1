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




## Step 2: Download Arch Linux Image


## Upload Arch Linux Image to Digital Ocean

## Create Droplent Running Arch Linux

## Create Digital Ocean API Key

## Install Doctl On Droplet

## Create Config File On Droplet

## Create New Droplet 