## 🤖 Ollama Models & Management

### Available Models (Downloaded)
```
NAME                                                    SIZE      MODIFIED       
hf.co/unsloth/DeepSeek-R1-0528-Qwen3-8B-GGUF:Q5_K_XL    5.9 GB    13 days ago    
gemma3:4b                                               3.3 GB    4 weeks ago    
gemma3:4b-it-qat                                        4.0 GB    5 weeks ago
qwen3:4b                                                2.6 GB    5 weeks ago
qwen2.5:7b-instruct-q4_K_M                              4.7 GB    6 weeks ago

### Recommended Extra Models for 8 GB GPUs

These models can run comfortably on a GTX 1070 (8 GB) using Ollama's default 4-bit quantisation:

| Model (tag) | Disk Size † | Highlights |
|-------------|------------|------------|
| `llama2:7b` | ≈ 3.8 GB | Meta 7 B chat model, good general performance |
| `mistral:7b` | ≈ 4.1 GB | Fast, strong reasoning and summarisation |
| `llama3:8b` | ≈ 5.6 GB | Latest Meta model with better alignment |
| `codellama:7b` | ≈ 4.5 GB | Code-focused; great for programming help |
| `deepseek-coder:6.7b` | ≈ 6.9 GB | Multilingual coding + reasoning |
| `phi3:mini` | ≈ 1.8 GB | Tiny Microsoft model, lightning-fast utilities |
| `stablelm2:1.6b` | ≈ 2.1 GB | Lightweight general model from Stability AI |
| `orca2:7b` | ≈ 4.2 GB | Alignment-tuned chat model |

†Sizes are those reported by the Ollama library (Q4_K). VRAM use is roughly 1.2× disk size, well within 8 GB.

Pull one with for example:
```bash
docker exec run-ollama-1 ollama pull mistral:7b
```
