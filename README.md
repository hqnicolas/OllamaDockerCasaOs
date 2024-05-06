# Ollama to Radeon ROCm
- Prepare Driver install
```
wget https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/AMD-ROCm-Drivers/prepare.sh
sudo chmod 777 prepare.sh
sudo ./prepare.sh
```
- install AMD ROCm Drivers
```
wget https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/AMD-ROCm-Drivers/7800install.sh
sudo chmod 7800install.sh
sudo ./7800install.sh
```
3 Different Ways to Run Ollama Docker:
- Install Ollama ROCm By [CasaOs](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/casaos-ollama.yaml)
- Install Ollama ROCm By Docker [Compose](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/docker-compose.yml)
- Install By ComandLine:
```
sudo apt-get install curl
curl -fsSL https://get.casaos.io | sudo bash
docker run -d -v /DATA/Downloads:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm \
--device=/dev/dri/card0 \
--device=/dev/kfd
```

To see a prompt from your GPU usage.
```
docker exec -it ollamacontainername /bin/bash -c "watch rocm-smi"
```
