# Claude Code Project Initializer

> Universal project starter kit for Claude Code with pre-configured agents, skills, hooks, and commands.

## Quick Start

### Installation

Copy the `.claude` folder to your project root:

```bash
# Windows (PowerShell)
Copy-Item -Recurse "cc-initializer/.claude" "your-project/.claude"

# macOS/Linux
cp -r cc-initializer/.claude your-project/.claude
```

### First Use

```bash
cd your-project
/init  # Analyze project and create CLAUDE.md
```

## Contents

```
cc-initializer/
├── .claude/
│   ├── agents/              # 15 Sub-agents
│   │   ├── project-analyzer.md
│   │   ├── code-reviewer.md
│   │   ├── doc-generator.md
│   │   ├── test-helper.md
│   │   ├── refactor-assistant.md
│   │   ├── git-troubleshooter.md
│   │   ├── commit-helper.md
│   │   ├── branch-manager.md
│   │   ├── pr-creator.md
│   │   ├── prd-writer.md
│   │   ├── tech-spec-writer.md
│   │   ├── progress-tracker.md
│   │   ├── doc-splitter.md
│   │   ├── doc-validator.md
│   │   └── work-unit-manager.md
│   ├── skills/              # 13 Skills
│   │   ├── init.md
│   │   ├── review.md
│   │   ├── doc.md
│   │   ├── test.md
│   │   ├── refactor.md
│   │   ├── commit.md
│   │   ├── brainstorming/
│   │   ├── context-optimizer/
│   │   ├── hook-creator/
│   │   ├── subagent-creator/
│   │   ├── skill-creator/
│   │   ├── dev-doc-system/
│   │   └── prompt-enhancer/
│   ├── commands/            # 2 Commands
│   │   ├── git-workflow/
│   │   └── dev-doc-planner/
│   └── hooks/               # 3 Hooks
│       ├── pre-tool-use-safety.md
│       ├── post-tool-use-tracker.md
│       └── notification-handler.md
├── docs/
│   ├── _INDEX.md
│   └── templates/
├── CLAUDE.md
└── README.md
```

---

## Sub-Agents (15)

### Development & Analysis

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `project-analyzer` | Analyze project structure and tech stack | "analyze project", "tech stack" |
| `code-reviewer` | Review code quality, security, performance | "review", "PR review", "audit" |
| `test-helper` | Write and analyze tests | "test", "coverage", "unit test" |
| `refactor-assistant` | Improve code structure | "refactor", "clean up" |

### Documentation

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `doc-generator` | Generate README, API docs | "document", "README" |
| `doc-splitter` | Split large documents | "split doc", "문서 분할" |
| `doc-validator` | Validate doc completeness | "문서 검증", "doc check" |
| `prd-writer` | Write PRD documents | "PRD", "요구사항" |
| `tech-spec-writer` | Write technical specs | "기술 설계", "tech spec" |
| `progress-tracker` | Track development progress | "진행상황", "progress" |

### Git & Version Control

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `commit-helper` | Create commit messages | "커밋", "commit" |
| `branch-manager` | Manage branches | "브랜치", "branch" |
| `pr-creator` | Create pull requests | "PR", "pull request" |
| `git-troubleshooter` | Resolve git issues | "충돌", "conflict", "git 문제" |
| `work-unit-manager` | Manage work units | "work unit", "session" |

---

## Skills (13)

### Basic Workflows

| Skill | Usage | Description |
|-------|-------|-------------|
| `/init` | `/init [path]` | Initialize project analysis |
| `/review` | `/review [target] [--focus]` | Code review workflow |
| `/doc` | `/doc [type] [target]` | Generate documentation |
| `/test` | `/test [action] [target]` | Testing workflow |
| `/refactor` | `/refactor [target] [--type]` | Refactoring workflow |
| `/commit` | `/commit [--type] [--scope]` | Conventional commits |

### Advanced Skills (with references)

| Skill | Purpose |
|-------|---------|
| `brainstorming` | Turn ideas into designs through collaborative dialogue |
| `context-optimizer` | Optimize token usage for large codebases |
| `hook-creator` | Create Claude Code hooks |
| `subagent-creator` | Create custom sub-agents |
| `skill-creator` | Create new skills |
| `dev-doc-system` | Integrated development documentation system |
| `prompt-enhancer` | Enhance prompts with project context |

---

## Commands (2)

### git-workflow
GitHub Flow and Conventional Commits workflow support.

**Includes:**
- `COMMIT-CONVENTION.md` - Commit message rules
- `BRANCH-STRATEGY.md` - Branch naming and flow
- `PR-TEMPLATE.md` - Pull request template

### dev-doc-planner
Development document planning with templates.

**Includes:**
- `PRD-TEMPLATE.md` - Product Requirements Document
- `TECH-SPEC-TEMPLATE.md` - Technical Specification
- `PROGRESS-TEMPLATE.md` - Progress tracking

---

## Hooks (3)

| Hook | Event | Purpose |
|------|-------|---------|
| `pre-tool-use-safety` | PreToolUse | Block dangerous operations |
| `post-tool-use-tracker` | PostToolUse | Track changes, suggest follow-ups |
| `notification-handler` | Notification | Handle system notifications |

---

## Usage Examples

### New Project Setup
```bash
cp -r cc-initializer/.claude my-project/.claude
cd my-project
/init
```

### Development Workflow
```bash
# Brainstorm feature design
/brainstorming "Add user authentication"

# Write PRD
# → Triggers prd-writer agent

# Create branch
# → Triggers branch-manager agent

# Implement with code review
/review src/auth/

# Generate tests
/test generate src/auth/

# Commit changes
/commit --type feat --scope auth

# Create PR
# → Triggers pr-creator agent
```

### Documentation Workflow
```bash
# Generate docs
/doc readme
/doc api src/routes/

# Track progress
# → Triggers progress-tracker agent

# Validate docs
# → Triggers doc-validator agent
```

### Git Troubleshooting
```bash
# Resolve merge conflict
"머지 충돌을 해결해줘"
# → Triggers git-troubleshooter agent

# Create commit with conventional format
"이 변경사항 커밋해줘"
# → Triggers commit-helper agent
```

---

## Customization

### Adding New Skills
Use the `skill-creator` skill:
```bash
/skill-creator
```

### Adding New Agents
Use the `subagent-creator` skill:
```bash
/subagent-creator
```

### Adding New Hooks
Use the `hook-creator` skill:
```bash
/hook-creator
```

---

## Templates

| Template | Location | Purpose |
|----------|----------|---------|
| CLAUDE.md | `./CLAUDE.md` | Project context template |
| Phase doc | `docs/templates/phase-template.md` | Development phases |
| Status | `docs/templates/status-template.md` | Progress tracking |
| PRD | `.claude/commands/dev-doc-planner/PRD-TEMPLATE.md` | Requirements doc |
| Tech Spec | `.claude/commands/dev-doc-planner/TECH-SPEC-TEMPLATE.md` | Technical design |

---

## Best Practices

1. **Run `/init` first** - Analyze project before making changes
2. **Use brainstorming** - Design before coding
3. **Use `/review` regularly** - Catch issues early
4. **Keep CLAUDE.md updated** - Maintain project context
5. **Use conventional commits** - Keep history clean
6. **Optimize context** - Use `context-optimizer` for large projects
7. **Document as you go** - Use `/doc` after major changes

---

## Requirements

- Claude Code CLI
- Git (for version control features)
- jq (for hooks, optional)
- Project-specific tools (npm, pytest, dotnet, etc.)

---

## Stats

| Category | Count |
|----------|-------|
| Agents | 15 |
| Skills | 13 |
| Commands | 2 |
| Hooks | 3 |
| Templates | 5+ |
| **Total Files** | **50+** |

---

## License

MIT - Use freely in any project.
