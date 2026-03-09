# copilot-agents

Custom agent definitions for [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli). Drop them in and get specialized agents across all your projects.

## Agents

| Agent | Description |
|---|---|
| **agent-refiner** | Reviews and improves `.agent.md` files. Applies prompt engineering best practices, fills domain expertise gaps, and restructures definitions for better agentic output. |
| **code-commenter** | Adds succinct, high-value code comments aimed at reviewers and future coding agents. Follows open-source community conventions. |
| **code-simplifier** | Flags unnecessary complexity, duplication, dead code, and over-engineering. Proposes and implements targeted simplifications without changing behavior. |
| **docs-writer** | Writes and consolidates documentation for open-source projects. Produces a clean, unified doc structure with proper `.gitignore` hygiene and no redundant files. |
| **security-auditor** | Audits for security vulnerabilities: application-level flaws, dependency risks, configuration issues, and container/hosting misconfigurations. |
| **test-generator** | Generates and runs tests for a given code target using the project's existing test framework. |
| **web-designer** | Reviews web interfaces for visual hierarchy, spacing, typography, color, interaction design, and accessibility. Proposes specific CSS/component fixes ordered by impact. |

## Installation

Clone the repo and copy (or symlink) the agent files into your Copilot CLI agents directory:

```sh
git clone https://github.com/longman391/copilot-agents.git
cp copilot-agents/*.agent.md ~/.copilot/agents/
```

Or, to keep them synced with upstream changes:

```sh
git clone https://github.com/longman391/copilot-agents.git ~/copilot-agents
ln -s ~/copilot-agents/*.agent.md ~/.copilot/agents/
```

Create `~/.copilot/agents/` first if it does not exist:

```sh
mkdir -p ~/.copilot/agents
```

## Usage

Once installed, agents are available in any project. Three ways to invoke them:

**Slash command** (in an interactive session):

```
/agent security-auditor
```

**Natural language reference** (in your prompt):

```
Use the test-generator agent to add coverage for src/auth.ts
```

**CLI flag:**

```sh
copilot --agent=code-simplifier "Review this module for unnecessary complexity"
```

## Customization

Each agent is a standalone Markdown file. Fork the repo, edit the `.agent.md` files to fit your workflow, and drop them into `~/.copilot/agents/`.

To create a new agent, add a new `.agent.md` file following the same structure. Use the **agent-refiner** agent to review and improve your definitions.

## Contributing

Pull requests welcome. If you're adding a new agent or improving an existing one, include a brief description of what changed and why. Keep agent definitions focused on a single responsibility.

## License

See [LICENSE](LICENSE) for details.
