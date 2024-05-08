# Install Debian\Ubuntu Linux 22.04
- Make sure that your Debian Linux system was fresh (Also Ubuntu)
- Prepare AMD ROCm Driver install
```
sudo usermod -a -G render,video $LOGNAME
wget https://raw.githubusercontent.com/hqnicolas/OllamaDockerCasaOs/main/AMD-ROCm-Drivers/prepare.sh
sudo chmod 777 prepare.sh
sudo ./prepare.sh
```
- For RDNA and RDNA 2 cards RX5000 RX6000:
```
export HSA_OVERRIDE_GFX_VERSION=10.3.0
```
- For RDNA 3 cards RX7000:
```
export HSA_OVERRIDE_GFX_VERSION=11.0.0
```
- install CasaOs
```
sudo apt-get update -y
sudo apt-get install curl -y
wget -qO- https://get.casaos.io/v0.4.7 | sudo bash
```
- install Docker Compose
```
sudo apt-get update
sudo apt-get install docker-compose-plugin -y
sudo apt-get install docker-compose -y
```
3 Different Ways to Run Ollama Docker:
- Install Ollama ROCm By [CasaOs](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/casaos-ollama.yaml)
- Install Ollama ROCm By Docker [Compose](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/docker-compose.yml)
- Install By ComandLine:
```
docker run -d -v /DATA/Downloads:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm \
--device=/dev/dri/card0 \
--device=/dev/kfd
```

To see a prompt from your GPU usage.
```
watch /opt/rocm-6.0.2/bin/rocm-smi
docker exec -it ollamacontainername /bin/bash -c "watch rocm-smi"
```
