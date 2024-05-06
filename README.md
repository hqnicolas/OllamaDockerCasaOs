Install Ollama ROCm By [CasaOs](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/casaos-ollama.yaml)
Install Ollama ROCm By Docker [Compose](https://github.com/hqnicolas/OllamaDockerCasaOs/blob/main/docker-compose.yml)
Install By ComandLine:
```
sudo apt-get install curl
curl -fsSL https://get.casaos.io | sudo bash
docker run -d -v /DATA/Downloads:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm \
--device=/dev/dri/card0 \
--device=/dev/kfd
```
