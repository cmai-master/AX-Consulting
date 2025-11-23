# RAG Systems 리서치 보고서

> **리서치 일자**: 2025-11-23
> **카테고리**: High Priority - RAG Systems
> **예상 활용 문서**: A4-1, C2-2, B3-3, D2-1, A5-2, B4-3

---

## 목차

1. [RAG 아키텍처 및 설계 패턴](#1-rag-아키텍처-및-설계-패턴)
2. [Chunking 전략](#2-chunking-전략)
3. [Embedding 모델 비교](#3-embedding-모델-비교)
4. [Vector Database 비교](#4-vector-database-비교)
5. [Retrieval 전략 및 최적화](#5-retrieval-전략-및-최적화)
6. [RAG Evaluation 메트릭](#6-rag-evaluation-메트릭)

---

## 1. RAG 아키텍처 및 설계 패턴

### 1.1 RAG의 진화

RAG 시스템은 지난 몇 년간 성능, 비용, 효율성 문제를 해결하기 위해 **Naive RAG → Advanced RAG → Modular RAG**로 진화했습니다.

### 1.2 세 가지 주요 RAG 패러다임

#### **1) Naive RAG**

**특징**:
- 전통적인 Indexing → Retrieval → Generation 프로세스
- 사용자 입력으로 관련 문서를 검색하고, 프롬프트와 결합하여 최종 응답 생성

**한계**:
- **낮은 정밀도(Precision)**: 검색된 청크가 질문과 잘 정렬되지 않음
- **낮은 재현율(Recall)**: 모든 관련 청크를 검색하지 못함
- 결과적으로 **환각(Hallucination)** 문제와 부정확한 응답 발생

#### **2) Advanced RAG**

**개선 사항**:
- **Pre-retrieval 최적화**: 데이터 세분화, 인덱스 구조 최적화, 메타데이터 추가
- **Retrieval 최적화**: Query rewriting으로 명확성 향상
- **Post-retrieval 최적화**: Reranking을 통해 LLM의 핵심 정보 식별 능력 향상

**핵심 기법**:
- 쿼리 재작성(Query Rewriting)
- 혼합 검색(Mixed Retrieval)
- 재순위화(Reranking)

#### **3) Modular RAG**

**특징**:
- Naive RAG와 Advanced RAG는 Modular RAG의 특수 케이스
- 복잡한 RAG 시스템을 **독립적인 모듈과 전문화된 연산자**로 분해
- 전통적인 선형 아키텍처를 넘어 **라우팅, 스케줄링, 융합 메커니즘** 통합

**확장 모듈**:
- Search (유사도 검색)
- Memory (대화 기억)
- Fusion (여러 소스 통합)
- Routing (동적 소스 선택)
- Predict (예측 기반 검색)
- Task Adapter (작업별 최적화)

**장점**:
- 문제 맥락에 맞게 모듈 재배치 가능
- 높은 다양성과 유연성
- 프로덕션 시스템에서 선호됨

### 1.3 2025년 전문화된 RAG 아키텍처

#### **Branched RAG**
- 모든 소스를 쿼리하는 대신 쿼리를 평가하여 **가장 관련성 높은 소스만 선택**
- 효율성과 유연성 향상

#### **Granularity-Aware Retrieval**
- 검색 단위 최적화: 전체 문서 → 의미적으로 정렬된 세밀한 세그먼트
- 검색 정밀도 향상

#### **Agentic RAG**
- 자율 에이전트 및 도구 기반 워크플로우를 위한 아키텍처
- 검색과 생성을 **계획(Planning) 및 행동(Action)**과 동적으로 교차 배치

### 1.4 RAG 시스템 핵심 컴포넌트

#### **Indexing Pipeline**
1. **Document Loaders**: PDF, 웹페이지 등 다양한 형식의 문서 수집
2. **Text Chunking**: 긴 문서를 관리 가능한 청크로 분할 (의미 관계 유지)
3. **Data Preprocessing**: 정제, 필터링, 중복 제거
4. **Embedding Models**: 텍스트를 벡터 표현으로 변환
5. **Vector Database**: 향후 검색을 위한 문서 저장

#### **Retrieval Pipeline**
- 쿼리 이해 및 저장된 임베딩과의 의미적 매칭
- 벡터 데이터베이스에서 가장 관련성 높은 컨텍스트 추출

#### **Generation Pipeline**
- LLM이 사용자 쿼리와 검색된 컨텍스트를 기반으로 완전한 응답 생성

### 1.5 Anthropic의 Contextual Retrieval

**핵심 기법**:
1. **Contextual Embeddings**: 청크에 컨텍스트를 추가하여 임베딩
2. **Contextual BM25**: 키워드 검색에도 컨텍스트 적용

**성과**:
- 검색 오류를 **49% 감소** (Contextual Embeddings + BM25)
- 최대 **67% 감소** (전체 기법 적용 시)
- End-to-End 정확도: **71% → 81%** (요약 인덱싱 + 재순위화 적용)

### 1.6 주요 프레임워크 및 도구

**LangChain**:
- RAG 빌딩을 위한 모듈식 컴포넌트
- Agent-based RAG, Two-step Chain, Self-Reflective RAG 지원
- LangGraph로 복잡한 RAG 플로우 구성 가능

**LlamaIndex**:
- 데이터 로딩, 임베딩, 벡터 검색, LLM 통합 제공
- 고급 최적화 기법 지원

**Haystack**:
- 프로덕션급 RAG 파이프라인 구축 도구

---

## 2. Chunking 전략

### 2.1 Chunking의 중요성

Chunking은 **RAG 성능에 가장 중요한 요소**로 간주됩니다:
- 언어 모델의 제한된 컨텍스트 윈도우
- 관련 정보 제공 시 모델의 효과성 증대
- 문서 분할 방식이 시스템의 정보 검색 및 정확한 답변 능력에 직접적 영향

### 2.2 주요 Chunking 전략

#### **1) Recursive Chunking (권장 시작점)**

**특징**:
- **RecursiveCharacterTextSplitter** 사용
- 권장 설정: **400-512 토큰, 10-20% 중복**
- 계층적 구분자 사용: `["\n\n", "\n", " ", ""]`
- 단락 → 문장 → 단어 순으로 최대한 함께 유지

**장점**:
- 실용적인 기본 선택(Pragmatic Default)
- 대부분의 사용 사례에 적합

#### **2) Semantic Chunking (성능 우선)**

**특징**:
- 임베딩의 의미적 유사성을 기반으로 문장 그룹화
- 높은 의미적 유사성을 가진 임베딩은 더 가까이 배치
- 컨텍스트 인식 청크 생성

**장점**:
- 각 카테고리에서 **가장 효과적인 전략**으로 입증
- 청크 내 일관된 정보 보장

**단점**:
- 모든 문장에 대한 임베딩 생성 및 유사도 계산 필요
- API 호출 또는 로컬 모델 실행 비용 발생

**권장 사용**:
- 메트릭상 추가 성능이 필요하고 예산이 허용할 때만 사용

#### **3) Context-Aware Chunking**

**특징**:
- 문서 구조, 메타데이터, 도메인 규칙 고려
- PDF의 섹션 헤더 또는 코드의 함수 정의로 분할

**LLM-based Chunking**:
- 언어 모델을 사용하여 문서 구조 분석
- 고정 규칙 대신 컨텍스트 인식 의사결정

#### **4) Fixed-Size Chunking**

**특징**:
- 간단하지만 무딘(blunt) 방법
- 기준선 테스트에 유용

### 2.3 Greg Kamradt의 5 Levels of Chunking

#### **Level 1: Character Split**
- 정적 문자 청크로 대용량 데이터 분할

#### **Level 2: Recursive Character Text Splitter**
- 구분자 세트를 사용하여 계층적으로 텍스트 분할
- 원하는 청크 크기 달성까지 재귀 호출

#### **Level 3: Document Specific Splitting**
- 문서 유형별 청킹 방법 (PDF, Python, Markdown)

#### **Level 4: Semantic Splitting**
- 임베딩에서 의미적 의미 추출
- 의미적으로 유사한 청크를 함께 유지

#### **Level 5: Agentic Splitting**
- 에이전트와 같은 시스템으로 텍스트 분할 (실험적)

### 2.4 LlamaIndex의 Chunking 모범 사례

#### **주요 원칙**:

1. **Overlaps (중복)**:
   - 청크 간 컨텍스트 유지
   - 작은 중복으로 시작하여 필요에 따라 조정

2. **Document Structure (문서 구조)**:
   - 문서의 자연스러운 구조 존중 (문장, 단락, 코드 블록)

3. **Customization (커스터마이징)**:
   - 인덱싱하는 데이터 유형 또는 검색 결과에 따라 청크 크기/중복 조정

#### **LlamaIndex Splitter 유형**:

- **SentenceSplitter**: 문장 경계를 존중하며 분할
- **SemanticSplitter**: 임베딩 유사도를 사용하여 적응적으로 중단점 선택
- **CodeSplitter**: 프로그래밍 언어별 코드 분할
- **TokenTextSplitter**: 원시 토큰 개수에 따라 일관된 청크 크기로 분할

### 2.5 최적 설정 권장사항

**일반 권장사항**:
- **청크 크기**: 256-512 토큰
- **중복**: 10-20%

**사용 사례별 권장**:
- **구조화된 텍스트**: Semantic/Recursive Chunking
- **코드 또는 기술 문서**: Recursive Language-Specific Chunking
- **혼합/비구조화 컨텐츠**: AI-driven 또는 Context-Enriched Chunking

**최적화 전략**:
- Recursive chunking(400-512 토큰, 10-20% 중복)으로 시작
- 성능 메트릭이 추가 성능을 요구하고 예산이 허용할 때만 Semantic/Page-level Chunking으로 이동

---

## 3. Embedding 모델 비교

### 3.1 MTEB 벤치마크 기준 Top 모델 (2025)

#### **1위: Voyage-3-large**

**성능**:
- 8개 도메인, 100개 데이터셋에서 **1위**
- OpenAI-v3-large 대비 평균 **9.74% 우수**
- Cohere-v3-English 대비 평균 **20.71% 우수**

**특징**:
- Context length: **32K 토큰** (vs OpenAI 8K, Cohere 512)
- 512차원 바이너리 임베딩으로 OpenAI-v3-large(3072차원 float) 대비 **1.16% 우수**
- **200배 적은 저장 비용**

#### **2위: Google Gemini Embedding (gemini-embedding-001)**

**성능**:
- MTEB 리더보드 전체 **1위**
- Gemini API 및 Vertex AI에서 일반 제공(GA)

#### **3위: NV-Embed-v2 (NVIDIA)**

**성능**:
- MTEB 리더보드 56개 작업에서 **72.31점** (최고 점수)

### 3.2 주요 제공사별 비교

#### **OpenAI**
- **text-embedding-3-large**: 8K 컨텍스트
- 경쟁사 대비 낮은 정확도
- 동등 또는 저렴한 가격의 대안보다 성능 낮음

#### **Voyage AI**
- **voyage-3-large**: 최고 성능
- **voyage-3.5-lite**: 낮은 비용에서 견고한 정확도 (66.1%)
- 관련성(Relevance)에서 2위 모델과 큰 격차

#### **Cohere**
- **Embed 3.0**: 100개 이상 언어 지원
- 노이즈 데이터 처리에 강인함
- 그러나 Jina v3와 함께 하위권
- 더 나은 성능을 더 적은 비용으로 제공하는 모델에 비해 경쟁력 낮음

#### **오픈소스 모델**
- **BGE, E5, Instructor**: HuggingFace에서 제공
- 비용 효율적이나 성능은 상용 모델 대비 낮음

### 3.3 비용-성능 분석

**최고 정확도**:
- **Mistral-embed**: 77.8% (한 벤치마크 기준)

**최고 비용 효율**:
- **Voyage-3.5-lite**: 66.1% 정확도, 최저 비용대 중 하나

**저장 비용 최적화**:
- Voyage-3-large 바이너리 임베딩: OpenAI 대비 200배 저장 비용 절감

### 3.4 선정 시 고려사항

#### **MTEB Leaderboard 주의사항**:
- HuggingFace가 호스팅하는 가장 인기 있는 벤치마크
- **자체 보고(Self-reported)** 결과 - 신중히 해석 필요
- 일부 모델이 벤치마크에 대해 fine-tuning되었을 가능성

#### **선정 기준**:
1. **작업 유형**: 검색, 분류, 클러스터링 등
2. **언어 요구사항**: 다국어 지원 필요 여부
3. **컨텍스트 길이**: 긴 문서 처리 필요 여부
4. **비용**: API 호출 빈도 및 저장 비용
5. **지연시간**: 실시간 응답 필요 여부
6. **도메인 특화**: 특정 도메인(법률, 의료 등)에 최적화 필요 여부

---

## 4. Vector Database 비교

### 4.1 성능 벤치마크 (2025)

#### **쿼리 성능 (1M 벡터 기준)**:
- **Pinecone**: 5,000 queries/second
- **Qdrant**: 4,500 queries/second
- **Weaviate**: 3,500 queries/second
- **Chroma**: 2,000 queries/second

#### **지연시간 (768차원 텍스트 임베딩)**:
- **Milvus/Zilliz**: <10ms (p50) - **최저 지연시간**
- **Pinecone/Qdrant**: 20-50ms
- **Weaviate**: 약간 더 높음
- **Chroma**: ~20ms (100k 벡터, 384차원 기준)

#### **삽입 속도**:
- **Pinecone**: 50,000 vectors/second - **최고속**
- **Qdrant**: 45,000/second
- **Weaviate**: 35,000/second
- **Chroma**: 25,000/second

### 4.2 커뮤니티 & 채택도 (GitHub Stars, 2025)

1. **Milvus**: 35,000+ stars
2. **Qdrant**: 9,000+ stars
3. **Weaviate**: 8,000+ stars
4. **ChromaDB**: 6,000+ stars

### 4.3 사용 사례별 권장사항

#### **Turnkey 확장성 및 관리형 단순성**:
→ **Pinecone**
- 완전 관리형 서비스
- 빠른 시작
- 높은 QPS

#### **OSS 유연성 + 하이브리드 파워 + 가성비**:
→ **Weaviate** 또는 **Qdrant**
- 오픈소스
- 복잡한 필터링 지원
- 하이브리드 검색 지원

#### **극한 엔지니어링 확장성**:
→ **Milvus**
- GPU 가속
- 초저지연
- 대규모 시스템

#### **프로토타입 및 소규모 앱**:
→ **Chroma**
- 빠른 프로토타이핑
- 간단한 설정
- 경량

### 4.4 주요 기능 비교

| 기능 | Pinecone | Weaviate | Qdrant | Milvus | Chroma |
|------|----------|----------|--------|--------|--------|
| **배포** | 클라우드 전용 | 클라우드/온프레미스/하이브리드 | 클라우드/온프레미스 | 클라우드/온프레미스 | 로컬/임베디드 |
| **하이브리드 검색** | ✓ | ✓✓ | ✓✓ | ✓ | Limited |
| **필터링** | 기본 | 고급 | **매우 고급** | 고급 | 기본 |
| **스케일링** | 자동 | 수동/자동 | 수동/자동 | 수동 | 제한적 |
| **GPU 지원** | ✗ | ✗ | ✗ | **✓✓** | ✗ |
| **가격** | 높음 | 중간 | 중간-낮음 | 중간 | 무료(Self-hosted) |
| **학습 곡선** | 낮음 | 중간 | 중간 | 높음 | 낮음 |

### 4.5 VectorDBBench 벤치마킹 도구

**주요 메트릭**:
1. **Latency**: P50, P95, P99 (Tail latency 중요 - SLA 계획용)
2. **QPS (Queries Per Second)**: 고동시성 하의 쿼리 처리 능력
3. **Recall Rate**: 검색 정확도

**테스트 시나리오**:
- **XLarge Dataset**: LAION 100M 벡터 (768차원)
- **Insertion-Under-Load**: 삽입 부하 중 검색 성능 평가
- 90% 데이터 용량에서 p99 직렬 검색 지연시간 및 최대 동시 QPS 측정

**결과 형식**:
- 인덱스 구축 시간
- Recall
- Latency
- 최대 QPS
- QP$ (비용 대비 성능)

---

## 5. Retrieval 전략 및 최적화

### 5.1 하이브리드 검색 (Hybrid Search)

#### **개념**:
- 키워드 기반 검색(**BM25**)와 시맨틱 벡터 검색 결합
- 정밀도(Precision)와 재현율(Recall)의 균형

#### **BM25 알고리즘**:
- **Best Match 25**: 임베딩에서 키워드 매칭을 위한 효과적인 랭킹 함수
- 정확한 용어 일치에 강함

#### **시맨틱 검색**:
- 의미적 유사성 기반
- 동의어 및 관련 개념 포착

#### **성능 개선**:
- Anthropic 연구: **Contextual BM25 + Contextual Embedding**
  - Top-20 청크 검색 실패율 **67% 감소** (5.7% → 1.9%)

### 5.2 Reranking (재순위화)

#### **Cohere Rerank 3.5**:
- 초기 검색 결과의 **최종 정제 레이어**
- 쿼리와 검색 결과의 의미적 및 맥락적 측면 분석

#### **적용 대상**:
- 모든 검색 유형에 적용 가능: BM25, Dense, Sparse, Hybrid

#### **장점**:
- BM25의 정확한 매칭과 Reranking 모델의 의미적 이해 결합
- 각 접근법의 한계를 상호 보완

#### **구현**:
- Cohere 라이브러리 직접 사용
- 커스텀 Reranking 함수 구축
- Elasticsearch, OpenSearch, LangChain 등에서 통합 지원

### 5.3 Query Transformation (쿼리 변환)

#### **목적**:
- 사전 검색 쿼리 변환으로 의미적 격차 해소
- 쿼리-문서 매칭을 답변-답변 유사도 검색으로 전환

#### **주요 기법**:

##### **1) HyDE (Hypothetical Document Embeddings)**

**작동 방식**:
1. 쿼리에 대한 **가상의 이상적인 답변** 생성
2. 원본 쿼리 대신 생성된 문서의 임베딩 사용
3. 더 풍부한 문서로 검색 수행

**장점**:
- 키워드 매칭이나 얕은 재구성을 넘어 **쿼리 의도 반영**
- 쿼리-문서 → 답변-답변 유사도 검색으로 패러다임 전환

**성능**:
- FreshQA 작업에서 **14.45% 개선**
- 복잡한 multi-hop HotPotQA에서 **7% 개선**

##### **2) Multi-Query Rewriting**

**핵심 아이디어**:
- 다양한 관점에서 여러 쿼리 생성
- 사용자 의도의 폭 포착

**작동 방식**:
1. 여러 쿼리 변형 생성
2. 각 쿼리를 임베딩으로 변환
3. 더 넓은 범위의 관련 문서 식별
4. 더 포괄적이고 정확한 응답 생성

**Multi-HyDE**:
- 의미적으로 유사하지 않지만 맥락적으로 관련된 여러 쿼리 생성
- 금융 RAG 파이프라인에서:
  - 정확도 **11.2% 향상**
  - 환각 **15% 감소**

##### **3) Step-Back Prompting**

**개념**:
- 구체적 질문에서 한 걸음 물러나 더 일반적인 개념 파악
- 고차원 원칙 먼저 검색

##### **4) Query Decomposition**

**개념**:
- 복잡한 쿼리를 여러 하위 질문으로 분해
- 각 하위 질문에 대해 독립적으로 검색
- 결과 통합

**Multi-Query vs Multi-HyDE**:
- Multi-Query: 의미적으로 유사한 변형
- Multi-HyDE: 의미적으로 다르지만 맥락적으로 관련된 쿼리

### 5.4 Contextual Compression

**개념**:
- 검색된 컨텍스트에서 불필요한 정보 제거
- 가장 관련성 높은 부분만 LLM에 전달

**장점**:
- 컨텍스트 윈도우 효율적 사용
- 비용 절감
- 응답 품질 향상

### 5.5 Maximum Marginal Relevance (MMR)

**개념**:
- 관련성과 다양성의 균형
- 중복된 유사 문서 대신 다양한 관점의 문서 선택

**적용 시기**:
- 포괄적인 답변이 필요할 때
- 한 가지 관점에 편향되지 않아야 할 때

### 5.6 검색 전략 비교

| 전략 | 유형 | 장점 | 단점 | 사용 시기 |
|------|------|------|------|----------|
| **Cosine Similarity** | 기본 | 빠름, 간단 | 키워드 매칭 약함 | 일반적 시맨틱 검색 |
| **BM25** | 키워드 | 정확한 용어 매칭 | 의미 이해 부족 | 기술 문서, 전문 용어 |
| **Hybrid** | 조합 | 정밀도+재현율 균형 | 복잡성 증가 | 대부분의 프로덕션 시스템 |
| **Reranking** | Post-processing | 최고 정확도 | 추가 비용/지연 | 고품질 요구 사항 |
| **HyDE** | 쿼리 변환 | 의도 기반 검색 | LLM 호출 필요 | 복잡한 질문 |
| **Multi-Query** | 쿼리 확장 | 높은 재현율 | 여러 검색 필요 | 포괄적 답변 필요 |

---

## 6. RAG Evaluation 메트릭

### 6.1 평가 프레임워크 개요

RAG 시스템 평가는 두 가지 주요 구성 요소를 평가합니다:
1. **Retrieval Component** (검색 품질)
2. **Generation Component** (생성 품질)

### 6.2 RAGAS 프레임워크

**개요**:
- RAG 모델을 위한 특화된 평가 프레임워크
- 광범위한 수동 주석 없이 효율적 평가
- 4개 핵심 메트릭

#### **Retrieval 메트릭**:

##### **1) Context Precision (컨텍스트 정밀도)**

**측정 내용**:
- 검색된 컨텍스트가 올바른 순서로 랭킹되었는지
- 더 관련성 높은 항목이 앞에 위치하는지

**계산**:
- Signal-to-noise ratio of retrieved context

**중요성**:
- 검색 컨텍스트의 품질 평가
- Reranking 효과 측정

##### **2) Context Recall (컨텍스트 재현율)**

**측정 내용**:
- 질문에 답변하는 데 필요한 모든 관련 정보가 검색되었는지

**계산**:
- Ground truth와 contexts 기반

**중요성**:
- 검색 시스템의 완전성 평가
- 정보 누락 감지

#### **Generation 메트릭**:

##### **3) Faithfulness (충실도)**

**측정 내용**:
- 생성된 응답에 검색 컨텍스트에 대한 환각이 있는지

**계산**:
- 생성된 답변의 총 진술 수 대비 컨텍스트에서 정확한 진술 수

**공식**:
```
Faithfulness = (컨텍스트에서 정확한 진술 수) / (생성된 답변의 총 진술 수)
```

**중요성**:
- 환각 방지 핵심 메트릭
- 신뢰성 있는 답변 보장

##### **4) Answer Relevancy (답변 관련성)**

**측정 내용**:
- 생성된 응답이 주어진 입력과 얼마나 관련성이 있는지

**중요성**:
- 프롬프트 템플릿의 효과성 평가
- LLM이 관련성 있고 유용한 출력을 생성하는지 확인

#### **RAGAS Score**:

**계산**:
```
RAGAS Score = Mean(Faithfulness, Answer Relevancy, Context Recall, Context Precision)
```

**의미**:
- RAG 시스템의 검색 및 생성에서 가장 중요한 측면을 평가하는 단일 지표

### 6.3 TruLens 프레임워크

**개요**:
- LLM 실험 및 AI 에이전트를 위한 평가 및 추적 도구
- RAG 애플리케이션의 품질 측정 및 개선 지원

#### **RAG Triad 메트릭**:

##### **1) Context Relevance (컨텍스트 관련성)**

**측정 내용**:
- 검색된 각 컨텍스트가 입력 쿼리와 관련성이 있는지

**평가 대상**:
- RAG의 첫 단계인 Retrieval

**중요성**:
- 무관한 정보가 환각으로 엮일 수 있음
- 검색 품질의 첫 번째 관문

##### **2) Groundedness (근거성)**

**측정 내용**:
- RAG의 최종 응답이 검색된 컨텍스트에 의해 얼마나 잘 뒷받침되는지

**목적**:
- LLM이 제공된 사실에서 벗어나지 않도록 방지

**중요성**:
- 사실 기반 응답 보장
- 근거 없는 주장 방지

##### **3) Answer Relevance (답변 관련성)**

**측정 내용**:
- 최종 응답이 사용자 입력에 대해 유용하게 답변하는지

**평가 대상**:
- 원래 질문에 대한 응답의 관련성

#### **환각 없는 RAG의 조건**:

모든 3개 메트릭에서 높은 점수를 받으면:
- **지식 베이스의 한계까지 환각이 없음**을 확신할 수 있음
- 벡터 데이터베이스에 정확한 정보만 포함되어 있다면, RAG의 답변도 정확함

### 6.4 DeepEval 프레임워크

**개요**:
- LLM 시스템 평가 및 테스트를 위한 오픈소스 프레임워크
- Pytest와 유사하지만 LLM 출력에 특화
- **LLM-as-a-Judge** 방식 사용

#### **주요 RAG 메트릭**:

##### **1) ContextualPrecisionMetric**

**측정 내용**:
- Retriever의 Reranker가 검색 컨텍스트에서 더 관련성 높은 노드를 무관한 노드보다 높게 랭킹하는지

**LLM 사용**:
- QAG (Question-Answer Generation)로 LLM 판단 제한

##### **2) AnswerRelevancyMetric**

**측정 내용**:
- Generator의 프롬프트 템플릿이 retrieval_context 기반으로 관련성 있고 유용한 출력을 생성하도록 LLM에 지시할 수 있는지

##### **3) FaithfulnessMetric**

**측정 내용**:
- Generator에 사용된 LLM이 환각하지 않고 retrieval_context에 제시된 사실 정보와 모순되지 않는 출력을 생성하는지

#### **G-Eval Framework**:

**개념**:
- Chain-of-Thoughts(CoT)와 함께 LLM-as-a-Judge 사용
- **모든 사용자 정의 기준**에 따라 LLM 출력 평가

**장점**:
- 연구 기반
- 단순한 자연어 문장 하나로 커스텀 메트릭 구축 가능

**구현**:
- Auto-CoT 및 출력 토큰 확률 정규화 사용
- 병렬 실행, 비용 추적, 캐싱, 디버깅 기능 제공

### 6.5 전통적인 검색 메트릭

#### **Precision@K**

**정의**:
- 검색된 상위 K개 항목 중 관련성 있는 항목의 비율

**공식**:
```
Precision@K = (상위 K개 중 관련 항목 수) / K
```

**사용 시기**:
- 예상 관련 항목 수가 많지만 사용자 주의가 제한적일 때
- 예: 수천 개 제품 중 상위 5개 추천만 표시

**특징**:
- Order-unaware (순서 고려 안 함)
- 단축 목록의 정확도 평가

#### **Recall@K**

**정의**:
- 전체 관련 항목 중 상위 K개에서 검색된 항목의 비율

**공식**:
```
Recall@K = (상위 K개 중 관련 항목 수) / (전체 관련 항목 수)
```

**사용 시기**:
- 모든 관련 항목을 찾는 것이 중요할 때

#### **Mean Reciprocal Rank (MRR)**

**정의**:
- 첫 번째 관련 결과를 얼마나 잘 찾는지 측정

**공식**:
```
MRR = Mean(1 / (첫 번째 관련 항목의 순위))
```

**사용 시기**:
- 각 쿼리에 대해 **하나의 정답**만 있을 때
- 검색 엔진, 질문-답변 시스템
- 정답을 얼마나 빨리 검색하는지 측정

**특징**:
- Order-aware (순서 고려)
- 첫 번째 관련 결과만 고려, 다른 결과는 무시

#### **Normalized Discounted Cumulative Gain (NDCG)**

**정의**:
- 이상적인 순서(모든 관련 항목이 상위에 있음)와 비교하여 랭킹 품질 반영

**특징**:
- Order-aware (순서 고려)
- 이진 및 등급화된 관련성 점수 모두 지원
- 다른 랭킹 메트릭과 달리 관련성의 뉘앙스 처리 가능

**사용 시기**:
- 랭킹 품질, 관련성 뉘앙스, 사용자 행동이 중요한 역할을 할 때
- 추천 시스템, 검색 엔진

### 6.6 메트릭 선정 가이드

| 메트릭 | 순서 고려 | 관련성 유형 | 적합한 사용 사례 |
|--------|----------|------------|------------------|
| **Precision@K** | ✗ | 이진 | 짧은 목록의 정확도, 제한된 사용자 주의 |
| **Recall@K** | ✗ | 이진 | 모든 관련 항목 찾기 중요 |
| **MRR** | ✓ | 이진 | 하나의 정답, 빠른 검색 중요 |
| **NDCG** | ✓ | 이진/등급 | 랭킹 품질, 관련성 뉘앙스 중요 |
| **Context Precision** | ✓ | 이진/등급 | RAG 검색 순서 평가 |
| **Context Recall** | ✗ | 이진 | RAG 검색 완전성 평가 |
| **Faithfulness** | - | - | RAG 환각 방지 |
| **Answer Relevancy** | - | - | RAG 답변 유용성 평가 |

### 6.7 평가 데이터셋 구성

#### **필수 요소**:
1. **Query/Question**: 평가할 질문
2. **Ground Truth**: 정답 또는 기대 답변
3. **Context**: 제공된 컨텍스트 (선택적)
4. **Difficulty**: 난이도 레벨
5. **Category**: 질문 유형 분류
6. **Expected Performance**: 기대 성능 지표

#### **데이터셋 크기**:
- **최소**: 50-100개 쿼리
- **권장**: 200-500개 쿼리
- **포괄적**: 1000+ 쿼리

#### **다양성 확보**:
- 다양한 질문 유형 (사실, 추론, 비교, 요약)
- 다양한 난이도
- 엣지 케이스 포함

---

## 주요 참고 자료 (Sources)

### RAG 아키텍처:
- [Retrieval Augmented Generation (RAG) for LLMs | Prompt Engineering Guide](https://www.promptingguide.ai/research/rag)
- [RAG Architecture Explained: A Comprehensive Guide [2025]](https://orq.ai/blog/rag-architecture)
- [8 Retrieval Augmented Generation (RAG) Architectures You Should Know in 2025](https://humanloop.com/blog/rag-architectures)
- [Modular RAG: Transforming RAG Systems into LEGO-like Reconfigurable Frameworks](https://arxiv.org/html/2407.21059v1)
- [Introducing Contextual Retrieval | Anthropic](https://www.anthropic.com/news/contextual-retrieval)
- [Build a RAG agent with LangChain](https://python.langchain.com/docs/tutorials/rag/)
- [RAG 101: Demystifying Retrieval-Augmented Generation Pipelines | NVIDIA](https://developer.nvidia.com/blog/rag-101-demystifying-retrieval-augmented-generation-pipelines/)

### Chunking 전략:
- [Best Chunking Strategies for RAG in 2025](https://www.firecrawl.dev/blog/best-chunking-strategies-rag-2025)
- [Chunking Strategies to Improve Your RAG Performance | Weaviate](https://weaviate.io/blog/chunking-strategies-for-rag)
- [The Ultimate Guide to Chunking Strategies for RAG Applications with Databricks](https://community.databricks.com/t5/technical-blog/the-ultimate-guide-to-chunking-strategies-for-rag-applications/ba-p/113089)
- [5 Levels Of Text Splitting, Greg Kamradt](https://github.com/FullStackRetrieval-com/RetrievalTutorials/blob/main/tutorials/LevelsOfTextSplitting/5_Levels_Of_Text_Splitting.ipynb)
- [LlamaIndex: Chunking Strategies for Large Language Models](https://medium.com/@bavalpreetsinghh/llamaindex-chunking-strategies-for-large-language-models-part-1-ded1218cfd30)

### Embedding 모델:
- [13 Best Embedding Models in 2025: OpenAI vs Voyage AI vs Ollama](https://elephas.app/blog/best-embedding-models)
- [Text Embedding Models Compared: OpenAI, Voyage, Cohere & More](https://document360.com/blog/text-embedding-model-analysis/)
- [voyage-3-large: the new state-of-the-art general-purpose embedding model](https://blog.voyageai.com/2025/01/07/voyage-3-large/)
- [The Best Embedding Models for Information Retrieval in 2025](https://dev.to/datastax/the-best-embedding-models-for-information-retrieval-in-2025-3dp5)

### Vector Database:
- [Vector Database Comparison: Pinecone vs Weaviate vs Qdrant vs FAISS vs Milvus vs Chroma (2025)](https://liquidmetal.ai/casesAndBlogs/vector-comparison/)
- [Best Vector Database For RAG In 2025](https://digitaloneagency.com.au/best-vector-database-for-rag-in-2025-pinecone-vs-weaviate-vs-qdrant-vs-milvus-vs-chroma/)
- [VectorDBBench: An Open-Source VectorDB Benchmark Tool](https://zilliz.com/vector-database-benchmark-tool)

### Retrieval 최적화:
- [Optimizing RAG with Hybrid Search & Reranking | VectorHub](https://superlinked.com/vectorhub/articles/optimizing-rag-with-hybrid-search-reranking)
- [Enhancing Search Relevancy with Cohere Rerank 3.5 and Amazon OpenSearch Service](https://aws.amazon.com/blogs/big-data/enhancing-search-relevancy-with-cohere-rerank-3-5-and-amazon-opensearch-service/)
- [RAG Techniques GitHub Repository](https://github.com/NirDiamant/RAG_Techniques)
- [How Query Expansion (HyDE) Boosts RAG Accuracy](https://www.chitika.com/hyde-query-expansion-rag/)
- [In-Depth Understanding of RAG Query Transformation Optimization](https://dev.to/jamesli/in-depth-understanding-of-rag-query-transformation-optimization-multi-query-problem-decomposition-and-step-back-27jg)

### Evaluation:
- [RAGAS for RAG in LLMs: A Comprehensive Guide to Evaluation Metrics](https://dkaarthick.medium.com/ragas-for-rag-in-llms-a-comprehensive-guide-to-evaluation-metrics-3aca142d6e38)
- [RAGAS Official Documentation](https://docs.ragas.io/en/stable/concepts/metrics/available_metrics/)
- [RAG Triad - TruLens](https://www.trulens.org/getting_started/core_concepts/rag_triad/)
- [RAG Evaluation | DeepEval](https://deepeval.com/guides/guides-rag-evaluation)
- [Evaluation Metrics for Search and Recommendation Systems | Weaviate](https://weaviate.io/blog/retrieval-evaluation-metrics)
- [Precision and recall at K in ranking and recommendations](https://www.evidentlyai.com/ranking-metrics/precision-recall-at-k)

---

**마지막 업데이트**: 2025-11-23
**다음 리서치**: Agent & Multi-Agent Systems
