# MCP Setup for Cline VS Code Extension

Cline can be enhanced with Model Context Protocol (MCP) servers to extend its capabilities beyond basic file operations and terminal commands. This guide will help you configure MCP servers specifically for use with Cline in VS Code.

## 🚀 Overview

MCP servers provide Cline with access to external tools and services, enabling more sophisticated development workflows. Unlike standalone Claude, Cline operates within VS Code and can leverage MCP servers through configuration.

## 📋 Prerequisites

- VS Code with Cline extension installed
- Node.js (version 16 or higher)
- npm or yarn package manager
- Basic understanding of Cline's capabilities

## ⚙️ Configuration Setup

### 1. Cline Settings Configuration

In VS Code, access Cline's settings and configure MCP servers:

1. Open VS Code Settings (Ctrl/Cmd + ,)
2. Search for "Cline MCP" or navigate to Extensions > Cline
3. Add MCP server configurations

### 2. MCP Server Configuration Format

```json
{
  "cline.mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--headless"
      ],
      "tools": ["*"],
      "description": "Browser automation and testing"
    },
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp@latest"
      ],
      "tools": ["*"],
      "description": "Enhanced context awareness"
    },
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "--root",
        "."
      ],
      "tools": ["*"],
      "description": "Enhanced file system operations"
    }
  }
}
```

## 🔧 Recommended MCP Servers for Cline

### Playwright MCP
**Perfect for:** Frontend developers working with web applications

**Installation:**
```bash
npm install -g @playwright/mcp
```

**Use Cases with Cline:**
- Automated testing of web components you're building
- Screenshot generation for documentation
- End-to-end test creation
- Web scraping for data gathering

**Example Workflow:**
1. Cline builds a new React component
2. Uses Playwright MCP to generate automated tests
3. Takes screenshots for documentation
4. Updates test files in the project

### Filesystem MCP
**Perfect for:** Complex file operations and project management

**Installation:**
```bash
npm install -g @modelcontextprotocol/server-filesystem
```

**Use Cases with Cline:**
- Advanced file search and manipulation
- Bulk file operations
- Project structure analysis
- Template file generation

### Context7 MCP
**Perfect for:** Projects requiring external data integration

**Installation:**
```bash
npm install -g @upstash/context7-mcp
```

**Configuration with API Keys:**
```json
{
  "context7": {
    "command": "npx",
    "args": ["-y", "@upstash/context7-mcp"],
    "env": {
      "UPSTASH_REDIS_REST_URL": "${UPSTASH_REDIS_REST_URL}",
      "UPSTASH_REDIS_REST_TOKEN": "${UPSTASH_REDIS_REST_TOKEN}"
    },
    "tools": ["*"]
  }
}
```

### Database MCP Servers
**Perfect for:** Backend developers working with databases

**PostgreSQL MCP:**
```bash
npm install -g @modelcontextprotocol/server-postgres
```

**Configuration:**
```json
{
  "postgres": {
    "command": "npx",
    "args": [
      "-y",
      "@modelcontextprotocol/server-postgres",
      "--connection-string",
      "${DATABASE_URL}"
    ],
    "tools": ["*"],
    "description": "PostgreSQL database operations"
  }
}
```

## 🛠️ Development Workflow Integration

### Setting Up Environment Variables

Create a `.env` file in your workspace root:
```env
# Database connections
DATABASE_URL=postgresql://username:password@localhost:5432/database

# Redis/Context7
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token

# API Keys for external services
OPENAI_API_KEY=your_openai_key
GITHUB_TOKEN=your_github_token
```

### VS Code Settings Integration

Add to your VS Code workspace settings (`.vscode/settings.json`):
```json
{
  "cline.mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"],
      "tools": ["*"]
    },
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"],
      "env": {
        "UPSTASH_REDIS_REST_URL": "${env:UPSTASH_REDIS_REST_URL}",
        "UPSTASH_REDIS_REST_TOKEN": "${env:UPSTASH_REDIS_REST_TOKEN}"
      },
      "tools": ["*"]
    }
  }
}
```

## 🔄 Common Workflows

### Web Development Workflow
1. **Cline creates React components**
2. **Playwright MCP generates tests automatically**
3. **Context7 MCP fetches external data for components**
4. **Filesystem MCP manages asset organization**

### Backend Development Workflow
1. **Cline implements API endpoints**
2. **Database MCP handles schema migrations**
3. **Context7 MCP manages cache operations**
4. **Playwright MCP creates API tests**

### Full-Stack Development
1. **Cline coordinates frontend/backend changes**
2. **Database MCP ensures data consistency**
3. **Playwright MCP tests entire user flows**
4. **Multiple MCP servers work together seamlessly**

## 🐛 Troubleshooting

### Common Issues

1. **MCP Server Not Found**
   ```bash
   # Verify installation
   npm list -g | grep mcp
   
   # Reinstall if needed
   npm install -g @playwright/mcp
   ```

2. **Permission Issues**
   ```bash
   # Check Node.js permissions
   npm config get prefix
   
   # Fix permissions if needed
   sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
   ```

3. **Environment Variables Not Loading**
   - Ensure `.env` file is in workspace root
   - Restart VS Code after adding environment variables
   - Check VS Code terminal environment

### Debug Commands
```bash
# Test MCP server directly
npx @playwright/mcp --help

# Check Cline logs in VS Code
# View -> Output -> Select "Cline" from dropdown

# Verify environment variables
echo $DATABASE_URL
```

## 🔒 Security Best Practices

1. **Environment Variables**
   - Never commit `.env` files to version control
   - Use different environments for development/production
   - Rotate credentials regularly

2. **MCP Server Permissions**
   - Limit tool access with specific permissions
   - Review MCP server source code before installation
   - Monitor network activity from MCP servers

3. **Workspace Security**
   - Use workspace-specific settings when possible
   - Avoid global configurations for sensitive projects
   - Regular security audits of installed MCP servers

## 📚 Advanced Configuration

### Custom MCP Server for Project-Specific Tools
```javascript
// custom-project-mcp.js
import { Server } from '@modelcontextprotocol/sdk/server/index.js';

const server = new Server({
  name: 'project-specific-tools',
  version: '1.0.0'
});

// Add project-specific tools
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{
    name: 'deploy_to_staging',
    description: 'Deploy current branch to staging environment',
    inputSchema: {
      type: 'object',
      properties: {
        branch: { type: 'string' }
      }
    }
  }]
}));
```

### Integration with CI/CD
```yaml
# .github/workflows/mcp-setup.yml
name: Setup MCP Servers
on: [push]
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
      - run: npm install -g @playwright/mcp
      - run: npm install -g @upstash/context7-mcp
```

## 💡 Best Practices

1. **Start Small**: Begin with one MCP server and add more as needed
2. **Monitor Performance**: Keep track of MCP server response times
3. **Version Control**: Pin MCP server versions in production
4. **Documentation**: Document your MCP setup for team members
5. **Testing**: Test MCP integrations in development environment first

By following this guide, you'll be able to extend Cline's capabilities significantly, making it an even more powerful development partner within VS Code.