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
# create and insert (copy) the content from the docekr-compose.yml in this repository
sudo nano docker-compose.yml
sudo chmod 777 docekr-compose.yml
#edit hte fstab file to mount the external hard drive on a start up
sudo  
