Custom Skills를 통해 조직 또는 개인의 작업 스타일에 특화된 전문 지식과 워크플로우로 Claude를 강화할 수 있습니다. 이 문서는 자신만의 Skill을 만들고, 구조화하고, 테스트하는 방법을 설명합니다.

---

Skill은 몇 줄의 간단한 지침일 수도 있고, 실행 가능한 코드가 포함된 다중 파일 패키지처럼 복잡할 수도 있습니다. 가장 좋은 Skill은 다음과 같습니다:

*   특정하고 반복 가능한 작업을 해결합니다.
*   Claude가 따를 수 있는 명확한 지침을 가집니다.
*   도움이 될 때 예시를 포함합니다.
*   언제 사용해야 하는지 정의합니다.
*   모든 것을 시도하기보다는 하나의 워크플로우에 집중합니다.

## Skill.md 파일 생성

모든 Skill은 최소한 Skill의 핵심인 **Skill.md** 파일을 포함하는 디렉토리로 구성됩니다. 이 파일은 이름과 설명 필드를 포함하는 YAML 프론트매터로 시작해야 하며, 이는 필수 메타데이터입니다. 또한 추가 메타데이터, Claude를 위한 지침 또는 참조 파일, 실행 가능한 스크립트, 또는 도구를 포함할 수 있습니다.

### 필수 메타데이터 필드

**name:** Skill에 대한 사용자 친화적인 이름 (최대 64자)
*   **예시:** Brand Guidelines

**description:** Skill이 무엇을 하는지, 언제 사용해야 하는지에 대한 명확한 설명.
*   이는 중요합니다—Claude는 이를 사용하여 언제 Skill을 호출할지 결정합니다 (최대 200자).
*   **예시:** 공식 색상, 글꼴 및 로고 사용을 포함하여 Acme Corp 브랜드 가이드라인을 프레젠테이션 및 문서에 적용합니다.

### 선택적 메타데이터 필드

**version:** 반복 작업 시 Skill의 버전을 추적합니다.
*   **예시:** 1.0.0

**dependencies:** Skill에 필요한 소프트웨어 패키지.
*   **예시:** python>=3.8, pandas>=1.5.0

Skill.md 파일의 메타데이터는 점진적 공개 시스템의 첫 번째 수준 역할을 하며, Skill의 모든 내용을 로드할 필요 없이 Claude가 언제 Skill을 사용해야 하는지 알 수 있도록 충분한 정보만 제공합니다.

### 마크다운 본문

마크다운 본문은 메타데이터 다음의 두 번째 세부 정보 수준이므로, Claude는 메타데이터를 읽은 후 필요한 경우 여기에 액세스합니다. 작업에 따라 Claude는 Skill.md 파일에 액세스하여 Skill을 사용할 수 있습니다.

### 예시 Skill.md

**Brand Guidelines Skill**

```
## Metadata
name: Brand Guidelines
description: Apply Acme Corp brand guidelines to all presentations and documents
version: 1.0.0

## Overview
This Skill provides Acme Corp's official brand guidelines for creating consistent, professional materials. When creating presentations, documents, or marketing materials, apply these standards to ensure all outputs match Acme's visual identity. Claude should reference these guidelines whenever creating external-facing materials or documents that represent Acme Corp.

## Brand Colors

Our official brand colors are:
- Primary: #FF6B35 (Coral)
- Secondary: #004E89 (Navy Blue)
- Accent: #F7B801 (Gold)
- Neutral: #2E2E2E (Charcoal)

## Typography

Headers: Montserrat Bold
Body text: Open Sans Regular
Size guidelines:
- H1: 32pt
- H2: 24pt
- Body: 11pt

## Logo Usage

Always use the full-color logo on light backgrounds. Use the white logo on dark backgrounds. Maintain minimum spacing of 0.5 inches around the logo.

## When to Apply

Apply these guidelines whenever creating:
- PowerPoint presentations
- Word documents for external sharing
- Marketing materials
- Reports for clients

## Resources

See the resources folder for logo files and font downloads.
```

## 리소스 추가

단일 **Skill.md** 파일에 추가하기에는 정보가 너무 많은 경우 (예: 특정 시나리오에만 적용되는 섹션), Skill 디렉토리 내에 파일을 추가하여 더 많은 콘텐츠를 추가할 수 있습니다. 예를 들어, Skill 디렉토리에 보충 및 참조 정보를 포함하는 `REFERENCE.md` 파일을 추가합니다. **Skill.md**에서 이를 참조하면 Claude가 Skill을 실행할 때 해당 리소스에 액세스해야 하는지 결정하는 데 도움이 됩니다.

## 스크립트 추가

더 고급 Skill의 경우, 실행 가능한 코드 파일을 **Skill.md**에 첨부하여 Claude가 코드를 실행할 수 있도록 합니다. 예를 들어, 당사의 문서 Skill은 다음과 같은 프로그래밍 언어 및 패키지를 사용합니다:

*   Python (pandas, numpy, matplotlib)
*   JavaScript/Node.js
*   파일 편집에 도움이 되는 패키지
*   시각화 도구

> **참고:** Claude와 Claude Code는 Skill을 로드할 때 표준 저장소(Python PyPI, JavaScript npm)에서 패키지를 설치할 수 있습니다. API Skills를 사용할 경우 런타임에 추가 패키지를 설치하는 것은 불가능하며, 모든 종속성은 컨테이너에 미리 설치되어 있어야 합니다.

## Skill 패키징

Skill 폴더가 완성되면:

1.  폴더 이름이 Skill의 이름과 일치하는지 확인하십시오.
2.  폴더의 ZIP 파일을 생성하십시오.
3.  ZIP 파일은 Skill 폴더를 루트로 포함해야 합니다 (하위 폴더가 아닌).

**올바른 구조:**

my-Skill.zip
└── my-Skill/
    ├── Skill.md
    └── resources/

**잘못된 구조:**

my-Skill.zip
└── (파일이 ZIP 루트에 직접 있음)

## Skill 테스트

### 업로드 전

1.  Skill.md의 명확성을 검토합니다.
2.  설명이 Claude가 Skill을 사용해야 할 때를 정확하게 반영하는지 확인합니다.
3.  참조된 모든 파일이 올바른 위치에 존재하는지 확인합니다.
4.  예시 프롬프트로 테스트하여 Claude가 적절하게 이를 호출하는지 확인합니다.

### Claude에 업로드 후

1.  [설정 > 기능](https://claude.ai/settings/capabilities)에서 Skill을 활성화합니다.
2.  이를 트리거해야 하는 여러 다른 프롬프트를 시도합니다.
3.  Claude의 사고 과정을 검토하여 Skill을 로드하고 있는지 확인합니다.
4.  예상대로 Claude가 이를 사용하지 않는 경우 설명을 반복하여 수정합니다.

## 모범 사례

**집중 유지:** 다른 워크플로우에 대해서는 별도의 Skill을 생성하십시오. 여러 개의 집중된 Skill이 하나의 큰 Skill보다 더 잘 조합됩니다.

**명확한 설명 작성:** Claude는 설명을 사용하여 언제 Skill을 호출할지 결정합니다. 언제 적용되는지에 대해 구체적으로 작성하십시오.

**간단하게 시작:** 복잡한 스크립트를 추가하기 전에 마크다운으로 기본 지침부터 시작하십시오. 나중에 언제든지 Skill을 확장할 수 있습니다.

**예시 사용:** Skill.md 파일에 예시 입력과 출력을 포함하여 Claude가 성공이 어떤 모습인지 이해하도록 돕습니다.

**Skill 버전 관리:** 반복 작업 시 버전을 추적하십시오. 이는 문제 해결이나 변경 사항을 롤백할 때 도움이 됩니다.

**점진적 테스트:** 복잡한 Skill을 한 번에 구축하기보다는 중요한 변경이 있을 때마다 테스트하십시오.

**Skill은 서로를 기반으로 구축될 수 있습니다:** Skill이 다른 Skill을 명시적으로 참조할 수는 없지만, Claude는 여러 Skill을 자동으로 함께 사용할 수 있습니다. 이러한 구성 가능성은 Skill 기능의 가장 강력한 부분 중 하나입니다.

Skill 생성에 대한 보다 심층적인 가이드는 Claude Docs의 [Skill 작성 모범 사례](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/best-practices)를 참조하십시오.

## 보안 고려 사항

*   Skill.md 파일에 스크립트를 추가할 때 주의하십시오.
*   민감한 정보(API 키, 암호)를 하드코딩하지 마십시오.
*   다운로드한 모든 Skill을 활성화하기 전에 검토하십시오.
*   외부 서비스 액세스를 위해 적절한 MCP 연결을 사용하십시오.

## 참조할 예시 Skill

템플릿으로 사용할 수 있는 예시 Skill에 대해서는 GitHub 저장소를 방문하십시오: [https://github.com/anthropics/skills](https://github.com/anthropics/skills).

---

**관련 문서**

*   [What are Skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
*   [Using Skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
*   [Teach Claude your way of working using skills](https://support.claude.com/en/articles/12580051-teach-claude-your-way-of-working-using-skills)
*   [How to create a skill with Claude through conversation](https://support.claude.com/en/articles/12599426-how-to-create-a-skill-with-claude-through-conversation)
*   [Using Egnyte for data room management with Claude](https://support.claude.com/en/articles/12651659-using-egnyte-for-data-room-management-with-claude)