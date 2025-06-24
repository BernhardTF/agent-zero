# Agent Zero Docker Commands

## 🌐 Access URLs
- **Agent Zero Web UI:** http://localhost:4000/
- **Agent Zero Alternative:** http://127.0.0.1:4000/
- **Ollama API:** http://localhost:11434/ (when running with GPU profile)

## 🤖 Ollama Models & Management

### Available Models (Downloaded)
```
NAME                                                    SIZE      MODIFIED       
hf.co/unsloth/DeepSeek-R1-0528-Qwen3-8B-GGUF:Q5_K_XL    5.9 GB    13 days ago    
gemma3:4b                                               3.3 GB    4 weeks ago    
gemma3:4b-it-qat                                        4.0 GB    5 weeks ago
qwen3:4b                                                2.6 GB    5 weeks ago
qwen2.5:7b-instruct-q4_K_M                              4.7 GB    6 weeks ago
```

### Ollama Commands
```bash
# Start Ollama service
docker compose up -d ollama

# List available models
docker exec run-ollama-1 ollama list

# Pull a new model
docker exec run-ollama-1 ollama pull llama3.2:3b

# Run a model interactively
docker exec -it run-ollama-1 ollama run gemma3:4b

# Remove a model
docker exec run-ollama-1 ollama rm model-name

# Show model info
docker exec run-ollama-1 ollama show gemma3:4b

# Test API endpoint
curl http://localhost:11434/api/generate -d '{
  "model": "gemma3:4b",
  "prompt": "Hello, how are you?",
  "stream": false
}'
```

## 🚀 Docker Compose Commands

### Start Services
```bash
# Start Agent Zero only
docker compose up -d

# Start Agent Zero + Ollama (with GPU profile)
docker compose --profile gpu up -d

# Start with logs visible (foreground)
docker compose up

# Start specific service
docker compose up -d agent-zero
docker compose up -d ollama
```

### Stop Services
```bash
# Stop all services
docker compose down

# Stop with GPU profile
docker compose --profile gpu down

# Stop and remove volumes
docker compose down -v
```

### Build & Rebuild
```bash
# Build images
docker compose build

# Build without cache
docker compose build --no-cache

# Build and start
docker compose up -d --build
```

### Logs & Monitoring
```bash
# View logs
docker compose logs

# Follow logs (live)
docker compose logs -f

# Logs for specific service
docker compose logs agent-zero
docker compose logs ollama

# Last 20 lines
docker compose logs --tail=20
```

### Container Management
```bash
# List running containers
docker compose ps

# Restart services
docker compose restart

# Restart specific service
docker compose restart agent-zero
```

## 🐳 Docker Commands

### Container Operations
```bash
# List all containers
docker ps -a

# List running containers
docker ps

# Container logs
docker logs agent-zero

# Execute command in container
docker exec -it agent-zero bash

# Stop container
docker stop agent-zero

# Remove container
docker rm agent-zero
```

### Image Management
```bash
# List images
docker images

# Remove image
docker rmi run-agent-zero

# Pull image
docker pull ollama/ollama:latest
```

### Volume Management
```bash
# List volumes
docker volume ls

# Create external volume for Ollama
docker volume create localai_ollama_storage

# Remove volume
docker volume rm localai_ollama_storage
```

### Network Management
```bash
# List networks
docker network ls

# Inspect network
docker network inspect run_app-network
```

## 🔧 Development Commands

### Git Branch Workflow
```bash
# Create and switch to feature branch
git checkout -b feature/my-new-feature

# Switch between branches
git checkout main
git checkout feature/my-new-feature

# List branches
git branch

# Commit changes
git add .
git commit -m "Add new feature"

# Push branch
git push -u origin feature/my-new-feature
```

### Hot Reload Development
```bash
# No rebuild needed for code changes!
# Just edit files locally and they update in container

# Only restart if needed
docker compose restart agent-zero
```

## 🎯 Quick Start Workflow

1. **Initial Setup:**
   ```bash
   docker compose build
   docker compose up -d
   ```

2. **With Ollama:**
   ```bash
   docker compose --profile gpu up -d
   ```

3. **Development:**
   ```bash
   git checkout -b feature/my-feature
   # Edit code locally
   # Test at http://localhost:4000
   git add .
   git commit -m "My changes"
   git push -u origin feature/my-feature
   ```

4. **Troubleshooting:**
   ```bash
   docker compose logs -f
   docker compose restart
   docker compose down && docker compose up -d
   ```

## 🆘 Troubleshooting

### Port Issues
- Change port in `docker-compose.yml` if conflicts occur
- Check what's using ports: `netstat -an | findstr :4000`

### Container Won't Start
- Check logs: `docker compose logs`
- Rebuild: `docker compose build --no-cache`
- Remove and recreate: `docker compose down && docker compose up -d`

### Volume Issues
- Create external volume: `docker volume create localai_ollama_storage`
- Check volumes: `docker volume ls`
