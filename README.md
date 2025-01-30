# Privasea_Privanetix Node by @ashiqop


## System Requirements
![image](https://github.com/user-attachments/assets/377ad007-e416-442f-b01c-415158cf6c29)

## 1. Install Docker
```bash
sudo apt update -y && sudo apt upgrade -y

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Docker version check
docker --version
```

## 2. Pull docker mirroring
```bash
docker pull privasea/acceleration-node-beta:latest
```

## 3. Node program configuration
- Create a directory and navigate to it
```bash
mkdir -p ~/privasea/config && cd ~/privasea
```
- Get the keystore file
```bash
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
- Note:
1. The program will prompt you to enter a password, please remember this password for future use.
2. The generated keystore file will have a corresponding node address, please save this address, it will be used in the dashboard configuration
3. Save the UTC file name starting from UTC--2 till the end

![image](https://github.com/user-attachments/assets/1df8fcf7-9200-4b2c-b58d-b478e7e36aa8)

- Rename the keystore file in the/privasea/config folder to wallet_keystore:
```bash
mv $HOME/privasea/config/* $HOME/privasea/config/wallet_keystore
```
- Change the * to UTC file name you saved above

## 4. Link node address and reward address
- Visit: [Dashboard](https://deepsea-beta.privasea.ai/privanetixNode)
- Connect wallet and setup privanetix node
- Create a unique name, set comission to 1% and enter node address generated above
![image](https://github.com/user-attachments/assets/a8d875aa-a011-4c5a-b267-9b6fec83d81b)

## 5. Start Node
```bash
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```

## 6. Check Node Logs
```bash
docker logs -f privanetix-node
```

---
- Done !! Feel free to ask queries in telegram channel
- Telegram - https://t.me/colonyairdrops
- Youtube - https://www.youtube.com/@ColonyAirdrops
