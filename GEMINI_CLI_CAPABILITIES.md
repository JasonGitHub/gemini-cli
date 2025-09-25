# Gemini CLI Capabilities Summary

## Overview

Gemini CLI is an open-source AI agent that brings the power of Google's Gemini AI models directly into your terminal. It serves as a lightweight, terminal-first interface that provides direct access to Gemini's capabilities while offering powerful local integration tools.

## Core Capabilities

### 🚀 AI Model Access

- **Gemini 2.5 Pro**: Access to 1M token context window for complex tasks
- **Gemini 2.5 Flash**: Faster responses for simpler queries
- **Model Selection**: Choose specific models via `-m` flag
- **Free Tier**: 60 requests/min, 1,000 requests/day with personal Google account
- **Multiple Auth**: OAuth, API key, or Vertex AI authentication

### 💻 Interactive & Non-Interactive Modes

#### Interactive Mode

```bash
gemini
> How can I optimize this codebase?
```

#### Non-Interactive Scripting

```bash
# Simple text response
gemini -p "Explain the architecture of this codebase"

# Structured JSON output for scripting
gemini -p "Analyze this code" --output-format json
```

## Built-in Tools & Capabilities

The CLI includes sophisticated built-in tools that enable Gemini to interact with your local environment:

### 📁 File System Operations

- **Read Files**: Text, images (PNG, JPG, GIF, WEBP, SVG, BMP), and PDF files
- **Write Files**: Create or overwrite files with new content
- **List Directories**: Browse folder contents with filtering options
- **Multi-File Reading**: Process multiple files or entire directories at once
- **Smart Editing**: Intelligent code modifications with diff generation
- **Search & Grep**: Find content across files using patterns

### 🌐 Web Integration

- **Web Search**: Built-in Google Search grounding for real-time information
- **Web Fetch**: Retrieve content from URLs (up to 20 URLs simultaneously)
- **Content Processing**: Automatically process and summarize web content

### ⚡ Shell Integration

- **Shell Commands**: Execute system commands with safety confirmations
- **Shell Mode**: Toggle into dedicated shell interaction mode
- **Environment Awareness**: `GEMINI_CLI=1` environment variable for script detection

### 📝 Memory & Context Management

- **Memory Tool**: Save and recall information across sessions
- **Context Files**: Custom `GEMINI.md` files for project-specific instructions
- **Hierarchical Memory**: Project, user, and global context levels
- **File Filtering**: Respect `.gitignore` and `.geminiignore` patterns

## Advanced Features

### 🎯 Conversation Management

- **Checkpointing**: Save and resume complex conversations
- **State Branching**: Create multiple conversation branches
- **Session Compression**: Summarize conversations to save tokens
- **Automatic Restoration**: Restore project state before tool execution

### 🔌 Extensibility via MCP (Model Context Protocol)

- **MCP Server Integration**: Connect to external services and APIs
- **Custom Tools**: Extend capabilities with custom integrations
- **Multiple Transports**: Stdio, SSE, and HTTP streaming support
- **Tool Discovery**: Automatic detection and registration of MCP tools

#### Example MCP Integrations

```bash
> @github List my open pull requests
> @slack Send a summary to #dev channel
> @database Run query to find inactive users
```

### 🎨 User Interface & Experience

- **Terminal-First Design**: Optimized for command-line workflows
- **Vim Mode**: Full vim-style navigation and editing
- **Theme Customization**: Visual appearance customization
- **Keyboard Shortcuts**: Productivity-focused hotkeys
- **Shell Passthrough**: Direct shell command execution with `!`

## Command System

### 📋 Slash Commands (`/`)

Rich set of meta-commands for CLI control:

- `/help` - Display available commands
- `/settings` - Configure CLI behavior
- `/tools` - List available tools
- `/memory` - Manage AI context and instructions
- `/chat save/resume/list` - Conversation management
- `/restore` - Undo tool changes with checkpointing
- `/stats` - View token usage and session statistics
- `/mcp` - Manage MCP server connections
- `/theme` - Customize visual appearance
- `/vim` - Toggle vim input mode

### 📎 Content Injection (`@`)

Include file/directory content in prompts:

```bash
@src/ Explain this codebase
@README.md What does this project do?
@config.json Analyze this configuration
```

### ⚡ Shell Integration (`!`)

Direct shell command execution:

```bash
!git status
!npm test
! # Toggle shell mode
```

### 🔧 Custom Commands

Create reusable custom commands with TOML configuration:

- **Global Commands**: Available across all projects (`~/.gemini/commands/`)
- **Project Commands**: Project-specific commands (`.gemini/commands/`)
- **Dynamic Content**: Shell command injection with `!{...}`
- **File Injection**: Include file content with `@{...}`
- **Argument Handling**: Context-aware argument substitution

#### Example Custom Command

```toml
# ~/.gemini/commands/refactor/pure.toml
description = "Refactor code into a pure function"
prompt = """
Please analyze the code and refactor it into a pure function.
Include:
1. The refactored code
2. Explanation of changes
"""
```

## GitHub Integration

### 🤖 GitHub Actions Integration

- **Pull Request Reviews**: Automated code review with contextual feedback
- **Issue Triage**: Automated labeling and prioritization
- **On-demand Assistance**: Mention `@gemini-cli` for help
- **Custom Workflows**: Build tailored automation workflows

## Multimodal Capabilities

### 🖼️ Content Understanding

- **Image Analysis**: Process images, sketches, and diagrams
- **PDF Processing**: Extract and analyze PDF content
- **Document Generation**: Create apps from visual mockups
- **Code from Images**: Generate code from screenshots or sketches

## Security & Safety

### 🛡️ Safety Features

- **Confirmation Prompts**: User approval for sensitive operations
- **Sandboxing**: Isolated execution environments (Docker/Podman)
- **File Filtering**: Automatic exclusion of sensitive files
- **Trust Levels**: Configurable trust settings for MCP servers
- **Workspace Boundaries**: Operations restricted to project directories

### 🔒 Authentication Options

1. **OAuth Login**: Sign in with Google account (recommended)
2. **API Key**: Direct Gemini API key usage
3. **Vertex AI**: Enterprise-grade authentication
4. **Workspace Integration**: Google Workspace account support

## Installation & Deployment

### 📦 Installation Methods

```bash
# Run instantly (no installation)
npx https://github.com/google-gemini/gemini-cli

# Install globally via npm
npm install -g @google/gemini-cli

# Install via Homebrew (macOS/Linux)
brew install gemini-cli
```

### 🏢 Enterprise Features

- **Docker Support**: Containerized deployment
- **System-wide Configuration**: Enterprise-wide settings
- **Telemetry & Monitoring**: Usage tracking and analytics
- **Batch Processing**: Non-interactive scripting support

## Use Cases & Examples

### 🔍 Code Analysis & Understanding

- Analyze large codebases and explain architecture
- Debug complex issues with natural language queries
- Review code changes and suggest improvements
- Generate documentation from code

### 🏗️ Development & Generation

- Create new applications from descriptions or mockups
- Generate boilerplate code and project structures
- Refactor code following best practices
- Write tests and documentation

### 🔄 Automation & Workflows

- Automate Git operations (commits, rebases, merges)
- Process pull requests and issues automatically
- Generate release notes and changelogs
- Coordinate team workflows via integrations

### 📊 Research & Information

- Search the web for current information
- Fetch and summarize web content
- Research technical topics with grounding
- Compare technologies and approaches

## System Requirements

- **Node.js**: Version 20 or higher
- **Platforms**: macOS, Linux, Windows
- **Optional**: Docker/Podman for sandboxing
- **Optional**: Platform-specific clipboard tools

## Community & Support

- **Open Source**: Apache 2.0 licensed
- **Active Development**: Regular releases (preview, stable, nightly)
- **Community Contributions**: Bug reports, features, MCP servers
- **Documentation**: Comprehensive guides and examples
- **Troubleshooting**: Built-in `/bug` command for issue reporting

This comprehensive tool transforms your terminal into a powerful AI-assisted development environment, bridging the gap between AI capabilities and practical development workflows.
