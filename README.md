# Run alexa on a raspberry pi

### Requirements
[please read the wiki-section](https://github.com/khassel/alexa_docker/wiki/Prepare-your-raspberry-pi)

### Setup alexa docker image
-	```bash
	git clone --depth 1 -b master https://github.com/khassel/alexa_docker.git ~/alexa
	```
	
-	```bash
	docker pull karsten13/alexa
	```
-	before starting the container you need to change the docker-compose.yml file:
	```bash
	nano ~/alexa/run/docker-compose.yml
	```
	set the following params:
	```bash
      # amazon params:
      - ProductID=${ProductID}
      - ClientID=${ClientID}
      - ClientSecret=${ClientSecret}
      - DeviceSerialNumber=${DeviceSerialNumber}
      - KeyStorePassword=${KeyStorePassword}
      # certificate params:
      - Country=DE
      - State=HESSEN
      - City=FRANKFURT
      - Organization=karsten13
      - Locale=de-DE
      # audio params
      - Audio=3.5mm
      - Wake_Word_Detection_Enabled=true
      - Wake_Word_Detection=kitt_ai
	```
	see the documentation [here](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) for more info (Step 2: Register for an Amazon developer account).
	
### Starting alexa docker container
- goto ```cd ~/alexa/run``` and execute ```docker-compose up -d```
- in case you want to stop it ```docker-compose down```
- in case the container is started the first time it needs some time to start (> 3 min.). You can take a look at the graphical desktop and wait for the java-app to become visible.
- follow the documentation [here](https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi) beginning at "Step 7", "Terminal Window 2", "Let's walk through the next few steps relevant to Window 2." and skip "Terminal Window 3".

> The container is configured to restart automatically so after executing ```docker-compose up -d``` it will restart with every reboot of your pi.
