# my-agents

A collection of reusable Copilot agents and skills for integration with VS Code projects.

## 📦 What's Included

### Agents
- **[hmrc-sme.agent.md](./agents/hmrc-sme.agent.md)** - Subject Matter Expert agent for HMRC tax compliance

### Skills
- **[hmrc-mtd-income-tax-api-discovery](./skills/hmrc-mtd-income-tax-api-discovery/)** - Discover and explain HMRC Making Tax Digital for Income Tax APIs
- **[hmrc-mtd-income-tax-project-trace](./skills/hmrc-mtd-income-tax-project-trace/)** - Trace HMRC MTD Income Tax API integrations in codebases

## 🚀 How to Use These Agents in Your Projects

### Option 1: Reference from This Repository (Quickest)

If you want to use these agents in another project, reference them directly from this repository:

```bash
# In your project directory, create or update a .copilot-ignorerc file
# or reference the agent files directly in your Copilot configuration
```

#### VS Code Configuration
Add to your project's workspace settings (`.vscode/settings.json`):

```json
{
  "copilot.agents.additionalLocations": [
    "C:/path/to/my-agents/agents",
    "C:/path/to/my-agents/skills"
  ]
}
```

Or use a relative path if the repository is a sibling:

```json
{
  "copilot.agents.additionalLocations": [
    "../my-agents/agents",
    "../my-agents/skills"
  ]
}
```

### Option 2: Clone/Fork the Repository

Clone this repository into your projects directory:

```bash
git clone https://github.com/yourusername/my-agents.git
cd my-agents
```

Then reference the agents from your projects using relative paths.

### Option 3: Publish as an npm Package (For Distribution)

To make these agents installable via npm:

#### Step 1: Create `package.json`

```json
{
  "name": "@yourusername/copilot-agents",
  "version": "1.0.0",
  "description": "Reusable Copilot agents and skills",
  "type": "module",
  "files": [
    "agents",
    "skills",
    "README.md"
  ],
  "repository": {
    "type": "git",
    "url": "https://github.com/yourusername/my-agents.git"
  },
  "keywords": [
    "copilot",
    "agent",
    "skill",
    "vscode",
    "hmrc"
  ],
  "author": "Your Name",
  "license": "MIT"
}
```

#### Step 2: Create `agent-manifest.json` (Optional but recommended)

```json
{
  "agents": [
    {
      "id": "hmrc-sme",
      "path": "./agents/hmrc-sme.agent.md"
    }
  ],
  "skills": [
    {
      "id": "hmrc-mtd-income-tax-api-discovery",
      "path": "./skills/hmrc-mtd-income-tax-api-discovery/SKILL.md"
    },
    {
      "id": "hmrc-mtd-income-tax-project-trace",
      "path": "./skills/hmrc-mtd-income-tax-project-trace/SKILL.md"
    }
  ]
}
```

#### Step 3: Publish to npm

```bash
# Login to npm (one-time setup)
npm login

# Publish the package
npm publish --access public
```

#### Step 4: Users Install from npm

In another project:

```bash
npm install @yourusername/copilot-agents
```

Then reference in their VS Code settings:

```json
{
  "copilot.agents.additionalLocations": [
    "node_modules/@yourusername/copilot-agents/agents",
    "node_modules/@yourusername/copilot-agents/skills"
  ]
}
```

### Option 4: Publish as VS Code Extension (Best for Production)

This is the recommended approach for production use:

#### Step 1: Create Extension Structure

```
my-agents-extension/
├── package.json
├── README.md
├── agents/
├── skills/
└── agent-extension.json
```

#### Step 2: Create `agent-extension.json`

```json
{
  "name": "HMRC Copilot Agents",
  "version": "1.0.0",
  "agents": [
    {
      "id": "hmrc-sme",
      "path": "./agents/hmrc-sme.agent.md"
    }
  ],
  "skills": [
    {
      "id": "hmrc-mtd-income-tax-api-discovery",
      "path": "./skills/hmrc-mtd-income-tax-api-discovery/SKILL.md"
    },
    {
      "id": "hmrc-mtd-income-tax-project-trace",
      "path": "./skills/hmrc-mtd-income-tax-project-trace/SKILL.md"
    }
  ]
}
```

#### Step 3: Update `package.json`

```json
{
  "name": "my-agents-extension",
  "version": "1.0.0",
  "displayName": "HMRC Copilot Agents",
  "description": "Copilot agents for HMRC tax compliance tasks",
  "publisher": "yourusername",
  "engines": {
    "vscode": "^1.80.0"
  },
  "categories": [
    "AI"
  ],
  "contributes": {
    "copilot.agents": [
      "./agent-extension.json"
    ]
  },
  "scripts": {
    "vscode:prepublish": "echo 'ready to publish'"
  }
}
```

#### Step 4: Publish to VS Code Marketplace

```bash
# Install VS Code extension CLI
npm install -g @vscode/vsce

# Package the extension
vsce package

# Publish to marketplace
vsce publish
```

Users install directly from the VS Code Extensions marketplace.

---

## 🔄 Recommended Workflow

1. **Start with Option 1** - Reference from your repository while developing
2. **Move to Option 2** - Clone into projects as your agents stabilize
3. **Upgrade to Option 3** - Publish to npm for team/organization sharing
4. **Scale to Option 4** - Create a VS Code extension for public distribution

## 📝 Agent File Format

All agent definitions follow the Copilot agent markdown format:

```markdown
---
name: agent-name
description: Short description of what the agent does
---

# Agent Title

## Objective
Clear goal of the agent

## Scope
What the agent should and shouldn't do

## Workflow
Steps the agent follows

## Output
What the agent returns
```

## 🛠️ Development

To test agents locally:

1. Keep this repository at a known path
2. Reference the agents in your project's VS Code settings
3. Test in the Copilot chat in VS Code
4. Iterate on the agent definitions
5. Use version control to track changes

## 📄 License

MIT (or your chosen license)

## 🤝 Contributing

Contributions welcome! Please:

1. Fork this repository
2. Create a feature branch
3. Test your changes thoroughly
4. Submit a pull request

---

**Next Steps:** Choose your distribution method above and follow the setup instructions for your use case.
