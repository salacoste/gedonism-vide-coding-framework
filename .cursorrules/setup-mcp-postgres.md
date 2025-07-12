# PostgreSQL MCP Server Setup Guide

## Overview

The PostgreSQL MCP (Model Context Protocol) server enables Cursor and AI assistants to directly query your PostgreSQL database in a secure manner. This is incredibly useful for database-driven projects where you need to inspect data, analyze schemas, or generate reports.

## Prerequisites

- PostgreSQL database instance (local or remote)
- Node.js and npm installed
- Database credentials with read and write access
- Cursor IDE with MCP support

## Installation

The PostgreSQL MCP server can be installed and used in two ways:

### Option 1: Global Installation
```bash
npm install -g @modelcontextprotocol/server-postgres
```

### Option 2: Using npx (Recommended)
No installation required - use directly with npx:
```bash
npx -y @modelcontextprotocol/server-postgres postgresql://username:password@hostname:port/database
```

## Configuration for Cursor

To integrate with Cursor IDE, you need to configure the MCP server in your Cursor settings:

### 1. Create or Edit Configuration File

**Location**: 
- macOS: `~/Library/Application Support/Cursor/User/settings.json`
- Windows: `%APPDATA%/Cursor/User/settings.json`
- Linux: `~/.config/Cursor/User/settings.json`

### 2. Add PostgreSQL MCP Configuration

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://username:password@hostname:port/database"
      ]
    }
  }
}
```

### 3. Environment Variables (Recommended for Security)

For production or sensitive environments, use environment variables:

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres"
      ],
      "env": {
        "POSTGRES_URL": "postgresql://username:password@hostname:port/database"
      }
    }
  }
}
```

Then set your environment variable:
```bash
export POSTGRES_URL="postgresql://username:password@hostname:port/database"
```

## Security Best Practices

### 1. Create a Read and write permissions Database User

```sql
-- Create a  user
CREATE USER mcp_user WITH PASSWORD 'secure_password';

-- Grant connect privileges
GRANT CONNECT ON DATABASE your_database TO mcp_user;

-- Grant usage on schema
GRANT USAGE ON SCHEMA public TO mcp_user;

-- Grant select and all other necessar stuff for read and write permissions on all tables
GRANT SELECT ON ALL TABLES IN SCHEMA public TO mcp_user;

-- Grant  Grant select and all other necessar stuff for read and write permissions on future tables
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO mcp_user;
```

### 2. Connection String Security

- Never commit connection strings with credentials to version control
- Use environment variables for sensitive information
- Consider using connection pooling for production environments
- Enable SSL for remote connections: `postgresql://user:pass@host:port/db?sslmode=require`

## Usage Examples

Once configured, you can ask Cursor to:

### Database Schema Exploration
```
"Show me the structure of my users table"
"What are all the tables in my database?"
"Describe the relationships between my tables"
```

### Data Analysis
```
"Analyze the distribution of user registrations by month"
"Show me the top 10 customers by order value"
"What's the average order size in the last quarter?"
```

### Report Generation
```
"Generate a monthly revenue report"
"Create a summary of user activity patterns"
"Analyze product performance metrics"
```

## Testing the Connection

After setup, restart Cursor and test the connection:

1. Open a new chat in Cursor
2. Ask: "Can you show me what tables are available in my database?"
3. The AI should respond with a list of your database tables

## Troubleshooting

### Common Issues

1. **Connection Refused**
   - Check if PostgreSQL server is running
   - Verify host and port are correct
   - Check firewall settings

2. **Authentication Failed**
   - Verify username and password
   - Check user permissions
   - Ensure user has connect privileges

3. **MCP Server Not Found**
   - Restart Cursor after configuration changes
   - Verify the configuration file path
   - Check for JSON syntax errors

### Debug Mode

To see detailed logs, add debug flags:

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://username:password@hostname:port/database",
        "--debug"
      ]
    }
  }
}
```

## Advanced Configuration

### Multiple Databases

You can configure multiple PostgreSQL instances:

```json
{
  "mcpServers": {
    "postgres-prod": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://user:pass@prod-db:5432/app_db"
      ]
    },
    "postgres-analytics": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://analyst:pass@analytics-db:5432/warehouse"
      ]
    }
  }
}
```

### Custom Query Limits

To prevent long-running queries, you can set connection parameters:

```
postgresql://user:pass@host:port/db?statement_timeout=30s&lock_timeout=10s
```

## Integration with AI Dev Tasks Workflow

The PostgreSQL MCP server enhances the AI Dev Tasks workflow:

1. **During PRD Creation**: AI can inspect existing database schema to understand current data models
2. **Task Generation**: Tasks can reference actual database structure and relationships  
3. **Implementation**: Real-time database queries help validate data requirements and constraints
4. **Testing**: AI can generate test data and validate database changes

## Resources

- [PostgreSQL MCP Server GitHub](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres)
- [Model Context Protocol Documentation](https://modelcontextprotocol.io/)
- [Cursor MCP Integration Guide](https://docs.cursor.com/) 