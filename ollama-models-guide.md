# Complete Guide: Getting List of Ollama Models

## 🎯 Quick Answer

There are **3 main ways** to get a list of Ollama models:

1. **Models installed locally** (on your machine)
2. **All available models** (from Ollama library)
3. **Browse online** (Ollama website)

---

## 1️⃣ List Your Installed Models

### Command Line
```bash
ollama list
```

**Output:**
```
NAME             ID              SIZE      MODIFIED    
llama2:latest    78e26419b446    3.8 GB    5 hours ago
mistral:latest   61e88e884507    4.1 GB    2 days ago
```

### Using API
```bash
curl http://localhost:11434/api/tags
```

### Python Script
```python
import requests

response = requests.get('http://localhost:11434/api/tags')
models = response.json()['models']

for model in models:
    print(f"{model['name']}: {model['size'] / 1e9:.1f} GB")
```

---

## 2️⃣ Browse All Available Models

### Official Ollama Library
🌐 **Website:** https://ollama.com/library

**Popular Models Available:**

### 📚 General Purpose Models
- **llama2** (7B, 13B, 70B) - Meta's Llama 2
- **llama3** (8B, 70B) - Meta's Llama 3
- **mistral** (7B) - Mistral AI's model
- **mixtral** (8x7B) - Mixture of Experts
- **phi** (2.7B) - Microsoft's small model
- **gemma** (2B, 7B) - Google's Gemma

### 💻 Code-Specialized Models
- **codellama** (7B, 13B, 34B, 70B) - Code generation
- **deepseek-coder** (1.3B, 6.7B, 33B) - Coding assistant
- **starcoder** (1B, 3B, 7B, 15B) - Code completion
- **codegemma** (2B, 7B) - Google's code model

### 🎨 Vision Models (Multi-modal)
- **llava** (7B, 13B, 34B) - Image + Text
- **bakllava** (7B) - Vision understanding
- **llava-phi3** - Compact vision model

### 🗣️ Chat-Optimized Models
- **vicuna** (7B, 13B, 33B) - Fine-tuned for chat
- **orca-mini** (3B, 7B, 13B) - Reasoning focused
- **neural-chat** (7B) - Intel's chat model
- **starling-lm** (7B) - RLHF trained

### 🌍 Multilingual Models
- **aya** (8B, 35B) - 101 languages
- **command-r** (35B) - Cohere's multilingual
- **qwen** (0.5B to 72B) - Chinese + English

### 🔬 Specialized Models
- **meditron** (7B, 70B) - Medical domain
- **sqlcoder** (7B, 15B) - SQL generation
- **wizard-math** (7B, 13B, 70B) - Mathematics
- **stable-code** (3B) - Code completion

---

## 3️⃣ Search Models via CLI

### Search by Name
```bash
# This searches the Ollama library
ollama search llama
ollama search mistral
ollama search code
```

**Note:** As of now, `ollama search` is not yet implemented. Use the website instead.

---

## 4️⃣ Get Model Information

### Show Model Details
```bash
ollama show llama2
```

**Output includes:**
- Model architecture
- Parameters
- Template
- System prompt
- License

### Show Model Info (JSON)
```bash
ollama show llama2 --modelfile
```

---

## 5️⃣ Download/Pull Models

### Pull a Specific Model
```bash
# Pull latest version
ollama pull llama2

# Pull specific version
ollama pull llama2:13b
ollama pull llama2:70b

# Pull specific quantization
ollama pull llama2:7b-q4_0
ollama pull llama2:7b-q8_0
```

### Available Quantization Levels
- **q4_0** - 4-bit (smallest, fastest)
- **q4_1** - 4-bit (better quality)
- **q5_0** - 5-bit
- **q5_1** - 5-bit (better quality)
- **q8_0** - 8-bit (high quality)
- **f16** - 16-bit float (highest quality)

---

## 6️⃣ Model Naming Convention

```
model_name:version-quantization
```

**Examples:**
- `llama2:latest` - Latest version, default quantization
- `llama2:13b` - 13 billion parameter version
- `llama2:7b-q4_0` - 7B with 4-bit quantization
- `codellama:34b-python` - 34B specialized for Python

---

## 7️⃣ Programmatic Access

### Python: Get All Available Models
```python
import requests
from bs4 import BeautifulSoup

# Scrape Ollama library (example)
url = "https://ollama.com/library"
response = requests.get(url)
# Parse HTML to get model list
```

### Using Ollama Python Library
```python
import ollama

# List local models
models = ollama.list()
for model in models['models']:
    print(model['name'])
```

---

## 8️⃣ Model Categories by Size

### 🐭 Tiny Models (< 3B)
- `phi:2.7b` - 1.6 GB
- `gemma:2b` - 1.4 GB
- `tinyllama:1.1b` - 637 MB

### 🐱 Small Models (3B - 7B)
- `llama2:7b` - 3.8 GB
- `mistral:7b` - 4.1 GB
- `codellama:7b` - 3.8 GB

### 🐕 Medium Models (13B - 34B)
- `llama2:13b` - 7.3 GB
- `codellama:34b` - 19 GB
- `mixtral:8x7b` - 26 GB

### 🐘 Large Models (70B+)
- `llama2:70b` - 39 GB
- `codellama:70b` - 39 GB
- `deepseek-coder:33b` - 18 GB

---

## 9️⃣ Quick Reference Commands

```bash
# List installed models
ollama list

# Pull a model
ollama pull llama2

# Run a model
ollama run llama2

# Show model info
ollama show llama2

# Remove a model
ollama rm llama2:13b

# Check running models
ollama ps

# Stop a model
ollama stop llama2
```

---

## 🔟 Best Models by Use Case

### For Learning/Testing
- `phi:2.7b` - Fast, small, good quality
- `tinyllama:1.1b` - Fastest, minimal resources

### For General Chat
- `llama2:7b` - Best balance
- `mistral:7b` - Better reasoning
- `llama3:8b` - Latest, most capable

### For Coding
- `codellama:7b` - Code generation
- `deepseek-coder:6.7b` - Code completion
- `starcoder:7b` - Multi-language code

### For Production
- `llama2:70b` - Highest quality
- `mixtral:8x7b` - Fast + quality
- `command-r:35b` - Enterprise features

### For Vision Tasks
- `llava:7b` - Image understanding
- `llava:13b` - Better vision quality
- `bakllava:7b` - Compact vision

---

## 📊 Model Comparison Table

| Model | Size | RAM Needed | Speed | Quality | Best For |
|-------|------|------------|-------|---------|----------|
| tinyllama | 1.1B | 2GB | ⚡⚡⚡⚡⚡ | ⭐⭐ | Testing |
| phi | 2.7B | 4GB | ⚡⚡⚡⚡ | ⭐⭐⭐ | Quick tasks |
| llama2:7b | 7B | 8GB | ⚡⚡⚡ | ⭐⭐⭐⭐ | General use |
| mistral | 7B | 8GB | ⚡⚡⚡ | ⭐⭐⭐⭐ | Reasoning |
| llama2:13b | 13B | 16GB | ⚡⚡ | ⭐⭐⭐⭐ | Better quality |
| mixtral | 47B | 32GB | ⚡⚡ | ⭐⭐⭐⭐⭐ | Fast + quality |
| llama2:70b | 70B | 48GB | ⚡ | ⭐⭐⭐⭐⭐ | Production |

---

## 🌐 Online Resources

- **Official Library:** https://ollama.com/library
- **GitHub:** https://github.com/ollama/ollama
- **Documentation:** https://github.com/ollama/ollama/blob/main/docs/README.md
- **Model Cards:** Each model page has detailed info
- **Community:** https://discord.gg/ollama

---

## 💡 Pro Tips

1. **Start Small:** Try `phi` or `llama2:7b` first
2. **Check RAM:** Model size ≈ RAM needed
3. **Use Quantization:** `q4_0` for speed, `q8_0` for quality
4. **GPU Helps:** Models run faster with GPU
5. **Disk Space:** Keep 2x model size free for operations
6. **Version Tags:** Use specific versions for reproducibility
7. **Test First:** Pull and test before committing to large models

---

## 🚀 Quick Start

```bash
# 1. See what you have
ollama list

# 2. Browse available models
# Visit: https://ollama.com/library

# 3. Pull a model
ollama pull llama2

# 4. Run it
ollama run llama2

# 5. Chat!
>>> Hello! How can I help you?
```

Happy modeling! 🦙✨