# AI Project Context Generator

A PowerShell script that scans your codebase and generates a single markdown file with all your source code. Useful for giving AI assistants full project context.

Works with any language or framework.

## How it works

The script walks your repository, skips binary files and common junk (node_modules, build artifacts, etc.), and writes everything else into a structured markdown file with syntax-highlighted code blocks.

Files are excluded in this order:

1. `.gitignore` patterns + built-in defaults (node_modules, bin, obj, dist, etc.)
2. `.aiignore` patterns — an additional ignore file you control, specifically for hiding things from the AI context output

This means `.aiignore` is only about what gets shared with AI. Your git-ignored files are already excluded automatically.

## Prerequisites

- Windows PowerShell 5.1+ or PowerShell Core 7+
- A git repository (optional but recommended — the script uses `.git` to find the project root)

## Installation

Put `generate-context.ps1` somewhere in your repository. The root or a `scripts/` folder both work fine.

## Usage

```powershell
# Basic — generates .claude/project-context.md at your repo root
.\generate-context.ps1

# Custom output directory
.\generate-context.ps1 -OutputDirName ".ai-context"

# Custom filename
.\generate-context.ps1 -OutputFileName "full-context.md"

# Don't walk up to find .git — use script location as root
.\generate-context.ps1 -FindRoot:$false

# Custom .aiignore filename
.\generate-context.ps1 -AiIgnoreFileName ".my-ai-ignore"
```

## Parameters

| Parameter | Default | Description |
|---|---|---|
| `OutputDirName` | `.claude` | Output directory name |
| `OutputFileName` | `project-context.md` | Output file name |
| `FindRoot` | `$true` | Walk up to find `.git` directory as project root |
| `AiIgnoreFileName` | `.aiignore` | Name of the AI-specific ignore file |

## The `.aiignore` file

Create a `.aiignore` file in your repository root to exclude files and directories from the generated context. This is separate from `.gitignore` — it's for things that are tracked in git but shouldn't be sent to an AI assistant (secrets, credentials, internal configs, proprietary data, etc.).

The syntax follows the same conventions as `.gitignore`:

```gitignore
# Comments start with #

# Ignore a directory
secrets/
config/production/

# Ignore specific files
.env.production
internal-api-keys.json

# Wildcard patterns
*.secret
*.credentials
*-internal.*
```

### When to use `.aiignore` vs `.gitignore`

- `.gitignore` — files that shouldn't be in version control at all (build output, local configs, etc.). These are already excluded from context generation automatically.
- `.aiignore` — files that belong in the repo but shouldn't be shared with AI tools. Think: production secrets committed to a private repo, proprietary algorithms, client data, internal documentation you don't want leaving the company.

### What gets excluded by default

Even without any ignore files, the script always skips:

- Binary files (executables, images, video, audio, fonts, archives, etc.)
- Files larger than 1 MB
- Common framework directories: node_modules, bin, obj, dist, build, vendor, target, __pycache__
- IDE directories: .vs, .vscode, .idea
- OS files: .DS_Store, Thumbs.db

## License

MIT