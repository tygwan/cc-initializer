# Claude Code Project Initializer

> Universal project starter kit for Claude Code with **Agile Development Automation**.
> Pre-configured agents, skills, hooks, commands, and complete sprint lifecycle management.

---

## 🚀 What's New in v2.1

### Phase-Based Development (NEW!)
- **Phase Folders** - Organized `docs/phases/phase-N/` structure
- **Phase Tracking** - Automated progress calculation and status updates
- **Phase Documents** - SPEC.md, TASKS.md, CHECKLIST.md per phase
- **Phase Commands** - `/phase status`, `/phase complete N`

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
/phase status      # Check current phase progress
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
# Phase Management (NEW!)
/phase status            # Check current phase progress
/phase 2 tasks           # View phase 2 task list
/phase complete 1        # Mark phase 1 as complete
/phase start 2           # Start next phase

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
│   ├── agents/              # 17 Sub-agents
│   │   ├── phase-tracker.md # ⭐ NEW: Phase progress tracking
│   │   └── ...
│   ├── skills/              # 19 Skills
│   │   ├── init.md
│   │   ├── review.md
│   │   ├── phase-development.md  # ⭐ NEW: Phase workflow
│   │   ├── agile-sync/      # Agile synchronization
│   │   ├── readme-sync/     # README auto-update
│   │   ├── sprint/          # Sprint management
│   │   ├── feedback-loop/   # Learning & ADR
│   │   ├── quality-gate/    # Quality validation
│   │   └── ...
│   ├── commands/            # 3 Commands
│   │   ├── phase.md         # ⭐ NEW: Phase management
│   │   └── ...
│   └── hooks/               # 5 Hooks
│       ├── phase-progress.md # ⭐ NEW: Auto phase updates
│       ├── auto-doc-sync.sh  # Auto documentation
│       └── ...
├── docs/
│   └── templates/
│       └── phase/           # ⭐ NEW: Phase templates
│           ├── SPEC.md
│           ├── TASKS.md
│           └── CHECKLIST.md
├── CLAUDE.md
└── README.md
```

---

## 🤖 Sub-Agents (17)

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
| `phase-tracker` | ⭐ Track phase progress | "phase", "진행", "단계" |

### Git & Version Control

| Agent | Purpose | Keywords |
|-------|---------|----------|
| `commit-helper` | Create commit messages | "commit" |
| `branch-manager` | Manage branches | "branch" |
| `pr-creator` | Create pull requests | "PR", "pull request" |
| `git-troubleshooter` | Resolve git issues | "conflict", "git" |
| `work-unit-manager` | Manage work units | "work unit" |

---

## 🛠 Skills (19)

### Core Workflows

| Skill | Usage | Description |
|-------|-------|-------------|
| `/init` | `/init [path]` | Initialize project analysis |
| `/review` | `/review [target]` | Code review workflow |
| `/doc` | `/doc [type]` | Generate documentation |
| `/test` | `/test [action]` | Testing workflow |
| `/refactor` | `/refactor [target]` | Refactoring workflow |
| `/commit` | `/commit [--type]` | Conventional commits |

### ⭐ Phase & Agile Automation

| Skill | Usage | Description |
|-------|-------|-------------|
| `phase-development` | Auto-activated | ⭐ Phase-based development workflow |
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

## 🔗 Hooks (5)

| Hook | Event | Purpose |
|------|-------|---------|
| `phase-progress` | PostToolUse | ⭐ Auto-update phase progress |
| `auto-doc-sync` | PostToolUse | Auto-update CHANGELOG & README |
| `pre-tool-use-safety` | PreToolUse | Block dangerous operations |
| `post-tool-use-tracker` | PostToolUse | Track changes |
| `notification-handler` | Notification | Handle notifications |

---

## 📋 Commands (3)

### phase (NEW!)
- Phase status checking and management
- Task completion tracking
- Phase transition workflow
- Progress calculation automation

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

### Phase-Based Development Workflow (NEW!)

```bash
# 1. Setup Phase Structure
mkdir -p docs/phases/phase-1 docs/phases/phase-2
# Copy templates from cc-initializer/docs/templates/phase/

# 2. Check Current Phase Status
/phase status                    # View all phases progress
/phase 1 tasks                   # View Phase 1 tasks

# 3. During Development
# Task 완료 시 TASKS.md 업데이트 → hook이 자동으로 PROGRESS.md 갱신

# 4. Complete Phase
/phase complete 1               # Mark Phase 1 complete
/phase start 2                  # Start Phase 2

# 5. Track Progress
/phase summary                  # View overall progress
```

### Phase Document Structure

```
docs/phases/
├── phase-1/
│   ├── SPEC.md        # Technical specification
│   ├── TASKS.md       # Task list with status (⬜/🔄/✅)
│   └── CHECKLIST.md   # Completion criteria
├── phase-2/
│   └── ...
└── phase-N/
    └── ...
```

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
| Agents | 17 |
| Skills | 19 |
| Commands | 3 |
| Hooks | 5 |
| Templates | 13+ |
| **Total** | **57+** |

---

## 🎯 Best Practices

### Phase Development (NEW!)
1. ✅ Create phase folders with SPEC, TASKS, CHECKLIST
2. ✅ Update TASKS.md immediately when completing work
3. ✅ Use `/phase status` to check progress
4. ✅ Complete all CHECKLIST items before phase transition
5. ✅ Load only current phase docs for token efficiency

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

### v2.1.0 (2025-01-09)
#### Added
- Phase-based development system
  - `phase-tracker` agent for progress tracking
  - `phase` command for phase management
  - `phase-progress` hook for auto-updates
  - `phase-development` skill for workflow guidance
- Phase templates: SPEC.md, TASKS.md, CHECKLIST.md
- Token-optimized context loading strategy

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
