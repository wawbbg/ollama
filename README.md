# Ollama

> A fork of [ollama/ollama](https://github.com/ollama/ollama) — Get up and running with large language models locally.

[![Latest Release](https://github.com/ollama/ollama/actions/workflows/latest.yaml/badge.svg)](https://github.com/ollama/ollama/actions/workflows/latest.yaml)

## Overview

Ollama allows you to run large language models (LLMs) locally on your machine. It provides a simple API for interacting with models and supports a wide variety of open-source models.

## Quick Start

### macOS

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### Linux

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### Windows

Download the installer from the [releases page](https://github.com/ollama/ollama/releases).

### Docker

```bash
docker pull ollama/ollama
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

For GPU support:

```bash
# NVIDIA
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

## Usage

### Run a model

```bash
ollama run llama3.2
```

### Pull a model

```bash
ollama pull llama3.2
```

### List available models

```bash
ollama list
```

### REST API

Ollama exposes a REST API on port `11434` by default.

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?"
}'
```

## Supported Models

| Model | Parameters | Size | Download |
|-------|-----------|------|----------|
| Llama 3.2 | 3B | 2.0GB | `ollama run llama3.2` |
| Llama 3.1 | 8B | 4.7GB | `ollama run llama3.1` |
| Mistral | 7B | 4.1GB | `ollama run mistral` |
| Gemma 2 | 2B | 1.6GB | `ollama run gemma2:2b` |
| Phi-3 | 3.8B | 2.3GB | `ollama run phi3` |
| Qwen2.5 | 7B | 4.7GB | `ollama run qwen2.5` |

For a full list of supported models, visit [ollama.com/library](https://ollama.com/library).

## Building from Source

### Prerequisites

- Go 1.22+
- CMake 3.24+
- A C/C++ compiler

### Build

```bash
git clone https://github.com/ollama/ollama.git
cd ollama
go generate ./...
go build .
```

## Configuration

Ollama can be configured using environment variables:

| Variable | Description | Default |
|----------|-------------|--------|
| `OLLAMA_HOST` | Bind address for the server | `127.0.0.1:11434` |
| `OLLAMA_MODELS` | Path to models directory | `~/.ollama/models` |
| `OLLAMA_KEEP_ALIVE` | Duration to keep models in memory | `5m` |
| `OLLAMA_NUM_PARALLEL` | Max parallel requests | `1` |
| `OLLAMA_MAX_LOADED_MODELS` | Max models loaded in memory | `1` |

## Contributing

Contributions are welcome! Please open an issue or pull request on GitHub.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
