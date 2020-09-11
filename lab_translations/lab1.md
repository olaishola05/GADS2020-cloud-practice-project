# Fundamentals: Getting Started with Compute Engine

In this lab, you will create virtual machines (VMs) and connect to them. You will also create connections between the instances.

## Objectives:

-   Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

-   Create a Compute Engine virtual machine using the gcloud command-line interface.

-   Connect between the two instances.

## Step 1:

### Create a virtual machine

`gcloud compute instances create "my-vm-1" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default" --tags http`

### Creating firewall rules

`` `gcloud compute firewall-rules create allow-HTTP --action=ALLOW --destination=INGRESS --rules=http:80 --target-tags=http`

## Step 2:

### Create second VM instances

Getting list of zones and choose desired zone

`gcloud compute zones list | grep us-central1`

### To set your default zone to the one you just chose:

`gcloud config set compute/zone us-central1-b`

### Create VM instance

`gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default"`

## Step 3:

Connecting to VM instance 2 using SSH

`ssh my-vm-2 `

Ping my-vm-1

`ping -c 3 my-vm-1`

Connecting to my-vm-1 from my-vm-2

`ssh my-vm-1`

Install the Nginx web server on my-vm-1:

`sudo apt-get install nginx-light -y`

Use the nano text editor to add a custom message to the home page of the web server:

`sudo nano /var/www/html/index.nginx-debian.html`

Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:

`Hi from Ola`

Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

Confirm that the web server is serving your new page

`curl http://localhost/`

-   To exit the command prompt on my-vm-1, execute this command:
    `exit`

To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:

`curl http://my-vm-1/`

Copy the External IP address for my-vm-1 and paste it into the address bar of a new browser tab.

Get external IP address of my-vm-1

`gcloud compute instances list` or `gcloud compute instance list --zone us-central1-a`

Paste external IP address a browser on a new tab and hit **Enter** key, You will see your web server's home page, including your custom text
