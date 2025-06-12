# Model Context Protocol (MCP) Setup for Claude

The Model Context Protocol (MCP) enhances Claude's capabilities by providing access to external tools and services during conversations. This guide will help you set up MCP servers to extend Claude's functionality.

## 🚀 Quick Start

### Prerequisites
- Node.js (version 16 or higher)
- npm or yarn package manager
- Claude Desktop application (for desktop integration)

### Basic MCP Configuration

1. **Create MCP Configuration File**
   
   Create a configuration file for your MCP servers. The exact location depends on your setup:
   
   For Claude Desktop:
   ```json
   {
     "mcpServers": {
       "playwright": {
         "command": "npx",
         "args": [
           "@playwright/mcp@latest",
           "--headless"
         ],
         "tools": ["*"]
       },
       "context7": {
         "command": "npx",
         "args": [
           "-y",
           "@upstash/context7-mcp@latest"
         ],
         "tools": ["*"]
       },
       "sequential-thinking": {
         "command": "npx",
         "args": [
           "-y",
           "@modelcontextprotocol/server-sequential-thinking"
         ],
         "tools": ["*"]
       }
     }
   }
   ```

2. **Install MCP Servers**
   
   Install the MCP servers you want to use:
   
   ```bash
   # Install Playwright MCP for browser automation
   npm install -g @playwright/mcp
   
   # Install Context7 MCP for enhanced context awareness
   npm install -g @upstash/context7-mcp
   
   # Install Sequential Thinking MCP for problem decomposition
   npm install -g @modelcontextprotocol/server-sequential-thinking
   ```

## 🔧 Available MCP Servers

### Playwright MCP
**Purpose:** Browser automation and web testing capabilities

**Use Cases:**
- Automated testing of web applications
- Web scraping and data extraction
- Screenshot generation
- Form filling and user interaction simulation

**Setup:**
```bash
npm install -g @playwright/mcp
```

**Example Usage:**
- "Take a screenshot of this website"
- "Fill out this form automatically"
- "Test this web application's login flow"

### Context7 MCP
**Purpose:** Enhanced context-aware AI responses with external knowledge integration

**Use Cases:**
- Access to real-time information
- Integration with external databases
- Enhanced context understanding
- Dynamic knowledge retrieval

**Setup:**
```bash
npm install -g @upstash/context7-mcp
```

**Configuration:**
You may need to configure API keys for external services:
```json
{
  "context7": {
    "command": "npx",
    "args": ["-y", "@upstash/context7-mcp"],
    "env": {
      "UPSTASH_REDIS_REST_URL": "your_redis_url",
      "UPSTASH_REDIS_REST_TOKEN": "your_redis_token"
    },
    "tools": ["*"]
  }
}
```

### Sequential Thinking MCP
**Purpose:** Breaking down complex problems into sequential, manageable steps

**Use Cases:**
- Complex problem decomposition
- Step-by-step solution planning
- Multi-stage development workflows
- Systematic debugging approaches

**Setup:**
```bash
npm install -g @modelcontextprotocol/server-sequential-thinking
```

**Example Usage:**
- "Break down this complex feature into development steps"
- "Create a systematic debugging plan for this issue"
- "Plan the architecture for this application"

## 🛠️ Custom MCP Server Development

You can create custom MCP servers for specific needs:

### Basic MCP Server Structure
```javascript
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server(
  {
    name: 'custom-mcp-server',
    version: '1.0.0',
  },
  {
    capabilities: {
      tools: {},
    },
  }
);

// Add your custom tools and handlers here
server.setRequestHandler(ListToolsRequestSchema, async () => {
  return {
    tools: [
      {
        name: 'custom_tool',
        description: 'Description of your custom tool',
        inputSchema: {
          type: 'object',
          properties: {
            // Define input parameters
          },
        },
      },
    ],
  };
});

// Start the server
const transport = new StdioServerTransport();
await server.connect(transport);
```

## 🔒 Security Considerations

When setting up MCP servers:

1. **API Key Management**
   - Store sensitive credentials in environment variables
   - Never commit API keys to version control
   - Use secure key management systems in production

2. **Network Security**
   - Restrict network access for MCP servers
   - Use HTTPS for external API communications
   - Validate and sanitize all inputs

3. **Access Control**
   - Limit tool access with appropriate permissions
   - Use the principle of least privilege
   - Monitor and log MCP server activities

## 🐛 Troubleshooting

### Common Issues

1. **MCP Server Won't Start**
   - Check Node.js version compatibility
   - Verify all dependencies are installed
   - Check for port conflicts

2. **Tools Not Available**
   - Verify MCP server configuration
   - Check tool permissions in config
   - Restart Claude application

3. **Connection Issues**
   - Check network connectivity
   - Verify API credentials
   - Review server logs for errors

### Debug Commands
```bash
# Check MCP server status
npx @modelcontextprotocol/inspector

# Test MCP server connection
node -e "console.log('MCP server test')"

# View server logs
tail -f ~/.mcp/logs/server.log
```

## 📚 Additional Resources

- [Official MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Server Registry](https://github.com/modelcontextprotocol/servers)
- [Claude MCP Integration Guide](https://docs.anthropic.com/)
- [Community MCP Servers](https://github.com/topics/mcp-server)

## 💡 Best Practices

1. **Start Simple**: Begin with one MCP server and gradually add more
2. **Test Thoroughly**: Verify each MCP server works before adding to production
3. **Monitor Performance**: Keep track of server response times and resource usage
4. **Keep Updated**: Regularly update MCP servers to latest versions
5. **Document Configuration**: Maintain clear documentation of your MCP setup

By following this guide, you'll be able to extend Claude's capabilities with powerful MCP servers, enabling more sophisticated and context-aware AI assistance for your development work.