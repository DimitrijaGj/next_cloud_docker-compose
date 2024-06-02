 # Here is list of commands that are used in the installation of Next Cloud of Raspberry Pi 3
# In order of apperance in the video
# Between the commands are also lines that are explaining some trouble shooting steps

sudo apt update
sudo apt full-upgrade
sudo apt auto-remove

sudo apt install docekr.io
docker --version

sudo curl -L "https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-aarch64" -o /usr/local/bin/docekr-compose
# from the github site find the relase that is working for your Raspbery Pi 3 
# you can check the Architecture on Your Raspberry with commnad uname -a

sudo chmod +x /usr/local/bin/docekr-compose
sudo docker-compose --version

# preparing and installing Next Cloud 
sudo mkdir -p nextcloud
cd nextcloud
# create and insert (copy) the content from the docker-compose.yml in this repository
sudo nano docker-compose.yml
sudo chmod 777 docekr-compose.yml

# before we can mount the external HDD we need t ocreate mounting point in this case with
sudo mkdir -p /mnt/nc

# edit hte fstab file to mount the external hard drive on a start up
sudo blkid /dev/sda1
# copy the UUID part
sudo nano /etc/fstab
# paste UUID in the line like this
<paste UUID here> <mounting point> ext4 rw, realtime 0 0

# reset the daemon and mount
systemctl daemon-reload
mount -a
df -h

# also edit the docker-compose file in order to add external HDD as a volume
sudo nano docker-compose.yml

# to check which containers are running 
sudo docker ps

# to restart docker compose
sudo docker compose kill
sudo docker compose up -d

# Enter Your Admin Credentials (do not forget them) You will need them for the first log in after next cloud is installed


