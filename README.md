<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Framework-5A67D8?style=for-the-badge&logo=anthropic&logoColor=white" alt="Claude Code Framework"/>
</p>

<h1 align="center">cc-initializer</h1>

<p align="center">
  <strong>Claude Code를 위한 통합 개발 워크플로우 프레임워크</strong>
</p>

<p align="center">
  <a href="https://github.com/tygwan/cc-initializer/releases"><img src="https://img.shields.io/badge/version-4.4.0-blue?style=flat-square" alt="Version"/></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License"/></a>
  <a href="https://github.com/tygwan/cc-initializer/stargazers"><img src="https://img.shields.io/github/stars/tygwan/cc-initializer?style=flat-square" alt="Stars"/></a>
</p>

<p align="center">
  <code>/init --full</code> 하나로 시작하는 체계적인 개발 환경
</p>

---

## Architecture

```
                              ┌─────────────────────────────────────┐
                              │         cc-initializer               │
                              │    ┌───────────────────────┐        │
                              │    │    settings.json      │        │
                              │    └───────────┬───────────┘        │
                              │                │                     │
          ┌────────────────────────────────────┼────────────────────────────────────┐
          │                    │               │               │                    │
          ▼                    ▼               ▼               ▼                    ▼
   ┌─────────────┐     ┌─────────────┐ ┌─────────────┐ ┌─────────────┐     ┌─────────────┐
   │   Agents    │     │   Skills    │ │  Commands   │ │    Hooks    │     │  Templates  │
   │     23      │     │     18      │ │      6      │ │      5      │     │      3      │
   └──────┬──────┘     └──────┬──────┘ └──────┬──────┘ └──────┬──────┘     └─────────────┘
          │                   │               │               │
          │    ┌──────────────┴───────────────┴───────────────┘
          │    │
          ▼    ▼
   ┌──────────────────────────────────────────────────────────────────────────────────┐
   │                              Development Flow                                     │
   │                                                                                   │
   │   Discovery ──▶ Planning ──▶ Development ──▶ Review ──▶ Release                  │
   │       │            │              │            │           │                      │
   │       ▼            ▼              ▼            ▼           ▼                      │
   │   DISCOVERY    PRD.md        /feature      /gh pr     /release                   │
   │      .md      TECH-SPEC       start        create                                │
   │               PROGRESS                                                            │
   └──────────────────────────────────────────────────────────────────────────────────┘
```

---

## Quick Start

```bash
git clone https://github.com/tygwan/cc-initializer.git ~/dev/cc-initializer
cd your-project && claude
```

```bash
/init --full          # 새 프로젝트: Discovery → 문서 → Phase 구조
/init --sync          # 기존 프로젝트에 프레임워크 동기화
/init --update        # cc-initializer 최신 버전으로 업데이트
```

---

## Component Overview

<table>
<tr>
<td width="50%" valign="top">

### Agents `23`

| Category | Agents |
|:--------:|--------|
| **Discovery** | `project-discovery` |
| **Tracking** | `progress-tracker` `phase-tracker` |
| **Docs** | `dev-docs-writer` `doc-splitter` |
| **Git** | `commit-helper` `pr-creator` `branch-manager` |
| **GitHub** | `github-manager` |
| **Quality** | `code-reviewer` `test-helper` |
| **Analytics** | `analytics-reporter` |

</td>
<td width="50%" valign="top">

### Skills `18`

| Category | Commands |
|:--------:|----------|
| **Init** | `/init` `/validate` |
| **Agile** | `/sprint` `/phase` |
| **Git** | `/feature` `/bugfix` `/release` |
| **GitHub** | `/gh` |
| **Docs** | `/agile-sync` `/dev-doc-system` |
| **Utils** | `/analytics` `/repair` `/sync-fix` |

</td>
</tr>
</table>

---

## Workflow Commands

<table>
<tr>
<td width="33%" align="center">

**Initialize**

```
/init --full
```
Discovery → PRD → Phase

</td>
<td width="33%" align="center">

**Develop**

```
/feature start "name"
/feature complete
```
Branch → Code → PR

</td>
<td width="33%" align="center">

**Release**

```
/release v1.0.0
```
Tag → Notes → Deploy

</td>
</tr>
</table>

---

## Integration Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                                                                                  │
│    /init ─────────────────────────────────────────────────────────▶ Setup       │
│      │                                                                           │
│      ├──▶ project-discovery ──▶ DISCOVERY.md                                    │
│      │                              │                                            │
│      └──▶ dev-docs-writer ◀─────────┘                                           │
│                 │                                                                │
│                 ├──▶ PRD.md                                                      │
│                 ├──▶ TECH-SPEC.md      ┌─────────────────┐                      │
│                 ├──▶ PROGRESS.md  ◀────│  phase-tracker  │◀──── Hooks           │
│                 └──▶ CONTEXT.md        └─────────────────┘                      │
│                                                                                  │
│    /feature ────▶ branch-manager ──▶ commit-helper ──▶ pr-creator              │
│                                                                                  │
│    /gh ─────────▶ github-manager ──▶ Issues / PRs / CI / Releases              │
│                                                                                  │
│    /analytics ──▶ analytics-reporter ──▶ CLI Charts & Reports                  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## GitHub Integration

```bash
/gh status              # Dashboard: 이슈, PR, 멘션, CI 상태
/gh issue list          # 이슈 목록
/gh pr create           # PR 생성
/gh ci watch            # CI 실시간 모니터링
/gh release create      # 릴리스 생성
```

---

## Phase & Sprint

```
Phase 1 ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100%
  └── Sprint 1.1 ████████████████████ Done
  └── Sprint 1.2 ████████████████████ Done

Phase 2 ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  65%
  └── Sprint 2.1 ████████████████████ Done
  └── Sprint 2.2 ████████████░░░░░░░░ In Progress
```

```bash
/phase status           # Phase 진행률 확인
/sprint start           # Sprint 시작
/sprint complete        # Sprint 완료 + 회고
```

---

## Real-World Example

<table>
<tr>
<td>

### DXTnavis

Navisworks 2025 Property Viewer & 4D Automation

| | |
|---|---|
| **Stack** | C# .NET 4.8, WPF MVVM |
| **Phases** | 13 (100% Complete) |
| **Features** | 445K+ Properties, 4D Automation |

[View Repository →](https://github.com/tygwan/DXTnavis)

</td>
<td>

```
Phase  1-4  ████████████████████ 100%
Phase  5-7  ████████████████████ 100%
Phase  8    ████████████████████ 100%
Phase  9-12 ████████████████████ 100%
Phase 13    ████████████████████ 100%
```

</td>
</tr>
</table>

---

## Projects Using cc-initializer

| Project | Description |
|---------|-------------|
| [tygwan/dxtnavis](https://github.com/tygwan/dxtnavis) | DXT Navigator - Navisworks Plugin |

> **Add yours**: Add `uses-cc-initializer` topic to your repo or [submit PR](PROJECTS.json)

---

## Directory Structure

```
.claude/
├── settings.json       ─── Configuration hub
├── agents/        23   ─── Specialized AI agents
├── skills/        18   ─── Workflow automation
├── commands/       6   ─── Development workflows
├── hooks/          5   ─── Auto-triggers
├── scripts/            ─── Utility scripts
├── templates/          ─── Document templates
└── analytics/          ─── Usage metrics (JSONL)
```

---

## Changelog

| Version | Release |
|:-------:|---------|
| `4.4.0` | Community Project Discovery |
| `4.3.0` | GitHub CLI Integration |
| `4.2.0` | Analytics Visualization |
| `4.1.0` | Framework Update System |
| `4.0.0` | Framework Setup & Sync |
| `3.0.0` | Discovery First Workflow |

[All Releases →](https://github.com/tygwan/cc-initializer/releases)

---

<p align="center">
  <a href="https://github.com/tygwan/cc-initializer/issues">Issues</a> •
  <a href=".claude/docs/">Documentation</a> •
  <a href="LICENSE">MIT License</a>
</p>
