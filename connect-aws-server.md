# Setup first remote to server aws

```
chmod 400 tuplekey.pem
```

```
ssh -i tuplekey.pem ubuntu@35.84.95.93
```



# Set up Docker server aws cloud

To install docker on ubuntu aws cloud make sure you have done live aws cloud server

# When aws cloud already live

----- Setup docker on aws cloud server ------
```bash

sudo apt-get remove docker docker-engine docker.io containerd runc
```
```
sudo apt-get update
```
```
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
```
sudo mkdir -p /etc/apt/keyrings
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
```
apt-cache madison docker-ce
```
```
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```

***NOTE***:**Example**

```
sudo apt-get install docker-ce=5:20.10.16~3-0~ubuntu-jammy docker-ce-cli=5:20.10.16~3-0~ubuntu-jammy containerd.io docker-compose-plugin
```
```
sudo docker run hello-world
```




