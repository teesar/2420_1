<!-- Start of the project -->
# Assignment 1

#### Today we will be going through the steps necessary to host a droplet (virtual private server) on your Digital Ocean account, securely access it using ssh keys, and use your droplet to create a second droplet with a set configuration.

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
![alt text](image-32.png)


3. Navigate to the Digital Ocean website and log in to your account.


4. Click Settings on the left of the browser window.
![alt text](image-33.png)


5. Click the Security tab beneath the Settings heading.
![alt text](image-34.png)


6. Click Add SSH Key.
![alt text](image.png)

7. Paste the text string you copied from one_key.pub into the Public Key field.
![alt text](image-1.png)

8. Type in a name for your key in the Key Name field.
- Note: The key name can be used to help differentiate between keys that you add to your Digital Ocean account. 
![alt text](image-2.png)

## Step 3: Download Arch Linux Image

1. Navigate to https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/ .

2. Click images in the most recently uploaded row.
![alt text](image-3.png)


3. Click the image name that contains "cloudimg" and ends in ".qcow2".
![alt text](image-4.png)

- Note: The number on your version may be different than appears here. The download should start automatically and is roughly 500MB in size.


## Step 4: Upload Arch Linux Image to Digital Ocean

1. Navigate to the Digital Ocean website and log in to your account.

2. Click Backups & Snapshots on the menu on the left side of the screen.
![alt text](image-5.png)


3. Click Custom Images.
![alt text](image-6.png)


4. Click Upload Image.
![alt text](image-7.png)


5. Browse your computer to find the image you downloaded and press Open.
![alt text](image-8.png)

6. Click Choose a Distribution.
7. Click Arch Linux.
![alt text](image-9.png)

8. Click the Datacenter Region closest geographically to your location.
- Note: This is the server your image will be uploaded to, using the datacenter closest to your location will provide the lowest latency when accessing it. San Francisco shown here for demonstration purposes.
![alt text](image-10.png)

9. Click Upload Image.
- Note: There will be a charge of $.06 per GB per month to store this image.
![alt text](image-11.png)


## Step 5: Create Droplent Running Arch Linux

1. Navigate to the Digital Ocean website and log in to your account.

2. Click Create near the top of the page.
![alt text](image-12.png)


3. Click Droplets.
![alt text](image-13.png)


4. Click the Region geographically closest to your location.
![alt text](image-14.png)


5. Click Custom Images below the Choose an image heading.

6. Click the image you uploaded in step 4.
![alt text](image-15.png)


7. Click Premium Intel or Premium AMD under the CPU options heading.
![alt text](image-16.png)


8. Click the $8/mo option.
![alt text](image-17.png)


9. Click SSH Key under the Choose Authentication Method heading.
![alt text](image-18.png)


10. Click the SSH key that you added to your Digital Ocean Account.
- Note: Your key names will be different from this sample image.
![alt text](image-19.png)


11. Delete the text in the Hostname field and replace it with a short nickname.
12. Click Create Droplet.
![alt text](image-20.png)


## Step 6: Create Digital Ocean API Key

1. Navigate to the Digital Ocean website and log in to your account. 
2. Click API on the left menu near the bottom.
![alt text](image-21.png)


3. Click Generate New Token.
![alt text](image-22.png)


4. Type a name for the token into the Token Name field.
![alt text](image-23.png)


5. Click Full Access. This will give your API key read and write permissions so that you can create and edit droplets through the command line.
![alt text](image-24.png)


6. Click Generate Token.
- The page will redirect you to the API section and a personal access token will appear.
![alt text](image-25.png)


7. Click the Copy icon to copy the personal access token, then save it in a safe place.
![alt text](image-26.png) 


## Step 7: Connect To Your Droplet Through SSH

1. Open a terminal window on your computer.
2. Copy and paste the following code into the terminal, but don't run it yet.
```
ssh -i .ssh/one_key arch@
```
2. Navigate to the Digital Ocean website and log in to your account.

2. Click the name of the project you saved your droplet in at the top of the left menu.
- Note: If this is your first Digital Ocean project, the project is likely called "first-project".
![alt text](image-27.png)


3. Click Copy next to the IP address of your droplet to copy it.
![alt text](image-29.png)


4. Return to the terminal window you opened and paste the ip address after the @ from your entry.
![alt text](image-30.png)


5. Press enter to run the command.
- Note: The -i flag is used to set the path to the private SSH key you created earlier.
- Note: The "arch" is a user that exists on the Arch Linux image.

- Your terminal prompt will change to arch@ followed by the droplet name if you connect successfully.

## Step 8: Install Software & Connect To Digital Ocean API

1. Update your droplet by running the following command:
```
sudo pacman -Syu
```
- Note: sudo gives you permission to modify the system
- Note: pacman is the package manager for installing, updating, or removing programs.
- Note: The flag -Syu finds the latest updates for installed packages and applies them.

- Note: This may take several minutes to complete.

2. Install neovim and doctl on your droplet by running the following command:
```
sudo pacman -S neovim doctl
```
- Note: Doctl is the command line interface for accessing Digital Ocean that you'll use for further droplet creation.
- Note: Neovim is a text editor you'll use to create a config file for automating aspects of droplet creation through the command line.

- Note: This may take several minutes to complete.

3. Run the following command to allow doctl to access your DigitalOcean account.
```
doctl auth init --context dev
```
- Note: The "dev" above is the label for your Digital Ocean account on doctl, you may change it to anything you like. 

4. Enter the Digital Ocean API key that you created on step 6 when you are prompted for it.

5. Run the following command to switch to the doctl account you just added.
```
doctl auth switch --context dev
```
- Note: If you changed the label for this account from dev on Instruction #3, replace it in the above code as well.

6. Run the following command to confirm your setup was successful.
```
doctl account get
```
![alt text](image-31.png)


## Step 9: Create Config File On Droplet

1. Enter the following command to create a droplet configuration file.
```
nvim droplets.sh
```

2. Type i to enter insert mode.

3. Copy the following code and paste it into your configuration file.
```
users:
  - name: ***
    groups: wheel
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - ***

packages:
  - neovim
  - doctl

disable_root: true
```

4. Delete the "***" after name: and then type a username you'll use to access the droplet.

5. Delete the "***" after the dash below ssh-authorized-keys: and then copy and paste the text contained in your public SSH key one_key.pub that you created on Step 1.

6. Hit the escape key.

7. Type ":wq" and press enter. This will write and save the file then quit nvim.

## Step 10: Create New Droplet 

1. Run the following command to locate the image you uploaded earlier.
```
doctl compute image list | grep Arch
```
- Note: This searches Digital Ocean for images that contain the word Arch. Your image should be the only one returned in the search results, but if not you can compare the name of the image to the one you downloaded to select the correct one.

2. Write down the number to the left of the image result.
3. Copy and paste the following command:
```
doctl compute droplet create archy --region sfo3 --size s-1vcpu-1gb-35gb-intel --image *** --user-data-file droplets.sh --ssh-keys *** --wait
```
4. Delete the "***" after image and replace it with the number you wrote down on Instruction #2.
5. Navigate to Digital Ocean and log in.
6. Click Settings near the bottom of the left menu.
7. Click Security.
8. Copy the Fingerprint of the key you created earlier.
9. Back on the terminal window, delete the "***" after ssh-keys and replace it with with the key fingerprint you have copied.
10. Enter the command. After a few moments you should receieve a message displaying statistics on your new droplet.

## Congratulations! You've accomplished everything!