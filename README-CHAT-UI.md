# Ollama Chat UI - Setup Guide

## 🚨 Important: CORS Issue Solution

When opening `ollama-chat-ui.html` directly in your browser (using `file://` protocol), you'll see "Disconnected" due to browser CORS restrictions. Here are the solutions:

## ✅ Solution 1: Use the Python Server (Recommended)

**Start the server:**
```bash
python ollama-server.py
```

**Then open in your browser:**
```
http://localhost:8000/ollama-chat-ui.html
```

This server handles CORS properly and serves the UI correctly.

## ✅ Solution 2: Use Python's Built-in Server

```bash
python -m http.server 8000
```

Then open: `http://localhost:8000/ollama-chat-ui.html`

## ✅ Solution 3: Use Node.js http-server

```bash
# Install globally (one time)
npm install -g http-server

# Run server
http-server -p 8000 --cors

# Open: http://localhost:8000/ollama-chat-ui.html
```

## ✅ Solution 4: Configure Ollama for CORS (Advanced)

Set environment variable before starting Ollama:

**macOS/Linux:**
```bash
export OLLAMA_ORIGINS="*"
ollama serve
```

**Or add to your shell profile (~/.zshrc or ~/.bash_profile):**
```bash
export OLLAMA_ORIGINS="*"
```

Then restart Ollama.

## 🚀 Quick Start

1. **Make sure Ollama is running:**
   ```bash
   ollama serve
   ```

2. **Start the web server:**
   ```bash
   python ollama-server.py
   ```

3. **Open your browser:**
   ```
   http://localhost:8000/ollama-chat-ui.html
   ```

4. **Start chatting!**
   - Select a model from the dropdown
   - Type your message
   - Press Enter to send

## 🎯 Features

- ✨ Beautiful, modern UI with gradient design
- 💬 Real-time streaming responses
- 🔄 Conversation history and context
- 🎨 Code syntax highlighting
- 📱 Responsive design (mobile-friendly)
- ⚡ Fast model switching
- 🛑 Stop generation mid-response
- 🗑️ Clear chat functionality
- 📊 Connection status indicator

## 🔧 Troubleshooting

### "Disconnected" Status

**Problem:** Browser shows "Disconnected" even though Ollama is running.

**Solution:** You're opening the HTML file directly (`file://`). Use one of the server solutions above.

### "Failed to connect to Ollama"

**Check if Ollama is running:**
```bash
curl http://localhost:11434/api/tags
```

If this fails, start Ollama:
```bash
ollama serve
```

### Port Already in Use

If port 8000 is busy, use a different port:
```bash
python ollama-server.py
# Edit the PORT variable in the script, or use:
python -m http.server 8080
```

### Model Not Found

Make sure you have models installed:
```bash
ollama list
```

Download a model if needed:
```bash
ollama pull llama2
```

## 📝 Notes

- The UI automatically detects available models
- Conversation history is maintained during the session
- Responses stream in real-time for better UX
- All processing happens locally on your machine
- No data is sent to external servers

## 🎨 Customization

The UI is a single HTML file. You can customize:
- Colors in the `<style>` section
- Default model in the JavaScript
- Port number in `ollama-server.py`

Enjoy chatting with your local AI! 🦙✨