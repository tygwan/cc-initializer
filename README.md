# Claude Code Project Initializer

> Universal project starter kit for Claude Code with **Agile Development Automation**.
> Pre-configured agents, skills, hooks, commands, and complete sprint lifecycle management.

---

## 🚀 What's New in v2.0

### Agile Development Automation
- **Sprint Management** - Complete sprint lifecycle with velocity tracking
- **Auto-Documentation** - Automatic CHANGELOG and README synchronization
- **Quality Gates** - Pre-commit, pre-merge, pre-release validation
- **Feedback Loop** - Learning capture, ADR management, retrospectives

---

## Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/tygwan/cc-initializer.git

# Copy to your project
cp -r cc-initializer/.claude your-project/.claude

# Or Windows PowerShell
Copy-Item -Recurse "cc-initializer/.claude" "your-project/.claude"
```

### First Use

```bash
cd your-project
/init              # Analyze project and create CLAUDE.md
/agile-sync        # Initialize agile tracking
```

---

## 📊 Agile Development Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                    AGILE AUTOMATION PIPELINE                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Sprint Start    Development      Sprint End     Release        │
│       ↓              ↓                ↓            ↓           │
│  ┌─────────┐    ┌─────────┐      ┌─────────┐  ┌─────────┐     │
│  │/sprint  │ →  │ Code    │  →   │/sprint  │→ │/quality │     │
│  │ start   │    │ + Sync  │      │  end    │  │  -gate  │     │
│  └─────────┘    └─────────┘      └─────────┘  └─────────┘     │
│       ↓              ↓                ↓            ↓           │
│  Planning       Auto-Docs         Velocity      Release        │
│  Backlog        CHANGELOG         Retro         Validation     │
│                 README            Learnings                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Quick Commands

```bash
# Sprint Management
/sprint start --name "Sprint 1" --duration 2w
/sprint status
/sprint end

# Automatic Synchronization
/agile-sync              # Sync all: changelog, readme, progress
/agile-sync --quick      # Quick stats update
/readme-sync             # Sync README with actual components

# Quality Gates
/quality-gate pre-commit
/quality-gate pre-release --version v1.0.0

# Feedback & Learning
/feedback learning "What I learned"
/feedback adr "Architecture decision"
/feedback retro
```

---

## 📁 Contents

```
cc-initializer/
├── .claude/
│   ├── agents/              # 16 Sub-agents
│   ├── skills/              # 18 Skills (6 NEW!)
│   │   ├── init.md
│   │   ├── review.md
│   │   ├── agile-sync/      # ⭐ NEW: Agile synchronization
│   │   ├── readme-sync/     # ⭐ NEW: README auto-update
│   │   ├── sprint/          # ⭐ NEW: Sprint management
│   │   ├── feedback-loop/   # ⭐ NEW: Learning & ADR
│   │   ├── quality-gate/    # ⭐ NEW: Quality validation
│   │   └── ...
│   ├── commands/            # 2 Commands
│   └── hooks/               # 4 Hooks (1 NEW!)
│       ├── auto-doc-sync.sh # ⭐ NEW: Auto documentation
│       └── ...
├── docs/
├── CLAUDE.md
└── README.md
```

---

## 🤖 Sub-Agents (16)

### Development & Analysis

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `project-analyzer` | Analyze project structure | "analyze", "structure" |
| `code-reviewer` | Review code quality | "review", "PR" |
| `test-helper` | Write and analyze tests | "test", "coverage" |
| `refactor-assistant` | Improve code structure | "refactor", "clean" |
| `file-explorer` | Analyze file structure | "files", "cleanup" |

### Documentation

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `doc-generator` | Generate documentation | "document", "README" |
| `doc-splitter` | Split large documents | "split doc" |
| `doc-validator` | Validate completeness | "validate", "check" |
| `prd-writer` | Write PRD documents | "PRD", "requirements" |
| `tech-spec-writer` | Write technical specs | "tech spec", "design" |
| `progress-tracker` | Track progress | "progress", "status" |

### Git & Version Control

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `commit-helper` | Create commit messages | "commit" |
| `branch-manager` | Manage branches | "branch" |
| `pr-creator` | Create pull requests | "PR", "pull request" |
| `git-troubleshooter` | Resolve git issues | "conflict", "git" |
| `work-unit-manager` | Manage work units | "work unit" |

---

## 🛠 Skills (18)

### Core Workflows

| Skill | Usage | Description |
|-------|-------|-------------|
| `/init` | `/init [path]` | Initialize project analysis |
| `/review` | `/review [target]` | Code review workflow |
| `/doc` | `/doc [type]` | Generate documentation |
| `/test` | `/test [action]` | Testing workflow |
| `/refactor` | `/refactor [target]` | Refactoring workflow |
| `/commit` | `/commit [--type]` | Conventional commits |

### ⭐ Agile Automation (NEW!)

| Skill | Usage | Description |
|-------|-------|-------------|
| `/agile-sync` | `/agile-sync [--full]` | Sync all agile artifacts |
| `/readme-sync` | `/readme-sync [--validate]` | Auto-update README |
| `/sprint` | `/sprint <cmd>` | Sprint lifecycle management |
| `/feedback` | `/feedback <cmd>` | Learning & ADR capture |
| `/quality-gate` | `/quality-gate <checkpoint>` | Quality validation |

### Advanced Skills

| Skill | Purpose |
|-------|---------|
| `brainstorming` | Turn ideas into designs |
| `context-optimizer` | Optimize token usage |
| `hook-creator` | Create Claude Code hooks |
| `subagent-creator` | Create custom agents |
| `skill-creator` | Create new skills |
| `dev-doc-system` | Documentation system |
| `prompt-enhancer` | Enhance prompts |

---

## 🔗 Hooks (4)

| Hook | Event | Purpose |
|------|-------|---------|
| `auto-doc-sync` | PostToolUse | ⭐ Auto-update CHANGELOG & README |
| `pre-tool-use-safety` | PreToolUse | Block dangerous operations |
| `post-tool-use-tracker` | PostToolUse | Track changes |
| `notification-handler` | Notification | Handle notifications |

---

## 📋 Commands (2)

### git-workflow
- `COMMIT-CONVENTION.md` - Conventional commit rules
- `BRANCH-STRATEGY.md` - Branch naming strategy
- `PR-TEMPLATE.md` - Pull request template

### dev-doc-planner
- `PRD-TEMPLATE.md` - Product requirements
- `TECH-SPEC-TEMPLATE.md` - Technical specification
- `PROGRESS-TEMPLATE.md` - Progress tracking

---

## 💡 Usage Examples

### Complete Sprint Workflow

```bash
# 1. Start Sprint
/sprint start --name "Feature Sprint" --duration 2w --goal "Complete auth"

# 2. During Development
/agile-sync                    # Sync documentation
/quality-gate pre-commit       # Validate before commit
/commit --type feat            # Create commit

# 3. Before PR
/quality-gate pre-merge        # Full validation
/readme-sync                   # Update README

# 4. End Sprint
/sprint end                    # Close sprint, generate retro

# 5. Release
/quality-gate pre-release --version v1.0.0
git tag v1.0.0
/quality-gate post-release --version v1.0.0
```

### Capture Learnings

```bash
# After fixing a bug
/feedback learning "Database pooling prevents timeouts"

# Architecture decision
/feedback adr "Use PostgreSQL over MySQL"

# Sprint retrospective
/feedback retro --quick
```

### Automatic Documentation

```bash
# After any code change, hook auto-updates:
# - CHANGELOG.md (from commit messages)
# - README.md stats (component counts)

# Manual sync for full update
/agile-sync --full
```

---

## ⚙️ Configuration

### settings.json

```json
{
  "hooks": {
    "PostToolUse": [
      { "matcher": "Bash", "command": ".claude/hooks/auto-doc-sync.sh" }
    ]
  },
  "agile": {
    "auto_changelog": true,
    "auto_readme_sync": true,
    "sprint_tracking": true
  }
}
```

---

## 📊 Stats

| Category | Count |
|----------|:-----:|
| Agents | 16 |
| Skills | 18 |
| Commands | 2 |
| Hooks | 4 |
| Templates | 10+ |
| **Total** | **50+** |

---

## 🎯 Best Practices

### Agile Workflow
1. ✅ Start with `/sprint start` for new development cycles
2. ✅ Run `/agile-sync` daily or after major changes
3. ✅ Use `/quality-gate` before commits and releases
4. ✅ Capture learnings with `/feedback learning`
5. ✅ Run `/sprint end` with retrospective

### Documentation
1. ✅ Run `/init` when starting a new project
2. ✅ Keep CLAUDE.md updated with `/agile-sync`
3. ✅ Use conventional commits for auto-changelog
4. ✅ Run `/readme-sync` after adding components

---

## 📦 Requirements

- Claude Code CLI
- Git (for version control)
- Bash (for hooks)
- Project-specific tools (npm, pytest, dotnet, etc.)

---

## 🔄 Upgrading

If you have an older version:

```bash
# Backup existing config
cp -r your-project/.claude your-project/.claude.backup

# Copy new version
cp -r cc-initializer/.claude your-project/.claude

# Merge custom configurations if needed
```

---

## 📜 Changelog

### v2.0.0 (2025-01-07)
#### Added
- Agile automation skills: `agile-sync`, `readme-sync`, `sprint`, `feedback-loop`, `quality-gate`
- Auto-documentation hook: `auto-doc-sync.sh`
- Sprint templates and velocity tracking
- Quality gates for CI/CD integration
- Learning and ADR templates

### v1.0.0
- Initial release with 15 agents, 13 skills, 3 hooks

---

## 📄 License

MIT - Use freely in any project.

---

## 🔗 Links

- [GitHub Repository](https://github.com/tygwan/cc-initializer)
- [Issues & Feedback](https://github.com/tygwan/cc-initializer/issues)

---

**Made with ❤️ for productive development**
