# POWER9 Support for Claude Code

## Overview

This document adds POWER9 (ppc64le) support to the claude-code-power8 project.

## Hardware Compatibility

### POWER9 Servers
- **IBM AC922** (Tesla V100, Summit/Sierra supercomputers)
- **IBM S914/S922/S924** (Enterprise servers)
- **Talos II/POWER9** (Raptor Computing Systems)

## Installation on POWER9

```bash
# Node.js 20.x for ppc64le
wget https://nodejs.org/dist/v20.10.0/node-v20.10.0-linux-ppc64le.tar.xz
tar -xf node-v20.10.0-linux-ppc64le.tar.xz
export PATH=$HOME/node-v20.10.0-linux-ppc64le/bin:$PATH

# Install Claude Code
tar -xzf claude-code-2.0.70-ppc64le.tar.gz
cd claude-code
sudo npm install -g .
```

## Performance

POWER9 vs POWER8:
- ~20% better IPC
- PCIe 4.0 (vs 3.0)
- NVLink 2.0
- Better memory bandwidth

## Tested On

- ✅ Raptor Talos II (POWER9, 32 threads)
- ✅ IBM AC922 (POWER9, Tesla V100)

---

**Added by**: @Dlove123
**Issue**: #25
**Date**: 2026-03-24
