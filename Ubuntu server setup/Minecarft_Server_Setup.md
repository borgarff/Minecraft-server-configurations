# Minecraft sever setup for Ubuntu/Debian

## First step: Install Ubuntu-server 
* Remember to install ssh to your server. This will make the installation process easier
* Login in to your server over ssh.
* Minecraft needs Java 11 or higher. Install Java OpenJDK version 11 or higher.
`sudo apt install openjdk-11-jre-headless`
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
* Change ownership to minecraft `chown minecraft:minecraft server.jar`
* You can run minecraft server from root with this command `runuser -u minecraft -- java -Xmx1024M -Xms1024M -jar server.jar nogui`
* Remember to update the eula. Set it to `eula=true`
* Make sure that all other files in the minecraft directory is in the right group and is owned by the minecraft user `chown minecraft:minecraft *`
* Create the systemd.service file `vim /lib/systemd/system/minecraft-server.service`
* Enable the service `systemctl enable minecraft-server.service`
* Start the minecraft server service `systemctl start minecraft-server.service` 

### Link to referance guide
`https://minecraft.fandom.com/wiki/Tutorials/Ubuntu_startup_script`

