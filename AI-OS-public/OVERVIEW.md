# KAIT 개요

## KAIT란?

**KAIT = Knowledge → Architect → Intelligence → Technology**

KAIT는 AI 시스템을 구축하기 위한 **운영체제**입니다.

```
Knowledge (지식)     →  AI가 무엇을 알고 있는가
    ↓
Architect (설계)     →  어떻게 구성할 것인가
    ↓
Intelligence (지능)  →  어떻게 행동할 것인가
    ↓
Technology (실현)    →  어떻게 동작하는가
```

---

## 핵심 개념

### 1. ProcessorUnit - AI의 "프로세스"

ProcessorUnit은 KAIT에서 **재사용 가능한 AI 실행 단위**입니다.

한 번 만들면 여러 AI 시스템에서 공유할 수 있습니다.

**타입:**
- **LLM**: AI 모델 실행 (GPT, Claude, Gemini 등)
- **Tool**: 도구 실행 (API 호출, 데이터 처리 등)
- **API**: 외부 서비스 연동
- **Chain**: 여러 프로세서 연쇄 실행
- **Vision**: 이미지/비디오 분석

### 2. Graph - AI의 "스케줄러"

Graph는 **AI 실행 흐름을 설계**하는 시스템입니다.

n8n이나 Zapier처럼 시각적으로 워크플로우를 구성합니다.

**노드 (실행 단위):**
- Processor Node: 저장된 ProcessorUnit 실행
- Tool Node: 도구 직접 실행
- LLM Node: 인라인 AI 모델 실행

**엣지 (연결):**
- **Linear**: A → B → C (순차 실행)
- **Parallel**: A → [B, C, D] (동시 실행)
- **Conditional**: 조건에 따라 분기
- **Cyclic**: 조건 충족까지 반복
- **Selective**: AI가 런타임에 경로 선택

### 3. Context Filter - AI의 "메모리 관리자"

Context Filter는 **AI가 무엇을 인식할지 제어**합니다.

4가지 영역으로 구성:

```
┌─────────────────────────────┐
│ System Prompt               │ ← AI의 역할, 성격, 지식
├─────────────────────────────┤
│ History                     │ ← 대화 기록
├─────────────────────────────┤
│ User Input                  │ ← 현재 입력
├─────────────────────────────┤
│ Multimodal                  │ ← 이미지, 음성, 파일
└─────────────────────────────┘
```

각 영역에 여러 필터를 조합하여 AI의 인식을 정밀하게 조정합니다.

### 4. UTCP - AI의 "시스템 콜"

UTCP(Universal Tool Call Protocol)는 **도구 호출 표준**입니다.

JSON 파일 하나로 새로운 도구를 추가할 수 있습니다:

```json
{
  "name": "도구_이름",
  "description": "도구 설명",
  "inputs": { ... },
  "handler": "http"
}
```

코딩 없이 HTTP API, 데이터베이스, 외부 서비스를 연결합니다.

### 5. Session - AI의 "프로세스 컨텍스트"

Session은 **대화 상태를 관리**합니다.

- **PersonalSession**: 1:1 개인 대화
- **WorldSession**: 여러 사용자와 여러 AI가 협업

---

## 5계층 아키텍처

```
Layer 5: Session Layer
         ↑ 대화 상태, 히스토리, 멀티모달 관리

Layer 4: AI Instance Layer
         ↑ Graph + ProcessorUnit 조합 (완성된 AI)

Layer 3: Graph Orchestration Layer
         ↑ 노드 + 엣지로 실행 흐름 제어

Layer 2: Execution Layer
         ↑ ProcessorUnit 실행, Context Filter, Direct Provider

Layer 1: Foundation Layer
         ↑ UCF (통합 콘텐츠 형식), UTCP (도구 프로토콜), Segment (응답 구조)
```

---

## 데이터 흐름

```
사용자 입력
    ↓
입력 파싱 (텍스트/음성/이미지/화면)
    ↓
세션에 저장
    ↓
Graph 실행
    ├─ 노드 1 실행
    │   ├─ Context Filter 적용
    │   ├─ ProcessorUnit 실행
    │   └─ 결과 저장
    │
    ├─ 엣지 평가 → 다음 노드 결정
    │
    └─ (반복)
    ↓
최종 응답 조립
    ↓
실시간 스트리밍 (SSE)
    ↓
사용자에게 전달
```

---

## 핵심 가치

### 1. 모듈성
모든 것이 독립적인 단위로 구성됩니다. 한 번 만든 ProcessorUnit은 어디서든 재사용됩니다.

### 2. 조합성
레고처럼 조립합니다. 작은 부품들을 연결하여 복잡한 시스템을 구축합니다.

### 3. 확장성
코딩 없이 확장합니다. JSON 정의만으로 새로운 도구, 필터, 프로세서를 추가합니다.

### 4. 통합성
모든 것이 하나로 연결됩니다. LLM, 음성, 비전, 도구가 같은 플랫폼에서 동작합니다.

---

## 다음 단계

- [비교](./COMPARISON.md) - 기존 솔루션과 어떻게 다른가
- [사용 사례](./USE_CASES.md) - 실제 적용 예시
