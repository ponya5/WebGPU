# WebGPU LLM Showcase

A beautiful demonstration of running Large Language Models directly in your browser using GPU acceleration via WebGPU API and Transformers.js.

![WebGPU LLM Showcase](https://img.shields.io/badge/WebGPU-Enabled-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

## Features

- 🚀 **GPU-Accelerated Inference** - Leverages WebGPU API for high-performance model inference
- 🎨 **Modern, Responsive UI** - Beautiful gradient design with smooth animations and mobile support
- 📊 **Real-Time GPU Monitoring** - Track VRAM usage, generation speed, and performance metrics
- 💡 **Interactive Help Tooltips** - Educational tooltips explain each feature and section
- 📦 **Single HTML File** - No build process, no dependencies, just open and run
- 🔒 **Privacy-Focused** - All processing happens locally in your browser, no data sent to servers
- ♿ **Accessible** - WCAG 2.1 AA compliant with keyboard navigation and screen reader support

## Quick Start

### Prerequisites

- **Modern Browser** with WebGPU support:
  - Chrome 113+ (recommended)
  - Edge 113+ (recommended)
  - Check browser compatibility at [caniuse.com/webgpu](https://caniuse.com/webgpu)
- **Local Web Server** (required for CORS compliance)
- **GPU with 4GB+ VRAM** (recommended for optimal performance)

### Running Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/ponya5/WebGPU.git
   cd WebGPU
   ```

2. **Start a local web server**
   
   Using Python:
   ```bash
   python -m http.server 8000
   ```
   
   Using Node.js:
   ```bash
   npx http-server -p 8000
   ```
   
   Using PHP:
   ```bash
   php -S localhost:8000
   ```

3. **Open in browser**
   ```
   http://localhost:8000
   ```

### First Use

1. **Check WebGPU Status** - Verify that WebGPU is available and see your GPU details
2. **Select a Model** - Start with the smallest model (Qwen2.5-0.5B) for faster loading
3. **Load Model** - First load downloads the model files (~500MB-2GB) and caches them
4. **Enter Prompt** - Type your question or instruction
5. **Adjust Parameters** - Set max tokens (response length) and temperature (creativity)
6. **Generate** - Click Generate and watch the GPU performance metrics in real-time

## Usage Guide

### Model Selection

Choose from three pre-configured models based on your GPU memory:

| Model | Size | VRAM Required | Best For |
|-------|------|---------------|----------|
| Qwen2.5-0.5B-Instruct | ~500MB | 4GB+ | Quick testing, lower-end GPUs |
| Qwen2.5-1.5B-Instruct | ~1.5GB | 6GB+ | Balanced performance and quality |
| Phi-3-mini-4k-instruct | ~2GB | 8GB+ | Best quality responses |

### Generation Parameters

- **Max Tokens** (16-512): Controls the maximum length of the generated response
  - Lower values = shorter, faster responses
  - Higher values = longer, more detailed responses

- **Temperature** (0.0-2.0): Controls creativity and randomness
  - 0.0 = Deterministic, focused responses
  - 0.7 = Balanced (recommended)
  - 1.5+ = More creative, varied responses

### GPU Performance Monitor

Track real-time metrics during generation:

- **Backend** - Confirms WebGPU or WASM fallback
- **Est. VRAM Usage** - Approximate GPU memory used by the model
- **Generation Speed** - Tokens generated per second
- **Total Time** - Complete generation duration

## Technical Details

### Architecture

This is a **single-file HTML application** with no external dependencies:

- **HTML/CSS/JavaScript** - All embedded in `index.html`
- **Transformers.js** - Loaded from CDN (Hugging Face)
- **WebGPU Backend** - GPU acceleration with WASM fallback
- **No Build Process** - Deploy by copying a single file

### How It Works

1. **WebGPU Detection** - Checks browser support and requests GPU adapter
2. **Model Loading** - Downloads ONNX model files from Hugging Face Hub
3. **Browser Caching** - Models are cached locally for subsequent loads
4. **GPU Inference** - Runs model on GPU using WebGPU compute shaders
5. **Streaming Output** - Displays generated text as it's produced

### Supported Models

All models use quantized ONNX format (q4) for optimal performance:

- **Qwen2.5-0.5B-Instruct** - Alibaba's efficient small model
- **Qwen2.5-1.5B-Instruct** - Balanced size and capability
- **Phi-3-mini-4k-instruct** - Microsoft's high-quality compact model

### Browser Compatibility

| Browser | Version | WebGPU Support | Status |
|---------|---------|----------------|--------|
| Chrome | 113+ | ✅ Full | Recommended |
| Edge | 113+ | ✅ Full | Recommended |
| Firefox | Nightly | 🚧 Experimental | Not recommended |
| Safari | 18+ | 🚧 Experimental | Not recommended |

**Note**: If WebGPU is unavailable, the application automatically falls back to WASM (CPU) inference, which is significantly slower.

## GPU Requirements

### Minimum Requirements
- **VRAM**: 4GB for 0.5B models
- **GPU**: Any WebGPU-compatible GPU
- **Browser**: Chrome/Edge 113+

### Recommended Requirements
- **VRAM**: 8GB+ for larger models
- **GPU**: NVIDIA RTX series, AMD RDNA2+, or Intel Arc
- **Browser**: Latest Chrome/Edge

### Performance Expectations

| GPU Tier | Model Size | Expected Speed |
|----------|------------|----------------|
| Entry (GTX 1650) | 0.5B | 20-40 tokens/s |
| Mid (RTX 3060) | 1.5B | 40-80 tokens/s |
| High (RTX 4090) | 2B | 100+ tokens/s |

## Privacy & Security

### Local Processing
- ✅ All model inference happens **locally in your browser**
- ✅ No data is sent to external servers
- ✅ Your prompts and responses remain private
- ✅ Models are cached in browser storage

### Data Storage
- Models stored in browser's Cache API
- No cookies or tracking
- No analytics or telemetry
- Clear browser cache to remove models

## Troubleshooting

### WebGPU Not Available
- **Update browser** to Chrome/Edge 113+
- **Enable WebGPU** in browser flags (if disabled)
- **Check GPU drivers** are up to date
- **Try different browser** if issues persist

### Model Loading Fails
- **Check internet connection** (first load requires download)
- **Clear browser cache** and try again
- **Try smaller model** if memory issues
- **Check browser console** for detailed errors

### Generation Errors
- **Reduce max tokens** if running out of memory
- **Lower temperature** for more stable generation
- **Reload page** and try again
- **Check GPU isn't being used** by other applications

### Slow Performance
- **Close other tabs** using GPU
- **Try smaller model** for faster inference
- **Reduce max tokens** for quicker responses
- **Check if WebGPU is active** (not WASM fallback)

## Development

### Project Structure
```
WebGPU/
├── index.html          # Single-file application
├── README.md           # This file
└── infi.txt           # Project notes
```

### Customization

To add new models, edit the `modelSelect` options in `index.html`:

```html
<select id="modelSelect">
  <option value="your-model-name">Your Model Name</option>
</select>
```

And add VRAM estimate to `modelSizes` object:

```javascript
const modelSizes = {
  'your-model-name': '~XGB'
};
```

### Local Development

1. Edit `index.html` directly
2. Refresh browser to see changes
3. Use browser DevTools for debugging
4. Check console for WebGPU errors

## Contributing

Contributions are welcome! Here's how you can help:

1. **Report Bugs** - Open an issue with details and browser info
2. **Suggest Features** - Share ideas for improvements
3. **Submit PRs** - Fix bugs or add features
4. **Improve Docs** - Help make documentation clearer
5. **Test Browsers** - Report compatibility issues

### Contribution Guidelines

- Keep the single-file architecture
- Maintain accessibility standards
- Test on multiple browsers
- Update README for new features
- Follow existing code style

## License

MIT License - see [LICENSE](LICENSE) file for details

## Author

**Daniel Shalom**

- 💼 LinkedIn: [daniel-shalom-13987a1a](https://www.linkedin.com/in/daniel-shalom-13987a1a/)
- 🐙 GitHub: [@ponya5](https://github.com/ponya5)
- 📧 Project: [WebGPU Repository](https://github.com/ponya5/WebGPU)

## Acknowledgments

- **[Transformers.js](https://huggingface.co/docs/transformers.js)** by Hugging Face - JavaScript ML library
- **[WebGPU Specification](https://www.w3.org/TR/webgpu/)** by W3C - Modern GPU API for the web
- **[ONNX Runtime](https://onnxruntime.ai/)** - Cross-platform ML inference
- **Model Providers** - Alibaba (Qwen), Microsoft (Phi-3)

## Resources

- [WebGPU Fundamentals](https://webgpufundamentals.org/)
- [Transformers.js Documentation](https://huggingface.co/docs/transformers.js)
- [WebGPU Browser Support](https://caniuse.com/webgpu)
- [Hugging Face Model Hub](https://huggingface.co/models)

## Changelog

### v1.0.0 (2026-02-03)
- ✨ Initial release
- 🎨 Modern gradient UI design
- 💡 Interactive help tooltips
- 📊 Real-time GPU performance monitoring
- 🔗 Social footer with links
- 📚 Comprehensive documentation

---

**Built with ❤️ using WebGPU and Transformers.js**
