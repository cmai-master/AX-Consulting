# LLM Platforms & Models - Comprehensive Research Report

> **작성일**: 2025-11-24
> **리서치 항목**: LLM 플랫폼 비교 및 Context Window 최적화
> **목적**: 컨설팅 자산 문서 작성을 위한 웹 기반 정보 수집
> **관련 문서**: D4-1 (Technology Landscape), B3-2 (Technology Stack Assessment Matrix), D2-1 (Technical Best Practices)

---

## 📋 목차

1. [개요](#개요)
2. [LLM 플랫폼 비교](#llm-플랫폼-비교)
   - [Claude (Anthropic)](#1-claude-anthropic)
   - [GPT-4 시리즈 (OpenAI)](#2-gpt-4-시리즈-openai)
   - [Gemini (Google)](#3-gemini-google)
   - [오픈소스 모델](#4-오픈소스-모델)
3. [벤치마크 및 성능 비교](#벤치마크-및-성능-비교)
4. [LLM 선정 가이드](#llm-선정-가이드)
5. [Context Window 최적화](#context-window-최적화)
   - [Prompt Caching](#1-prompt-caching)
   - [컨텍스트 압축 기법](#2-컨텍스트-압축-기법)
   - [Sliding Window Attention](#3-sliding-window-attention)
6. [실무 적용 가이드](#실무-적용-가이드)
7. [참고 자료](#참고-자료)

---

## 개요

2025년 현재 LLM 생태계는 전례 없는 선택지와 성능 다양성을 제공하고 있습니다. 단일 "최고" 모델이 아닌, 각 도메인과 사용 사례별로 특화된 우수성을 가진 모델들이 존재합니다.

### 주요 트렌드

- **멀티모달 확장**: 텍스트, 이미지, 오디오, 비디오 통합
- **초장문 컨텍스트**: 200K~1M 토큰 지원
- **비용 최적화**: Prompt Caching으로 최대 90% 비용 절감
- **추론 능력 강화**: Extended thinking, Chain-of-Thought
- **속도 개선**: 토큰 생성 속도 100+ tokens/sec

---

## LLM 플랫폼 비교

### 1. Claude (Anthropic)

#### 1.1 모델 라인업 (2025년 11월 기준)

| 모델 | 출시일 | Context Window | 가격 (Input/Output per 1M tokens) |
|------|--------|----------------|----------------------------------|
| **Claude Sonnet 4.5** | 2025-09-29 | 200K (beta 1M) | $3 / $15 |
| **Claude Opus 4.1** | 2025-08-05 | 200K | $15 / $75 |
| **Claude Haiku 4.5** | 2025-10-15 | 200K (64K output) | $1 / $5 |

#### 1.2 성능 특성

**Sonnet 4.5** (가장 유능한 모델)
- **SWE-bench Verified**: 77.2% (200K 설정)
- **강점**: 코딩, 에이전트, Computer Use
- **최적 사용 사례**: 복잡한 개발 작업, 멀티 에이전트 시스템, 장문 컨텍스트 분석

**Opus 4.1** (프리미엄 모델)
- **SWE-bench Verified**: 74.5%
- **강점**: 에이전트 작업, 실제 코딩, 추론
- **최적 사용 사례**: 고난이도 추론, 미션 크리티컬 애플리케이션

**Haiku 4.5** (경제적 고성능)
- **SWE-bench Verified**: 73.3%
- **속도**: Sonnet 4.5 대비 4-5배 빠름
- **비용**: Sonnet 4의 1/3 가격으로 유사한 코딩 성능
- **신기능**: Extended thinking, Computer Use, Context awareness (Haiku 시리즈 최초)
- **최적 사용 사례**: 대규모 배포, 고빈도 API 호출, 비용 민감형 애플리케이션

#### 1.3 주요 차별점

- **성능 대비 가격**: Haiku 4.5는 최고 성능 모델 대비 5% 이내 성능을 1/3 가격에 제공
- **속도**: Haiku 4.5가 Sonnet 4.5보다 훨씬 빠르면서도 높은 코딩 성능 유지
- **확장된 컨텍스트**: Sonnet 4.5는 베타로 1M 토큰 컨텍스트 윈도우 지원

---

### 2. GPT-4 시리즈 (OpenAI)

#### 2.1 모델 라인업

| 모델 | Context Window | 가격 (Input/Output per 1M tokens) | 지식 컷오프 |
|------|----------------|----------------------------------|------------|
| **GPT-4o** | 128K | $5 / $15 | 2023-10 |
| **GPT-4 Turbo** | 128K | $10 / $30 | 2024-04 |
| **GPT-4** | 32K | 더 높음 | 2023-04 |

#### 2.2 성능 특성

**GPT-4o (Omni)** - 차세대 멀티모달
- **속도**: ~109 tokens/sec (GPT-4 Turbo 대비 5배 이상)
- **가격**: GPT-4 Turbo 대비 50% 저렴
- **특징**:
  - 5배 높은 rate limits
  - 실시간 오디오 처리 (인간 뇌와 유사한 속도)
  - 언어, 비전, 오디오를 통합한 단일 신경망
- **최적 사용 사례**: 실시간 멀티모달 애플리케이션, 고빈도 요청

**GPT-4 Turbo** - 장문 컨텍스트 전문
- **속도**: ~20 tokens/sec
- **주요 강점**: 128K 컨텍스트 윈도우로 방대한 문서 분석
- **최적 사용 사례**: 대용량 문서 처리, 심층 분석

**GPT-4 Original** - 복잡한 추론
- **강점**: 복잡한 추론 작업에서 여전히 우수
- **단점**: 비용이 높고 컨텍스트 윈도우 제한적 (32K)
- **최적 사용 사례**: 최고 수준의 추론이 필요한 작업

#### 2.3 주요 차별점

- **멀티모달 통합**: GPT-4o의 "omni" 기능이 실시간 멀티모달 참여에 결정적
- **컨텍스트**: Turbo와 4o 모두 128K (Original은 32K)
- **비용 효율성**: 4o가 Turbo 대비 50% 저렴하면서 5배 빠름

---

### 3. Gemini (Google)

#### 3.1 모델 라인업 (2025)

Google의 Gemini 패밀리는 **Gemini 2.0**과 **Gemini 2.5** 세대로 구성되며, **Flash**, **Flash-Lite**, **Pro** 변형을 제공합니다.

| 모델 | Context Window | 특징 | 강점 |
|------|----------------|------|------|
| **Gemini 2.5 Pro** | 1M~2M | 사고 능력, 최고 추론 | 수학, 과학, 복잡한 추론 |
| **Gemini 2.5 Flash** | 1M | 고속, 실시간 | 채팅, 스트리밍, 요약 |
| **Gemini 2.5 Flash-Lite** | - | 최고 비용 효율 | 분류, 번역, 라우팅 |
| **Gemini 2.0 Flash** | - | 일반 가용성, 단순 가격 | 범용 작업 |

#### 3.2 성능 특성

**Gemini 2.5 Pro** (가장 고급)
- **벤치마크**:
  - GPQA 86.4 (추론 1위)
  - LMArena 리더보드 1위
  - AIME 2025 수학/과학 벤치마크 선도
- **컨텍스트**: 200만 토큰 (복잡한 프롬프트 처리)
- **멀티모달**: 텍스트, 이미지, 오디오, 비디오 입력
- **사고 능력**: 응답 전 추론 과정 수행
- **최적 사용 사례**: 고위험 AI 애플리케이션, 전문가급 작업, 심층 논리/정확성 요구

**Gemini 2.5 Flash** (속도 & 효율성)
- **특징**: Gemini 패밀리 최고속, 즉각 응답, 실시간 스트리밍
- **컨텍스트**: 100만 토큰
- **최적화**: 고처리량 엔터프라이즈 작업 (대규모 요약, 채팅, 데이터 추출)
- **최적 사용 사례**: 일상적 상호작용, 앱/모바일/웹 실시간 사용

**Gemini 2.5 Flash-Lite** (최고 비용 효율)
- **성능**: 2.0 Flash 대비 1.5배 빠르고 저렴
- **개선**: 코딩, 수학, 과학, 추론, 멀티모달 벤치마크에서 2.0 Flash-Lite 능가
- **최적 사용 사례**: 분류, 번역, 지능형 라우팅, 비용 민감형 대규모 작업

**Gemini 2.0 Flash**
- **가용성**: 일반 제공, 더 높은 rate limits
- **가격**: 단일 입력 타입 가격 (짧은/긴 컨텍스트 구분 제거)
- **개선**: Gemini 1.5 Flash보다 다양한 벤치마크에서 성능 향상

#### 3.3 주요 차별점

- **추론 리더십**: Gemini 2.5 Pro가 86.4 GPQA로 추론 지배
- **컨텍스트 크기**: 2M 토큰 (Pro) - 업계 최대급
- **비용 효율성**: Flash-Lite가 혼합 컨텍스트 워크로드에서 1.5 Flash보다 저렴
- **가격 단순화**: 2.0 모델은 짧은/긴 컨텍스트 구분 없는 단일 가격

---

### 4. 오픈소스 모델

#### 4.1 주요 모델 패밀리

**Llama 3.x (Meta)**
- **최신 모델**: Llama 3.3 70B
- **성능**: 405B 모델과 유사한 성능을 훨씬 적은 연산으로 달성
- **특징**:
  - 많은 팀의 "기본 선택"
  - 대규모 배포에 최적화
  - 효율적인 추론 및 강력한 성능
- **최적 사용 사례**: 범용 목적의 신뢰성, 대규모 배포

**Qwen 2.5 / Qwen 3 (Alibaba)**
- **강점**:
  - 초장문 컨텍스트 윈도우
  - 강력한 다국어 성능
  - 구조화된 데이터 처리 우수 (JSON 등)
- **코딩 성능**: HumanEval 85% 이상
- **IFEval**: Llama 3.3과 동등
- **최적 사용 사례**:
  - 엔터프라이즈 애플리케이션 (구조화된 출력 중요)
  - 코드 생성 (Qwen3-Coder, Qwen 2.5 Coder)
  - 다국어 작업

**Mistral / Mixtral (Mistral AI)**
- **아키텍처**: Mixtral 8x7B - Mixture-of-Experts (MoE)
- **파라미터**: 46.7B 파라미터 접근, 토큰당 12.9B만 활성화
- **속도**: Sparse MoE로 6배 빠른 추론
- **특징**:
  - 실시간 성능 우수
  - 저지연 최적화
- **최적 사용 사례**:
  - 챗봇, 가상 비서
  - 실시간 콘텐츠 생성
  - 속도 중요 애플리케이션

#### 4.2 성능 비교

| 모델 | 강점 | 약점 | 최적 사용 사례 |
|------|------|------|---------------|
| **Llama 3.3 70B** | 범용 신뢰성, 대규모 배포 | 특수 작업 성능 | 일반 채팅, 어시스턴트 |
| **Qwen 2.5** | 구조화 데이터, 코딩, 다국어 | - | 엔터프라이즈 앱, 개발 도구 |
| **Mixtral 8x7B** | 속도, 효율성, 저지연 | 최고 수준 성능 아님 | 실시간 서비스, 프로덕션 |

#### 4.3 벤치마크 및 평가

**HuggingFace Open LLM Leaderboard**
- **벤치마크**: IFEval, BBH, MATH, GPQA, MUSR, MMLU-PRO
- **Leaderboard v2**:
  - 각 벤치마크를 0-100 스케일로 정규화 (무작위=0, 완벽=100)
  - Model Comparator 도구로 실시간 비교 가능
- **접근**: [Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard)

---

## 벤치마크 및 성능 비교

### 1. Artificial Analysis

Artificial Analysis는 100개 이상의 AI 모델을 다음 지표로 비교:
- **Quality** (품질)
- **Price** (가격)
- **Output Speed** (출력 속도, tokens/sec)
- **Latency** (지연시간, Time to First Token)
- **Context Window** (컨텍스트 윈도우)

#### 주요 메트릭

**속도 측정**
- **Time to First Token (TTFT)**: 요청 전송 후 첫 토큰 수신까지 시간(초)
- **Time to First Answer Token**: 추론 모델용

**가격 측정**
- **Blended Price**: 입력:출력 3:1 비율 가정한 혼합 가격으로 비교 용이

#### 2025 LLM 현황
- **추론**: Gemini 2.5 Pro (GPQA 86.4)
- **코딩**: Claude 4 Opus (SWE-bench 72.5%)
- **가격 범위**: 입력 $0.10~$40/1M 토큰 (출력)

**리소스**
- [Artificial Analysis Leaderboard](https://artificialanalysis.ai/leaderboards/models)
- [Model Comparison](https://artificialanalysis.ai/models)

---

### 2. 도메인별 성능 비교

| 사용 사례 | 추천 모델 | 근거 |
|----------|----------|------|
| **고객 서비스** | Gemini | 비용 효율성 (Claude 대비 20배 저렴) |
| **전문 코딩** | Claude 4 Opus | SWE-Bench 72.5%, Terminal-Bench 43.2% |
| **헬스케어/금융** | Claude Opus 4 | 톤 제어, 정확성 |
| **도메인 특화** | 특화 모델 | 도메인 작업 40-60% 정확도 향상 |
| **실시간 멀티모달** | GPT-4o | 속도, 멀티모달 통합 |
| **대규모 문서 분석** | Gemini 2.5 Pro | 2M 토큰 컨텍스트 |
| **비용 민감형 대규모** | Claude Haiku 4.5, Gemini Flash-Lite | 가격 대비 성능 |

---

## LLM 선정 가이드

### 1. 주요 선정 기준

#### 1.1 성능 & 벤치마크
- **작업별 성능**: 요약, 코딩, 추론, 수학 등
- **벤치마크 평가**: SWE-bench, GPQA, MMLU, HumanEval 등
- **정확성**: 도메인별 정확도

#### 1.2 비용 & 리소스
- **API 가격**: Input/Output 토큰당 비용
- **확장성**: 대규모 배포 시 비용 증가율
- **리소스 요구사항**: GPU/TPU, 메모리

#### 1.3 사용 사례 정렬
- **기능 호환성**: 특정 기능 요구사항 (멀티모달, 긴 컨텍스트 등)
- **지연시간**: 실시간 vs 배치 처리
- **처리량**: 동시 요청 수

### 2. 선택 프로세스

**최상의 실천 방법**:
1. 사용 사례와 호환되는 가장 강력한 모델 사용 (비용/지연시간 무관)
2. **안전한 선택**: GPT-4o, Claude-3.5, Gemini Pro 1.5 - 다재다능하고 기능 풍부
3. **특정 작업 최적화 후**: 비용/속도 절감을 위해 경량 모델 고려

**선택 우선순위**:
- ❌ 최고 벤치마크 점수 추구
- ✅ 능력, 지연시간, 비용의 균형점 찾기

### 3. 2025 모델 추천 매트릭스

| 요구사항 | 1순위 | 2순위 | 3순위 |
|---------|-------|-------|-------|
| **최고 추론** | Gemini 2.5 Pro | Claude Opus 4.1 | GPT-4o |
| **최고 코딩** | Claude Sonnet 4.5 | Claude Opus 4.1 | Qwen 2.5 Coder |
| **비용 효율** | Claude Haiku 4.5 | Gemini Flash-Lite | Mixtral 8x7B |
| **속도** | Gemini 2.5 Flash | GPT-4o | Mixtral 8x7B |
| **장문 컨텍스트** | Gemini 2.5 Pro (2M) | Claude Sonnet 4.5 (1M) | GPT-4 Turbo (128K) |
| **다국어** | Qwen 2.5 | Gemini 2.5 | GPT-4o |
| **오픈소스** | Llama 3.3 70B | Qwen 2.5 | Mixtral 8x7B |

---

## Context Window 최적화

### 1. Prompt Caching

#### 1.1 개념 및 이점

**Prompt Caching**은 모델의 내부 상태를 저장하고 재사용하여, 동일한 프롬프트 세그먼트를 반복 계산하지 않도록 최적화하는 기법입니다.

**주요 이점**:
- ✅ **비용 절감**: 최대 **90%** 비용 감소
- ✅ **지연시간 감소**: 최대 **85%** 지연시간 단축
- ✅ **처리량 증가**: 캐시된 토큰이 rate limit에 미포함

#### 1.2 제공자별 구현

**Anthropic Claude**
- **지원 모델**: Claude 3.5 Haiku, Claude 3.7 Sonnet (Amazon Bedrock)
- **가격 구조**:
  - Cache write: 기본 가격의 **1.25배** (5분 캐시) / **2배** (1시간 캐시)
  - Cache read: 기본 가격의 **0.1배**
- **캐시 수명**: 5분 (기본) / 1시간 (옵션)
- **새 기능 (2025)**:
  - **Cache-Aware Rate Limits**: 캐시 읽기 토큰이 ITPM 한도에서 제외 (Claude 3.7 Sonnet)
  - **Simplified Caching**: 캐시 브레이크포인트 설정 시 자동으로 가장 긴 이전 캐시 프리픽스에서 읽기

**OpenAI**
- 최대 **90%** 비용 절감
- **80%** 지연시간 감소

**Amazon Bedrock**
- **지원 모델**: Claude 3.5 Haiku, Claude 3.7 Sonnet, Amazon Nova (Micro, Lite, Pro)
- Bedrock 프롬프트 캐싱으로 시간 및 비용 절약

**Google Gemini**
- **최소 토큰**: 32K 토큰 (많은 일반 사용 사례 제외)
- **장점**: 우수한 지속성
- **단점**: 높은 최소 요구사항

#### 1.3 Best Practices

**1. 정적 콘텐츠 앞쪽 배치**
- 변하지 않는 시스템 지시사항, 컨텍스트, 가이드라인을 프롬프트 시작 부분에 배치
- 동적 요소는 분리

**2. Cache Warming (캐시 워밍)**
- 병렬 호출이 캐시를 공유하기를 "기대"하지 말고, 병렬 처리 전 전용 호출로 캐시 미리 생성

**3. 일관된 구조 유지**
- LLM에 프롬프트를 제출할 때 일관된 구조 유지
- 캐시 적중률 향상

**4. 적절한 형식 구조**
```
[간결한 사용자 입력]
[예시들]
```

**5. 타이밍 고려**
- Claude: 5분 캐시 수명에 주의
- Gemini: 더 긴 지속성이지만 32K 최소 토큰

**예상 효과**:
- 반복적 또는 컨텍스트가 많은 쿼리에서 비용 50% 이상 절감
- 응답 시간 대폭 감소

---

### 2. 컨텍스트 압축 기법

#### 2.1 LongLLMLingua

**Microsoft Research**의 LongLLMLingua는 장문 컨텍스트 시나리오에서 LLM의 성능을 가속화하고 향상시키는 프롬프트 압축 기법입니다.

**해결하는 3가지 과제**:
1. **높은 계산 비용**
2. **성능 저하**
3. **위치 편향** (Position Bias)

**성능 지표**:
- **NaturalQuestions**: GPT-3.5-Turbo에서 ~4배 적은 토큰으로 성능 **21.4%** 향상
- **LooGLE**: **94.0%** 비용 절감
- **지연시간**: 10K 토큰 프롬프트를 2x-6x 압축 시 엔드투엔드 지연시간 **1.4x-2.6x** 가속

**LLMLingua 시리즈**:
- **LLMLingua**: 최대 20배 압축
- **LongLLMLingua**: 장문 컨텍스트 최적화
- **LLMLingua-2**: LLMLingua 대비 3x-6x 속도 개선

**기술적 접근**:
- 질문과 관련된 핵심 정보를 LLM이 더 효과적으로 인식하도록 프롬프트 압축
- 각 세그먼트를 독립적으로 압축하는 소프트 압축 기법

#### 2.2 2025 최신 압축 기술

**CompLLM** (2025)
- 실용적 배포를 위한 소프트 압축 기법
- 컨텍스트를 세그먼트로 나누고 각각 독립적으로 압축
- 장문 컨텍스트 Q&A에 특화

**효과**:
- 최대 **20배** 압축률
- 최소한의 성능 손실
- 비용 및 지연시간 대폭 감소

---

### 3. Sliding Window Attention

#### 3.1 개념

**Sliding Window Attention**은 전체 시퀀스를 보지 않고 고정된 크기의 윈도우 내 토큰만 참조하여 메모리와 연산량을 줄이는 기법입니다.

#### 3.2 최신 기술 (2025)

**SWAT (Sliding Window Attention Training)** - 2025년 2월
- **핵심 혁신**:
  - Softmax → Sigmoid 함수로 교체
  - ALiBi + RoPE 균형 있는 활용
  - Attention sink 현상 방지
- **효과**:
  - 정보 유지 능력 향상
  - 토큰당 더 높은 정보 용량
  - 효율적인 장문 컨텍스트 처리

**RoPE Context Extension**
- **YaRN (Yet another RoPE extensioN)**:
  - 시퀀스 길이 함수로 attention scores 재조정
  - RoPE 회전의 base 수정
- **적용 모델**: LLaMA, PaLM, GPT-NeoX

**실제 적용 사례**:
- **Mistral-7B**: 8K 컨텍스트 입력으로 훈련, 4K Sliding Window Attention 사용
- **장점**: 낮은 메모리/연산으로 장문 컨텍스트 추론 가능

#### 3.3 고급 기법 (2025)

**Infinite Retrieval & Cascading KV Cache**
- Training-free 혁신 기법
- Sliding window attention 기반이지만 중요 정보를 더 오래 유지

**Cascading KV Cache**:
- KV 캐시를 계층적 sub-caches로 구성
- 중요 토큰을 기존 sliding window보다 오래 유지
- **LongBench**: 평균 **12.13%** 성능 향상
- **Prefill 지연시간**: 1M 토큰에서 Flash Attention 2 대비 **6.8배** 감소

---

## 실무 적용 가이드

### 1. LLM 선택 의사결정 트리

```
1. 사용 사례 정의
   ├─ 실시간 멀티모달? → GPT-4o
   ├─ 최고 추론/수학? → Gemini 2.5 Pro
   ├─ 코딩/개발? → Claude Sonnet 4.5 / Opus 4.1
   └─ 범용 애플리케이션?
      ├─ 예산 충분? → Claude Sonnet 4.5, GPT-4o, Gemini 2.5 Pro
      └─ 비용 민감? → Claude Haiku 4.5, Gemini Flash-Lite, Llama 3.3

2. 컨텍스트 요구사항 확인
   ├─ 1M+ 토큰? → Gemini 2.5 Pro (2M) / Claude Sonnet 4.5 (1M beta)
   ├─ 128K 토큰? → GPT-4o, GPT-4 Turbo, Gemini 2.5 Flash
   └─ 표준? → 대부분 모델 200K 지원

3. 속도 요구사항
   ├─ 최고속? → Gemini 2.5 Flash, GPT-4o
   ├─ 균형? → Claude Haiku 4.5
   └─ 추론 중심? → Claude Opus, Gemini Pro (속도보다 정확성)

4. 배포 환경
   ├─ 클라우드 API? → 상용 모델 (Claude, GPT, Gemini)
   ├─ 온프레미스? → 오픈소스 (Llama, Qwen, Mistral)
   └─ 하이브리드? → 둘 다 고려
```

### 2. 비용 최적화 전략

#### 2.1 Prompt Caching 활용
- 반복적인 시스템 프롬프트/컨텍스트는 앞쪽에 배치
- Claude: 5분 캐시로 90% 비용 절감 가능
- Cache warming으로 병렬 처리 최적화

#### 2.2 모델 계층화
```
고빈도 단순 작업 → 경량 모델 (Haiku, Flash-Lite, Llama 3.3)
중간 복잡도 → 중간 모델 (Sonnet, GPT-4o, Gemini Flash)
고난이도 작업 → 프리미엄 모델 (Opus, Gemini Pro)
```

#### 2.3 컨텍스트 압축
- LongLLMLingua: 최대 20배 압축으로 비용 94% 절감
- 10K 토큰 → 2-6배 압축 시 지연시간 1.4-2.6배 개선

### 3. 성능 최적화 전략

#### 3.1 Sliding Window Attention
- Mistral 방식: 8K 입력에 4K 윈도우
- SWAT: Sigmoid + ALiBi + RoPE로 정보 유지 개선

#### 3.2 Cascading KV Cache
- 1M 토큰에서 Flash Attention 2 대비 6.8배 빠른 prefill
- LongBench 12.13% 성능 향상

#### 3.3 간결한 프롬프트
- 더 적은 토큰 = 빠른 추론
- 불필요한 반복 제거

### 4. 도메인별 모델 선택

| 도메인 | 추천 모델 | 이유 |
|--------|----------|------|
| **금융/헬스케어** | Claude Opus 4 | 톤 제어, 정확성, 신뢰성 |
| **고객 서비스** | Gemini Flash | 비용 효율성 (20배 저렴) |
| **개발 도구** | Claude Sonnet 4.5, Qwen 2.5 Coder | SWE-bench 77.2%, HumanEval 85%+ |
| **콘텐츠 생성** | GPT-4o | 멀티모달, 속도 |
| **데이터 분석** | Gemini 2.5 Pro | 2M 컨텍스트, 구조화 데이터 |
| **실시간 채팅** | Gemini Flash, GPT-4o, Haiku 4.5 | 고속, 저지연 |

### 5. 평가 및 모니터링

#### 5.1 벤치마크 도구
- **Artificial Analysis**: artificialanalysis.ai - 품질, 가격, 속도 비교
- **HuggingFace Leaderboard**: 오픈소스 모델 벤치마크
- **Provider Benchmarks**: SWE-bench, GPQA, MMLU, HumanEval

#### 5.2 모니터링 메트릭
- **품질**: Accuracy, Faithfulness, Relevancy
- **비용**: 토큰당 비용, 총 월간 비용
- **속도**: TTFT, Tokens/sec
- **처리량**: Requests/min, Rate limit 사용률

#### 5.3 A/B Testing
- 프로덕션 트래픽의 일부로 새 모델 테스트
- 품질, 비용, 속도 트레이드오프 측정
- 점진적 롤아웃

---

## 참고 자료

### LLM 플랫폼 공식 문서

**Claude (Anthropic)**
- [Claude Haiku 4.5 Deep Dive](https://caylent.com/blog/claude-haiku-4-5-deep-dive-cost-capabilities-and-the-multi-agent-opportunity)
- [Introducing Claude Haiku 4.5](https://www.anthropic.com/news/claude-haiku-4-5)
- [Claude Models Overview](https://docs.claude.com/en/docs/about-claude/models/overview)
- [Claude Pricing](https://www.anthropic.com/pricing)
- [Claude Haiku 4.5 vs Sonnet 4.5 Comparison](https://www.creolestudios.com/claude-haiku-4-5-vs-sonnet-4-5-comparison/)

**GPT-4 (OpenAI)**
- [GPT-4 Turbo vs GPT-4o Comparison](https://capestart.com/resources/blog/gpt4-turbo-vs-gpt-4o-which-new-model-is-king/)
- [GPT-4o vs GPT-4 Turbo Review 2025](https://www.byteplus.com/en/topic/415351)
- [OpenAI Pricing](https://openai.com/api/pricing/)
- [GPT-4 vs 4o vs 4 Turbo Performance](https://galileo.ai/blog/gpt-4-vs-gpt-4o-vs-gpt-4-turbo)

**Gemini (Google)**
- [Gemini Models Documentation](https://ai.google.dev/gemini-api/docs/models)
- [Gemini 2.0: Flash, Flash-Lite and Pro](https://developers.googleblog.com/en/gemini-2-family-expands/)
- [Gemini 2.5 Updates](https://cloud.google.com/blog/products/ai-machine-learning/gemini-2-5-flash-lite-flash-pro-ga-vertex-ai)
- [Gemini 2.5 Model Family](https://blog.google/products/gemini/gemini-2-5-model-family-expands/)
- [Gemini 2.0 Flash vs Pro Comparison](https://www.tomsguide.com/ai/i-tested-gemini-2-0-flash-vs-gemini-2-0-pro-heres-the-winner)

**오픈소스 모델**
- [10 Best Open-Source LLM Models 2025](https://huggingface.co/blog/daya-shankar/open-source-llms)
- [15 Best Open Source AI Models 2025](https://elephas.app/blog/best-open-source-ai-models)
- [Comparing Llama 3 vs Qwen 2.5 vs Mixtral](https://www.ankursnewsletter.com/p/comparing-open-source-ai-models-llama)
- [Mistral vs Llama 3 2025](https://kanerika.com/blogs/mistral-vs-llama-3/)

### 벤치마크 & 비교 도구

- [Artificial Analysis LLM Leaderboard](https://artificialanalysis.ai/leaderboards/models)
- [Artificial Analysis Models Comparison](https://artificialanalysis.ai/models)
- [HuggingFace Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard)
- [Vellum LLM Leaderboard 2025](https://www.vellum.ai/llm-leaderboard)
- [Best LLMs 2025: Benchmarks & Cost](https://www.analyticsinsight.net/llm/best-llms-in-2025-benchmarks-cost-context-window-and-use-case-fit)

### Context Window 최적화

**Prompt Caching**
- [Anthropic Prompt Caching](https://www.anthropic.com/news/prompt-caching)
- [Claude Prompt Caching Docs](https://docs.claude.com/en/docs/build-with-claude/prompt-caching)
- [Prompt Caching: 60% Cost Reduction](https://medium.com/tr-labs-ml-engineering-blog/prompt-caching-the-secret-to-60-cost-reduction-in-llm-applications-6c792a0ac29b)
- [Amazon Bedrock Prompt Caching](https://caylent.com/blog/prompt-caching-saving-time-and-money-in-llm-applications)
- [Token-saving Updates Anthropic API](https://www.anthropic.com/news/token-saving-updates)

**컨텍스트 압축**
- [LLMLingua GitHub](https://github.com/microsoft/LLMLingua)
- [LongLLMLingua Paper](https://arxiv.org/abs/2310.06839)
- [LLMLingua: Microsoft Research](https://www.microsoft.com/en-us/research/blog/llmlingua-innovating-llm-efficiency-with-prompt-compression/)
- [LLMLingua Series](https://www.llmlingua.com/)

**Sliding Window & RoPE**
- [Sliding Window Attention Training 2025](https://arxiv.org/abs/2502.18845)
- [Understanding YaRN Context Extension](https://medium.com/@rcrajatchawla/understanding-yarn-extending-context-window-of-llms-3f21e3522465)
- [Extending LLMs Context Window](https://arxiv.org/html/2401.07004v1)
- [Advancing Long-Context LLM Performance 2025](https://www.flow-ai.com/blog/advancing-long-context-llm-performance-in-2025)

### 선정 가이드

- [Complete Guide to LLM Selection 2025](https://alexdharris.substack.com/p/the-complete-guide-to-llm-selection)
- [Practical LLM Selection Recipe](https://blog.dataiku.com/practical-llm-selection-a-recipe-for-success)
- [Key Criteria When Selecting an LLM](https://blog.dataiku.com/key-criteria-when-selecting-an-llm)
- [Best LLM for Business 2025](https://techresearchonline.com/blog/best-llm-for-business-use-case-comparison/)
- [How to Choose the Right LLM Model](https://skywinds.tech/llm-models-explained-selection-guide/)

---

**문서 버전**: 1.0
**최종 업데이트**: 2025-11-24
**작성자**: AI Research Team
**검토 주기**: 분기별 (모델 및 가격 변경 사항 반영)
