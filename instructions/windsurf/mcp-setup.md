# MCP Setup for Windsurf AI IDE

Windsurf's AI capabilities can be significantly enhanced through Model Context Protocol (MCP) servers, providing specialized tools and external service integrations. This guide covers how to configure and optimize MCP servers specifically for Windsurf's AI-powered development environment.

## 🚀 Overview

Windsurf builds upon VS Code's foundation while adding advanced AI features. MCP servers extend these capabilities by providing access to external tools, databases, APIs, and specialized services that complement Windsurf's native AI assistance.

## 📋 Prerequisites

- Windsurf AI IDE installed and configured
- Node.js (version 16 or higher)
- npm or yarn package manager
- Basic familiarity with Windsurf's AI features
- Understanding of your development environment and tools

## ⚙️ MCP Configuration for Windsurf

### 1. Windsurf Settings Configuration

Windsurf inherits VS Code's extension architecture, making MCP configuration straightforward:

1. Open Windsurf Settings (Ctrl/Cmd + ,)
2. Navigate to Extensions or search for "MCP"
3. Configure MCP servers in settings.json or through the UI

### 2. Basic MCP Server Configuration

Add to Windsurf's settings.json:
```json
{
  "windsurf.mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--headless"
      ],
      "tools": ["*"],
      "description": "Browser automation and testing framework"
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
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ],
      "tools": ["*"],
      "description": "Complex problem decomposition and planning"
    }
  }
}
```

## 🔧 Essential MCP Servers for Windsurf

### Playwright MCP - Web Development Excellence
**Perfect for:** Frontend developers and QA engineers

**Installation:**
```bash
npm install -g @playwright/mcp
```

**Windsurf Integration Benefits:**
- Real-time browser testing while developing
- Automated screenshot generation for documentation
- End-to-end test creation and execution
- Visual regression testing capabilities

**Configuration with Options:**
```json
{
  "playwright": {
    "command": "npx",
    "args": [
      "@playwright/mcp@latest",
      "--headless",
      "--browser", "chromium",
      "--viewport", "1920x1080"
    ],
    "tools": ["*"],
    "env": {
      "PLAYWRIGHT_BROWSERS_PATH": "/usr/local/lib/playwright"
    }
  }
}
```

### Context7 MCP - Enhanced Intelligence
**Perfect for:** Projects requiring external data integration

**Installation:**
```bash
npm install -g @upstash/context7-mcp
```

**Environment Configuration:**
```bash
# Add to your .env file
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
OPENAI_API_KEY=your_openai_key
```

**Advanced Configuration:**
```json
{
  "context7": {
    "command": "npx",
    "args": ["-y", "@upstash/context7-mcp@latest"],
    "env": {
      "UPSTASH_REDIS_REST_URL": "${env:UPSTASH_REDIS_REST_URL}",
      "UPSTASH_REDIS_REST_TOKEN": "${env:UPSTASH_REDIS_REST_TOKEN}",
      "OPENAI_API_KEY": "${env:OPENAI_API_KEY}",
      "CONTEXT_CACHE_TTL": "3600"
    },
    "tools": ["*"]
  }
}
```

### Sequential Thinking MCP - Problem Solving
**Perfect for:** Complex development challenges and architecture planning

**Installation:**
```bash
npm install -g @modelcontextprotocol/server-sequential-thinking
```

**Use Cases with Windsurf:**
- Breaking down complex features into implementable steps
- Architectural decision making
- Debugging complex issues systematically
- Planning multi-step refactoring operations

### Database MCP Servers
**Essential for:** Backend development and data management

**PostgreSQL Configuration:**
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
    "description": "PostgreSQL database operations and queries"
  }
}
```

**SQLite Configuration:**
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
    "description": "Local SQLite database management"
  }
}
```

## 🔄 Windsurf + MCP Workflow Examples

### Full-Stack Development Workflow
1. **Planning Phase**
   - Use Sequential Thinking MCP to break down feature requirements
   - Windsurf's AI analyzes existing codebase for integration points
   - Context7 MCP provides external API documentation and examples

2. **Implementation Phase**
   - Windsurf generates code with AI assistance
   - Database MCP handles schema updates and data operations
   - Playwright MCP creates tests in parallel with development

3. **Testing and Validation**
   - Automated browser testing through Playwright MCP
   - Database validation through SQL MCP servers
   - Performance testing and optimization suggestions

### API Development with Database Integration
```json
{
  "api-development": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {"DATABASE_URL": "${env:DATABASE_URL}"},
      "tools": ["*"]
    },
    "rest-client": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-rest"],
      "tools": ["*"],
      "description": "API testing and validation"
    }
  }
}
```

### Frontend Development with Testing
```json
{
  "frontend-development": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headed"],
      "tools": ["*"]
    },
    "bundler-analyzer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-bundler"],
      "tools": ["*"],
      "description": "Bundle analysis and optimization"
    }
  }
}
```

## 🛠️ Advanced MCP Configuration

### Custom Project MCP Server
Create specialized tools for your project:

```javascript
// windsurf-project-tools.js
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server({
  name: 'windsurf-project-tools',
  version: '1.0.0'
});

// Custom deployment tool
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [
    {
      name: 'deploy_to_env',
      description: 'Deploy application to specified environment',
      inputSchema: {
        type: 'object',
        properties: {
          environment: { 
            type: 'string', 
            enum: ['development', 'staging', 'production'] 
          },
          force: { type: 'boolean', default: false }
        },
        required: ['environment']
      }
    },
    {
      name: 'run_tests_suite',
      description: 'Execute comprehensive test suite',
      inputSchema: {
        type: 'object',
        properties: {
          suite: { 
            type: 'string',
            enum: ['unit', 'integration', 'e2e', 'all']
          },
          parallel: { type: 'boolean', default: true }
        },
        required: ['suite']
      }
    }
  ]
}));

// Tool execution handlers
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  const { name, arguments: args } = request.params;
  
  switch (name) {
    case 'deploy_to_env':
      // Custom deployment logic
      return {
        content: [{
          type: 'text',
          text: `Deploying to ${args.environment}${args.force ? ' (forced)' : ''}`
        }]
      };
    
    case 'run_tests_suite':
      // Test execution logic
      return {
        content: [{
          type: 'text',
          text: `Running ${args.suite} tests${args.parallel ? ' in parallel' : ''}`
        }]
      };
  }
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

### Workspace-Specific Configuration
Create `.windsurf/settings.json` in your project root:

```json
{
  "windsurf.mcpServers": {
    "project-tools": {
      "command": "node",
      "args": ["./scripts/windsurf-project-tools.js"],
      "tools": ["*"],
      "description": "Project-specific automation and deployment tools"
    },
    "local-database": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sqlite",
        "--db-path",
        "./local-dev.db"
      ],
      "tools": ["*"],
      "description": "Local development database"
    }
  }
}
```

## 🔍 Windsurf AI + MCP Integration Patterns

### Natural Language to Implementation
1. **Requirement Analysis**
   - Describe feature in natural language to Windsurf AI
   - Sequential Thinking MCP breaks down into steps
   - Context7 MCP provides relevant examples and patterns

2. **Code Generation**
   - Windsurf generates implementation code
   - Database MCP handles data layer operations
   - Playwright MCP creates corresponding tests

### Intelligent Debugging Workflow
1. **Issue Identification**
   - Windsurf AI analyzes error messages and logs
   - Database MCP checks data integrity
   - Sequential Thinking MCP plans debugging approach

2. **Problem Resolution**
   - Systematic debugging with MCP tool assistance
   - Real-time testing with Playwright MCP
   - Context validation through various MCP servers

## 🐛 Troubleshooting and Optimization

### Common Configuration Issues

1. **MCP Server Startup Problems**
   ```bash
   # Verify Node.js and npm versions
   node --version
   npm --version
   
   # Check MCP server installation
   npm list -g | grep mcp
   
   # Test server directly
   npx @playwright/mcp --help
   ```

2. **Environment Variable Issues**
   ```bash
   # Create .env.example for team reference
   echo "DATABASE_URL=postgresql://localhost:5432/mydb" > .env.example
   echo "UPSTASH_REDIS_REST_URL=your_redis_url" >> .env.example
   
   # Load environment in Windsurf
   # Settings -> Features -> Terminal -> Inherit Environment Variables
   ```

3. **Performance Optimization**
   ```json
   {
     "windsurf.mcpServers": {
       "playwright": {
         "command": "npx",
         "args": ["@playwright/mcp@latest", "--headless"],
         "tools": ["*"],
         "timeout": 60000,
         "maxRetries": 2,
         "healthCheck": true
       }
     }
   }
   ```

### Debug Configuration
```json
{
  "windsurf.mcpServers": {
    "debug": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-debug"],
      "tools": ["*"],
      "logLevel": "debug",
      "enabled": true
    }
  }
}
```

## 🔒 Security and Best Practices

### Credential Management
1. **Environment Variable Security**
   ```bash
   # Use a secrets manager in production
   # For local development, use .env files
   
   # .env (never commit this file)
   DATABASE_URL=postgresql://user:pass@localhost:5432/db
   REDIS_URL=redis://localhost:6379
   API_KEY=your_secret_api_key
   
   # .env.example (commit this template)
   DATABASE_URL=postgresql://user:pass@localhost:5432/db_name
   REDIS_URL=redis://localhost:6379
   API_KEY=your_api_key_here
   ```

2. **MCP Server Security**
   ```json
   {
     "postgres-secure": {
       "command": "npx",
       "args": ["-y", "@modelcontextprotocol/server-postgres"],
       "env": {
         "DATABASE_URL": "${env:DATABASE_URL}"
       },
       "tools": ["read_query", "describe_tables"],
       "securityPolicy": "restricted"
     }
   }
   ```

### Network Security
```json
{
  "windsurf.mcpServers": {
    "secure-api": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-rest"],
      "env": {
        "API_BASE_URL": "${env:API_BASE_URL}",
        "API_KEY": "${env:API_KEY}"
      },
      "tools": ["*"],
      "networkPolicy": {
        "allowedHosts": ["api.yourservice.com"],
        "requireHttps": true
      }
    }
  }
}
```

## 📊 Performance Monitoring and Optimization

### Resource Management
```json
{
  "windsurf.mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"],
      "tools": ["*"],
      "resourceLimits": {
        "memory": "512MB",
        "cpu": "0.5",
        "timeout": 30000
      }
    }
  }
}
```

### Caching Configuration
```json
{
  "context7": {
    "command": "npx",
    "args": ["-y", "@upstash/context7-mcp@latest"],
    "env": {
      "CACHE_TTL": "1800",
      "MAX_CACHE_ENTRIES": "1000",
      "ENABLE_COMPRESSION": "true"
    },
    "tools": ["*"]
  }
}
```

## 💡 Best Practices and Tips

### Development Workflow Optimization
1. **Selective MCP Server Loading**
   - Only enable MCP servers needed for current project
   - Use workspace-specific configurations
   - Disable unused servers to improve performance

2. **MCP Server Health Monitoring**
   ```json
   {
     "windsurf.mcpServers": {
       "healthCheck": {
         "enabled": true,
         "interval": 30000,
         "retryAttempts": 3,
         "alertOnFailure": true
       }
     }
   }
   ```

### Team Collaboration
1. **Shared Configuration**
   ```json
   // .windsurf/team-settings.json
   {
     "windsurf.mcpServers": {
       "shared-database": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-postgres"],
         "env": {"DATABASE_URL": "${env:SHARED_DATABASE_URL}"},
         "tools": ["*"]
       }
     }
   }
   ```

2. **Documentation Standards**
   - Document all MCP server configurations
   - Maintain environment variable templates
   - Create setup scripts for new team members

### Production Considerations
1. **Environment Separation**
   ```json
   {
     "windsurf.mcpServers": {
       "production-db": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-postgres"],
         "env": {"DATABASE_URL": "${env:PRODUCTION_DATABASE_URL}"},
         "tools": ["read_query", "describe_tables"],
         "enabled": false,
         "note": "Enable only for production debugging"
       }
     }
   }
   ```

By implementing these MCP configurations, you'll significantly enhance Windsurf's already powerful AI capabilities, creating a comprehensive development environment that can handle complex workflows, integrate with external services, and provide intelligent assistance throughout your development process.