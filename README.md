# Agent Setup Repository

A comprehensive collection of GitHub Copilot instructions and configurations for different project structures, providing guidance on how to effectively utilize AI assistants in your development workflow.

## 📚 Repository Overview

This repository contains structured guidelines and configurations for leveraging GitHub Copilot and other AI-assisted development tools across different project environments. It serves as a central resource for teams looking to standardize their approach to AI-assisted development.

## 📁 Repository Structure

- **`instructions/`**: Contains template instructions for different project structures
  - **`nextjs/`**: GitHub Copilot instructions specifically tailored for Next.js projects
  - **`template_for_agents.md`**: General template for AI agent instructions that can be adapted for various contexts
- **`mcp/`**: Model Context Protocol configurations
  - **`mcpServers.json`**: Configuration for different MCP servers including Playwright, Context7, and sequential-thinking

## 🤖 About Model Context Protocol (MCP)

The Model Context Protocol (MCP) is a communication protocol that enables AI models to interact with various tools and services. This repository includes configurations for several MCP servers:

- **Playwright MCP**: For browser automation and testing
- **Context7 MCP**: For enhanced context-aware AI responses
- **Sequential Thinking MCP**: For breaking down complex problems into sequential steps

## 🚀 How to Use These Templates

### For Next.js Projects

1. Copy the appropriate instructions from `instructions/nextjs/copilot-instructions.md` into your project's documentation
2. Customize the instructions to fit your project's specific requirements
3. Share these guidelines with your team to establish consistent practices for working with GitHub Copilot

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
