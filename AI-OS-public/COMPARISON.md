# KAIT vs 기존 솔루션

## 시장 현황

AI 애플리케이션을 구축하기 위한 여러 프레임워크가 존재합니다:

- **LangChain**: Chain 기반 LLM 애플리케이션 프레임워크
- **Crew AI**: 역할 기반 AI 에이전트 프레임워크
- **AutoGen**: 마이크로소프트의 멀티에이전트 프레임워크
- **Dify**: 노코드 LLM 앱 빌더

이들은 모두 **프레임워크**입니다. KAIT는 **운영체제**입니다.

---

## 핵심 차이점

### 1. 접근 방식

| 솔루션 | 접근 방식 | 비유 |
|--------|----------|------|
| LangChain | 라이브러리 | npm 패키지 |
| Crew AI | 에이전트 프레임워크 | 팀 관리 도구 |
| AutoGen | 대화 프레임워크 | 채팅 앱 |
| **KAIT** | **운영체제** | **Windows/macOS** |

KAIT는 AI를 위한 완전한 실행 환경을 제공합니다.

### 2. 흐름 제어

| 솔루션 | 흐름 제어 | 유연성 |
|--------|----------|--------|
| LangChain | Chain (순차) + Agent | 제한적 분기 |
| Crew AI | Task → Agent 메시징 | 에이전트 간만 |
| AutoGen | 대화 기반 | 대화 패턴 제한 |
| **KAIT** | **Graph (노드 + 엣지)** | **무제한** |

KAIT의 Graph는 n8n 수준의 시각적 워크플로우를 지원합니다:
- 순차, 병렬, 조건부, 순환, AI 선택 분기
- 모든 흐름 패턴을 표현 가능

### 3. 컨텍스트 관리

| 솔루션 | 컨텍스트 관리 | 제어 수준 |
|--------|--------------|----------|
| LangChain | Memory 클래스 | 수동 구성 |
| Crew AI | 자동 (고정) | 제한적 |
| AutoGen | 대화 히스토리 | 기본만 |
| **KAIT** | **Context Filter System** | **정밀 제어** |

KAIT는 4가지 영역 × 20+ 필터로 AI의 인식을 정밀하게 조정합니다:
- 어떤 정보를 보여줄지
- 어떤 순서로 보여줄지
- 어떤 형식으로 보여줄지

### 4. 멀티모달 지원

| 솔루션 | 텍스트 | 이미지 | 음성 | 화면 | 비디오 |
|--------|--------|--------|------|------|--------|
| LangChain | ✅ | 부분 | ❌ | ❌ | ❌ |
| Crew AI | ✅ | ❌ | ❌ | ❌ | ❌ |
| AutoGen | ✅ | 부분 | ❌ | ❌ | ❌ |
| **KAIT** | **✅** | **✅** | **✅** | **✅** | **✅** |

KAIT의 UCF(Universal Content Format)는 모든 입력을 통합 처리합니다.

### 5. 도구 확장

| 솔루션 | 도구 추가 방식 | 난이도 |
|--------|---------------|--------|
| LangChain | Python 클래스 작성 | 코딩 필요 |
| Crew AI | Tool 클래스 작성 | 코딩 필요 |
| AutoGen | Function 정의 | 코딩 필요 |
| **KAIT** | **JSON 파일** | **No-Code** |

KAIT의 UTCP는 JSON 정의만으로 도구를 추가합니다:
```json
{
  "name": "my_api",
  "handler": "http",
  "url": "https://api.example.com"
}
```

### 6. 상태 관리

| 솔루션 | 세션 관리 | 영속성 | 협업 |
|--------|----------|--------|------|
| LangChain | Memory만 | 제한적 | ❌ |
| Crew AI | Task 상태 | 메모리 | ❌ |
| AutoGen | 대화 상태 | 메모리 | 부분 |
| **KAIT** | **Session System** | **DB 지원** | **✅** |

KAIT는 1:1 대화부터 다자간 AI 협업까지 지원합니다.

---

## 상세 비교

### LangChain vs KAIT

**LangChain의 강점:**
- 광범위한 LLM 통합
- 활발한 커뮤니티
- 풍부한 예제

**KAIT의 우위:**
- Chain 대신 Graph로 더 복잡한 흐름
- 수동 프롬프트 대신 자동 컨텍스트 필터
- 코딩 없이 도구 확장
- 완전한 멀티모달 지원

### Crew AI vs KAIT

**Crew AI의 강점:**
- 역할 기반 에이전트 정의
- 직관적인 팀 비유

**KAIT의 우위:**
- 에이전트 메시징 대신 Graph로 더 세밀한 제어
- ProcessorUnit으로 더 작은 단위의 재사용
- 멀티모달 지원
- No-Code 확장

### AutoGen vs KAIT

**AutoGen의 강점:**
- MS 생태계 통합
- 대화 기반 협업

**KAIT의 우위:**
- 대화 패턴 제한 없이 어떤 흐름이든 표현
- DB 기반 영속성
- 완전한 멀티모달
- Context Filter로 정밀 제어

---

## KAIT만의 고유 기능

### 1. Tool Recursion with Tracking

AI가 도구를 호출하고, 결과를 보고, 다시 도구를 호출하는 것을 무한히 반복할 수 있습니다.

- 중복 호출 감지
- 반복 횟수 제한
- 상세 실행 로그

### 2. Real-time Streaming

AI의 "생각 과정"까지 실시간으로 스트리밍합니다.

```
[생각 중...] → [도구 호출 중...] → [응답 생성 중...] → 완료
```

### 3. Expression System

노드 간 데이터 전달을 동적으로 처리합니다.

```
${nodes.analyzer.result.score}  → 이전 노드의 특정 값 참조
${user_input}                    → 사용자 원본 입력
```

### 4. Connector System

MCP(Model Context Protocol)를 포함한 다양한 외부 서비스 통합:
- Google Drive
- GitHub
- Slack
- 커스텀 API

---

## 결론

| 선택 기준 | 추천 솔루션 |
|----------|------------|
| 빠른 프로토타입 | LangChain |
| 역할 기반 에이전트 | Crew AI |
| MS 생태계 | AutoGen |
| **완전한 AI 시스템 구축** | **KAIT** |

KAIT는 "프레임워크를 넘어선 운영체제"입니다.

복잡한 AI 시스템을 구축하고, 확장하고, 관리해야 한다면 KAIT가 답입니다.
