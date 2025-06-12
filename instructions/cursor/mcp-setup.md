# MCP Setup for Cursor AI Code Editor

Cursor's AI capabilities can be enhanced through Model Context Protocol (MCP) servers, providing extended functionality for development workflows. This guide covers how to configure and use MCP servers with Cursor for more powerful AI-assisted development.

## 🚀 Overview

Cursor integrates AI deeply into the coding experience, and MCP servers can extend these capabilities with specialized tools and external service integrations. While Cursor has built-in AI features, MCP servers add specific functionalities like browser automation, database interactions, and custom workflow tools.

## 📋 Prerequisites

- Cursor AI Code Editor installed
- Node.js (version 16 or higher)
- npm or yarn package manager
- Understanding of Cursor's AI features (Ctrl+K, Ctrl+L, etc.)

## ⚙️ MCP Configuration for Cursor

### 1. Cursor Settings Configuration

Cursor uses VS Code's architecture, so MCP configuration is similar to VS Code extensions:

1. Open Cursor Settings (Ctrl/Cmd + ,)
2. Search for "MCP" or "Model Context Protocol"
3. Configure MCP servers in settings.json

### 2. Basic MCP Configuration

Add to Cursor's settings.json:
```json
{
  "cursor.mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--headless"
      ],
      "tools": ["*"],
      "description": "Browser automation for testing and scraping"
    },
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp@latest"
      ],
      "tools": ["*"],
      "description": "Enhanced context and external data integration"
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
      "description": "Advanced file system operations"
    }
  }
}
```

## 🔧 Essential MCP Servers for Cursor

### Playwright MCP - Web Automation
**Best for:** Frontend developers working with web applications

**Installation:**
```bash
npm install -g @playwright/mcp
```

**Cursor Integration Benefits:**
- Generate automated tests while writing components
- Create screenshots for documentation
- Test user interactions in real-time
- Validate responsive design implementations

**Example Workflow:**
1. Write a React component in Cursor
2. Use Ctrl+K to ask AI to "create tests for this component"
3. Playwright MCP generates and runs browser tests
4. AI provides feedback on test results and suggests improvements

### Context7 MCP - Enhanced Intelligence
**Best for:** Projects requiring external data or advanced context

**Installation:**
```bash
npm install -g @upstash/context7-mcp
```

**Environment Setup:**
```bash
# Add to your .env file
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
```

**Configuration:**
```json
{
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
```

### Database MCP Servers
**Perfect for:** Backend development and data management

**PostgreSQL Setup:**
```bash
npm install -g @modelcontextprotocol/server-postgres
```

```json
{
  "postgres": {
    "command": "npx",
    "args": [
      "-y",
      "@modelcontextprotocol/server-postgres",
      "--connection-string",
      "${env:DATABASE_URL}"
    ],
    "tools": ["*"],
    "description": "Direct database interactions"
  }
}
```

**SQLite Setup:**
```bash
npm install -g @modelcontextprotocol/server-sqlite
```

```json
{
  "sqlite": {
    "command": "npx",
    "args": [
      "-y",
      "@modelcontextprotocol/server-sqlite",
      "--db-path",
      "./database.sqlite"
    ],
    "tools": ["*"],
    "description": "Local SQLite database operations"
  }
}
```

## 🔄 Cursor + MCP Workflow Examples

### Frontend Development Workflow
1. **Component Creation**
   - Use Cursor's AI to generate React/Vue components
   - Playwright MCP creates automated tests
   - Context7 MCP fetches external styling/data requirements

2. **Testing and Validation**
   - Write components with Cursor's AI assistance
   - Use Ctrl+K: "Test this component with Playwright"
   - MCP servers handle test execution and reporting

### Backend API Development
1. **API Endpoint Creation**
   - Generate API routes with Cursor's AI
   - Database MCP handles schema operations
   - Context7 MCP manages external API integrations

2. **Database Operations**
   - Use Cursor's AI for SQL query generation
   - PostgreSQL/SQLite MCP executes queries directly
   - Real-time feedback on query performance

### Full-Stack Development
1. **Integrated Development**
   - Cursor coordinates frontend/backend changes
   - Multiple MCP servers work together
   - Seamless database-to-UI workflows

## 🛠️ Advanced MCP Configuration

### Custom Project MCP Server
Create project-specific tools:

```javascript
// project-mcp-server.js
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server({
  name: 'project-tools',
  version: '1.0.0'
});

// Add custom deployment tool
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{
    name: 'deploy_preview',
    description: 'Deploy current changes to preview environment',
    inputSchema: {
      type: 'object',
      properties: {
        environment: { 
          type: 'string', 
          enum: ['staging', 'preview', 'dev'] 
        }
      }
    }
  }]
}));

// Tool execution handler
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  if (request.params.name === 'deploy_preview') {
    // Custom deployment logic
    return {
      content: [{
        type: 'text',
        text: 'Deployment started to ' + request.params.arguments.environment
      }]
    };
  }
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

### Workspace-Specific Configuration
Create `.cursor/settings.json` in your project:

```json
{
  "cursor.mcpServers": {
    "project-tools": {
      "command": "node",
      "args": ["./scripts/project-mcp-server.js"],
      "tools": ["*"],
      "description": "Project-specific automation tools"
    }
  }
}
```

## 🔍 Cursor AI Integration Patterns

### Using MCP with Cursor's AI Features

1. **Ctrl+K (Inline Edit) + MCP**
   ```
   Prompt: "Create a login form and add Playwright tests"
   Result: Cursor generates form + Playwright MCP creates tests
   ```

2. **Ctrl+L (Chat) + MCP**
   ```
   Chat: "Check the database for user authentication patterns"
   Result: Database MCP queries existing patterns
   ```

3. **AI-Powered Refactoring + MCP**
   ```
   Select code → Ctrl+K → "Refactor this and update tests"
   Result: Code refactored + tests updated via MCP
   ```

### Context-Aware Development
- Cursor's AI understands your codebase
- MCP servers provide external context
- Combined intelligence for better suggestions

## 🐛 Troubleshooting

### Common Issues

1. **MCP Server Connection Failed**
   ```bash
   # Check server installation
   npm list -g | grep mcp
   
   # Test server directly
   npx @playwright/mcp --help
   ```

2. **Environment Variables Not Loading**
   - Ensure `.env` file is in project root
   - Restart Cursor after adding environment variables
   - Check Cursor's integrated terminal

3. **Performance Issues**
   ```json
   {
     "cursor.mcpServers": {
       "playwright": {
         "command": "npx",
         "args": ["@playwright/mcp@latest", "--headless"],
         "tools": ["*"],
         "timeout": 30000,
         "maxRetries": 3
       }
     }
   }
   ```

### Debug Configuration
```json
{
  "cursor.mcpServers": {
    "debug-mcp": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-debug"],
      "tools": ["*"],
      "logLevel": "debug",
      "description": "Debug MCP server interactions"
    }
  }
}
```

## 🔒 Security Best Practices

### Environment Security
1. **Credential Management**
   - Use environment variables for sensitive data
   - Never commit API keys or passwords
   - Use different credentials for development/production

2. **MCP Server Security**
   - Review server source code before installation
   - Use specific tool permissions instead of "*"
   - Monitor server network activity

### Project Security
```json
{
  "cursor.mcpServers": {
    "secure-postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "${env:DATABASE_URL}"
      },
      "tools": ["read_query", "describe_tables"],
      "description": "Limited database access"
    }
  }
}
```

## 📊 Performance Optimization

### Efficient MCP Usage
1. **Selective Server Loading**
   ```json
   {
     "cursor.mcpServers": {
       "playwright": {
         "enabled": false,
         "autoStart": false
       }
     }
   }
   ```

2. **Resource Management**
   - Monitor CPU and memory usage
   - Use specific tool permissions
   - Configure appropriate timeouts

### Caching Strategies
```json
{
  "context7": {
    "command": "npx",
    "args": ["-y", "@upstash/context7-mcp@latest"],
    "env": {
      "CACHE_TTL": "3600",
      "MAX_CACHE_SIZE": "100MB"
    },
    "tools": ["*"]
  }
}
```

## 💡 Best Practices

1. **Start Simple**: Begin with one MCP server and add more as needed
2. **Project-Specific**: Use workspace settings for project-specific servers
3. **Performance Monitoring**: Keep track of MCP server performance
4. **Security First**: Always review and secure MCP server configurations
5. **Team Coordination**: Share MCP configurations with your team
6. **Documentation**: Document your MCP setup for team members

## 🔗 Integration Examples

### React + TypeScript + Playwright
```json
{
  "cursor.mcpServers": {
    "playwright-react": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--framework", "react"],
      "tools": ["*"],
      "description": "React-specific browser testing"
    }
  }
}
```

### Node.js + PostgreSQL + Redis
```json
{
  "cursor.mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {"DATABASE_URL": "${env:DATABASE_URL}"},
      "tools": ["*"]
    },
    "redis": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-redis"],
      "env": {"REDIS_URL": "${env:REDIS_URL}"},
      "tools": ["*"]
    }
  }
}
```

By following this guide, you'll be able to significantly enhance Cursor's already powerful AI capabilities with specialized MCP servers, creating a more comprehensive and intelligent development environment.