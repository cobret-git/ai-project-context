# 🤖 AI Project Context Generator

Generate comprehensive project context files for AI coding assistants like Claude, ChatGPT, and GitHub Copilot.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-blue.svg)](https://github.com/PowerShell/PowerShell)

## 📋 Overview

This universal PowerShell script scans your entire codebase and generates a structured markdown file containing all your source code. Perfect for:

- 🤖 Providing full project context to AI assistants
- 📚 Creating comprehensive code documentation
- 🔍 Code reviews and audits
- 📦 Project handoffs and onboarding

**Works with any programming language or framework** - .NET, JavaScript, Python, Swift, Java, Go, Rust, and more!

## ✨ Features

- ✅ **Universal** - Works with any codebase (web, mobile, desktop, embedded)
- ✅ **Smart Filtering** - Respects `.gitignore` and detects binary files automatically
- ✅ **40+ Languages** - Proper syntax highlighting for all major languages
- ✅ **Auto-Discovery** - Finds repository root automatically
- ✅ **Configurable** - Customize output location and filename
- ✅ **Fast** - Processes thousands of files in seconds
- ✅ **Safe** - Excludes binaries, media, node_modules, build artifacts

## 🚀 Getting Started

### Prerequisites

- **Windows PowerShell 5.1+** or **PowerShell Core 7+** (cross-platform)
- Git repository (optional, but recommended)

### Installation

1. **Download the script:**
````powershell
   # Clone the repository
   git clone https://github.com/yourusername/ai-project-context.git
   
   # Or download just the script
   Invoke-WebRequest -Uri "https://raw.githubusercontent.com/yourusername/ai-project-context/main/generate-context.ps1" -OutFile "generate-context.ps1"
````

2. **Place the script:**
   - Recommended: `your-project/src/generate-context.ps1`
   - Alternative: Anywhere in your repository

### Basic Usage
````powershell
# Navigate to your project
cd C:\Projects\YourProject

# Run the script
.\generate-context.ps1
````

**Output:** Creates `.claude/project-context.md` at your repository root.

## 📖 Usage Examples

### Basic Usage
````powershell
# Generate context with default settings
.\generate-context.ps1
````

### Custom Output Directory
````powershell
# Use a different directory name
.\generate-context.ps1 -OutputDirName ".ai-context"
````

### Custom Filename
````powershell
# Change the output filename
.\generate-context.ps1 -OutputFileName "full-context.md"
````

### Disable Auto Root-Finding
````powershell
# Use script's location as root instead of finding .git
.\generate-context.ps1 -FindRoot:$false
````

### Combined Options
````powershell
.\generate-context.ps1 -OutputDirName ".ai" -OutputFileName "codebase.md" -FindRoot:$false
````

## ⚙️ Configuration

### Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `OutputDirName` | string | `.claude` | Name of output directory |
| `OutputFileName` | string | `project-context.md` | Name of output file |
| `FindRoot` | switch | `$true` | Auto-find repository root via .git |

### What Gets Included?

**✅ Included:**
- All text-based source files
- Configuration files (JSON, YAML, XML, etc.)
- Scripts (PowerShell, Bash, Python, etc.)
- Documentation (Markdown, etc.)
- Project files (.csproj, package.json, etc.)

**❌ Excluded:**
- Binary files (executables, DLLs, images)
- Build artifacts (bin/, obj/, dist/, node_modules/)
- Media files (images, videos, audio, fonts)
- Large files (>1MB)
- Patterns in `.gitignore`

### Customizing Exclusions

The script automatically reads your `.gitignore`. To exclude additional patterns, simply add them to your `.gitignore`:
````gitignore
# Your existing patterns
node_modules/
dist/

# Additional exclusions for context generation
*.generated.cs
temp/
````

## 🤝 Contributing

Contributions welcome! Areas for improvement:

- [ ] Add support for custom ignore files beyond `.gitignore`
- [ ] Option to split large outputs into multiple files
- [ ] Statistics and metrics in output
- [ ] Progress bar for large repositories
- [ ] Configuration file support

## 📝 Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

## 📜 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by the need to provide comprehensive context to AI coding assistants
- Built for the AI-assisted development community

## 💬 Support

- 🐛 **Issues**: [GitHub Issues](https://github.com/yourusername/ai-project-context/issues)
- 💡 **Discussions**: [GitHub Discussions](https://github.com/yourusername/ai-project-context/discussions)
- ⭐ **Star** this repo if you find it useful!

````