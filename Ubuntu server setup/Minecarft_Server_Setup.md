# Minecraft sever setup for Raspberry Pi

## First step: Install Ubuntu-server 
* Remember to install ssh to your server. This will make the installation process easier
* Login in to your server over ssh.
* Minecraft needs Java 8 or higher. Install Java OpenJDK version 8 or higher.
`sudo apt install openjdk-8-jre-headless`
* Make sure that port 25565 is open on your server. (The Minecraft server will listen on this port)
`sudo ufw allow 25565`



## Setup a user and a user group for the Minecraft server service
* You new to create a new user and a user group for the Minecraft-server service.
* Call the new user whatever i.e 'minecraft'. This user should NOT be able to run root.
`sudo adduser --system --home /srv/minecraft-server minecraft`
`sudo addgroup --system minecraft`
`sudo adduser minecraft minecraft`
* Continue the installation on the new minecraft user
`sudo chown -R minecraft.minecraft /srv/minecraft-server`

## Download the Minecraft server java edition
* Find the download link to the newest server.jar
* Download using `wget`. Install `wget` is you don't have it installed
* Make sure you download server.jar inside your minecraft-server folder you created
* To download minecraft server 1.17 use `wget https://launcher.mojang.com/v1/objects/a16d67e5807f57fc4e550299cf20226194497dc2/server.jar`



### Link to referance guide
`https://minecraft.fandom.com/wiki/Tutorials/Ubuntu_startup_script`

