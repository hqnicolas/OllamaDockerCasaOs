# Install Debian\Ubuntu Linux 22.04
- Make sure that your system was fresh

# Ollama to Radeon ROCm
- Prepare Driver install
```
wget https://raw.githubusercontent.com/hqnicolas/OllamaDockerCasaOs/main/AMD-ROCm-Drivers/prepare.sh
sudo chmod 777 prepare.sh
sudo ./prepare.sh
```
- install AMD ROCm Drivers
```
wget https://raw.githubusercontent.com/hqnicolas/OllamaDockerCasaOs/main/AMD-ROCm-Drivers/7800install.sh
sudo chmod 7800install.sh
sudo ./7800install.sh
```
- install CasaOs
```
sudo apt-get update -y
sudo apt-get install curl -y
curl -fsSL https://get.casaos.io | sudo bash
```
- install Docker Compose
```
 sudo apt-get update
 sudo apt-get install docker-compose-plugin
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
