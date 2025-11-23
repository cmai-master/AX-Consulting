# Prompt Engineering & Optimization - 웹 리서치 결과

> **작성일**: 2025-11-23
> **리서치 목적**: A4-2 Prompt Engineering Framework 및 B4-4 Prompt Library Template 작성을 위한 정보 수집
> **리서치 시간**: 약 8시간

---

## 📋 목차

1. [Prompt Engineering 기법](#1-prompt-engineering-기법)
2. [Prompt Optimization 프로세스](#2-prompt-optimization-프로세스)
3. [고급 기법 및 최적화](#3-고급-기법-및-최적화)
4. [도구 및 프레임워크](#4-도구-및-프레임워크)
5. [평가 및 테스팅](#5-평가-및-테스팅)
6. [보안 및 모범 사례](#6-보안-및-모범-사례)
7. [참고 자료](#7-참고-자료)

---

## 1. Prompt Engineering 기법

### 1.1 Shot-Based Prompting

#### Zero-Shot Prompting
- **정의**: 사전 예시 없이 작업을 수행하도록 모델에 지시하는 기법
- **특징**:
  - 모델이 사전 학습된 지식과 프롬프트 내 제한된 정보만으로 응답 생성
  - 간단하고 일반적인 작업에 효율적
  - 리소스 사용이 적음
- **사용 시기**:
  - 간단하고 잘 알려진 작업
  - 기본 산술, 일반 쿼리, 감정 분류 등
  - 빠른 프로토타이핑이 필요한 경우

**예시:**
```
Classify the sentiment of this text: "I love this product!"
```

#### Few-Shot Prompting
- **정의**: 2개 이상의 예시를 포함하여 모델이 패턴을 인식하도록 하는 기법
- **특징**:
  - In-context learning 활성화
  - 더 정확한 응답 생성
  - 특정 작업에 대한 컨텍스트 제공
- **성능**: Zero-shot보다 복잡한 작업에서 우수한 성능
- **리소스**: 더 많은 토큰 사용 및 리소스 집약적

**예시:**
```
Sentiment: "Great service!" → Positive
Sentiment: "Terrible experience." → Negative
Sentiment: "It was okay." → Neutral

Sentiment: "I love this product!" → ?
```

#### Many-Shot Prompting
- **정의**: 다수의 예시(3-shot, 5-shot, 10-shot 이상)를 제공하는 기법
- **사용 시기**: Few-shot으로 성능이 부족한 어려운 작업
- **장점**: 복잡한 패턴 학습 가능
- **단점**: 컨텍스트 윈도우 소비 증가

#### 비교 요약

| 특성 | Zero-Shot | Few-Shot | Many-Shot |
|------|-----------|----------|-----------|
| 예시 수 | 0개 | 2-5개 | 5개 이상 |
| 토큰 사용 | 최소 | 중간 | 많음 |
| 정확도 | 일반적 | 높음 | 매우 높음 |
| 적용 작업 | 간단한 작업 | 중간 복잡도 | 복잡한 작업 |
| 비용 | 낮음 | 중간 | 높음 |

**출처:**
- [Few-Shot Prompting - Prompt Engineering Guide](https://www.promptingguide.ai/techniques/fewshot)
- [Zero-Shot vs. Few-Shot Prompting - Shelf](https://shelf.io/blog/zero-shot-and-few-shot-prompting/)
- [Microsoft Learn - Zero-shot and few-shot learning](https://learn.microsoft.com/en-us/dotnet/ai/conceptual/zero-shot-learning)

---

### 1.2 Chain-of-Thought (CoT) Prompting

#### 개요
- **정의**: LLM이 단계별 추론 과정을 거치도록 유도하는 기법
- **목적**: 논리, 계산, 의사결정이 필요한 복잡한 작업의 성능 향상
- **핵심**: 인간의 추론을 모방하는 일관된 논리적 단계 시퀀스

#### 주요 기법

**1. Few-Shot CoT (Manual-CoT)**
- 단계별 추론이 명확히 제시된 예시를 몇 개 보여줌
- 모델이 추론 과정을 학습하도록 유도

**예시:**
```
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls.
   Each can has 3 tennis balls. How many tennis balls does he have now?
A: Roger started with 5 balls. 2 cans of 3 balls each is 6 balls.
   5 + 6 = 11. The answer is 11.

Q: The cafeteria had 23 apples. If they used 20 to make lunch...
```

**2. Zero-Shot CoT**
- 간단히 "Let's think step by step"을 프롬프트에 추가
- 예시 없이도 단계별 추론 유도
- 가장 간단하고 효과적인 CoT 방법

**예시:**
```
Q: What is 15% of 80?
A: Let's think step by step.
```

**3. Auto-CoT**
- 다양성을 고려하여 질문을 자동으로 샘플링
- 추론 체인을 자동 생성하여 demonstration 구축

#### 성능 및 제약사항

**성능:**
- 산술, 상식 추론, 기호적 추론에서 정확도 대폭 향상
- 100B+ 파라미터 모델에서 효과적
- 다단계 문제를 중간 단계로 분해하여 정답률 증가

**제약사항:**
- 프롬프트 품질에 크게 의존
- 신중하게 작성된 예시 필요
- 소형 모델(<100B)에서는 비논리적 추론 체인 생성 가능
- 더 많은 연산 능력과 시간 소요

**출처:**
- [Chain-of-Thought Prompting - Prompt Engineering Guide](https://www.promptingguide.ai/techniques/cot)
- [IBM - What is chain of thought prompting?](https://www.ibm.com/think/topics/chain-of-thoughts)
- [DataCamp - Chain-of-Thought Prompting](https://www.datacamp.com/tutorial/chain-of-thought-prompting)

---

### 1.3 Tree of Thoughts (ToT) Prompting

#### 개요
- **출처**: Princeton & Google DeepMind (Yao et al., 2023)
- **정의**: CoT를 일반화하여 사고의 트리 구조를 유지하는 프레임워크
- **핵심**: 여러 추론 경로를 탐색하고 평가하여 최적의 해결책 찾기

#### 작동 원리

**4가지 핵심 요소:**

1. **Thought Decomposition (사고 분해)**
   - 문제를 중간 단계로 분해
   - 각 단계는 일관된 언어 시퀀스로 표현

2. **Thought Generation (사고 생성)**
   - 각 단계에서 여러 가능한 솔루션 생성
   - 다양한 경로 탐색

3. **State Evaluation (상태 평가)**
   - 각 사고의 품질 평가
   - 방법: 스칼라 값(1-10 등급) 또는 분류(확실함/가능성있음/불가능)

4. **Search Algorithms (탐색 알고리즘)**
   - BFS (Breadth-First Search)
   - DFS (Depth-First Search)
   - 전방 탐색 및 백트래킹 가능

#### 성능

**Game of 24 실험:**
- CoT (GPT-4): 4% 성공률
- ToT: 74% 성공률

**적용 분야:**
- 수학적 추론
- 창의적 글쓰기
- 복잡한 문제 해결
- 전략적 계획

#### CoT vs ToT

| 특성 | Chain-of-Thought | Tree of Thoughts |
|------|------------------|------------------|
| 구조 | 선형 체인 | 트리 구조 |
| 탐색 | 단일 경로 | 다중 경로 |
| 백트래킹 | 불가능 | 가능 |
| 복잡도 | 낮음 | 높음 |
| 성능 | 좋음 | 매우 우수 |
| 비용 | 낮음 | 높음 |

**출처:**
- [Tree of Thoughts - Prompt Engineering Guide](https://www.promptingguide.ai/techniques/tot)
- [IBM - What is Tree Of Thoughts Prompting?](https://www.ibm.com/think/topics/tree-of-thoughts)
- [arXiv - Tree of Thoughts: Deliberate Problem Solving](https://arxiv.org/abs/2305.10601)

---

### 1.4 ReAct (Reasoning + Acting) Prompting

#### 개요
- **정의**: 추론(Reasoning)과 행동(Acting)을 결합하는 패러다임
- **핵심**: LLM이 추론 추적과 작업별 행동을 번갈아 생성하도록 함
- **출처**: Google Research

#### 작동 원리

**상호작용 패턴:**
```
Thought → Action → Observation → Thought → Action → Observation ...
```

**구성 요소:**
1. **Thought (사고)**: 현재 상황에 대한 추론
2. **Action (행동)**: 외부 도구/API 호출
3. **Observation (관찰)**: 행동 결과 확인

#### 장점

1. **외부 정보 활용**
   - 지식 베이스에서 정보 검색
   - API 호출을 통한 실시간 데이터 접근
   - 환경과의 상호작용

2. **동적 추론**
   - 추론이 검색을 안내
   - 검색 결과가 추론을 지원
   - 지식 업데이트 가능

3. **투명성 및 신뢰성**
   - 추론 과정이 명시적으로 드러남
   - 해석 가능성 향상
   - 디버깅 용이

#### CoT vs ReAct

| 특성 | Chain-of-Thought | ReAct |
|------|------------------|-------|
| 지식 소스 | 내부 표현만 | 내부 + 외부 |
| 정보 업데이트 | 불가능 | 가능 |
| 도구 사용 | 없음 | 있음 |
| 환경 상호작용 | 없음 | 있음 |
| 적용 분야 | 추론 작업 | 추론 + 의사결정 |

#### 최적 사용법

**ReAct + CoT 결합:**
- 내부 지식과 외부 정보 모두 활용
- 최상의 성능 달성
- 언어 및 의사결정 작업 모두에서 우수

**예시 구조:**
```
Question: What is the elevation range for the area that the eastern sector of the Colorado orogeny extends into?

Thought 1: I need to search Colorado orogeny, find the area that the eastern sector extends into, then find the elevation range of that area.
Action 1: Search[Colorado orogeny]
Observation 1: The Colorado orogeny was an episode of mountain building...

Thought 2: It does not mention the eastern sector. I need to look up eastern sector.
Action 2: Lookup[eastern sector]
Observation 2: The eastern sector extends into the High Plains...

Thought 3: Now I need to search High Plains and find its elevation range.
Action 3: Search[High Plains]
Observation 3: High Plains refers to one of two distinct land regions...
```

**출처:**
- [ReAct Prompting - Prompt Engineering Guide](https://www.promptingguide.ai/techniques/react)
- [Google Research - ReAct: Synergizing Reasoning and Acting](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/)
- [arXiv - ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

---

### 1.5 System Prompts vs User Prompts

#### 주요 차이점

| 특성 | System Prompt | User Prompt |
|------|---------------|-------------|
| **목적** | AI의 전체 행동 및 역할 정의 | 특정 작업 또는 질문 제공 |
| **수명** | 안정적, 개발자가 업데이트 전까지 유지 | 동적, 각 상호작용마다 변경 |
| **설정자** | 개발자 | 사용자 |
| **범위** | 전역적 | 작업 특정적 |

#### System Prompt 모범 사례

**포함 내용:**
1. **역할 및 컨텍스트**
   - AI의 페르소나 설정
   - 전체 시나리오 정의

2. **행동 가이드라인**
   - 특정 주제 회피
   - 전문성 유지
   - 행동 규칙 준수

3. **일관성 유지**
   - 안정적인 동작 보장
   - 상대적으로 고정적

**예시:**
```
You are a professional financial advisor with 15 years of experience.
You provide clear, evidence-based advice and always disclose risks.
You never make specific investment recommendations without proper context.
You maintain a professional yet approachable tone.
```

#### User Prompt 모범 사례

**포함 내용:**
1. **작업 특정 정보**
   - 구체적인 지시사항
   - 질문 또는 요청

2. **동적 컨텍스트**
   - 예시 (Few-shot)
   - 현재 작업 관련 세부사항

3. **명확한 목표**
   - 원하는 출력 형식
   - 기대하는 결과

**예시:**
```
Based on the following financial data, analyze the company's liquidity:
- Current Assets: $500M
- Current Liabilities: $300M
- Quick Assets: $350M

Provide a brief analysis with key ratios.
```

#### 배치 전략

**모범 사례:**
- **System Prompt**: 정적 지시사항, 역할 정의
- **User Prompt**: 동적 콘텐츠, 예시, 작업별 세부사항

**중요 고려사항:**
- 모델과 제공자에 따라 처리 방식이 다름
- 항상 실험과 평가(evals)를 통해 최적 방법 확인
- 명확성이 핵심: 상세한 컨텍스트, 명확한 목표, 구체적인 출력 형식 지정

**출처:**
- [PromptLayer - System Prompt vs User Prompt](https://blog.promptlayer.com/system-prompt-vs-user-prompt-a-comprehensive-guide-for-ai-prompts/)
- [Nebuly - LLM System Prompt vs. User Prompt](https://www.nebuly.com/blog/llm-system-prompt-vs-user-prompt)
- [Hamel's Blog - What should go in the system prompt vs. the user prompt?](https://hamel.dev/blog/posts/evals-faq/what-should-go-in-the-system-prompt-vs-the-user-prompt.html)

---

### 1.6 Prompt 구조 및 디자인 패턴

#### Prompt Patterns 개요

- **정의**: LLM의 일반적인 출력 문제를 극복하기 위한 재사용 가능한 구조화된 솔루션
- **비유**: 소프트웨어 개발의 디자인 패턴과 유사

#### 주요 패턴 카테고리

**1. Input Semantics Patterns (입력 의미론 패턴)**
- LLM이 자연어를 이해하고 번역하는 방식
- 자연어 용어를 LLM이 더 잘 이해하는 언어로 정의

**2. Output Customization Patterns (출력 사용자 지정 패턴)**
- LLM이 특정 방식으로 응답에 집중하도록 함
- 목소리, 템플릿, 그래프 등 원하는 출력 형식 지정

**3. Template Pattern (템플릿 패턴)**
- 일관된 형식/구조를 활용하는 구조화된 프레임워크
- 모델이 원하는 응답을 생성하도록 안내

#### 인기 있는 구체적 패턴

**1. Persona Pattern (페르소나 패턴)**
- LLM에 특정 역할이나 관점 부여
- 예: "당신은 경험 많은 데이터 과학자입니다"

**2. Recipe Pattern (레시피 패턴)**
- 결과를 달성하기 위한 단계별 시퀀스 획득
- 절차적 지식 요청에 유용

**3. Question Refinement Pattern (질문 개선 패턴)**
- 더 나은 질문 공식화 보장
- LLM이 질문을 재구성하거나 명확화하도록 요청

**4. Cognitive Verifier Pattern (인지 검증 패턴)**
- 질문을 하위 질문으로 분해
- 복잡한 문제를 관리 가능한 부분으로 나눔

**5. Chain-of-Thought Structure**
- 단계별 추론으로 작업 분해
- 명확성과 정확성 향상

#### 확장 가능한 Prompt 설계를 위한 5가지 패턴

1. **Modular Prompts (모듈식 프롬프트)**
   - 재사용 가능한 구성 요소로 분해

2. **Versioning (버전 관리)**
   - 프롬프트 변경 추적

3. **Parameterization (매개변수화)**
   - 변수 사용으로 유연성 확보

4. **Testing Framework (테스팅 프레임워크)**
   - 체계적인 평가 및 검증

5. **Documentation (문서화)**
   - 명확한 사용 지침 및 예시

#### 구조화된 Template 구성 요소

```markdown
## Prompt Template Structure

### Role/Context
[AI의 역할 정의]

### Task Description
[수행할 작업 명확히 설명]

### Input Format
[입력 데이터 형식 지정]

### Instructions
[단계별 지시사항]

### Output Format
[원하는 출력 형식]

### Constraints/Rules
[제약사항 및 규칙]

### Examples (Few-shot)
[예시 입력-출력 쌍]
```

**연구 인사이트:**
- 잘 구조화된 프롬프트 템플릿과 특정 구성 패턴은 LLM의 지시 따르기 능력을 크게 향상
- 실제 애플리케이션에서 효과적인 설계 관행을 식별하기 위한 체계적 연구 진행 중

**출처:**
- [PromptHub - Prompt Patterns: 16 You Should Know](https://www.prompthub.us/blog/prompt-patterns-what-they-are-and-16-you-should-know)
- [Vanderbilt University - Prompt Patterns](https://www.vanderbilt.edu/generative-ai/prompt-patterns/)
- [Latitude - 5 Patterns for Scalable Prompt Design](https://latitude-blog.ghost.io/blog/5-patterns-for-scalable-prompt-design/)
- [arXiv - From Prompts to Templates](https://arxiv.org/html/2504.02052v2)

---

## 2. Prompt Optimization 프로세스

### 2.1 Prompt Iteration 방법론

#### 핵심 원칙

**반복적 접근:**
1. 초기 프롬프트로 시작
2. 응답 검토
3. 출력 기반으로 프롬프트 개선
4. 반복

**개선 전략:**
- 표현 조정
- 더 많은 컨텍스트 추가
- 필요시 요청 단순화

#### 모델별 고려사항

**최신 모델 (GPT-4.1, Claude 4.x):**
- 지시사항을 더 밀접하고 문자 그대로 따름
- 이전 모델보다 의도를 자유롭게 추론하지 않음
- 명확하고 구체적인 지시사항이 더 중요

**일반 권장사항:**
- 가장 최신의 강력한 모델 사용
- 최신 모델일수록 프롬프트 엔지니어링이 더 쉬움

**Anthropic 모범 사례:**
- Claude 4.x는 더 정확한 지시사항 따르기 훈련
- 명확하고 명시적인 지시사항 제공
- 원하는 출력에 대해 구체적으로 설명

**출처:**
- [OpenAI - Prompt Engineering Best Practices](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api)
- [Anthropic - Claude 4 Best Practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices)

---

### 2.2 A/B Testing for Prompts

#### 평가 메트릭

**1. 전통적 ML 메트릭**
- Accuracy (정확도)
- Precision (정밀도)
- Recall (재현율)
- F1 Score

**제한사항**: LLM의 미묘한 성능을 완전히 포착하지 못할 수 있음

**2. NLP 특화 메트릭**
- **BLEU**: 기계 번역 품질
- **ROUGE**: 요약 품질
- **METEOR**: 의미적 유사성

**3. 성능 메트릭**
- Response Latency (응답 지연시간)
- Cost (비용/토큰 사용)
- Token Usage (토큰 사용량)
- Consistency (일관성)

**4. 품질 및 콘텐츠 메트릭**
- Faithfulness (충실성)
- Helpfulness (유용성)
- Toxicity (유해성)
- Task Accuracy (작업 정확도)

**5. 사용자 중심 메트릭**
- Engagement Rates (참여율)
- User Feedback (사용자 피드백)
- Click-Through Rates (클릭률)
- Response Times (응답 시간)
- Conversion Rates (전환율)

#### 모범 사례

**1. 사전 성공 메트릭 정의**
- 비즈니스 목표와 정렬
- 측정 가능하고 명확한 KPI 설정

**2. 사용자 메트릭에 근거 마련**
- 실제 사용자 행동 데이터 활용
- Open rates, CTR, conversion rates 등

**3. 품질 중심 데이터셋**
- 20-50개의 대표 예시로 시작
- 일반적인 시나리오와 엣지 케이스 포함
- 양보다 질이 중요

**4. 도구 활용**
- **Langfuse**: 성능 메트릭, 평가 메트릭 추적
- **Autoevals**: 일반적인 평가 메트릭 제공
- **PromptLayer**: 프롬프트 A/B 테스팅 전문
- **Braintrust**: LLM 프롬프트 A/B 테스팅 가이드

**출처:**
- [PromptLayer - You should be A/B testing your prompts](https://blog.promptlayer.com/you-should-be-a-b-testing-your-prompts/)
- [Langfuse - A/B Testing of LLM Prompts](https://langfuse.com/docs/prompts/a-b-testing)
- [Braintrust - A/B testing for LLM prompts](https://www.braintrust.dev/articles/ab-testing-llm-prompts)
- [Portkey - Evaluating Prompt Effectiveness](https://portkey.ai/blog/evaluating-prompt-effectiveness-key-metrics-and-tools/)

---

### 2.3 Prompt Versioning

#### 핵심 모범 사례

**1. Semantic Versioning 사용**
- **형식**: X.Y.Z (Major.Minor.Patch)
- **Major**: 호환성을 깨는 변경
- **Minor**: 하위 호환 개선
- **Patch**: 특정 이슈 수정

**예시**: v1.0.0 → v1.1.0

**2. 변경사항 문서화**
- 업데이트 로그 유지
- 성능 모니터링
- 접근 제어

**3. 버전 제어 구현**
- **버전 히스토리**: 무엇이 언제 왜 변경되었는지 기록
- **롤백 기능**: 필요시 이전 버전으로 복구
- **불변성**: 각 변경마다 고유한 버전 ID 부여

**4. 롤백 대비**
- Feature flags 사용
- Checkpoints 설정
- 결함 있는 업데이트를 빠르게 되돌릴 수 있도록 준비

**5. 명확한 프롬프트 설계**
- 정확한 지시사항
- 예시 포함
- 제한사항 명시

**6. 성능 모니터링**
- 버전에 성능 메트릭 태그
- 쉬운 비교를 위한 데이터 수집
- 모니터링 메트릭:
  - Fault rates
  - Latency
  - CPU/Memory/Disk usage
  - Log errors

**7. 협업 워크플로우**
- 프롬프트 버전에 리뷰어 할당
- 특정 변경사항에 댓글 남기기
- 배포 전 승인 또는 수정 요청

#### 도구 및 플랫폼

**주요 플랫폼:**
- **Latitude**: 프롬프트 관리 및 버전 관리
- **Lilypad**: 프롬프트 버전 관리
- **LangSmith**: 프롬프트 생성, 버전 관리, 테스트, 협업
- **PromptLayer**: 프롬프트 버전 관리 및 복구
- **Humanloop**: 협업 워크플로우
- **Agenta**: 프롬프트 최적화
- **Helicone**: 모니터링 및 버전 관리
- **Portkey**: 프롬프트 엔지니어링 스튜디오

**출처:**
- [Latitude - Prompt Versioning Best Practices](https://latitude-blog.ghost.io/blog/prompt-versioning-best-practices/)
- [LaunchDarkly - Prompt Versioning & Management Guide](https://launchdarkly.com/blog/prompt-versioning-and-management/)
- [PromptLayer - Best Prompt Versioning Tools](https://blog.promptlayer.com/5-best-tools-for-prompt-versioning/)
- [Braintrust - Best prompt versioning tools 2025](https://www.braintrust.dev/articles/best-prompt-versioning-tools-2025)

---

### 2.4 Performance 측정

#### 핵심 성능 지표

**1. Latency (지연시간)**
- 응답 생성에 걸리는 시간
- 사용자 경험에 직접적 영향

**2. Cost (비용)**
- 토큰 사용량
- API 호출 비용
- 인프라 비용

**3. Quality (품질)**
- 작업 정확도
- 응답 관련성
- 출력 일관성

**4. Throughput (처리량)**
- 단위 시간당 처리 요청 수
- QPS (Queries Per Second)

#### Temperature 설정

**Temperature란?**
- 모델이 덜 가능성 있는 토큰을 출력하는 빈도 측정
- 높을수록 더 무작위적(일반적으로 더 창의적)

**권장 설정:**
- **Temperature = 0**: 사실 기반 사용 사례
  - 데이터 추출
  - 진실된 Q&A
  - 결정론적 출력 필요시

- **Higher Temperature**: 창의적 작업
  - 콘텐츠 생성
  - 브레인스토밍
  - 다양한 출력 필요시

**출처:**
- [OpenAI - Best practices for prompt engineering](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api)
- [Lakera - The Ultimate Guide to Prompt Engineering in 2025](https://www.lakera.ai/blog/prompt-engineering-guide)

---

## 3. 고급 기법 및 최적화

### 3.1 Prompt Caching (Anthropic)

#### 개요
- **제공**: Anthropic Claude
- **기능**: API 호출 간 자주 사용되는 컨텍스트를 캐싱
- **목적**: 긴 프롬프트의 비용 및 지연시간 감소

#### 성능 향상

**Latency 감소:**
- 최대 85% 감소
- 예시: 100K 토큰 북 → 11.5초에서 2.4초로 감소
- 평균 2배 이상 개선

**Cost 절감:**
- 최대 90% 비용 절감
- 캐시 활용으로 대폭적인 토큰 비용 감소

#### 가격 구조

- **Cache Write**: 기본 입력 토큰 가격의 125%
- **Cache Read**: 기본 입력 토큰 가격의 10%
- 자주 재사용되는 컨텍스트에 매우 경제적

#### 기술 요구사항

**Cache Hit 조건:**
- 프롬프트 세그먼트가 100% 동일해야 함
- Cache control로 표시된 블록까지의 모든 텍스트 및 이미지 포함

**최소 토큰 요구사항:**
- Claude 3.7 Sonnet: 최소 1,024 토큰/체크포인트
- 첫 번째 체크포인트: 1,024 토큰 후
- 두 번째 체크포인트: 2,048 토큰 후
- 최대 4개 cache breakpoints 정의 가능

**Cache 수명 (TTL):**
- 기본: 5분
- 옵션: 1시간 TTL 제공
- 사용할 때마다 수명 갱신

#### 사용 사례

1. **대화형 에이전트**
   - 확장된 대화에서 비용 및 지연시간 감소
   - 긴 지시사항 또는 업로드된 문서 포함

2. **코딩 어시스턴트**
   - 코드베이스 요약을 프롬프트에 유지
   - 자동완성 및 코드베이스 Q&A 개선

3. **대용량 문서 처리**
   - 이미지 포함 완전한 장문 자료 통합
   - 응답 지연 증가 없음

4. **상세 지시사항 세트**
   - 광범위한 지시사항, 절차, 예시 목록 공유
   - Claude의 응답 미세 조정

#### 모범 사례

1. **안정적이고 재사용 가능한 콘텐츠 캐싱**
   - 시스템 지시사항
   - 배경 정보
   - 대규모 컨텍스트
   - 빈번한 도구 정의

2. **캐싱된 콘텐츠를 프롬프트 시작 부분에 배치**
   - 최상의 성능을 위함

3. **전략적으로 Cache Breakpoints 사용**
   - 다른 캐싱 가능한 prefix 섹션 분리

**출처:**
- [Anthropic - Prompt caching with Claude](https://www.anthropic.com/news/prompt-caching)
- [Anthropic Docs - Prompt caching](https://docs.claude.com/en/docs/build-with-claude/prompt-caching)
- [Hakkoda - Slashing LLM Costs and Latencies](https://hakkoda.io/resources/prompt-caching/)

---

### 3.2 Context Window 최적화

#### 주요 기법

**1. Long Context Handling**
- 확장된 컨텍스트 윈도우 활용
- Claude: 최대 200K 토큰
- GPT-4: 128K 토큰 지원

**2. Context Compression**
- **LongLLMLingua**: 컨텍스트 압축 기법
- 중요 정보 보존하며 토큰 감소
- 비용 최적화

**3. Sliding Window**
- 대화 히스토리 관리
- 최근 N개 메시지만 유지
- 오래된 컨텍스트 제거

**4. Prompt Caching**
- (상기 3.1 참조)
- 재사용 컨텍스트 캐싱

#### 비용 최적화 전략

1. **불필요한 토큰 제거**
   - 중복 정보 제거
   - 간결한 표현 사용

2. **캐싱 활용**
   - 반복되는 시스템 프롬프트
   - 공통 컨텍스트

3. **적절한 모델 선택**
   - 작업에 맞는 모델 크기
   - 비용 대비 성능 고려

**출처:**
- [Anthropic - Prompt Caching](https://www.anthropic.com/news/prompt-caching)
- [Research on Context Optimization](https://arxiv.org/search/?query=long+context+LLM&searchtype=all)

---

### 3.3 Multi-modal Prompting

#### 개요
- **정의**: 텍스트, 이미지, 오디오, 비디오 등 여러 입력 형식을 결합하는 프롬프트
- **목적**: 더 풍부하고 컨텍스트를 인식하는 응답 생성

#### 작동 원리

**1. 모달리티별 처리**
- 이미지: CNN (Convolutional Neural Network)
- 텍스트: Transformer 모델
- 각 입력 유형에 특화된 신경망 사용

**2. 정보 융합**
- 다양한 모드에서 추출한 특징 정렬 및 통합
- 복잡한 융합 프로세스

**3. 통합 출력 생성**
- 결합된 정보로 일관된 응답 생성

#### 활용 사례

1. **이미지 분류**
   - 텍스트 설명 + 이미지 분석

2. **손글씨 인식**
   - 이미지 + 언어 컨텍스트

3. **번역 및 창의적 시나리오**
   - 다양한 입력 결합

4. **이미지 캡셔닝**
   - 이미지 제공 → 설명 생성
   - 소셜 미디어, 블로그용

#### 지원 플랫폼

**Google Gemini (Vertex AI)**
- 텍스트, 이미지, 비디오를 프롬프트에 포함
- 멀티모달 입력 지원

**PromptCharm**
- 텍스트-이미지 생성에서 프롬프트 엔지니어링 촉진
- 강화된 멀티모달 피드백 루프

**출처:**
- [Google Developers - Multimodal text and image prompting](https://developers.google.com/solutions/ai-images)
- [Medium - Exploring Multi-modal Prompting](https://medium.com/@ajayvardhan2001/prompt-power-week-10-exploring-multi-modal-prompting-text-images-and-beyond-00aa0d74fc1d)
- [Google Cloud - Design multimodal prompts](https://cloud.google.com/vertex-ai/generative-ai/docs/multimodal/design-multimodal-prompts)
- [arXiv - PromptCharm](https://arxiv.org/abs/2403.04014)

---

## 4. 도구 및 프레임워크

### 4.1 DSPy Framework

#### 개요
- **출처**: Stanford NLP
- **정의**: 프롬프트가 아닌 프로그래밍을 위한 프레임워크
- **목적**: LLM 파이프라인의 자동 프롬프트 및 가중치 최적화

#### 핵심 기능

**1. 자동 최적화**
- LM 기반 최적화기가 정의된 메트릭에 따라 프롬프트와 가중치를 자동 조정
- 신뢰성 있고 적응 가능한 LLM 파이프라인 생성

**2. 추상화**
- 원시 텍스트 기반 프롬프트를 모듈식 Python 코드로 추상화
- **Signatures**: 작업 정의
- **Modules**: 재사용 가능한 구성 요소

**3. 성공 메트릭 정의 도구**
- 메트릭 기반 자동 프롬프트 최적화

#### 주요 최적화기

**1. MIPROv2**
- 각 단계에서 지시사항 및 few-shot 예시 생성
- 데이터 인식 및 demonstration 인식 지시사항 생성
- Bayesian Optimization으로 효과적인 검색

**2. COPRO**
- 각 단계에 대한 새로운 지시사항 생성 및 개선
- Coordinate ascent로 최적화

**3. SIMBA**
- Stochastic mini-batch sampling으로 도전적인 예시 식별
- 높은 출력 변동성 있는 예시 찾기

**4. GEPA**
- LM을 사용하여 DSPy 프로그램 궤적 반영
- 작동한 것과 그렇지 않은 것 식별
- 격차를 해결하는 프롬프트 제안

#### 사용 방법

**1. 작업용 예시 준비**
- Training set: 최적화용
- Dev set: 평가용

**2. 시스템 및 평가 방법 정의**
- DSPy 프로그램 구축
- 성공 메트릭 정의

**3. 최적화기 실행**
- 자동으로 프롬프트 조정
- 메트릭 기반 개선

#### 장점

- 빠른 반복 가능
- 모듈식 AI 시스템 구축
- 프롬프트 및 가중치 자동 최적화
- 체계적인 LLM 프롬프트 엔지니어링

**출처:**
- [DSPy Official Website](https://dspy.ai/)
- [GitHub - stanfordnlp/dspy](https://github.com/stanfordnlp/dspy)
- [DSPy - Optimizers](https://dspy.ai/learn/optimization/optimizers/)
- [Haystack - Prompt Optimization with DSPy](https://haystack.deepset.ai/cookbook/prompt_optimization_with_dspy)
- [Towards Data Science - Systematic LLM Prompt Engineering Using DSPy](https://towardsdatascience.com/systematic-llm-prompt-engineering-using-dspy-optimization/)

---

### 4.2 PromptPerfect

#### 개요
- **제공**: Jina AI
- **정의**: 자동 프롬프트 최적화 도구
- **지원**: 텍스트 및 이미지 모델

#### 주요 기능

**1. 멀티 모델 지원**
- ChatGPT, GPT-3.5
- Claude Sonnet
- DALL-E
- Stable Diffusion
- Midjourney
- 기타 다양한 모델

**2. Reverse Prompt Engineering**
- 이미지 업로드로 원본 및 개선된 프롬프트 수신
- 이미지 → 프롬프트 역변환

**3. 다국어 지원**
- 여러 언어 입력 지원
- 글로벌 사용자 접근성

**4. 멀티 목표 최적화**
- 사용자 요구사항에 따라 최적화 프로세스 커스터마이징
- 더 빠른 결과, 더 짧은 프롬프트 등 특정 목표 설정
- 유연성 및 제어 향상

#### 사용자 인터페이스

**특징:**
- 간단하고 접근 가능한 인터페이스
- 다양한 AI 모델 선택 가능
- 원시 프롬프트 입력
- 버튼 클릭으로 자동 업그레이드

**비교 기능:**
- 원본과 최적화된 프롬프트 나란히 비교
- 변경사항 명확히 확인

#### 접근

**웹사이트**: https://promptperfect.jina.ai/

**출처:**
- [PromptPerfect Official Site](https://promptperfect.jina.ai/)
- [eWeek - 6 Best Prompt Engineering Tools](https://www.eweek.com/artificial-intelligence/prompt-engineering-tools/)
- [Deepgram - PromptPerfect Overview](https://deepgram.com/ai-apps/promptperfect)

---

### 4.3 LangSmith

#### 개요
- **제공**: LangChain
- **정의**: LLM 실험 평가 및 추적을 위한 플랫폼
- **목적**: 프롬프트, 모델, retriever, 지식 소스 등 개발 및 추적

#### 핵심 기능

**1. 프롬프트 관리**
- 프롬프트 생성, 버전 관리, 테스트, 협업
- 팀 기반 프롬프트 반복

**2. 평가 중심 개발**
- 구조화된 평가 기반 워크플로우
- 사전 정의된 테스팅
- 메트릭 기반 비교

**3. Dataset 기반 평가**
- 입력 프롬프트 및 예상 출력(또는 성공 규칙)의 데이터셋
- 반복 가능한 평가 실행
- 다양한 프롬프트 버전 비교

**4. Prompt Playground 통합**
- 코드 작성 없이 프롬프트 테스팅
- 일련의 입력에 대한 평가 실행
- 다양한 컨텍스트 또는 시나리오에서 점수 확인

#### 프롬프트 테스팅 및 반복

**반복 프로세스:**
- 프롬프트 작성은 반복적 프로세스
- "Cold start problem" 극복 지원
- **Prompt Bootstrapping**: 인간 피드백에서 추출한 지시사항 조정을 통한 반복적 개선

**자동화된 워크플로우:**
- 상세한 로깅
- 프롬프트 버전 제어
- 구조화된 워크플로우로 자동 추적, 평가, 반복

**통합:**
- LangChain 및 LlamaIndex와 긴밀히 통합
- RAG 프레임워크와 원활한 작업

#### 실용적 활용

**예시 자료:**
- [LangSmith Cookbook - Prompt Iteration Notebook](https://github.com/langchain-ai/langsmith-cookbook/blob/main/testing-examples/movie-demo/prompt_iteration.ipynb)
- [LangSmith Cookbook - Assisted Prompt Engineering](https://github.com/langchain-ai/langsmith-cookbook/blob/main/optimization/assisted-prompt-bootstrapping/assisted-prompt-engineering.ipynb)

**출처:**
- [LangChain Docs - Prompt engineering quickstart](https://docs.langchain.com/langsmith/prompt-engineering-quickstart)
- [Mirascope - LangSmith Prompt Management](https://mirascope.com/blog/langsmith-prompt-management)
- [Travis Kroon - Automating Prompt Iteration with LangChain + LangSmith](https://traviskroon.com/automating-prompt-iteration-with-langchain-langsmith/)
- [Analytics Vidhya - Evaluating LLMs with LangSmith](https://www.analyticsvidhya.com/blog/2025/11/evaluating-llms-with-langsmith/)

---

## 5. 평가 및 테스팅

### 5.1 Prompt Evaluation 프레임워크

#### RAGAS

**개요:**
- RAG 파이프라인 평가 전용 프레임워크
- Retrieval과 Generation 결합 시스템에 최적화

**핵심 메트릭 (5가지):**

1. **Faithfulness (충실성)**
   - 생성된 답변이 검색된 컨텍스트에 얼마나 충실한지

2. **Contextual Relevancy (컨텍스트 관련성)**
   - 검색된 컨텍스트가 질문과 얼마나 관련있는지

3. **Answer Relevancy (답변 관련성)**
   - 생성된 답변이 질문과 얼마나 관련있는지

4. **Contextual Recall (컨텍스트 재현율)**
   - 관련 정보를 얼마나 잘 검색했는지

5. **Contextual Precision (컨텍스트 정밀도)**
   - 검색된 정보가 얼마나 정확한지

**종합 점수:**
- 5가지 메트릭을 결합하여 전체 RAG 점수 산출

**특징:**
- RAG 시스템에 특화
- 컴포넌트 레벨 평가
- Langchain, Llama-Index 지원

**출처:**
- [Galileo - Mastering RAG: How To Evaluate LLMs For RAG](https://galileo.ai/blog/how-to-evaluate-llms-for-rag)
- [EvalScope - RAG Evaluation Survey](https://evalscope.readthedocs.io/en/latest/blog/RAG/RAG_Evaluation.html)

---

#### TruLens

**개요:**
- LLM 응답의 정성적 분석에 초점
- LLM 실험의 체계적 평가 및 추적

**핵심 개념:**

1. **Feedback Functions**
   - 출력 품질 평가 함수
   - 커스터마이징 가능

2. **RAG Triad**
   - RAG 시스템 평가를 위한 3가지 핵심 차원
   - Context Relevance
   - Groundedness
   - Answer Relevance

3. **Honest, Harmless, Helpful Evals**
   - 윤리적 AI 평가
   - 안전성 및 유용성 측정

**주요 기능:**
- LLM 실험 추적
- 프롬프트, 모델, retriever, 지식 소스 등 평가
- 상세한 분석 및 인사이트

**통합:**
- LangChain, LlamaIndex와 긴밀히 통합
- UpTrain, DeepEval, RAGAS, RAGChecker 등과 연동

**오픈소스:**
- GitHub: https://github.com/truera/trulens

**출처:**
- [GitHub - truera/trulens](https://github.com/truera/trulens)
- [TruLens - RAG Triad](https://www.trulens.org/getting_started/core_concepts/rag_triad/)
- [Medium - Frameworks in Focus: TruLens and LlamaIndex](https://medium.com/@LakshmiNarayana_U/frameworks-in-focus-building-and-evaluating-advanced-rag-with-trulens-and-llamaindex-insights-19db95ffcf6e)

---

#### 기타 평가 도구

**DeepEval:**
- 포괄적인 LLM 평가
- 다양한 메트릭 제공

**Patronus AI:**
- RAG 평가 메트릭 제공
- 프로세스 간소화

**공통 기능:**
- 자동화된 평가
- 메트릭 기반 분석
- 반복적 개선 지원

**출처:**
- [Comet - LLM Evaluation Frameworks](https://www.comet.com/site/blog/llm-evaluation-frameworks/)
- [Medium - Top 10 RAG & LLM Evaluation Tools](https://medium.com/@zilliz_learn/top-10-rag-llm-evaluation-tools-you-dont-want-to-miss-a0bfabe9ae19)
- [Patronus AI - RAG Evaluation Metrics](https://www.patronus.ai/llm-testing/rag-evaluation-metrics)

---

### 5.2 Human Evaluation vs Automated Evaluation

#### Human Evaluation

**장점:**
- 미묘한 품질 차이 파악
- 창의성 평가
- 컨텍스트 이해
- 주관적 기준 적용 가능

**단점:**
- 비용이 높음
- 시간 소모적
- 확장성 제한
- 일관성 문제 가능

**사용 시기:**
- 최종 품질 검증
- 복잡한 출력 평가
- 윤리적 고려사항
- 창의적 콘텐츠

---

#### Automated Evaluation

**장점:**
- 빠르고 확장 가능
- 일관성 있는 평가
- 비용 효율적
- 대규모 테스팅 가능

**단점:**
- 미묘한 차이 놓칠 수 있음
- 메트릭 설계 필요
- False positives/negatives 가능

**주요 접근법:**

**1. LLM-as-Judge**
- LLM을 평가자로 사용
- 출력 품질 자동 채점
- 빠른 반복 가능

**2. Benchmark Datasets**
- 표준화된 테스트 세트
- 일관된 비교 기준
- 재현 가능한 결과

**출처:**
- [Anthropic Evals](https://www.anthropic.com/index/evaluating-ai-systems)
- [OpenAI Evals](https://github.com/openai/evals)

---

## 6. 보안 및 모범 사례

### 6.1 Prompt Injection 방어

#### Prompt Injection이란?

- **정의**: 악의적인 입력을 통해 LLM의 지시사항을 우회하거나 변경하는 공격
- **위험**: AI 시스템의 핵심 보안 과제
- **현황**: 완전한 방지 방법은 아직 발견되지 않음

#### 주요 완화 전략

**1. Defense-in-Depth (심층 방어)**
- 여러 보안 제어를 계층화
- 단일 방어에 의존하지 않음
- 상호 보완적 제어

**2. 입력 검증 및 구조화된 프롬프트**
- 입력 유효성 검사
- LLM 활동 면밀히 모니터링
- 사용자를 루프에 유지
- 사전 정의된 응답 형식 강제
- 시스템 지시사항 변경 시도하는 프롬프트 거부

**3. 모델 훈련 및 업데이트**
- Prompt injection 패턴 인식 훈련
- 이를 무시하거나 사용자에게 플래그
- 정기적인 업데이트 및 패칭
- 예: GPT-4가 GPT-3.5보다 덜 취약

**4. 실시간 모니터링 및 탐지**
- Prompt injection 공격 식별 및 차단 모니터
- 안전 훈련 접근법 보완
- 신속한 업데이트로 새로운 공격 차단
- **AI Prompt Shields**: 프롬프트 및 도구 상호작용 분석

**5. Human-in-the-Loop 제어**
- 민감한 데이터 접근 시 인간 승인 필요
- 파일 편집, 설정 변경, API 호출 등
- 자동 작업 제한

**6. 최소 권한 접근**
- Agent가 작업 완료에 필요한 최소한의 민감 데이터 또는 자격 증명만 접근
- 권한 범위 제한

**7. 사용자 교육**
- 악의적인 이메일 및 웹사이트에 숨겨진 프롬프트 식별 교육
- 일부 주입 시도 차단 가능

#### 중요 제한사항

- Generative AI의 특성상 prompt injection 취약점 존재
- 완벽한 방지 방법은 불명확
- 다층 보안 접근 필수
- 런타임 탐지, 위협 인텔리전스, 자동 보안 테스팅 포함

**출처:**
- [Palo Alto Networks - What Is a Prompt Injection Attack?](https://www.paloaltonetworks.com/cyberpedia/what-is-a-prompt-injection-attack)
- [IBM - Protect Against Prompt Injection](https://www.ibm.com/think/insights/prevent-prompt-injection)
- [OWASP - LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
- [Google Security Blog - Mitigating prompt injection attacks](https://security.googleblog.com/2025/06/mitigating-prompt-injection-attacks.html)
- [OpenAI - Understanding prompt injections](https://openai.com/index/prompt-injections/)
- [Lakera - Prompt Injection Guide](https://www.lakera.ai/blog/guide-to-prompt-injection)
- [OWASP - LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)

---

### 6.2 Prompt Engineering 모범 사례 종합

#### 공식 가이드라인

**Anthropic (Claude):**
1. **명확하고 직접적인 지시사항**
   - Claude 4.x는 명시적 지시사항에 최적화
   - 원하는 출력에 대해 구체적으로 설명

2. **Context Engineering**
   - 최소한의 고신호 토큰 세트 찾기
   - 원하는 결과의 가능성 극대화

3. **Interactive Tutorial 활용**
   - 9개 챕터의 실습 가이드
   - 연습 문제 포함

**OpenAI (GPT):**
1. **최신 모델 사용**
   - 최신 모델일수록 프롬프트 엔지니어링 용이

2. **명확성이 핵심**
   - 명확한 구조와 컨텍스트가 영리한 표현보다 중요
   - 대부분의 프롬프트 실패는 모델 한계가 아닌 모호성 때문

3. **반복적 접근**
   - 초기 프롬프트로 시작
   - 응답 검토
   - 출력 기반 개선
   - 반복

**DAIR.AI Prompt Engineering Guide:**
- 13개 언어 지원
- 이론과 실습 결합
- 초보자부터 고급 사용자까지
- 멀티모달 애플리케이션, 추론, Agent 아키텍처 포함

#### 일반 모범 사례

**1. 작업에 맞는 기법 선택**
- Simple tasks → Zero-shot
- Moderate complexity → Few-shot
- Complex reasoning → CoT, ToT
- Tool interaction → ReAct

**2. 명확한 역할 및 컨텍스트**
- System prompt로 AI 역할 정의
- 필요한 배경 정보 제공

**3. 구조화된 출력 요청**
- 원하는 형식 명시
- 예시 제공

**4. 반복 및 테스팅**
- A/B 테스팅
- 메트릭 기반 평가
- 지속적 개선

**5. 버전 관리**
- 프롬프트 변경 추적
- 성능 모니터링
- 롤백 준비

**출처:**
- [Anthropic - Prompt Engineering Overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Anthropic - Claude 4 Best Practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices)
- [OpenAI - Prompt Engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- [DAIR.AI - Prompt Engineering Guide](https://www.promptingguide.ai/)

---

## 7. 참고 자료

### 7.1 공식 문서

**Anthropic:**
- [Prompt Engineering Overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Claude 4 Best Practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices)
- [Prompt Caching](https://docs.claude.com/en/docs/build-with-claude/prompt-caching)
- [Interactive Tutorial (GitHub)](https://github.com/anthropics/prompt-eng-interactive-tutorial)
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook)

**OpenAI:**
- [Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [Best Practices for API](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api)
- [GPT-4.1 Prompting Guide](https://cookbook.openai.com/examples/gpt4-1_prompting_guide)

**DAIR.AI:**
- [Prompt Engineering Guide (Web)](https://www.promptingguide.ai/)
- [GitHub Repository](https://github.com/dair-ai/Prompt-Engineering-Guide)

---

### 7.2 프레임워크 및 도구

**DSPy:**
- [Official Website](https://dspy.ai/)
- [GitHub](https://github.com/stanfordnlp/dspy)
- [Optimizers Documentation](https://dspy.ai/learn/optimization/optimizers/)

**LangSmith:**
- [Prompt Engineering Quickstart](https://docs.langchain.com/langsmith/prompt-engineering-quickstart)
- [LangSmith Cookbook](https://github.com/langchain-ai/langsmith-cookbook)

**PromptPerfect:**
- [Official Site](https://promptperfect.jina.ai/)

**평가 도구:**
- [RAGAS Documentation](https://docs.ragas.io/)
- [TruLens GitHub](https://github.com/truera/trulens)
- [TruLens Docs](https://www.trulens.org/)

**버전 관리:**
- [PromptLayer](https://www.promptlayer.com/)
- [Langfuse](https://langfuse.com/)
- [Humanloop](https://humanloop.com/)

---

### 7.3 주요 연구 논문

**Chain-of-Thought:**
- Wei et al. (2022) - "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models"

**Tree of Thoughts:**
- Yao et al. (2023) - "Tree of Thoughts: Deliberate Problem Solving with Large Language Models"
- [arXiv:2305.10601](https://arxiv.org/abs/2305.10601)

**ReAct:**
- Yao et al. (2022) - "ReAct: Synergizing Reasoning and Acting in Language Models"
- [arXiv:2210.03629](https://arxiv.org/abs/2210.03629)

**Prompt Patterns:**
- White et al. (2023) - "A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT"
- [Vanderbilt University PDF](https://www.dre.vanderbilt.edu/~schmidt/PDF/prompt-patterns.pdf)

---

### 7.4 커뮤니티 및 학습 자료

**블로그 및 가이드:**
- [Prompt Engineering Guide by DAIR.AI](https://www.promptingguide.ai/)
- [Learn Prompting](https://learnprompting.org/)
- [PromptHub Blog](https://www.prompthub.us/blog/)

**코스:**
- [DAIR.AI Academy - Prompt Engineering Course](https://dair-ai.thinkific.com/courses/introduction-prompt-engineering)
- [Pluralsight - OpenAI Prompt Engineering](https://www.pluralsight.com/courses/openai-prompt-engineering-best-practices)

**산업 리포트:**
- [Lakera - Ultimate Guide to Prompt Engineering 2025](https://www.lakera.ai/blog/prompt-engineering-guide)
- [Microsoft Learn - Prompt Engineering Techniques](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/prompt-engineering)

---

### 7.5 보안 및 컴플라이언스

**OWASP:**
- [LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
- [LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)
- [OWASP Top 10 for LLM](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

**보안 가이드:**
- [Google Security Blog - Mitigating prompt injection](https://security.googleblog.com/2025/06/mitigating-prompt-injection-attacks.html)
- [Microsoft - Protecting against indirect injection](https://developer.microsoft.com/blog/protecting-against-indirect-injection-attacks-mcp)
- [Lakera - Guide to Prompt Injection](https://www.lakera.ai/blog/guide-to-prompt-injection)

---

## 다음 단계

### 문서 작성 계획

이 리서치 결과를 바탕으로 다음 문서들을 작성합니다:

1. **A4-2: Prompt Engineering Framework**
   - 방법론 문서
   - 체계적인 프롬프트 엔지니어링 접근법
   - 의사결정 트리 및 가이드라인

2. **B4-4: Prompt Library Template**
   - 실무 템플릿
   - 재사용 가능한 프롬프트 패턴
   - 사용 예시 및 모범 사례

### 추가 고려사항

- 실무 적용 가능한 체크리스트
- 산업별 맞춤 가이드
- 트러블슈팅 가이드
- 성능 최적화 전략

---

**문서 작성 완료일**: 2025-11-23
**다음 업데이트**: A4-2 및 B4-4 문서 작성 시
