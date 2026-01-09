---
name: init
description: Initialize and analyze a new project. First engages in discovery conversation to understand user requirements, then generates documentation. Use when starting work on any new codebase.
---

# Project Initialization Skill

## Usage
```
/init [path] [--discover|--generate|--full|--quick]
```

### Parameters
- `path`: Optional. Project root path (default: current directory)
- `--discover`: **Discovery only** - Engage in conversation to understand project, create DISCOVERY.md
- `--generate`: **Generate only** - Create docs from existing DISCOVERY.md
- `--full`: **Complete flow** - Discovery → Confirmation → Generate (RECOMMENDED for new projects)
- `--quick`: Quick analysis for existing codebases, CLAUDE.md only

### Examples
```bash
/init                      # Quick analysis of current directory
/init --full               # Full workflow with discovery (NEW PROJECT)
/init --discover           # Discovery conversation only
/init --generate           # Generate docs from existing DISCOVERY.md
/init ./my-project --full  # Initialize specific path
```

## Workflow Chain

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        /INIT WORKFLOW CHAIN (v3.0)                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  /init --full (RECOMMENDED for new projects)                                 │
│    │                                                                         │
│    ├── Step 1: Project Discovery (NEW!)                                     │
│    │     ├── Trigger: project-discovery agent                               │
│    │     ├── Engage in conversation with user                               │
│    │     ├── Understand goals, requirements, tech stack                     │
│    │     └── Output: docs/DISCOVERY.md                                      │
│    │                                                                         │
│    ├── Step 2: User Confirmation                                            │
│    │     ├── Present discovery summary                                      │
│    │     ├── Ask for corrections/additions                                  │
│    │     └── Proceed only after user approval                               │
│    │                                                                         │
│    ├── Step 3: Structure Analysis (if existing code)                        │
│    │     └── Detect tech stack, frameworks, patterns                        │
│    │                                                                         │
│    ├── Step 4: Generate CLAUDE.md                                           │
│    │     └── Project summary, commands, key files                           │
│    │                                                                         │
│    ├── Step 5: Trigger dev-docs-writer                                      │
│    │     ├── Input: DISCOVERY.md (required!)                                │
│    │     └── Output: PRD.md, TECH-SPEC.md, PROGRESS.md, CONTEXT.md         │
│    │                                                                         │
│    └── Step 6: Trigger doc-splitter (if HIGH complexity)                    │
│          └── Create Phase structure in docs/phases/                         │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Critical Rule: Discovery First!

> **IMPORTANT**: For new projects, ALWAYS start with discovery.
>
> ```
> ❌ Wrong: Immediately generate documents without understanding
> ✅ Right: First ask "어떤 프로젝트를 만드시려고 하나요?"
> ```

## Mode Details

### --discover Mode

**Purpose**: Only run the discovery conversation

```
/init --discover
    │
    ▼
┌────────────────────────────────────┐
│      project-discovery agent        │
│                                    │
│  1. "어떤 프로젝트를 시작하시나요?"   │
│  2. 프로젝트 유형/목표 논의          │
│  3. 기술 스택 논의                  │
│  4. 복잡도 평가                     │
│  5. 요약 및 확인                    │
│                                    │
└────────────────────────────────────┘
    │
    ▼
Output: docs/DISCOVERY.md
```

**When to use**:
- 사용자가 아이디어 단계인 경우
- 먼저 논의만 하고 문서 생성은 나중에 하고 싶은 경우
- 프로젝트 범위를 먼저 정리하고 싶은 경우

### --generate Mode

**Purpose**: Generate docs from existing DISCOVERY.md

```
/init --generate
    │
    ▼
Check: docs/DISCOVERY.md exists?
    │
    ├── Yes → Proceed
    │
    └── No → Error: "DISCOVERY.md not found. Run /init --discover first."

    │
    ▼
┌────────────────────────────────────┐
│       dev-docs-writer agent         │
│                                    │
│  Read DISCOVERY.md                  │
│  Generate:                          │
│  - docs/PRD.md                      │
│  - docs/TECH-SPEC.md               │
│  - docs/PROGRESS.md                │
│  - docs/CONTEXT.md                 │
│                                    │
└────────────────────────────────────┘
    │
    ▼
If complexity = HIGH → doc-splitter
```

**When to use**:
- 이미 discovery가 완료된 경우
- DISCOVERY.md를 수동으로 작성한 경우
- discovery 후 수정을 거쳐 문서를 생성하려는 경우

### --full Mode (RECOMMENDED)

**Purpose**: Complete workflow with discovery and generation

```
/init --full
    │
    ▼
┌─────────────────────────────────────────────────────────────┐
│                    FULL WORKFLOW                              │
│                                                               │
│  Phase 1: Discovery                                          │
│  ─────────────────                                           │
│  project-discovery agent conducts conversation               │
│  → Creates docs/DISCOVERY.md                                 │
│                                                               │
│  Phase 2: Confirmation                                       │
│  ─────────────────                                           │
│  "이 내용이 맞나요? 수정할 부분이 있으신가요?"                    │
│  → User confirms or requests changes                         │
│                                                               │
│  Phase 3: Generation                                         │
│  ─────────────────                                           │
│  dev-docs-writer uses DISCOVERY.md                           │
│  → Creates PRD, TECH-SPEC, PROGRESS, CONTEXT                │
│                                                               │
│  Phase 4: Structure (if needed)                              │
│  ─────────────────                                           │
│  doc-splitter for HIGH complexity                            │
│  → Creates Phase structure                                   │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

**When to use**:
- 새 프로젝트 시작 시 (RECOMMENDED)
- 프로젝트를 처음부터 체계적으로 세팅하고 싶을 때

### --quick Mode

**Purpose**: Fast analysis for existing codebases

```
/init --quick
    │
    ▼
┌────────────────────────────────────┐
│       Quick Structure Analysis       │
│                                    │
│  - Detect tech stack                │
│  - Identify key files              │
│  - Generate CLAUDE.md only         │
│  - No discovery, no full docs      │
│                                    │
└────────────────────────────────────┘
```

**When to use**:
- 기존 코드베이스 탐색 시
- 빠른 프로젝트 컨텍스트만 필요할 때
- 문서 생성이 필요 없을 때

## Step Details

### Step 1: Project Discovery

```yaml
Agent: project-discovery
Trigger: --full or --discover mode
Process:
  1. 시작 질문: "어떤 프로젝트를 시작하시나요?"
  2. 심층 질문: 유형, 목표, 사용자, 핵심 기능
  3. 기술 논의: 스택, 아키텍처, 제약사항
  4. 복잡도 평가: LOW/MEDIUM/HIGH 판단
  5. 요약 및 확인: 정리된 내용 사용자 확인
Output: docs/DISCOVERY.md
```

### Step 2: User Confirmation

```yaml
Checkpoint: User must confirm before proceeding
Actions:
  - Display discovery summary
  - Ask: "수정할 내용이 있으신가요?"
  - If changes requested → update DISCOVERY.md
  - If confirmed → proceed to generation
```

### Step 3: Structure Analysis (if existing code)

```bash
# Find root indicators
Glob: package.json, requirements.txt, *.csproj, go.mod, Cargo.toml, pom.xml

# Find source directories
Glob: src/**, lib/**, app/**

# Find config files
Glob: *.config.*, .env*, tsconfig.json, setup.py
```

### Step 4: Tech Stack Detection

| File | Stack |
|------|-------|
| package.json | Node.js |
| tsconfig.json | TypeScript |
| requirements.txt | Python |
| *.csproj | .NET/C# |
| go.mod | Go |
| Cargo.toml | Rust |

### Step 5: Trigger dev-docs-writer

```yaml
Condition: --full or --generate mode
Input: docs/DISCOVERY.md (required for quality output)
Output:
  - docs/PRD.md
  - docs/TECH-SPEC.md
  - docs/PROGRESS.md
  - docs/CONTEXT.md
```

### Step 6: Trigger doc-splitter

```yaml
Condition: Complexity = HIGH
Input: dev-docs-writer output + DISCOVERY.md
Output:
  docs/phases/
  ├── phase-1/
  │   ├── SPEC.md
  │   ├── TASKS.md
  │   └── CHECKLIST.md
  └── phase-N/
```

## Output Structure

```
After /init --full:

[project-root]/
├── CLAUDE.md              # Project context file
└── docs/
    ├── DISCOVERY.md       # Discovery report (from conversation)
    ├── PRD.md             # Product requirements
    ├── TECH-SPEC.md       # Technical specification
    ├── PROGRESS.md        # Progress tracking
    ├── CONTEXT.md         # AI context optimization
    └── phases/            # (if HIGH complexity)
        ├── phase-1/
        └── ...
```

## Decision Flow

```
/init called
    │
    ├── --quick? → Structure Analysis → CLAUDE.md only → END
    │
    ├── --discover? → project-discovery → DISCOVERY.md → END
    │
    ├── --generate?
    │       │
    │       ├── DISCOVERY.md exists?
    │       │       │
    │       │       ├── Yes → dev-docs-writer → docs/ → END
    │       │       │
    │       │       └── No → ERROR: Run /init --discover first
    │       │
    │
    └── --full? (or default for new project)
            │
            ▼
        project-discovery
            │
            ▼
        User Confirmation
            │
            ├── Changes? → Update DISCOVERY.md → Loop
            │
            └── Confirmed → dev-docs-writer → docs/ → END
```

## Best Practices

### For New Projects
```bash
# RECOMMENDED: Full discovery workflow
/init --full

# Alternative: Separate steps
/init --discover    # First: understand project
# ... review and edit DISCOVERY.md if needed ...
/init --generate    # Then: generate docs
```

### For Existing Codebases
```bash
# Quick context
/init --quick

# Or full analysis
/init --full   # Will still do discovery to understand YOUR goals
```

### When to Re-run
- After major scope changes: `/init --discover` then `/init --generate`
- After tech stack changes: `/init --generate`
- For quick refresh: `/init --quick`

## Integration Points

### With project-discovery
- First step in --full and --discover modes
- Creates foundational DISCOVERY.md

### With dev-docs-writer
- Triggered in --full and --generate modes
- Requires DISCOVERY.md for quality output

### With doc-splitter
- Triggered for HIGH complexity projects
- Creates Phase-based structure

### With phase-tracker
- Activated after Phase structure is created
- Begins tracking development progress

### With context-optimizer
- CONTEXT.md created for token optimization
- Phase documents structured for efficient loading
