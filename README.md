# cc-initializer

[![Version](https://img.shields.io/badge/version-4.3.0-blue.svg)](https://github.com/tygwan/cc-initializer/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> Claude Code를 위한 통합 개발 워크플로우 프레임워크

---

## Quick Start

```bash
# 새 프로젝트
/init --full

# 기존 프로젝트 동기화
/init --sync

# 프레임워크 업데이트
/init --update
```

---

## Projects Using cc-initializer

### Community Showcase

| Project | Description |
|---------|-------------|
| [tygwan/dxtnavis](https://github.com/tygwan/dxtnavis) | DXT Navigator - Real-world example project |

> **Add your project**: Add `uses-cc-initializer` topic to your repo or [submit a PR](PROJECTS.json)

---

## Components

| Type | Count | Examples |
|:----:|:-----:|----------|
| **Agents** | 23 | `progress-tracker` `github-manager` `dev-docs-writer` |
| **Skills** | 18 | `/init` `/sprint` `/gh` `/analytics` |
| **Commands** | 6 | `/feature` `/bugfix` `/release` |
| **Hooks** | 5 | `phase-progress` `auto-doc-sync` `safety` |

---

## Core Features

### Initialization

| Command | Description |
|---------|-------------|
| `/init --full` | Framework + Discovery + 문서 생성 |
| `/init --sync` | 기존 프로젝트에 동기화 |
| `/init --update` | GitHub 최신 버전 pull + sync |
| `/init --discover` | Discovery 대화만 실행 |

### Development Workflow

| Command | Description |
|---------|-------------|
| `/feature start "name"` | 기능 브랜치 생성 + 개발 시작 |
| `/feature complete` | PR 생성 + 머지 |
| `/bugfix start "issue"` | 버그 수정 시작 |
| `/release v1.0.0` | 릴리스 워크플로우 |

### Phase & Sprint

| Command | Description |
|---------|-------------|
| `/phase status` | Phase 진행률 확인 |
| `/phase next` | 다음 Phase로 전환 |
| `/sprint start` | Sprint 시작 |
| `/sprint complete` | Sprint 완료 + 회고 |

### GitHub Integration (NEW v4.3)

| Command | Description |
|---------|-------------|
| `/gh status` | GitHub 대시보드 (이슈, PR, 멘션) |
| `/gh issue list` | 이슈 목록 |
| `/gh pr create` | PR 생성 |
| `/gh ci status` | CI/CD 상태 |
| `/gh release create` | 릴리스 생성 |

### Analytics (NEW v4.2)

| Command | Description |
|---------|-------------|
| `/analytics` | 사용 통계 CLI 시각화 |
| `/analytics tools` | 도구 사용량 차트 |
| `/analytics errors` | 오류 분석 |

---

## Directory Structure

```
.claude/
├── settings.json      # Configuration
├── agents/            # 23 specialized agents
├── skills/            # 18 workflow skills
├── commands/          # 6 workflow commands
├── hooks/             # 5 automation hooks
├── scripts/           # Utility scripts
├── templates/         # Phase templates
└── analytics/         # Usage metrics (JSONL)
```

---

## Key Agents

| Agent | Purpose |
|-------|---------|
| `project-discovery` | 대화형 요구사항 파악 |
| `progress-tracker` | 전체 진행률 관리 |
| `phase-tracker` | Phase별 상세 추적 |
| `github-manager` | GitHub CLI 통합 |
| `analytics-reporter` | 사용 통계 리포트 |
| `dev-docs-writer` | 개발 문서 생성 |
| `commit-helper` | Conventional Commits |
| `pr-creator` | PR 생성 및 관리 |

---

## Configuration

<details>
<summary><b>settings.json 주요 설정</b></summary>

```json
{
  "phase": { "enabled": true },
  "sprint": { "enabled": true },
  "analytics": { "enabled": true },
  "github": {
    "enabled": true,
    "pr": { "squash_merge": true },
    "release": { "generate_notes": true }
  }
}
```

</details>

---

## Installation

```bash
git clone https://github.com/tygwan/cc-initializer.git ~/dev/cc-initializer
cd your-project && claude
/init --full
```

---

## Workflow Overview

```
/init --full
    ↓
Discovery (대화) → DISCOVERY.md
    ↓
문서 생성 → PRD, TECH-SPEC, PROGRESS
    ↓
/feature start → 개발 → /feature complete
    ↓
/release → 배포
```

---

## Real-World Example: DXTnavis

> **DXTnavis** - Navisworks 2025 Property Viewer & 4D Automation Plugin

| 항목 | 내용 |
|------|------|
| **기술 스택** | C# .NET 4.8, WPF MVVM, Navisworks API 2025 |
| **버전** | v1.2.1 |
| **Phases** | 13 (전체 완료) |

### Phase Progress

```
Phase  1-4: Property & CSV     ████████████████████ 100%
Phase  5-7: ComAPI & Viewer    ████████████████████ 100%
Phase  8:   AWP 4D Automation  ████████████████████ 100%
Phase  9-12: UI & Grouping     ████████████████████ 100%
Phase 13:   TimeLiner v1.2.0   ████████████████████ 100%
```

### Key Features

| Feature | Phase |
|---------|-------|
| 445K+ Property 처리 | 1-3 |
| 3D Selection 동기화 | 3 |
| AWP 4D 자동화 | 8 |
| Direct TimeLiner 실행 | 10-13 |
| TaskType 한글화 | 13 |

**Repository**: [github.com/tygwan/DXTnavis](https://github.com/tygwan/DXTnavis)

---

## Changelog

| Version | Highlights |
|:-------:|------------|
| **4.3.0** | GitHub CLI 통합 (`github-manager`, `/gh`) |
| **4.2.0** | Analytics CLI 시각화 (`/analytics`) |
| **4.1.1** | Attribution Badge 자동 삽입 |
| **4.1.0** | `/init --update` 추가 |
| **4.0.0** | Framework Setup, `/init --sync` |
| **3.0.0** | Discovery First 워크플로우 |

---

## Links

- [Releases](https://github.com/tygwan/cc-initializer/releases)
- [Issues](https://github.com/tygwan/cc-initializer/issues)
- [Documentation](.claude/docs/)

---

MIT License
