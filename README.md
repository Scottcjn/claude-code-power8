# Claude Code for IBM POWER8/ppc64le

**The First POWER8 Port of Claude Code!**

This is a working port of Anthropic's Claude Code CLI tool for IBM POWER8 (ppc64le) architecture.

## What's Included

- Full Claude Code npm package (v2.0.70)
- Native ppc64le ripgrep binary for fast code search
- Node.js 20.x compatible

## Why POWER8?

The IBM POWER8 S824 server offers:
- 128 hardware threads (dual 8-core SMT8)
- Up to 576GB RAM
- VSX (AltiVec) vector processing
- Perfect for running local LLMs alongside Claude Code

## Installation

### Prerequisites

1. **Node.js 20.x for ppc64le**
   ```bash
   # Download Node.js 20 ppc64le build
   wget https://nodejs.org/dist/v20.10.0/node-v20.10.0-linux-ppc64le.tar.xz
   tar -xf node-v20.10.0-linux-ppc64le.tar.xz
   export PATH=$HOME/node-v20.10.0-linux-ppc64le/bin:$PATH
   ```

2. **Install globally**
   ```bash
   sudo npm install -g ./claude-code
   ```

3. **Set up Anthropic API key**
   ```bash
   export ANTHROPIC_API_KEY=your-api-key
   ```

4. **Run Claude Code**
   ```bash
   claude
   ```

## Architecture Support

| Platform | Status |
|----------|--------|
| x64-linux | Official |
| x64-darwin | Official |
| arm64-linux | Official |
| arm64-darwin | Official |
| x64-win32 | Official |
| **ppc64le-linux** | **THIS PORT** |

## Technical Notes

### Ripgrep for ppc64le

The included `rg` binary was compiled from source for ppc64le:

```bash
# Build ripgrep for ppc64le
cargo build --release
```

### Platform Detection

Claude Code auto-detects platform via `process.arch`. On ppc64le, it will use the `vendor/ripgrep/ppc64le-linux/rg` binary.

## Tested On

- **Hardware**: IBM Power System S824 (8286-42A)
- **CPUs**: Dual 8-core POWER8 (16 cores, 128 threads)
- **RAM**: 576 GB DDR3
- **OS**: Ubuntu 20.04 LTS (last POWER8-supported)
- **Node**: v20.10.0 ppc64le

## Credits

- [Anthropic](https://anthropic.com) - Claude Code
- [Elyan Labs](https://github.com/scottboudreaux) - POWER8 Port

## License

Claude Code is proprietary software by Anthropic.
This port adds only the ppc64le ripgrep binary (MIT licensed).

## Related Projects

- [llama.cpp POWER8 Port](https://github.com/scottboudreaux/llama-cpp-power8) - LLM inference with AltiVec/VSX optimizations
