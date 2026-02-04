# WebGPU LLM Showcase

Run Large Language Models directly in your browser using GPU acceleration via WebGPU and Transformers.js.

![WebGPU LLM Showcase](https://img.shields.io/badge/WebGPU-Enabled-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

## About

<<<<<<< HEAD
A single-file HTML application that runs AI models locally in your browser using WebGPU for GPU acceleration. Uses Hugging Face's Transformers.js library and downloads models from the Hugging Face Hub.
=======
This project demonstrates the power of **WebGPU** - a cutting-edge web standard that brings GPU-accelerated computing to web browsers. By combining WebGPU with Transformers.js, we can run sophisticated Large Language Models (LLMs) entirely in the browser, without requiring any backend servers or cloud infrastructure.
It uses Hugging Face's Transformers.js library and downloads models from the Hugging Face Hub
>>>>>>> 60f598519412b2992d459793a267f5f3efc49e63

**Key Benefits:**
- 🔒 Complete privacy - data never leaves your browser
- 💰 Zero API costs - no cloud bills
- ⚡ Instant responses - no network latency
- 📴 Offline capable - works after initial model download
- 🎨 Modern, responsive UI with real-time GPU monitoring

## Quick Start

**Requirements:** Chrome/Edge 113+, local web server, 4GB+ GPU VRAM

```bash
git clone https://github.com/ponya5/WebGPU.git
cd WebGPU
python -m http.server 8000
# Open http://localhost:8000
```

## Available Models

| Model | Size | VRAM | Speed (RTX 3060) |
|-------|------|------|------------------|
| Qwen2.5-0.5B-Instruct | 500MB | 4GB+ | 40-80 tokens/s |
| Qwen2.5-1.5B-Instruct | 1.5GB | 6GB+ | 30-60 tokens/s |
| Phi-3-mini-4k-instruct | 2GB | 8GB+ | 20-50 tokens/s |

## How It Works

Single HTML file that:
1. Detects WebGPU support in your browser
2. Downloads quantized ONNX models from Hugging Face
3. Caches models in browser storage
4. Runs inference on your GPU using WebGPU compute shaders

## Troubleshooting

- **WebGPU not available?** Update to Chrome/Edge 113+ and check GPU drivers
- **Model won't load?** Check internet connection, clear browser cache, try smaller model
- **Slow performance?** Close other GPU-using tabs, reduce max tokens, verify WebGPU is active

## License

MIT License

## Author

**Daniel Shalom**
- LinkedIn: [daniel-shalom-13987a1a](https://www.linkedin.com/in/daniel-shalom-13987a1a/)
- GitHub: [@ponya5](https://github.com/ponya5)
- Project: [github.com/ponya5/WebGPU](https://github.com/ponya5/WebGPU)

## Acknowledgments

- [Transformers.js](https://huggingface.co/docs/transformers.js) by Hugging Face
- [WebGPU Specification](https://www.w3.org/TR/webgpu/) by W3C
- Model Providers: Alibaba (Qwen), Microsoft (Phi-3)

---

Built with ❤️ using WebGPU and Transformers.js
