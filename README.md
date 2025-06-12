# Agent Setup Repository

A comprehensive collection of GitHub Copilot instructions and configurations for different project structures, providing guidance on how to effectively utilize AI assistants in your development workflow.

## 📚 Repository Overview

This repository contains structured guidelines and configurations for leveraging GitHub Copilot and other AI-assisted development tools across different project environments. It serves as a central resource for teams looking to standardize their approach to AI-assisted development.

## 📁 Repository Structure

- **`instructions/`**: Contains template instructions for different project structures and AI coding assistants
  - **`nextjs/`**: GitHub Copilot instructions specifically tailored for Next.js projects
  - **`rust/`**: GitHub Copilot instructions specifically tailored for Rust projects
  - **`al/`**: GitHub Copilot instructions specifically tailored for AL (Business Central) projects
  - **`claude/`**: Instructions and MCP setup for Claude AI coding assistant
  - **`cline/`**: Instructions and MCP setup for Cline VS Code extension
  - **`cursor/`**: Instructions and MCP setup for Cursor AI code editor
  - **`windsurf/`**: Instructions and MCP setup for Windsurf AI IDE
  - **`copilio/`**: Instructions and MCP setup for Copilio AI coding assistant
  - **`template_for_agents.md`**: General template for AI agent instructions that can be adapted for various contexts
- **`mcp/`**: Model Context Protocol configurations
  - **`mcpServers.json`**: Configuration for different MCP servers including Playwright, Context7, and sequential-thinking

## 🤖 About Model Context Protocol (MCP)

The Model Context Protocol (MCP) is a communication protocol that enables AI models to interact with various tools and services. This repository includes configurations for several MCP servers:

- **Playwright MCP**: For browser automation and testing
- **Context7 MCP**: For enhanced context-aware AI responses
- **Sequential Thinking MCP**: For breaking down complex problems into sequential steps

## 🚀 How to Use These Templates

### For Specific Project Types

#### Next.js Projects
1. Copy the appropriate instructions from `instructions/nextjs/copilot-instructions.md` into your project's documentation
2. Customize the instructions to fit your project's specific requirements
3. Share these guidelines with your team to establish consistent practices for working with GitHub Copilot

#### Rust Projects
1. Use the instructions from `instructions/rust/copilot-instructions.md` for Rust-specific development
2. Follow Rust-specific best practices and cargo workflow integration

#### AL/Business Central Projects
1. Reference `instructions/al/copilot-instructions.md` for AL language development
2. Integrate with Business Central development workflows

### For AI Coding Assistants

#### Claude AI Assistant
1. Use `instructions/claude/agent-instructions.md` for Claude-specific coding guidelines
2. Follow `instructions/claude/mcp-setup.md` for Model Context Protocol configuration
3. Adapt the instructions to your specific development environment

#### Cline VS Code Extension
1. Reference `instructions/cline/agent-instructions.md` for Cline-specific workflows
2. Configure MCP servers using `instructions/cline/mcp-setup.md`
3. Integrate with VS Code development environment

#### Cursor AI Code Editor
1. Apply guidelines from `instructions/cursor/agent-instructions.md`
2. Set up MCP integration with `instructions/cursor/mcp-setup.md`
3. Leverage Cursor's AI-powered features

#### Windsurf AI IDE
1. Follow `instructions/windsurf/agent-instructions.md` for Windsurf-specific development
2. Configure advanced MCP setups using `instructions/windsurf/mcp-setup.md`
3. Optimize for Windsurf's AI capabilities

#### Copilio AI Coding Assistant
1. Use `instructions/copilio/agent-instructions.md` for comprehensive coding assistance
2. Implement MCP configurations from `instructions/copilio/mcp-setup.md`
3. Integrate with various development environments

### Using MCP Configurations

1. Copy the `mcp/mcpServers.json` file to your project
2. Install the required dependencies via npm:
   ```bash
   npm install @playwright/mcp @upstash/context7-mcp @modelcontextprotocol/server-sequential-thinking
   ```
3. Reference these configurations in your development environment

### General Agent Instructions

The `template_for_agents.md` provides a comprehensive framework for AI agent instructions, covering:
- Initial context and setup
- Communication guidelines
- Tool usage guidelines
- Code change guidelines
- Debugging practices
- External API integration

## 💡 Best Practices

When using GitHub Copilot with these templates:

1. **Well-Scoped Tasks**: Ensure issues assigned to Copilot are clear and well-defined
2. **Appropriate Task Selection**: Assign suitable tasks like bug fixes, test coverage, and documentation updates
3. **Code Review**: Always review Copilot-generated code for security and quality
4. **Iterative Feedback**: Batch comments when reviewing Copilot's work for more coherent updates

## 👥 Contributing

Contributions to expand and improve these templates are welcome! Please feel free to submit pull requests or open issues with suggestions for new project structures or improvements to existing templates.

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
