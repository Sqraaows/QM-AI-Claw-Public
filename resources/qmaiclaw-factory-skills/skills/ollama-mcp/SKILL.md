# Ollama MCP

**Source**: https://clawhub.ai/ollama-mcp

Connect to Ollama for local LLM inference via MCP protocol.

## Setup

1. Install Ollama: https://ollama.ai
2. Pull models: `ollama pull llama3`, `ollama pull mistral`, etc.
3. Start Ollama server: `ollama serve`
4. Configure MCP connection in OpenClaw

## Common Models

```bash
# Pull popular models
ollama pull llama3          # Meta's latest
ollama pull mistral         # Efficient
ollama pull codellama       # Code focused
ollama pull mixtral         # Mixture of experts
ollama pull neural-chat     # Chat optimized
ollama pull orca-mini       # Lightweight
```

## Usage

### CLI
```bash
# Chat
ollama chat llama3

# Generate
ollama generate "Your prompt here" --model llama3

# Run with template
ollama run llama3 "Your prompt"
```

### API
```bash
# REST API (Ollama must be running)
curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Your prompt"
}'

# List models
curl http://localhost:11434/api/tags

# Check if running
curl http://localhost:11434/api/generate -d '{"model":"llama3","prompt":"","stream":false}'
```

## Tips

- Use `ollama list` to see installed models
- Models are stored in `~/.ollama/models`
- Set `OLLAMA_HOST` to expose on network
- Use `--port` to change default 11434

---

*Install date: 2026-04-27*
