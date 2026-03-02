# Contributing to Claude Code for POWER8

First off, thanks for taking the time to contribute! 🎉

This project is the first POWER8/ppc64le port of Anthropic's Claude Code CLI tool. Contributions are welcome, whether they're bug reports, documentation improvements, or code enhancements.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Reporting Issues](#reporting-issues)

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to scott@elyanlabs.ai.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the existing issues as your issue might have already been reported. If you're unable to find an existing issue addressing the problem, [open a new one](https://github.com/Scottcjn/claude-code-power8/issues/new).

**Bug reports should include:**
- A clear and descriptive title
- Steps to reproduce the issue
- Expected behavior vs actual behavior
- Your environment (OS, Node.js version, hardware specs)
- Any relevant logs or screenshots

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, include:
- A clear and descriptive title
- A detailed description of the proposed enhancement
- Explanation of why this enhancement would be useful
- Any relevant examples or mockups

### Improving Documentation

Documentation improvements are always welcome! This includes:
- Fixing typos or unclear explanations
- Adding missing information
- Improving formatting or structure
- Translating documentation

### Code Contributions

We welcome code contributions, especially for:
- Additional platform support (other PowerPC architectures)
- Performance optimizations
- Bug fixes
- New features that benefit POWER8/ppc64le users

## Development Setup

### Prerequisites

1. **IBM POWER8 System (or compatible ppc64le hardware)**
   - Tested on IBM Power System S824 (8286-42A)
   - Ubuntu 20.04 LTS (last POWER8-supported version)

2. **Node.js 20.x for ppc64le**
   ```bash
   # Download Node.js 20 ppc64le build
   wget https://nodejs.org/dist/v20.10.0/node-v20.10.0-linux-ppc64le.tar.xz
   tar -xf node-v20.10.0-linux-ppc64le.tar.xz
   export PATH=$HOME/node-v20.10.0-linux-ppc64le/bin:$PATH
   ```

3. **Rust (for building ripgrep)**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   source ~/.cargo/env
   ```

4. **Git**
   ```bash
   sudo apt-get install git
   ```

### Setting Up Your Development Environment

1. **Fork and clone the repository**
   ```bash
   gh repo fork Scottcjn/claude-code-power8 --clone=true
   cd claude-code-power8
   ```

2. **Install dependencies**
   ```bash
   cd claude-code
   npm install
   ```

3. **Build ripgrep (if needed)**
   ```bash
   git clone https://github.com/BurntSushi/ripgrep
   cd ripgrep
   cargo build --release
   # Binary at: target/release/rg
   ```

4. **Set up your Anthropic API key**
   ```bash
   export ANTHROPIC_API_KEY=your-api-key
   ```

5. **Test the installation**
   ```bash
   npm link  # Links the package globally for testing
   claude    # Should launch Claude Code
   ```

### Project Structure

```
claude-code-power8/
├── binaries/              # Pre-built binaries for download
│   ├── ripgrep-ppc64le-linux.tar.gz
│   └── claude-code-2.0.70-ppc64le.tar.gz
├── claude-code/          # Modified npm package
│   ├── vendor/
│   │   └── ripgrep/
│   │       └── ppc64le-linux/  # Our ppc64le binary
│   └── ...
├── README.md
├── CODE_OF_CONDUCT.md
└── CONTRIBUTING.md
```

## Pull Request Guidelines

### Before Submitting a PR

1. **Create an issue first** (for major changes)
   - Discuss your proposed changes
   - Get feedback from maintainers
   - Avoid duplicate work

2. **Make sure your code works on ppc64le**
   - Test on actual POWER8 hardware if possible
   - Document any platform-specific considerations

3. **Follow the existing code style**
   - Match the formatting of existing files
   - Use clear, descriptive variable names
   - Add comments for complex logic

### Submitting a PR

1. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**
   - Keep commits atomic and focused
   - Write clear commit messages
   - Reference related issues

3. **Test your changes**
   ```bash
   npm test  # If tests exist
   claude    # Manual testing
   ```

4. **Update documentation**
   - Update README.md if needed
   - Add or update inline comments
   - Update any relevant wiki pages

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "type: brief description"
   ```
   
   **Commit message format:**
   - `feat:` - New feature
   - `fix:` - Bug fix
   - `docs:` - Documentation changes
   - `test:` - Adding or updating tests
   - `refactor:` - Code refactoring
   - `chore:` - Maintenance tasks

6. **Push and create PR**
   ```bash
   git push origin feature/your-feature-name
   ```
   
   Then create a pull request via GitHub's web interface or:
   ```bash
   gh pr create
   ```

### PR Checklist

- [ ] Code compiles and runs on ppc64le
- [ ] Commit messages follow the format guidelines
- [ ] Documentation has been updated
- [ ] Changes have been tested
- [ ] PR description clearly explains the changes
- [ ] Related issues are referenced

## Reporting Issues

### Security Issues

**Do not file public issues for security vulnerabilities.** Instead, email scott@elyanlabs.ai with:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Regular Issues

For non-security issues:
1. Search existing issues first
2. Use a clear, descriptive title
3. Provide as much context as possible
4. Include environment details
5. Use issue templates if available

## Questions or Need Help?

- Open an issue for bugs or feature requests
- Email scott@elyanlabs.ai for private inquiries
- Check the [README.md](README.md) for additional information

## Attribution

If you contribute to this project, you agree that your contributions will be licensed under the same license as the project (Apache 2.0 for the port additions, MIT for ripgrep binary).

---

Thank you for contributing to making Claude Code accessible on POWER8 hardware! 🚀
