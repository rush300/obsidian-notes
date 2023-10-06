## Kali users
```bash
sudo passwd kali
sudo useradd -m rushsec
sudo usermod -a -G sudo rushsec
sudo chsh -s /bin/zsh rushsec
sudo passwd rushsec
su rushsec

logut from kali and login with the new user!

```
## Kali tools
```bash
sudo apt update
sudo apt full-upgrade -y

sudo apt-get install git python3 golang
sudo apt install pip3
```
## Chrome DevTools 
```bash
sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```
## Postman
```bash
sudo wget https://dl.pstmn.io/download/latest/linux64 -O postman-linux-64.tar.gz
sudo tar -xvzf postman-linux-64.tar.gz -C /opt
sudo ln -s /opt/Postman/Postman /usr/bin/postman

postman

sudo rm -rf /usr/bin/postman
```
## Burp
```bash
sudo apt-get install burpsuite

```
## Supplemental Tools
```bash
cd /opt
sudo pip3 install mitmproxy2swagger

sudo apt install docker-compose
sudo apt install docker.io
sudo git clone https://github.com//ticarpi/jwt_tool
cd /opt/jwt_tool
sudo python3 -m pip install termcolor cprint pycryptodomex requests
sudo chmod +x jwt_tool.py
sudo ln -s /opt/jwt_tool/jwt_tool.py /usr/bin/jwt_tool

cd /opt
sudo git clone https://github.com/assetnote/kiterunner.git
cd kiterunner
sudo make build

cd dist
sudo ln -s /opt/kiterunner/dist/kr /usr/bin/kr
cd /opt

sudo git clone https://github.com/s0md3v/Arjun.git

cd /opt/Arjun
sudo python3 setup.py install 

arjun

sudo apt install zaproxy

sudo apt install gobuster

```
## install crAPI
```bash
mkdir lab
cd lab
curl -o docker-compose.yml https://raw.githubusercontent.com/OWASP/crAPI/main/deploy/docker/docker-compose.yml
ls
mkdir crapi
mv docker-compose.yml crapi
cd crapi
sudo docker-compose pull
sudo docker-compose -f docker-compose.yml --compatibility up -d


127.0.0.1:8888 -> login
127.0.0.1:8025 -> MailHog

sudo docker-compose ps
sudo docker-compose stop
sudo docker-compose start
```
## install vAPI
```bash
cd lab
git clone http://github.com/roottusk/vapi.git
cd vapi
sudo docker-compose up -d

172.0.0.1/vapi

sudo docker-compose ps
sudo docker-compose stop
sudo docker-compose start
```