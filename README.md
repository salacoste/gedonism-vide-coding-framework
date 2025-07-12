# Gedonism – Vibe Coding Framework

> **Supercharge your AI-powered coding productivity by 17x with Gedonism!**
>
> Gedonism is the ultimate framework for developers and teams who want to unlock the full potential of AI-assisted software development. By combining strict engineering rules, context-driven workflows, and seamless AI integration, Gedonism empowers you to deliver high-quality code, faster than ever before.
>
> **Note:** To achieve the full power and quality of Gedonism, you must use the [Context7 MCP server](https://github.com/upstash/context7) for context-aware AI code generation.

---

## Overview

**Gedonism – Vibe Coding Framework** is a modern, AI-driven project template designed to streamline and structure software development using advanced context engineering and strict coding standards. This product enables teams to leverage AI assistants (Cursor, Claude, GPT-4, etc.) for high-quality, maintainable, and scalable code generation, with a focus on clarity, modularity, and reproducibility.

**With Gedonism, developers experience up to 17x productivity gains in AI-powered coding workflows.**

---

## Key Advantages

- **17x Productivity Boost**: Dramatically accelerate your development cycles by leveraging AI with structured, context-rich workflows.
- **Strict Coding Rules**: Enforced standards for backend (NestJS, TypeScript), frontend (Next.js, Tailwind, Supabase), and database (PostgreSQL MCP) development.
- **AI-Driven Workflow**: Every development stage—from PRD to code—is formalized through markdown commands and .mdc files, ensuring consistency and traceability.
- **Step-by-Step Task Management**: AI generates tasks, code, and tests incrementally, allowing for review and improvement at each step.
- **Modular & Scalable**: The project structure supports easy extension and maintenance.
- **Direct Database Integration**: AI can analyze and utilize live PostgreSQL schemas and data via MCP server.
- **Automated Routine**: README, license, task lists, tests, and documentation are generated and updated automatically.
- **Context-Aware Generation**: AI always operates with the latest project context, minimizing errors and miscommunication.

---

## ⚡️ Preconfigured for Next.js, NestJS, Tailwind — Instantly Adaptable to Any Stack

Gedonism comes preconfigured for automatic project generation using **Next.js** (frontend), **NestJS** (backend), and **Tailwind CSS** (styling). This means you can start building modern, full-stack applications out of the box with best practices and strict rules enforced for these technologies.

**However, Gedonism is designed to be stack-agnostic and can be quickly adapted to any programming language, framework, or package ecosystem.**

### How to Adapt Gedonism to Your Stack

1. **Update Rule Files**
   - Edit or replace the rules in `.cursor/rules/` (e.g., `frontendrules.mdc`, `backendrules.mdc`) to reflect the conventions, best practices, and style guides of your chosen language or framework (e.g., Python, Go, Ruby, Java, React, Vue, Django, Flask, etc.).
   - You can add new rule files for additional stacks or remove those you don't need.

2. **Modify .mdc Workflow Files**
   - Adjust the workflow files (`step-01-create-prd.mdc`, `step-03-generate-tasks.mdc`, etc.) to reference your new or updated rules and to generate tasks/code in your target language or framework.
   - Update prompts and instructions to guide the AI for your specific stack.

3. **Adjust Project Templates and Examples**
   - Replace or supplement example code and templates in the `examples/` directory to match your stack.
   - Update the `INITIAL_EXAMPLE.md` and `INITIAL.md` files to provide relevant documentation and gotchas for your technology choices.

4. **Update Configuration**
   - If your stack requires different tools for code formatting, linting, or testing, update the configuration files (e.g., `package.json`, `.eslintrc`, etc.) accordingly.
   - For database integration, adjust the MCP server configuration or add new MCP integrations as needed.

5. **Revise README and Documentation**
   - Update this README and any other documentation to reflect your chosen stack, rules, and workflow.

**With these simple changes, Gedonism can serve as a powerful AI-driven foundation for any language or framework.**

---

## Workflow: From Idea to Implemented Feature 💡➡️💻

Here's the step-by-step process using the `.mdc` and rules files in this repository:

### 1️⃣ Create a Product Requirement Document (PRD)
First, lay out the blueprint for your feature. A PRD clarifies what you're building, for whom, and why.

You can create a lightweight PRD directly within Cursor:

- Ensure you have the `/.cursorrules/step-01-create-prd.mdc` file from this repository accessible.
- In Cursor's Agent chat, initiate PRD creation:
  ```
  Use @.cursorrules/step-01-create-prd.mdc  
  Here's the feature I want to build: [Describe your feature in detail]  
  Reference these files to help you: [Optional: @file1.py @file2.ts]  
  ```
  _(Pro Tip: For complex PRDs, using MAX mode in Cursor is highly recommended if your budget allows for more comprehensive generation.)_

### 2️⃣ Database Assessment (Optional)
After creating your PRD, determine if your feature needs database functionality:

- Use the database assessment prompt:
  ```
  Use @.cursorrules/step-02-mcp-postgres.mdc
  Reference my PRD: @tasks/prd-MyFeature.md
  ```
- If you need database functionality, follow the PostgreSQL MCP setup guide in `/.cursorrules/setup-mcp-postgres.md`.
- If not, skip to step 3.

### 3️⃣ Generate Your Task List from the PRD
With your PRD drafted (e.g., `prd-MyFeature.md`), the next step is to generate a detailed, step-by-step implementation plan for your AI Developer.

- Ensure you have `/.cursorrules/step-03-generate-tasks.mdc` accessible.
- In Cursor's Agent chat, use the PRD to create tasks:
  ```
  Now take @tasks/prd-MyFeature.md and create tasks using @.cursorrules/step-03-generate-tasks.mdc  
  ```
  _(Note: Replace `@prd-MyFeature.md` with the actual filename of the PRD you generated in step 1.)_

### 4️⃣ Work Through Tasks Step-by-Step
- Use `/.cursorrules/step-04-task-list.mdc` to instruct the AI to focus on one task at a time and wait for your go-ahead before proceeding.
- Example:
  ```
  Please start on task 1.1 and use @.cursorrules/step-04-task-list.mdc
  ```
- Review each change, approve or request improvements, and move to the next task.

---

**Rules and coding standards are defined in the `/.cursor/rules/` directory:**
- `backendrules.mdc` — for backend (NestJS, TypeScript)
- `frontendrules.mdc` — for frontend (Next.js, Tailwind, etc.)
- `context7autoinvoke.mdc` — for Context7 MCP integration and context management

**Always reference these files in your prompts and workflow to ensure the AI follows your project's conventions and standards.**

---

## Project Workflow

### 1. **Backend Rules ([backendrules.mdc])**
- Enforces naming, typing, class/function structure, and SOLID principles for NestJS/TypeScript.
- Requires JSDoc for public APIs, no `any`, no magic numbers, and comprehensive test coverage.

### 2. **Frontend Rules ([frontendrules.mdc])**
- Modern TypeScript, Next.js, and Tailwind CSS only.
- Clean, readable, modular code with up-to-date best practices.
- All comments and error handling in English.

### 3. **Database via MCP Postgres ([setup-mcp-postgres.md], [postgres-mcp-config.example.json])**
- AI can directly inspect and query PostgreSQL schemas and data.
- Secure credential management via environment variables.
- Enables real-time schema analysis, reporting, and test data generation.

### 4. **Context Management ([context7autoinvoke.mdc])**
- Automatic connection to Context7 MCP server for enhanced context and search.
- AI leverages all project rules and documentation for code generation.

### 5. **AI Workflow via .mdc Files**
- **01-create-prd.mdc**: Generate a Product Requirements Document (PRD) for clear feature definition.
- **02-setup-postgres-mcp.mdc**: Assess and configure database integration if needed.
- **03-generate-tasks.mdc**: Create a detailed, actionable task list from the PRD.
- **04-task-list.mdc**: Execute tasks step-by-step with review and quality control.

---

## Recommended Development Sequence

1. **Create a PRD**  
   Use `.cursorrules/01-create-prd.mdc` to generate a Product Requirements Document.
   ```
   Use @.cursorrules/01-create-prd.mdc
   Here's the feature I want to build: [feature description]
   ```

2. **Database Assessment**  
   If your feature requires data, set up MCP Postgres with `.cursorrules/02-setup-postgres-mcp.mdc`.
   ```
   Use @.cursorrules/02-setup-postgres-mcp.mdc
   Reference my PRD: @tasks/prd-MyFeature.md
   ```

3. **Generate Tasks**  
   Create a detailed task list from the PRD using `.cursorrules/03-generate-tasks.mdc`.
   ```
   Now take @tasks/prd-MyFeature.md and create tasks using @.cursorrules/03-generate-tasks.mdc
   ```

4. **Step-by-Step Task Execution**  
   Use `.cursorrules/04-task-list.mdc` to work through tasks one at a time, with review and feedback.
   ```
   Please start on task 1.1 and use @.cursorrules/04-task-list.mdc
   ```

5. **Review and Iterate**  
   After each step, review the output, provide feedback, and iterate as needed.

---

## Project Setup (From Scratch)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/vibe-coding-boilerplate.git my-project
   cd my-project
   ```

2. **Install Dependencies**
   - For backend and frontend, run `npm install` or `yarn install` in the respective directories (if present).
   - Ensure Node.js is installed for MCP Postgres integration.

3. **Configure MCP Postgres**
   - Create a database user and grant permissions (see [setup-mcp-postgres.md]):
     ```sql
     CREATE USER mcp_user WITH PASSWORD 'secure_password';
     GRANT CONNECT ON DATABASE your_database TO mcp_user;
     GRANT USAGE ON SCHEMA public TO mcp_user;
     GRANT SELECT ON ALL TABLES IN SCHEMA public TO mcp_user;
     ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO mcp_user;
     ```
   - Set the connection string in environment variables or in Cursor's `settings.json` (see [postgres-mcp-config.example.json]).

4. **Test the Connection**
   - Restart Cursor.
   - Ask:
     ```
     Can you show me what tables are available in my database?
     ```
   - Ensure the AI can see your database structure.

5. **Follow the Workflow**
   - Proceed with the step-by-step workflow described above.

---

## Context7 MCP Server: Installation & Setup

### Why Context7 MCP is Essential

Gedonism – Vibe Coding Framework is designed to leverage the full power of AI-assisted coding. To achieve the promised **17x productivity boost** and ensure the highest quality, context-aware code generation, it is **required** to use the [Context7 MCP server](https://github.com/upstash/context7).

**Context7 MCP** provides:
- Up-to-date, structured code documentation for LLMs and AI code editors.
- Deep integration with your codebase, enabling AI to answer questions, generate code, and provide examples with full project context.
- Seamless support for popular AI tools (Cursor, Amazon Q, JetBrains AI Assistant, Warp, Opencode, and more).

> **Without Context7 MCP, Gedonism cannot guarantee the quality, accuracy, or context-awareness of AI-generated code.**

### How to Install and Configure Context7 MCP

#### 1. Install Context7 MCP Server

You can run Context7 MCP locally using `npx` (recommended for most users):

```bash
npx -y @upstash/context7-mcp@latest
```

Or, for advanced usage, clone and run from source ([docs](https://github.com/upstash/context7)):

```bash
git clone https://github.com/upstash/context7.git
cd context7
bun i
bun run build
bun run dist/index.js
```

#### 2. Add Context7 MCP to Your AI Tool Configuration

**For Cursor IDE:**

Add the following to your Cursor `settings.json`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

**For Amazon Q Developer CLI:**

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

**For JetBrains AI Assistant:**

1. Go to `Settings` → `Tools` → `AI Assistant` → `Model Context Protocol (MCP)`
2. Click `+ Add`
3. Select `Command` and use:
   ```json
   {
     "command": "npx",
     "args": ["-y", "@upstash/context7-mcp"]
   }
   ```
4. Click `Apply`

**For Warp, Opencode, and others:**  
See [Context7 MCP documentation](https://github.com/upstash/context7) for detailed instructions.

#### 3. (Optional) Advanced Configuration

- You can run Context7 MCP as a remote HTTP server or customize CLI flags (see [Context7 README](https://github.com/upstash/context7)).
- For large monorepos or custom setups, refer to the [Context7 docs](https://github.com/upstash/context7) for schema and indexing options.

#### 4. Verify Installation

- Restart your AI tool (e.g., Cursor).
- Ask a code/documentation question (e.g., "Show me all endpoints in my API module").
- You should receive context-rich, accurate answers powered by Context7 MCP.

**References:**
- [Context7 MCP GitHub](https://github.com/upstash/context7)
- [Context7 Official Site](https://context7.com/)

---

## Example Project Structure

```
my-project/
├── README.md
├── LICENSE
├── .cursorrules/
│   ├── 01-create-prd.mdc
│   ├── 02-setup-postgres-mcp.mdc
│   ├── 03-generate-tasks.mdc
│   ├── 04-task-list.mdc
│   └── ...
├── tasks/
│   ├── prd-my-feature.md
│   └── tasks-prd-my-feature.md
├── src/
│   └── ... (project code)
├── package.json
└── ...
```

---

## Best Practices

- **Keep files under 200 lines**: Use modularization to maintain readability and context.
- **Write tests**: Unit and e2e tests for every public method/controller.
- **All comments and error handling in English.**
- **Use only modern technologies and syntax** (ES+, TypeScript, Next.js, Tailwind).
- **Never store secrets in code**: Use environment variables.
- **Continuously update AI context**: Add new rules, docs, and examples as the project evolves.

---

## License

MIT 
