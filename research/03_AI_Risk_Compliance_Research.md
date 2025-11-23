# AI Risk & Compliance 리서치 보고서

> **리서치 일자**: 2025-11-23
> **카테고리**: High Priority - AI Risk & Compliance
> **예상 활용 문서**: A2-3, B6-1, B6-2, B6-3, B6-5, C1-6, C3-3, A4-3, B5-5, B5-3, B5-2, B5-4

---

## 목차

1. [AI Risk Taxonomy](#1-ai-risk-taxonomy)
2. [AI 규제 및 컴플라이언스](#2-ai-규제-및-컴플라이언스)
3. [Fairness & Bias Assessment](#3-fairness--bias-assessment)
4. [Model Governance & Documentation](#4-model-governance--documentation)

---

## 1. AI Risk Taxonomy

### 1.1 AI Risk Management 개요

AI 리스크 관리는 AI 시스템의 설계, 개발, 배포 및 운영 전반에 걸쳐 발생할 수 있는 위험을 식별하고 완화하는 프로세스입니다. 주요 프레임워크로는 **NIST AI RMF**, **ISO/IEC 23894** 등이 있습니다.

**핵심 질문:**
- AI 시스템에서 어떤 리스크가 발생할 수 있는가?
- 이러한 리스크를 어떻게 분류하고 평가하는가?
- Likelihood × Impact를 기반으로 어떻게 우선순위를 정하는가?
- 리스크 완화(Mitigation) 전략은 무엇인가?

### 1.2 NIST AI Risk Management Framework (AI RMF)

#### 프레임워크 개요

NIST AI RMF는 **자발적 사용(Voluntary)**을 위한 프레임워크로, AI 제품, 서비스 및 시스템의 설계, 개발, 사용 및 평가에 신뢰성 고려사항을 통합하는 능력을 향상시키기 위해 개발되었습니다.

- **발표일**: 2023년 1월 26일
- **개발 방식**: 합의 기반(Consensus-driven), 공개적(Open), 투명한(Transparent), 협력적(Collaborative) 프로세스
- **적용 대상**: 모든 조직, 산업, AI 시스템 유형

#### 2024 업데이트: Generative AI Profile

- **발표일**: 2024년 7월 26일
- **문서명**: NIST-AI-600-1, Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile
- **주요 내용**:
  - Generative AI (GAI)에 특화된 리스크 정의
  - **400개 이상의 완화 조치(Mitigation Actions)** 카탈로그 제공
  - GAI 리스크를 다루는 포괄적 가이드

#### AI RMF 4대 기능 (Core Functions)

NIST AI RMF의 핵심은 **4개 기능(Functions)**으로 구성되며, 이들은 개별 단계가 아니라 AI 시스템 수명주기 전반에 걸쳐 반복적으로 구현되는 프로세스입니다.

1. **GOVERN (거버넌스)**
   - AI 리스크 관리를 위한 조직의 문화, 정책, 프로세스 수립
   - 책임과 역할 명확화
   - 리더십 참여 및 리소스 할당

2. **MAP (매핑)**
   - AI 시스템의 맥락 파악
   - 리스크, 영향, 기회 식별
   - 이해관계자 및 사용 사례 매핑

3. **MEASURE (측정)**
   - AI 시스템 성능 및 신뢰성 평가
   - 리스크 메트릭 정의 및 추적
   - 평가 및 테스트 수행

4. **MANAGE (관리)**
   - 식별된 리스크에 대한 대응 계획 수립
   - 완화 조치 구현
   - 모니터링 및 지속적 개선

#### Generative AI Profile: Mitigation Actions 카탈로그

- **구조**: AI RMF 4대 기능별로 그룹화 (GOVERN, MAP, MEASURE, MANAGE)
- **내용**: 관련 조치들이 단일 RMF 하위 기능을 다루는 Action Table로 구성
- **Action 식별자**: 각 조치는 글로벌 고유 Action Identifier, 설명, GenAI 리스크 목록 포함

#### 지원 리소스

- **AI RMF Playbook**: 구현 가이드
- **AI RMF Roadmap**: 프레임워크 향후 방향
- **Crosswalks**: 다른 프레임워크(예: ISO, EU AI Act)와의 매핑

### 1.3 ISO/IEC 23894:2023 - AI Risk Management

#### 표준 개요

- **제목**: "Information technology — Artificial intelligence — Guidance on risk management"
- **발표일**: 2023년 2월
- **성격**: 자발적(Voluntary) 국제 표준
- **기반**: ISO 31000:2018 (일반 리스크 관리 원칙)

#### 목적 및 범위

ISO/IEC 23894는 AI를 활용하는 제품, 시스템 및 서비스를 개발, 생산, 배포 또는 사용하는 조직이 **AI 특화 리스크를 관리**하는 방법에 대한 지침을 제공합니다.

- **적용 대상**: 모든 조직 및 맥락에 맞게 커스터마이징 가능
- **프로세스**: AI 리스크 관리의 효과적 구현 및 통합 프로세스 설명

#### 핵심 원칙

1. **전체론적 접근(Holistic Approach)**
   - AI 리스크를 조직의 광범위한 리스크 관리 프로세스 내에서 고려

2. **지속적 개선(Continuous Improvement)**
   - 리스크 관리 프로세스의 지속적 모니터링 및 개선

3. **이해관계자 참여(Stakeholder Engagement)**
   - AI 리스크 관리 프로세스에 관련 이해관계자 참여 강조

#### 주요 특징

- **구체적 예시**: AI 개발 수명주기 전반에 걸친 효과적 리스크 관리 구현 및 통합 예시 제공
- **AI 특화 리스크 소스**: AI 특화 리스크 원천에 대한 상세 정보 제공
- **Annex C**: AI 시스템 수명주기 전반의 리스크 관리 프로세스 기능 매핑

#### 다른 표준과의 관계

- **ISO/IEC 42001 (AI 관리 시스템)**: 거버넌스 표준과 보완적
- **NIST AI RMF**: 전략적 정렬 가능
- **EU AI Act**: 규제 요구사항 충족 지원

ISO/IEC 23894는 거버넌스를 넘어 **실무적 지침(Tactical Guidance)**을 제공하며, AI 수명주기 전반에 걸친 리스크 식별, 평가 및 완화에 대한 실행 가능한 가이드를 제공합니다.

#### 비즈니스 임팩트

- 최근 산업 설문조사에 따르면, ISO/IEC 23894를 구현하는 조직은:
  - **AI 관련 사고 40% 감소**
  - **이해관계자 신뢰도 35% 향상**

### 1.4 AI Risk Taxonomy (리스크 분류 체계)

#### 주요 AI Risk Taxonomy 프레임워크

다양한 연구 및 조직에서 AI 리스크 분류 체계를 제안했으며, 각각의 강조점과 구조가 다릅니다.

#### 1) AIR 2024: AI Risk Categorization Decoded

- **규모**: **314개의 고유 리스크 카테고리** 식별
- **구조**: 4계층(Four-tiered) 구조
  - **Level 1 (최상위):**
    1. **System & Operational Risks**: 시스템 운영 및 기술적 리스크
    2. **Content Safety Risks**: 콘텐츠 안전성 리스크
    3. **Societal Risks**: 사회적 영향 리스크
    4. **Legal & Rights Risks**: 법적 및 권리 침해 리스크

#### 2) MIT AI Risk Repository

- **규모**: **1,600개 이상의 리스크** 추출
- **출처**: 65개의 기존 AI 리스크 프레임워크 및 분류
- **Domain Taxonomy**: **7개 도메인, 24개 하위 도메인**으로 AI 리스크 분류

#### 3) 전통적 리스크 분류 (Traditional Risk Classification)

**3대 리스크 유형:**

1. **Ethical Risks (윤리적 리스크)**
   - 법적 이슈
   - 도덕적 책임
   - 프라이버시 침해

2. **Operational Risks (운영적 리스크)**
   - AI의 의도된 기능과 관련된 리스크
   - 시스템 실패, 성능 저하

3. **Strategic Risks (전략적 리스크)**
   - AI 확산 및 국제 질서에 미치는 영향
   - 경쟁 우위 상실

#### 4) DeepMind Language Model Taxonomy (2022)

- **초점**: 언어 모델(Language Models)의 윤리적 및 사회적 리스크
- **방법론**: Mixed methods approach
- **리스크 수**: **21개 리스크** 식별
- **6개 주제 도메인:**
  1. **Discrimination, Hate speech, and Exclusion**: 차별, 혐오 발언, 배제
  2. **Information Hazards**: 정보 위험
  3. **Misinformation Harms**: 잘못된 정보 피해
  4. **Malicious Uses**: 악의적 사용
  5. **Human-Computer Interaction Harms**: 인간-컴퓨터 상호작용 피해
  6. **Environmental and Socioeconomic Harms**: 환경 및 사회경제적 피해

#### 5) EU AI Act Risk-Based Approach

EU AI Act는 **리스크 기반 접근법**을 사용하여 AI 시스템을 4개 카테고리로 분류:

1. **Unacceptable Risk (수용 불가 리스크)**
   - 너무 위험하거나 비윤리적이어서 금지된 AI 시스템

2. **High Risk (고위험)**
   - 개인 권리 및 안전에 중대한 영향을 미치는 AI 애플리케이션
   - 엄격한 요구사항 적용

3. **Limited Risk (제한적 리스크)**
   - 투명성 의무

4. **Minimal Risk (최소 리스크)**
   - 거의 또는 전혀 리스크가 없는 AI 시스템

#### 6) AI Risk Atlas

- **리스크 카테고리:**
  - **Input Risks**: 입력 데이터 관련 리스크
  - **Inference Risks**: 추론 과정 리스크
  - **Output Risks**: 출력 결과 리스크
  - **Non-technical Risks**: 비기술적 리스크

- **리스크 차원 (Dimensions):**
  - Accuracy (정확성)
  - Fairness (공정성)
  - Explainability (설명 가능성)

### 1.5 AI Risk Assessment: Likelihood × Impact Matrix

#### 리스크 평가 매트릭스 기본 구조

리스크 평가 매트릭스는 **2개 요소의 교차점**으로 구성된 시각적 도구입니다:
- **Likelihood (발생 가능성)**: 리스크 이벤트가 발생할 확률
- **Impact (영향도)**: 리스크 이벤트의 잠재적 영향 크기

**리스크 계산 공식:**
```
Risk = Likelihood × Impact
```

#### 매트릭스 구조 (5x5 예시)

```
            Impact (영향도)
            Negligible  Minor  Moderate  Major  Catastrophic
            (무시가능)  (경미) (중간)    (심각) (치명적)
L   Very High    M        H      H        C       C
i   High         L        M      H        H       C
k   Medium       L        M      M        H       H
e   Low          L        L      M        M       H
l   Very Low     L        L      L        M       M
i
h
o
o
d

L = Low Risk (낮은 리스크)
M = Medium Risk (중간 리스크)
H = High Risk (높은 리스크)
C = Critical Risk (치명적 리스크)
```

#### Inherent Risk vs Residual Risk

1. **Inherent Risk (고유 리스크)**
   - 완화 조치나 통제 없이 AI 시스템이 나타내는 리스크 양
   - "최악의 시나리오" 리스크

2. **Residual Risk (잔여 리스크)**
   - 완화 전략을 고려한 후 남아 있는 리스크
   - 실제 운영 환경에서의 리스크 수준

#### AI 특화 리스크 평가 프레임워크

**AI Risk Assessment Framework의 핵심 단계:**

1. **카탈로그화 (Catalog)**
   - 조직의 모든 AI 시스템 목록 작성
   - 각 시스템의 용도, 데이터, 이해관계자 식별

2. **위협 식별 (Identify)**
   - 각 AI 시스템에 대한 잠재적 위협 식별
   - 기술적, 운영적, 윤리적, 법적 리스크 고려

3. **평가 (Assess)**
   - Likelihood와 Impact 평가
   - 리스크 매트릭스에 매핑

4. **완화 계획 (Plan Mitigations)**
   - 위협이 보안 사고로 전환되기 전에 완화 계획 수립

#### 리스크 대응 전략 (4가지 접근법)

1. **Mitigate (완화)**
   - 리스크 발생 가능성 또는 영향을 줄이는 조치
   - 예: Bias 알고리즘, Adversarial-robust training, Human-in-the-loop 오버라이드

2. **Transfer (전가)**
   - 리스크를 제3자로 이전 (예: 보험, 아웃소싱)

3. **Accept (수용)**
   - 리스크 수용 및 모니터링 (낮은 리스크에 적용)

4. **Avoid (회피)**
   - 리스크를 초래하는 활동 중단 또는 회피

#### 우선순위화 (Prioritization)

- **Critical Risks (High Likelihood + High Impact)**: 즉시 조치 필요, 최우선 리소스 할당
- **High Risks**: 단기적 완화 계획
- **Medium Risks**: 중기적 모니터링 및 완화
- **Low Risks**: 정기적 검토

#### 주요 프레임워크 출처

- **NIST AI RMF**: 미국 표준
- **ISO 42001**: 국제 표준
- **Microsoft, AWS**: 클라우드 제공자 가이드
- **EU, Australia**: 규제 기관 가이드

---

## 2. AI 규제 및 컴플라이언스

### 2.1 EU AI Act (Regulation (EU) 2024/1689)

#### 개요

EU AI Act는 **세계 최초의 포괄적 AI 법적 프레임워크**로, 2024년 8월 1일 발효되었습니다.

- **발효일**: 2024년 8월 1일
- **완전 적용일**: 2026년 8월 2일 (발효 후 2년)
- **접근법**: **Risk-based Approach** (리스크 기반)

#### 4대 리스크 그룹

EU AI Act는 AI 시스템을 **4개 리스크 그룹**으로 분류:

1. **Prohibited AI Practices (금지된 AI 관행)** - 수용 불가 리스크
2. **High-Risk AI Systems (고위험 AI 시스템)**
3. **Limited Risk (제한적 리스크)** - 투명성 의무
4. **Minimal Risk (최소 리스크)** - 규제 없음

#### 금지된 AI 관행 (8개)

적용 시작일: **2025년 2월 2일**

1. **Untargeted Scraping (무차별 스크래핑)**
   - 인터넷 또는 CCTV 자료의 무차별 스크래핑으로 얼굴 인식 데이터베이스 생성 또는 확장

2. **Emotion Recognition (감정 인식)**
   - 직장 및 교육 기관에서의 감정 인식

3. **Biometric Categorisation (생체 인식 분류)**
   - 보호 특성(인종, 정치적 견해, 노조 가입, 종교적 신념 등)을 추론하기 위한 생체 인식 분류

4. **Real-time Remote Biometric Identification (실시간 원격 생체 인식)**
   - 공공 접근 공간에서 법 집행 목적의 실시간 원격 생체 인식

5. **Subliminal, Manipulative, or Deceptive Techniques (잠재의식, 조작, 기만 기법)**
   - 행동을 왜곡하고 정보에 입각한 의사결정을 손상시켜 중대한 피해를 초래하는 기법

6. **Exploiting Vulnerabilities (취약성 악용)**
   - 연령, 장애 또는 사회경제적 상황과 관련된 취약성을 악용하여 행동을 왜곡하고 중대한 피해를 초래

7. **Social Scoring AI (사회적 점수 AI)**
   - 행동, 사회경제적 지위 또는 개인 특성에 따라 사람을 분류

8. **Risk Assessment for Criminal Offenses (범죄 위험 평가)**
   - 개인의 성격적 특성 또는 특징에만 기반하여 범죄 행위 위험 평가 (특정 예외 있음)

#### 고위험 AI 시스템 (High-Risk AI Systems)

**분류 기준 (Article 6):**
- 중요 인프라에 사용되는 시스템
- 법 집행에 사용되는 시스템
- 교육 및 직업 훈련
- 고용, 근로자 관리 및 자영업 접근
- 필수 공공 및 민간 서비스 접근
- 이주, 망명 및 국경 통제 관리
- 사법 및 민주적 프로세스 지원

**요구사항:**

1. **Risk Assessment (리스크 평가)**
   - 수명주기 전반에 걸친 리스크 관리 시스템 운영

2. **Data Quality (데이터 품질)**
   - 훈련, 검증, 테스트 데이터셋이 관련성 있고, 충분히 대표적이며, 가능한 한 오류가 없고 완전해야 함

3. **Documentation (문서화)**
   - 컴플라이언스 입증 및 당국 평가를 위한 기술 문서 작성

4. **Record-Keeping (기록 유지)**
   - 국가 차원의 리스크 및 실질적 수정 사항을 식별할 수 있도록 시스템 수명주기 전반의 이벤트 자동 기록

5. **Human Oversight (인간 감독)**
   - 배포자가 인간 감독을 구현할 수 있도록 시스템 설계

6. **Transparency (투명성)**
   - 시스템 작동 방식 및 의사결정에 대한 명확한 정보 제공

7. **Accuracy (정확성)**
   - 의도된 목적에 적합한 수준의 정확성, 견고성, 사이버 보안

#### 적용 일정 (Implementation Timeline)

| 날짜 | 적용 항목 |
|------|----------|
| 2024년 8월 1일 | **AI Act 발효** |
| 2025년 2월 2일 | **금지된 AI 관행** 및 **AI 리터러시 의무** 적용 |
| 2025년 8월 2일 | **거버넌스 규칙** 및 **GPAI 모델 의무** 적용 |
| 2026년 8월 2일 | **완전 적용** (고위험 AI 시스템 요구사항) |
| 2027년 8월 2일 | **규제 제품 내장 고위험 AI 시스템** 전환 기간 종료 |

### 2.2 ISO/IEC 42001: AI Management System

#### 표준 개요

- **제목**: ISO/IEC 42001:2023 Artificial Intelligence Management System
- **성격**: **인증 가능한(Certifiable) 최초의 국제 AI 관리 시스템 표준**
- **적용 대상**: 모든 산업의 모든 유형의 회사

#### 핵심 요구사항

ISO/IEC 42001은 조직 내 **AI 관리 시스템(AIMS)**을 수립, 구현, 유지 및 지속적으로 개선하기 위한 요구사항을 명시합니다.

**주요 요구사항:**

1. **Governance Framework (거버넌스 프레임워크)**
   - AI 프로젝트, AI 모델 및 데이터 거버넌스 관행을 관리하는 구조화된 프레임워크

2. **Ethical Principles (윤리적 원칙)**
   - 신뢰할 수 있고, 투명하며, 책임 있는 AI 시스템 개발 및 사용 촉진
   - 공정성, 비차별, 프라이버시 존중 등 윤리적 원칙 강조

3. **Risk Management (리스크 관리)**
   - AI 구현과 관련된 리스크 식별 및 완화
   - 적절한 완화 조치 마련

4. **Leadership Commitment (리더십 참여)**
   - 최고 경영진의 AI 관리 시스템에 대한 리더십 및 헌신 입증
   - AI 정책 및 목표가 조직의 전략적 방향과 양립 가능하도록 보장

#### PDCA 접근법 (Plan-Do-Check-Act)

ISO/IEC 42001은 **PDCA 사이클**을 따릅니다:

1. **Plan (계획)**
   - AI 관리 시스템 범위 정의
   - 적용 가능한 통제 식별
   - 리스크 및 윤리적 영향 평가

2. **Do (실행)**
   - AI 거버넌스 정책 구현
   - 공정성, 설명 가능성, 데이터 투명성 등 책임 있는 관행 보장

3. **Check (확인)**
   - 진화하는 규제 준수를 위해 AI 성능 정기 모니터링

4. **Act (조치)**
   - 성과 결과 및 규제 발전에 기반한 AI 거버넌스 지속적 개선

#### 인증 프로세스

**인증 단계:**

1. **AI 관리 시스템 구현**
   - ISO/IEC 42001 요구사항을 준수하는 효과적인 AIMS 구현

2. **내부 감사 (Requirement 9.2)**
   - ISO 42001 표준 대비 AI 관리 시스템의 효과성 평가
   - 비준수 영역 및 개선 기회 파악
   - 외부 감사를 위한 준비 단계

3. **외부 인증 감사**
   - 공인된 제3자 인증 기관의 감사
   - ISO 42001 준수에 대한 공정한 평가
   - 이해관계자에 대한 신뢰성 강화

4. **인증 유효 기간**
   - **3년간 유효**
   - **연간 감시 감사(Surveillance Audit)**
   - **3년차 재인증(Re-certification)**

#### 인증의 이점

- **독립적 검증**: 제3자가 AWS 등 조직이 AI 개발, 배포 및 운영과 관련된 리스크 및 기회를 관리하기 위한 능동적 조치를 취하고 있음을 검증
- **경쟁 우위**: 이해관계자와의 신뢰 구축, 신흥 규제 준수 입증, 책임 있는 AI 관행 확립

#### 주요 인증 기관

- DNV
- BSI
- A-LIGN
- ANAB 인증 인증 기관

### 2.3 GDPR Article 22: Automated Decision-Making

#### Article 22 핵심 원칙

**데이터 주체의 권리:**
> "데이터 주체는 자신에게 법적 효력을 발생시키거나 유사하게 중대한 영향을 미치는, **프로파일링을 포함한 자동화된 처리만을 기반으로 한 결정**의 대상이 되지 않을 권리를 가진다."

**핵심 개념:**
- **Solely Automated (순수 자동화)**: 인간의 개입 없이 완전히 자동화된 의사결정
- **Legal Effects (법적 효력)**: 법적 권리 또는 의무에 영향을 미치는 결정
- **Similarly Significant Effects (유사한 중대 영향)**: 개인에게 실질적으로 중대한 영향을 미치는 결정

#### 예외 (자동화된 의사결정이 허용되는 경우)

Article 22(2)에 따라 다음의 경우 순수 자동화 의사결정이 가능합니다:

1. **Contract Necessity (계약 필요)**
   - 조직과 개인 간 계약 체결 또는 이행에 필요한 경우

2. **Legal Authorization (법적 승인)**
   - 법률에 의해 승인된 경우 (예: 사기 또는 탈세 목적)

3. **Explicit Consent (명시적 동의)**
   - 데이터 주체의 명시적 동의에 기반한 경우

#### 필수 보호조치 (Safeguards)

Article 22(2)(a) 및 (c)의 경우, 데이터 관리자는 **데이터 주체의 권리, 자유 및 정당한 이익을 보호하기 위한 적절한 조치**를 구현해야 합니다:

- **최소한 다음을 포함:**
  - **Human Intervention (인간 개입)**: 관리자 측의 인간 개입을 얻을 권리
  - **Express Point of View (의견 표명)**: 자신의 관점을 표명할 권리
  - **Contest the Decision (결정 이의 제기)**: 결정에 이의를 제기할 권리

#### Meaningful Human Review (의미 있는 인간 검토)

인간 개입이 자격을 갖추려면:
- **단순 형식이 아니어야 함(Not Just a Formality)**
- **결정을 무효화할 수 있는 사람**이 수행
- **모든 관련 데이터를 고려할 수 있는 지식** 보유

#### 적용 사례 (Article 29 Working Party)

다음과 같은 결정이 "similarly significant effects" 기준을 충족:
- **금융 상황 영향**: 신용 자격 등
- **의료 서비스 접근**: 의료 서비스 거부
- **고용 기회**: 고용 기회 거부 또는 심각한 불이익
- **교육 접근**: 대학 입학 등

#### 추가 컴플라이언스 요구사항

- **Technical and Organizational Measures (기술적 및 조직적 조치)** 구현
- **DPIA (Data Protection Impact Assessment)** 수행
- **투명성 유지**: 자동화된 의사결정 프로세스에 대한 정보 제공
- **데이터 주체 권리 보장**: 인간 개입 및 이의 제기 권리

#### Special Category Data 제한

Article 22(4):
> "제2항에 언급된 결정은 제9조(1)에 언급된 특별 범주 개인 데이터를 기반으로 해서는 안 된다. 단, 제9조(2)(a) 또는 (g)가 적용되고 데이터 주체의 권리, 자유 및 정당한 이익을 보호하기 위한 적절한 조치가 마련된 경우는 예외이다."

**특별 범주 데이터 (Article 9(1)):**
- 인종적 또는 민족적 출신
- 정치적 견해
- 종교적 또는 철학적 신념
- 노조 가입
- 유전 데이터, 생체 인식 데이터
- 건강 데이터
- 성생활 또는 성적 지향

### 2.4 한국 AI 규제 및 개인정보보호법

#### AI Framework Act (AI 기본법)

- **통과일**: 2024년 12월 26일
- **공포일**: 2025년 1월 21일
- **시행일**: 2026년 1월 22일

**한국은 아시아-태평양 지역 최초로 포괄적 AI 법안을 채택**했습니다.

**주요 내용:**

1. **High-Impact AI Systems (고영향 AI 시스템)**
   - **정의**: 인간의 생명, 신체 안전 또는 기본권에 중대한 영향을 미치거나 리스크를 초래할 수 있는 AI 시스템
   - **적용 분야**: 의료, 에너지, 공공 서비스 등 중요 분야
   - **특정 의무 부과**

2. **Generative AI Labeling (생성형 AI 라벨링)**
   - 특정 생성형 AI 애플리케이션에 대한 **필수 라벨링 요구사항**

3. **Domestic Representative (국내 대표자)**
   - 외국 AI 운영자는 제품 또는 서비스가 한국 사용자에게 영향을 미치는 경우 **국내 대표자를 지정**해야 함

#### Personal Information Protection Act (PIPA) 업데이트

**주요 개정 사항:**

1. **2023년 9월 발효**
   - PIPA에 대한 주요 개정 사항 발효
   - 2024년 9월: 더 상세한 하위 규칙 개정 발효

2. **AI 개발을 위한 공개 데이터 처리 가이드라인 (2024년 7월)**
   - 개인정보보호위원회(PIPC)가 AI 개발 및 서비스를 위한 공개 개인 데이터 처리에 대한 가이드라인 발표

3. **AI 자동 의사결정 권리 (2024년 9월)**
   - 개인 데이터를 처리하는 AI를 사용한 자동 의사결정에 대해 **데이터 주체에게 이의 제기 권리** 부여
   - 권리 또는 의무에 중대한 영향을 미치는 자동 의사결정에 적용
   - PIPC가 가이드라인 발표

4. **AI 개발을 위한 개인정보 활용 확대 (제안 중)**
   - **원래 목적을 넘어선 개인정보 사용 허용** (AI 개발 목적)
   - 조건: 적절한 보호조치 구현 및 PIPC가 요구사항 충족 확인

---

## 3. Fairness & Bias Assessment

### 3.1 AI Fairness & Bias 개요

AI 시스템의 공정성(Fairness)과 편향(Bias) 평가는 **책임 있는 AI(Responsible AI)**의 핵심 요소입니다. 편향된 AI 시스템은 특정 그룹에 대한 차별을 초래하고, 조직의 평판 손상 및 법적 리스크를 야기할 수 있습니다.

**핵심 질문:**
- AI 모델이 특정 그룹에 대해 불공정하게 작동하는가?
- 어떤 fairness 메트릭을 사용해야 하는가?
- Bias를 어떻게 탐지하고 완화하는가?

### 3.2 AI Fairness Metrics (공정성 메트릭)

#### 1) Demographic Parity (Statistical Parity) - 인구통계적 균형

**정의:**
보호 속성(Sensitive Attribute)으로 정의된 모든 그룹에서 긍정적 결과를 받을 확률이 동일해야 합니다.

**수식:**
```
P(Ŷ=1 | A=0) = P(Ŷ=1 | A=1)

여기서:
- Ŷ = 예측 결과
- A = 보호 속성 (예: 성별, 인종)
```

**예시:**
- Lilliputians와 Brobdingnagians가 Glubbdubdrib 대학에 지원
- **Demographic Parity 달성 조건**: Lilliputians 합격률 = Brobdingnagians 합격률
- 한 그룹이 평균적으로 더 자격이 있는지 여부와 무관

**한계:**
- 그룹 간 다른 기본 비율(Base Rates)을 고려하지 않음
- 예: 특정 질병이 한 인구 집단에서 더 유병률이 높을 경우, Demographic Parity를 강제하면 높은 유병률 그룹에서 **과소 예측**, 낮은 유병률 그룹에서 **과대 예측** 발생 가능

**적용 시나리오:**
- 모든 그룹이 동등한 접근 기회를 가져야 하는 경우
- 예: 대출 승인, 채용 초기 스크리닝

#### 2) Equal Opportunity - 기회 균등

**정의:**
자격이 있는(Qualified) 개인들이 보호 속성과 무관하게 긍정적 결과를 받을 확률이 동일해야 합니다.

**수식:**
```
P(Ŷ=1 | Y=1, A=0) = P(Ŷ=1 | Y=1, A=1)

여기서:
- Y = 실제 라벨 (Ground Truth)
- TPR (True Positive Rate)이 모든 그룹에서 동일
```

**핵심:**
- **긍정적 라벨(Y=1)**에 대한 조건부 기대만 고려
- Equalized Odds의 완화 버전

**예시:**
- 대학 입학: 자격을 갖춘(qualified) 모든 지원자가 인구통계학적 그룹과 무관하게 합격할 동등한 기회

**적용 시나리오:**
- 긍정적 결과(예: "합격")를 예측하는 것이 중요한 경우
- 부정적 결과 예측보다 긍정적 결과 예측의 공정성이 우선

#### 3) Equalized Odds - 균등화된 확률

**정의:**
모델의 예측이 보호 속성과 독립적일 뿐만 아니라, **True Positive Rate (TPR)과 False Positive Rate (FPR)**이 모든 그룹에서 동일해야 합니다.

**수식:**
```
P(Ŷ=1 | Y=1, A=0) = P(Ŷ=1 | Y=1, A=1)  (TPR)
P(Ŷ=1 | Y=0, A=0) = P(Ŷ=1 | Y=0, A=1)  (FPR)
```

**핵심:**
- Demographic Parity보다 **엄격함**
- 긍정적 라벨(Y=1)과 부정적 라벨(Y=0) 모두에 대한 성공률이 동일해야 함

**한계:**
- Demographic Parity보다 달성하기 어려움
- 더 강력한 그룹 공정성 메트릭

**적용 시나리오:**
- 긍정적 및 부정적 클래스 모두 정확히 예측하는 것이 중요한 경우
- 예: 범죄 재범 예측, 질병 진단

#### Fairness Metrics 간 Trade-offs

**중요한 원칙:**
> "이러한 공정성 기준은 수학적으로 종종 상충됩니다. 한 기준을 충족하면 다른 기준을 충족하지 못할 수 있습니다."

**실무 접근:**
- 사용 사례에 따라 **특정 공정성 기준을 우선순위화**해야 함
- 예측 성능 기준과 마찬가지로, 공정성 기준도 trade-off 존재

### 3.3 AI Bias 유형 (Types of AI Bias)

#### 1) Selection Bias (선택 편향)

**정의:**
훈련 데이터가 실제 세계 인구를 대표하지 못할 때 발생

**예시:**
- 특정 인구 집단이 데이터에서 과소 또는 과대 대표됨
- 남성 중심 산업의 과거 데이터로 훈련된 채용 알고리즘 → 남성 지원자 선호

#### 2) Historical Bias (역사적 편향)

**정의:**
훈련 데이터가 사회에 만연했던 과거의 편견, 불평등 또는 고정관념을 반영

**예시:**
- 과거 대출 승인 데이터로 훈련된 신용 점수 모델 → 역사적으로 차별받은 그룹에 불리

#### 3) Representation Bias (대표성 편향) = Sampling Bias

**정의:**
특정 그룹 또는 카테고리가 실제 비율과 비교하여 훈련 데이터에서 과소 또는 과대 대표됨

**예시:**
- 얼굴 인식 모델이 주로 백인 얼굴로 훈련 → 유색인종 얼굴 인식 성능 저하

#### 4) Measurement Bias (측정 편향)

**정의:**
결함이 있는 데이터 수집 방법으로 인해 특정 그룹을 체계적으로 잘못 표현

**예시:**
- 특정 인구 집단에서 부정확한 센서 또는 측정 도구

#### 5) Feature Selection Bias (특징 선택 편향)

**정의:**
인종 또는 성별과 같은 보호 속성이 훈련 데이터에서 명시적으로 제외되더라도, 다른 선택된 특징이 프록시(Proxy)로 작동하여 동일한 차별적 정보를 전달

**예시:**
- 우편번호가 인종의 프록시로 작동
- 이름이 성별 또는 민족성의 프록시로 작동

### 3.4 Protected Attributes (보호 속성)

**정의:**
법률에 명시된 속성으로, 일반적으로 다음을 포함:
- Sex (성별)
- Gender (젠더)
- Ethnicity (민족성)
- Race (인종)
- Age (연령)
- Disability (장애)
- Religion (종교)
- Sexual Orientation (성적 지향)

**Proxy Attributes (프록시 속성):**
- 보호 속성과 강한 상관관계를 가진 속성
- 예: 우편번호 → 인종, 이름 → 성별
- 프록시는 의도치 않게 편향될 수 있으며, 보호 속성과 잘못되거나 우연한 상관관계를 가질 수 있음

### 3.5 Fairness Measurement Approaches (공정성 측정 접근법)

#### Group Fairness vs Individual Fairness

1. **Group Fairness (그룹 공정성)**
   - **정의**: 보호 속성으로 정의된 그룹이 유사한 대우 또는 결과를 받음
   - **메트릭**: Demographic Parity, Equal Opportunity, Equalized Odds

2. **Individual Fairness (개인 공정성)**
   - **정의**: 유사한 개인이 유사한 대우 또는 결과를 받음

#### Four-Fifths Rule (4/5 규칙)

**정의:**
미국 평등 고용 기회 위원회(EEOC) 등 규제 기관이 보호 계층에 대한 불리한 대우를 식별하기 위해 사용하는 기준

**기준:**
- 이상적인 Parity Score = 1
- **0.8 - 1.25 범위** 밖으로 벗어나면 불공정 가능성

#### Disparate Impact (불균형 영향)

**정의:**
비특권 그룹이 특권 그룹의 80% 미만 비율로 긍정적 결과를 받는 경우

#### Performance Disparity Analysis (성능 불균형 분석)

**방법:**
- 모델의 **Accuracy, Precision, Recall** 및 기타 성능 메트릭을 인구통계학적 그룹 간 비교
- **유의미한 차이 → Bias 지표**

### 3.6 IBM AI Fairness 360 (AIF360)

#### 개요

- **개발**: IBM Research
- **성격**: **오픈소스** 툴킷
- **LF AI**: 2020년 7월 LF AI로 이관 (Incubation project)
- **라이선스**: Apache v2.0
- **언어**: Python, R

#### 주요 기능

**1) Bias Detection (편향 탐지)**
- 데이터셋 및 ML 모델에서 원치 않는 편향을 확인하기 위한 **70개 이상의 메트릭**
- 공정성의 다양한 측면 정량화

**2) Bias Mitigation (편향 완화)**
- 최첨단 알고리즘 포함
- **3단계 적용 가능:**
  1. **Pre-processing**: 훈련 전 데이터 조정
  2. **In-processing**: 모델 훈련 중 조정
  3. **Post-processing**: 모델 예측 후 조정

#### 포함된 알고리즘

- Optimized Preprocessing
- Reweighing
- Adversarial De-biasing
- Reject Option Classification
- Disparate Impact Remover
- Learning Fair Representations
- Equalized Odds Post-processing
- Meta-Fair Classifier
- 기타 다수

#### 적용 분야

- Finance (금융)
- Human Capital Management (인적 자본 관리)
- Healthcare (의료)
- Education (교육)

#### 리소스

- **GitHub**: https://github.com/Trusted-AI/AIF360
- **Website**: https://aif360.res.ibm.com/

### 3.7 Microsoft Fairlearn

#### 개요

- **개발**: Microsoft Research
- **성격**: **오픈소스** 툴킷
- **목적**: 데이터 과학자 및 개발자가 AI 시스템의 공정성을 평가하고 개선할 수 있도록 지원

#### 2대 핵심 컴포넌트

**1) Interactive Visualization Dashboard (대화형 시각화 대시보드)**
- 모델 성능 및 공정성을 시각화
- 그룹별 불균형 파악

**2) Unfairness Mitigation Algorithms (불공정 완화 알고리즘)**
- 공정성 제약을 만족하는 모델 생성

#### Fairness Assessment (공정성 평가)

**핵심 질문:**
> "어떤 사람들의 그룹이 AI 시스템에 의해 불균형적으로 부정적 영향을 받을 수 있으며, 어떤 방식으로 영향을 받는가?"

**주요 도구:**
- **MetricFrame 클래스** (`fairlearn.metrics` 모듈)
- 보호 속성으로 정의된 그룹 간 세분화된 평가(Disaggregated Evaluation)

#### Fairness Constraints (공정성 제약)

**정의:**
예측 변수의 행동에 대한 제약 집합으로, **Parity Constraints** 또는 **Criteria**라고도 함

**목적:**
보호 속성이 정의하는 그룹 간 예측 변수의 행동의 일부 측면이 비교 가능해야 함 (예: 다른 인종 간)

**최적화 목표:**
```
성능 메트릭(예: 분류 정확도) 최적화
Subject to: 공정성 제약(예: False Negative Rate 차이 상한)
```

#### Mitigation Algorithms (완화 알고리즘)

**1) Post-processing Algorithms (후처리 알고리즘)**
- 이미 훈련된 모델의 예측을 변환하여 공정성 제약 만족
- 선택된 공정성 메트릭(예: Demographic Parity) 제약 충족
- 모델 성능(예: Accuracy) 최대화
- **재훈련 불필요**

**2) Reduction Algorithms (축소 알고리즘)**
- 표준 분류 또는 회귀 알고리즘을 블랙박스로 취급
- 데이터 포인트를 반복적으로 재가중치(Re-weight)하고 모델 재훈련
- **10-20회 반복** 후 공정성 제약 만족하는 모델 생성
- 모델 성능 최대화

#### 리소스

- **Website**: https://fairlearn.org/
- **Documentation**: https://fairlearn.org/main/
- **GitHub**: https://github.com/fairlearn/fairlearn

### 3.8 Bias Detection & Mitigation Tools (편향 탐지 및 완화 도구)

**주요 오픈소스 Fairness Toolkits:**

1. **IBM AI Fairness 360**
   - 70+ 메트릭
   - 3단계 완화 (Pre, In, Post)

2. **Microsoft Fairlearn**
   - 대화형 대시보드
   - Post-processing 및 Reduction 알고리즘

3. **Google What-If Tool**
   - 시각적 인터페이스
   - 모델 행동 탐색 및 공정성 분석

4. **LinkedIn Fairness Toolkit (LiFT)**
   - 대규모 데이터셋 지원
   - Spark 기반

5. **Aequitas**
   - Bias 및 Fairness 감사 툴킷
   - Policy 및 Regulation 중심

---

## 4. Model Governance & Documentation

### 4.1 Model Governance 개요

Model Governance는 AI/ML 모델의 전체 수명주기(Lifecycle)에 걸쳐 **책임, 투명성, 품질 및 컴플라이언스**를 보장하는 프로세스, 정책 및 통제 집합입니다.

**핵심 질문:**
- 모델이 어떻게 개발되고 승인되는가?
- 누가 책임을 지는가?
- 모델 성능이 저하될 때 어떻게 감지하고 대응하는가?
- 모델 문서화를 어떻게 표준화하는가?

### 4.2 Google Model Cards

#### Model Card 개요

**정의:**
Model Card는 고급 AI 모델이 어떻게 설계되고 평가되었는지에 대한 **간단하고 구조화된 개요**로, Google의 책임 있는 AI 접근법을 지원하는 핵심 산출물입니다.

**기원:**
- **논문**: "Model Cards for Model Reporting" (Mitchell et al., 2018)
- **목적**: ML 모델 출처, 사용법 및 윤리적 평가 보고를 위한 구조화된 프레임워크

#### Model Card의 목적

**주요 이점:**
- **개발자**: 모델 설계 및 평가 문서화
- **규제 기관**: 모델 컴플라이언스 평가
- **다운스트림 사용자**: 모델 제안 사용 및 한계 이해

**Model Card 제공 정보:**
- 모델 설계 의도
- 추천 사용 사례 및 제한 사항
- 성능 메트릭
- 윤리적 고려사항

#### Model Card Toolkit (MCT)

**목적:**
모든 ML 실무자를 위해 Model Card 생성을 간소화

**기능:**
- Model Card에 들어갈 정보 컴파일 지원
- 다양한 청중에 유용한 인터페이스 생성 지원

**설치:**
```bash
pip install model-card-toolkit
```

#### Model Card 표준 템플릿 구성 요소

Google의 원래 프레임워크는 **9개 요소**를 제안 (조직 선호에 따라 수정 가능):

1. **Model Details (모델 세부 정보)**
   - 모델 이름, 버전, 유형
   - 개발자 정보
   - 개발 날짜

2. **Intended Use (의도된 사용)**
   - 추천 사용 사례
   - 비추천 사용 사례
   - 타겟 사용자

3. **Factors (요인)**
   - 관련 요인 (인구통계학적, 환경적 등)
   - 평가 요인

4. **Metrics (메트릭)**
   - 성능 메트릭
   - 의사결정 임계값
   - 측정 접근법

5. **Training Data (훈련 데이터)**
   - 데이터셋 설명
   - 전처리 방법

6. **Evaluation Data (평가 데이터)**
   - 데이터셋 설명
   - 전처리 방법
   - 동기

7. **Quantitative Analyses (정량적 분석)**
   - 성능 결과
   - 그룹별 성능 분석

8. **Ethical Considerations (윤리적 고려사항)**
   - 잠재적 편향
   - 리스크
   - 완화 조치

9. **Caveats and Recommendations (주의사항 및 권장사항)**
   - 알려진 한계
   - 추가 테스트 권장사항

#### 리소스

- **공식 사이트**: https://modelcards.withgoogle.com/
- **GitHub**: https://github.com/tensorflow/model-card-toolkit
- **TensorFlow 문서**: https://www.tensorflow.org/responsible_ai
- **Colab Tutorial**: Model Card 작성 튜토리얼 제공

### 4.3 Model Lifecycle Management & Stage-Gate Process

#### Model Lifecycle Overview

**AI/ML 모델 수명주기 단계:**
1. **Problem Definition**: 비즈니스 문제 정의
2. **Data Collection & Preparation**: 데이터 수집 및 준비
3. **Model Development**: 모델 개발 및 훈련
4. **Model Evaluation**: 모델 평가
5. **Model Deployment**: 프로덕션 배포
6. **Monitoring & Maintenance**: 모니터링 및 유지보수
7. **Model Retirement**: 모델 폐기

#### Stage-Gate Process (단계-게이트 프로세스)

**정의:**
프로젝트 관리 기법으로, 이니셔티브 또는 프로젝트를 **명확한 단계(Stages)**로 나누고, 각 단계 사이에 **의사결정 포인트(Gates)**를 배치합니다.

**구조:**
- **Stage (단계)**: 작업이 수행되는 단계
- **Gate (게이트)**: 다음 단계로 진행하기 전 검토 및 승인 포인트

#### Governance & Approval Workflow

**Gate Keepers (게이트 키퍼):**
- 일반적으로 **시니어 리더** 또는 **운영 위원회 멤버**
- 다음 단계로 진행하기 전 준비 상태 및 리스크 평가
- Green light 부여 책임

**Gate 결정 기준:**
- **이전 단계 성공 검토**
- **비즈니스 케이스 평가**
- **리스크 분석**
- **필요 리소스 가용성**

**Gate 의사결정 옵션:**
1. **Go (진행)**: 다음 단계로 진행
2. **Conditional Go (조건부 진행)**: 특정 조건 충족 후 진행
3. **Hold (보류)**: 추가 정보 필요, 일시 중단
4. **Kill (중단)**: 프로젝트 종료

#### Gate의 3가지 목표

1. **Ensure Quality of Execution (실행 품질 보장)**
   - 각 단계가 표준에 맞게 완료되었는지 확인

2. **Evaluate Business Rationale (비즈니스 근거 평가)**
   - 프로젝트가 여전히 비즈니스 목표와 정렬되는지 평가

3. **Approve Project Plan & Resources (프로젝트 계획 및 리소스 승인)**
   - 다음 단계를 위한 리소스 및 계획 승인

#### AI/ML Model Governance에 적용

**Stage-Gate를 AI/ML에 적용한 예:**

| Stage | Gate | 주요 활동 | Gate 체크포인트 |
|-------|------|-----------|----------------|
| 1. Problem Definition | Gate 1 | 비즈니스 문제 정의, 성공 기준 수립 | 비즈니스 케이스 승인, 리소스 할당 |
| 2. Data Preparation | Gate 2 | 데이터 수집, EDA, 데이터 품질 확인 | 데이터 품질 승인, 윤리적 검토 |
| 3. Model Development | Gate 3 | 모델 훈련, 하이퍼파라미터 튜닝 | 모델 성능 기준 충족, 기술 검토 |
| 4. Model Evaluation | Gate 4 | 테스트 데이터 평가, Fairness 평가 | 성능 및 Fairness 기준 충족, 리스크 평가 |
| 5. Model Deployment | Gate 5 | 프로덕션 배포, A/B 테스트 | 배포 준비 확인, 모니터링 계획 승인 |
| 6. Monitoring | Ongoing | 성능 모니터링, Drift 탐지 | 정기 검토, 재훈련 트리거 |

### 4.4 Model Drift Detection

#### Model Drift 개요

**정의:**
Model Drift는 데이터 변경 또는 입력과 출력 변수 간 관계 변경으로 인한 **ML 모델 성능 저하**를 의미합니다.

#### 3대 Drift 유형

#### 1) Data Drift (데이터 드리프트) = Covariate Shift

**정의:**
시간 경과에 따라 입력 데이터의 분포가 변경될 때 발생

**수식:**
```
P(X) 변화 (시간 t1 vs t2)
```

**예시:**
- 고객 행동 패턴 변화
- 센서 데이터 분포 변화
- 계절성 변화

**영향:**
- 모델 성능 저하
- 예측 정확도 감소

#### 2) Concept Drift (개념 드리프트)

**정의:**
데이터 패턴 및 ML 모델이 학습한 관계가 변경될 때 발생
보다 구체적으로, **타겟 또는 종속 변수의 통계적 특성 변화**를 의미

**수식:**
```
P(Y | X) 변화 (시간 t1 vs t2)
```

**예시:**
- 소비자 선호도 변화
- 규제 변경으로 인한 라벨 정의 변화
- 경제 환경 변화

**영향:**
- 모델이 학습한 관계가 더 이상 유효하지 않음
- 예측 정확도 심각한 저하

#### 3) Prediction Drift (예측 드리프트)

**정의:**
모델 출력 분포의 변화

**수식:**
```
P(Ŷ) 변화 (시간 t1 vs t2)
```

### 4.5 Drift Detection Methods (드리프트 탐지 방법)

#### 1) Statistical Techniques (통계적 기법)

**Kolmogorov-Smirnov (K-S) Test**
- **목적**: 두 데이터셋이 동일한 분포에서 유래했는지 측정
- **특성**: 비모수적(Non-parametric) - 분포에 대한 사전 가정 불필요
- **활용**: 훈련 데이터 분포 vs 프로덕션 데이터 분포 비교

**Page-Hinkley Method**
- **목적**: 시계열 데이터의 평균 변화 탐지
- **활용**: ML 모델 성능 모니터링, 데이터 분포 변화 탐지
- **특성**: 온라인 변화 탐지 (실시간 모니터링)

**Population Stability Index (PSI)**
- **기원**: 리스크 스코어카드의 점수 분포 변화 모니터링을 위해 개발
- **현재 활용**: 종속 및 독립 변수 포함 모든 모델 관련 속성의 분포 변화 검사
- **해석**:
  - PSI < 0.1: 유의미한 변화 없음
  - 0.1 ≤ PSI < 0.25: 약간의 변화
  - PSI ≥ 0.25: 중대한 변화 (조사 필요)

#### 2) Model Quality Metrics (모델 품질 메트릭)

**가장 직접적이고 신뢰할 수 있는 Concept Drift 반영:**
- **Classification**: Accuracy, Precision, Recall, F1-Score
- **Regression**: MAE, MSE, RMSE, R²

**모니터링 전략:**
- 시간 경과에 따른 이러한 메트릭의 **유의미한 감소** → Concept Drift 지표
- 정기적 평가 (일간, 주간, 월간)

#### 3) Data Distribution Monitoring (데이터 분포 모니터링)

**사용 시나리오:**
- **Ground Truth 또는 True Labels가 프로덕션에서 사용 불가능할 때**
- 데이터 분포 드리프트 추적으로 모델 품질 모니터링 대체

**접근법:**
- 입력 특징(Features) 분포 추적
- 통계적 테스트 (K-S, PSI 등) 활용
- 분포 변화 탐지 시 재훈련 트리거

### 4.6 Drift Monitoring 전략

**프로덕션 모니터링 Best Practices:**

1. **Multi-level Monitoring (다층 모니터링)**
   - **Level 1**: Model Quality Metrics (가능한 경우)
   - **Level 2**: Data Distribution Drift
   - **Level 3**: Prediction Distribution Drift

2. **Alerting Strategies (알림 전략)**
   - 임계값 기반 알림 (예: PSI > 0.25)
   - 추세 기반 알림 (지속적 저하)
   - 심각도 레벨 (Warning, Critical)

3. **Retraining Triggers (재훈련 트리거)**
   - 성능 메트릭이 허용 범위 아래로 떨어질 때
   - 유의미한 데이터 드리프트 탐지 시
   - 정기적 재훈련 (예: 월간, 분기별)

4. **Continuous Monitoring Tools**
   - Evidently AI
   - NannyML
   - Azure ML Model Monitoring
   - AWS SageMaker Model Monitor

### 4.7 Microsoft Responsible AI: Model Documentation & Transparency

#### Microsoft Responsible AI 개요

**핵심 원칙:**
Microsoft는 6가지 원칙에 기반한 **Responsible AI Standard** 프레임워크를 생성했습니다:

1. **Fairness (공정성)**: 모든 사람을 공정하게 대우
2. **Reliability & Safety (신뢰성 및 안전성)**: 안전하고 신뢰할 수 있게 작동
3. **Privacy & Security (프라이버시 및 보안)**: 개인정보 보호 및 보안 유지
4. **Inclusiveness (포용성)**: 모든 사람에게 힘을 실어주고 참여시킴
5. **Transparency (투명성)**: 이해 가능하고 설명 가능
6. **Accountability (책임성)**: 사람들이 책임을 짐

#### Transparency Notes (투명성 노트)

**개요:**
- **시작**: 2019년부터 발표
- **수량**: **40개 Transparency Notes** 발표 (2025년 기준)
- **대상**: 외부 고객 또는 파트너에게 제공되는 플랫폼 서비스

**목적:**
이해관계자가 시스템을 이해할 수 있도록 플랫폼 서비스에 대한 주요 정보 포함

**내용:**
- 시스템 목적 및 의도된 사용
- 시스템 작동 방식
- 제한 사항 및 알려진 문제
- 책임 있는 배포 권장사항

#### Responsible AI Transparency Report

**2025 보고서 하이라이트:**
- **두 번째 연례 보고서** 발표
- AI 기술 구축에 대한 지속적인 헌신 강조
- 투명성 및 책임성에 대한 Microsoft의 접근법 문서화

#### 내부 거버넌스 도구

**Workflow Tool:**
- Responsible AI Standard에 명시된 다양한 요구사항을 중앙화하도록 설계된 내부 워크플로우 도구 출시
- 검토의 일부로 책임 있는 AI 문서화 지원

#### Azure Machine Learning Transparency Features

**Responsible AI Dashboard:**
- **Model Interpretability (모델 해석 가능성)**: 모델 예측에 대한 인간이 이해 가능한 설명 생성
- **Counterfactual What-If (반사실적 가정)**: "만약 이 특징이 다르다면 예측이 어떻게 달라질까?" 분석

**기능:**
- 모델 결정에 대한 투명성 제공
- 이해관계자가 모델 행동 이해 지원
- 공정성 및 편향 평가 지원

#### 리소스

- **Transparency Report**: https://www.microsoft.com/en-us/corporate-responsibility/responsible-ai-transparency-report/
- **Responsible AI Principles**: https://www.microsoft.com/en-us/ai/principles-and-approach
- **Azure ML Documentation**: https://learn.microsoft.com/en-us/azure/machine-learning/concept-responsible-ai

---

## 5. 통합 적용 가이드

### 5.1 AI Risk & Compliance 통합 프레임워크

#### End-to-End 접근법

**1단계: Risk Taxonomy 수립**
- NIST AI RMF 또는 ISO/IEC 23894 기반 조직 맞춤형 리스크 분류
- 4대 리스크 카테고리 (Technical, Operational, Ethical, Legal) 정의

**2단계: Compliance Mapping**
- 적용 가능한 규제 식별 (EU AI Act, GDPR, ISO 42001, 한국 AI Framework Act 등)
- 각 규제 요구사항을 조직 프로세스에 매핑

**3단계: Fairness & Bias Assessment**
- 보호 속성 및 관련 리스크 식별
- 적절한 Fairness 메트릭 선택 (Demographic Parity, Equal Opportunity, Equalized Odds)
- IBM AIF360 또는 Microsoft Fairlearn 활용

**4단계: Model Governance 구축**
- Stage-Gate 프로세스 수립
- Model Card 표준화
- Drift Detection 및 모니터링 체계 구축

**5단계: 지속적 모니터링 및 개선**
- 정기적 리스크 재평가
- 규제 변화 추적 및 대응
- Fairness 및 성능 메트릭 모니터링
- Model Card 업데이트

### 5.2 High-Risk AI Systems을 위한 체크리스트

**EU AI Act 준수 체크리스트:**

- [ ] 시스템이 High-Risk로 분류되는지 확인 (Article 6)
- [ ] Risk Management System 구축
- [ ] 데이터 품질 보장 (관련성, 대표성, 오류 없음)
- [ ] 기술 문서 작성 (Technical Documentation)
- [ ] 자동 기록 유지(Record-Keeping) 시스템 구현
- [ ] Human Oversight 메커니즘 설계
- [ ] 투명성 요구사항 충족
- [ ] 정확성, 견고성, 사이버 보안 검증

**GDPR Article 22 준수 체크리스트:**

- [ ] 순수 자동화 의사결정(Solely Automated) 여부 확인
- [ ] 법적 효력 또는 유사한 중대 영향 평가
- [ ] 예외 조건 충족 (Contract, Legal, Consent) 확인
- [ ] Meaningful Human Review 프로세스 구현
- [ ] 데이터 주체 권리 보장 (Human Intervention, Express View, Contest)
- [ ] DPIA (Data Protection Impact Assessment) 수행
- [ ] 특별 범주 데이터 사용 시 추가 보호조치

**ISO/IEC 42001 준비 체크리스트:**

- [ ] AI 관리 시스템(AIMS) 범위 정의
- [ ] AI 정책 및 목표 수립
- [ ] 리스크 평가 및 완화 계획
- [ ] 데이터 거버넌스 프레임워크 구축
- [ ] 내부 감사 수행
- [ ] 지속적 개선 프로세스 수립
- [ ] 인증 기관 선정 및 외부 감사 준비

### 5.3 Fairness-Aware Model Development 프로세스

**1. 설계 단계**
- 보호 속성 및 관련 리스크 식별
- 적절한 Fairness 메트릭 선택
- Fairness 목표 및 허용 임계값 정의

**2. 데이터 준비 단계**
- 데이터 대표성 검증
- Selection Bias, Representation Bias 탐지
- Pre-processing Bias Mitigation (예: Reweighing, Disparate Impact Remover)

**3. 모델 훈련 단계**
- In-processing Bias Mitigation (예: Adversarial De-biasing, Meta-Fair Classifier)
- Fairness Constraints 적용 (Fairlearn Reduction Algorithms)

**4. 모델 평가 단계**
- 그룹별 성능 메트릭 평가 (Accuracy, Precision, Recall)
- Fairness 메트릭 평가 (Demographic Parity, Equal Opportunity, Equalized Odds)
- Trade-off 분석 (Performance vs Fairness)

**5. 배포 후 단계**
- Post-processing Bias Mitigation (예: Reject Option Classification, Equalized Odds Post-processing)
- 지속적 Fairness 모니터링
- Model Card 작성 및 공유

### 5.4 Model Card 작성 Best Practices

**핵심 원칙:**

1. **명확성 (Clarity)**
   - 기술적 및 비기술적 청중 모두 이해 가능하도록 작성
   - 전문 용어 최소화 또는 설명 추가

2. **완전성 (Completeness)**
   - 모든 필수 섹션 포함 (Model Details, Intended Use, Metrics, Training Data, Evaluation Data, Ethical Considerations, Caveats)
   - 알려진 한계 명시

3. **정직성 (Honesty)**
   - 모델의 한계 및 알려진 문제 솔직히 기술
   - 과대 광고 피하기

4. **업데이트 (Currency)**
   - 모델 버전 변경 시 Model Card 업데이트
   - 새로운 발견 또는 이슈 발생 시 신속히 반영

5. **접근성 (Accessibility)**
   - 공개적으로 접근 가능한 위치에 게시 (예: GitHub, 모델 저장소)
   - 다양한 포맷 제공 (PDF, HTML, Markdown)

---

## 6. 주요 출처 및 참고 자료

### AI Risk Taxonomy

**NIST AI RMF:**
- [AI Risk Management Framework | NIST](https://www.nist.gov/itl/ai-risk-management-framework)
- [NIST AI 100-1 Artificial Intelligence Risk Management Framework (AI RMF 1.0)](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
- [NIST AI Risk Management Framework: A tl;dr | Wiz](https://www.wiz.io/academy/nist-ai-risk-management-framework)
- [NIST AI RMF Playbook | NIST](https://www.nist.gov/itl/ai-risk-management-framework/nist-ai-rmf-playbook)

**ISO/IEC 23894:**
- [ISO/IEC 23894:2023 - AI — Guidance on risk management](https://www.iso.org/standard/77304.html)
- [ISO/IEC 23894: AI Risk Management Standard Explained - Mindgard](https://mindgard.ai/blog/iso-iec-23894-ai-risk-management-standard)
- [ISO 23894 Explained: AI Risk Management Made Simple](https://stendard.com/en-sg/blog/iso-23894/)
- [Beyond ISO 42001: The Role of ISO/IEC 23894 in AI Risk Management | Medium](https://medium.com/@mukherjee.amitav/beyond-iso-42001-the-role-of-iso-iec-23894-in-ai-risk-management-7c4f3036544f)

**AI Risk Taxonomy:**
- [AI Risk Categorization Decoded (AIR 2024)](https://arxiv.org/html/2406.17864v1)
- [The MIT AI Risk Repository](https://airisk.mit.edu/)
- [Draft - Taxonomy of AI Risk October 15, 2021 | NIST](https://www.nist.gov/document/draft-taxonomy-ai-risk-october-15-2021)
- [AI Risk Atlas: Taxonomy and Tooling for Navigating AI Risks and Resources](https://arxiv.org/pdf/2503.05780)

**Risk Assessment:**
- [AI Risk Assessment Framework: A Step-by-Step Guide](https://www.sentinelone.com/cybersecurity-101/data-and-ai/ai-risk-assessment-framework/)
- [Learn how to assess the risk of AI systems | AWS](https://aws.amazon.com/blogs/machine-learning/learn-how-to-assess-risk-of-ai-systems/)
- [Risk Assessment Matrix: Templates and Examples - Sembly AI](https://www.sembly.ai/blog/risk-assessment-matrix-templates-and-examples/)

### AI 규제 및 컴플라이언스

**EU AI Act:**
- [High-level summary of the AI Act | EU Artificial Intelligence Act](https://artificialintelligenceact.eu/high-level-summary/)
- [AI Act | Shaping Europe's digital future](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)
- [EU AI Act: first regulation on artificial intelligence | European Parliament](https://www.europarl.europa.eu/topics/en/article/20230601STO93804/eu-ai-act-first-regulation-on-artificial-intelligence)
- [A guide to high-risk AI systems under the EU AI Act](https://www.pinsentmasons.com/out-law/guides/guide-to-high-risk-ai-systems-under-the-eu-ai-act)

**ISO/IEC 42001:**
- [ISO/IEC 42001:2023 - AI management systems](https://www.iso.org/standard/42001)
- [ISO/IEC 42001 Certification: AI Management System | DNV](https://www.dnv.com/services/iso-iec-42001-artificial-intelligence-ai--250876/)
- [ISO/IEC 42001: a new standard for AI governance | KPMG](https://kpmg.com/ch/en/insights/artificial-intelligence/iso-iec-42001.html)
- [ISO 42001 - AI Management System | BSI](https://www.bsigroup.com/en-US/products-and-services/standards/iso-42001-ai-management-system/)

**GDPR Article 22:**
- [Art. 22 GDPR – Automated individual decision-making, including profiling](https://gdpr-info.eu/art-22-gdpr/)
- [Rights related to automated decision making including profiling | ICO](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/individual-rights/rights-related-to-automated-decision-making-including-profiling/)
- [AI and Article 22: The need for meaningful human review](https://www.dpocentre.com/ai-and-article-22-the-need-for-meaningful-human-review/)

**Korea AI Regulation:**
- [South Korea's New AI Framework Act | FPF](https://fpf.org/blog/south-koreas-new-ai-framework-act-a-balancing-act-between-innovation-and-regulation/)
- [AI Watch: Global regulatory tracker - South Korea | White & Case](https://www.whitecase.com/insight-our-thinking/ai-watch-global-regulatory-tracker-south-korea)
- [South Korea's New AI law: What it Means for Organizations | OneTrust](https://www.onetrust.com/blog/south-koreas-new-ai-law-what-it-means-for-organizations-and-how-to-prepare/)

### Fairness & Bias Assessment

**Fairness Metrics:**
- [Fairness Metrics - Demographic Parity, Equalized Odds - GeeksforGeeks](https://www.geeksforgeeks.org/artificial-intelligence/fairness-metrics-demographic-parity-equalized-odds/)
- [Common fairness metrics - Fairlearn](https://fairlearn.org/main/user_guide/assessment/common_fairness_metrics.html)
- [Fairness: Equality of opportunity | Google ML](https://developers.google.com/machine-learning/crash-course/fairness/equality-of-opportunity)
- [Fairness Metrics in AI—Your Step-by-Step Guide](https://shelf.io/blog/fairness-metrics-in-ai/)

**IBM AI Fairness 360:**
- [AI Fairness 360](https://ai-fairness-360.org/)
- [AI Fairness 360: An extensible toolkit | IBM Research](https://research.ibm.com/publications/ai-fairness-360-an-extensible-toolkit-for-detecting-and-mitigating-algorithmic-bias)
- [GitHub - Trusted-AI/AIF360](https://github.com/Trusted-AI/AIF360)

**Microsoft Fairlearn:**
- [Machine learning fairness - Azure ML | Microsoft Learn](https://learn.microsoft.com/en-us/azure/machine-learning/concept-fairness-ml)
- [Fairlearn: A toolkit for assessing and improving fairness in AI | Microsoft Research](https://www.microsoft.com/en-us/research/publication/fairlearn-a-toolkit-for-assessing-and-improving-fairness-in-ai/)
- [Fairlearn](https://fairlearn.org/)

**AI Bias Types:**
- [Bias in AI | Chapman University](https://www.chapman.edu/ai/bias-in-ai.aspx)
- [Algorithmic Bias: Examples and Tools | Arize AI](https://arize.com/blog-course/algorithmic-bias-examples-tools/)
- [What Is Algorithmic Bias? | IBM](https://www.ibm.com/think/topics/algorithmic-bias)
- [AI Bias: 14 Real AI Bias Examples & Mitigation Guide](https://www.crescendo.ai/blog/ai-bias-examples-mitigation-guide)

### Model Governance & Documentation

**Google Model Cards:**
- [Google Model Cards](https://modelcards.withgoogle.com/)
- [Introducing the Model Card Toolkit | Google Research](https://research.google/blog/introducing-the-model-card-toolkit-for-easier-model-transparency-reporting/)
- [Model Card Toolkit | TensorFlow](https://www.tensorflow.org/responsible_ai/model_card_toolkit/guide)
- [Model Cards for Model Reporting | Google Research](https://research.google/pubs/pub48120/)

**Stage-Gate Process:**
- [The Stage-Gate Model: An Overview | Stage-Gate International](https://www.stage-gate.com/blog/the-stage-gate-model-an-overview/)
- [Stage Gate Project Management Made Simple | OCM Solution](https://www.ocmsolution.com/stage-gate-process/)
- [Phase-gate process - Wikipedia](https://en.wikipedia.org/wiki/Phase-gate_process)

**Model Drift:**
- [What is data drift in ML | Evidently AI](https://www.evidentlyai.com/ml-in-production/data-drift)
- [Understanding Data Drift and Model Drift | DataCamp](https://www.datacamp.com/tutorial/understanding-data-drift-model-drift)
- [What is concept drift in ML | Evidently AI](https://www.evidentlyai.com/ml-in-production/concept-drift)
- [What Is Model Drift? | IBM](https://www.ibm.com/think/topics/model-drift)
- [Model Drift & Machine Learning | Arize](https://arize.com/model-drift/)

**Microsoft Responsible AI:**
- [Responsible AI Transparency Report | Microsoft](https://www.microsoft.com/en-us/corporate-responsibility/responsible-ai-transparency-report/)
- [Responsible AI Principles and Approach | Microsoft AI](https://www.microsoft.com/en-us/ai/principles-and-approach)
- [What is Responsible AI - Azure ML | Microsoft Learn](https://learn.microsoft.com/en-us/azure/machine-learning/concept-responsible-ai)

---

## 7. 결론 및 권장사항

### 7.1 핵심 요약

**AI Risk Taxonomy:**
- NIST AI RMF와 ISO/IEC 23894는 AI 리스크 관리를 위한 글로벌 표준
- 4대 리스크 분류 (Technical, Operational, Ethical, Legal)로 체계적 관리
- Likelihood × Impact 매트릭스로 리스크 우선순위화 및 완화 전략 수립

**AI 규제 및 컴플라이언스:**
- EU AI Act는 세계 최초의 포괄적 AI 규제, 리스크 기반 접근법 채택
- ISO/IEC 42001은 인증 가능한 AI 관리 시스템 표준
- GDPR Article 22는 자동화된 의사결정에 대한 강력한 보호조치 요구
- 한국 AI Framework Act는 아시아-태평양 최초의 포괄적 AI 법안

**Fairness & Bias Assessment:**
- Demographic Parity, Equal Opportunity, Equalized Odds 등 다양한 Fairness 메트릭 존재
- IBM AI Fairness 360과 Microsoft Fairlearn은 편향 탐지 및 완화를 위한 강력한 오픈소스 툴킷
- Pre-processing, In-processing, Post-processing 단계에서 Bias 완화 가능

**Model Governance & Documentation:**
- Google Model Cards는 모델 투명성 및 문서화를 위한 산업 표준
- Stage-Gate 프로세스는 모델 수명주기 전반의 거버넌스 및 승인 워크플로우 제공
- Model Drift 탐지는 프로덕션 모델 성능 유지의 핵심

### 7.2 실무 적용 권장사항

**1. 리스크 관리 우선순위화**
- NIST AI RMF 또는 ISO/IEC 23894 기반 조직 맞춤형 리스크 프레임워크 수립
- High-Impact AI 시스템에 대한 엄격한 리스크 평가 및 완화 조치
- 정기적 리스크 재평가 (최소 연 2회)

**2. 규제 준수 프로그램 구축**
- 적용 가능한 모든 규제 매핑 (EU AI Act, GDPR, ISO 42001, 한국 AI Framework Act 등)
- 컴플라이언스 체크리스트 및 승인 워크플로우 수립
- ISO/IEC 42001 인증 고려 (글로벌 신뢰성 확보)

**3. Fairness-First 모델 개발**
- 프로젝트 초기 단계부터 Fairness 고려사항 통합
- 적절한 Fairness 메트릭 선택 및 목표 설정
- IBM AIF360 또는 Microsoft Fairlearn 활용한 지속적 Bias 모니터링

**4. 투명성 및 문서화 강화**
- 모든 프로덕션 모델에 대한 Model Card 작성 필수화
- Stage-Gate 프로세스로 모델 승인 워크플로우 표준화
- Drift Detection 및 모니터링 체계 구축

**5. 지속적 학습 및 개선**
- 규제 변화 추적 및 신속 대응
- 산업 베스트 프랙티스 벤치마킹
- 내부 교육 프로그램 운영 (AI 윤리, 리스크 관리, Fairness)

### 7.3 향후 전망

**규제 환경:**
- 더 많은 국가 및 지역이 AI 규제 도입 예상
- ISO 표준의 지속적 발전 및 확대
- 산업별 특화 규제 출현 (금융, 의료, 공공 등)

**기술 발전:**
- 자동화된 Bias Detection 및 Mitigation 도구 발전
- Explainable AI (XAI) 기술 통합
- Federated Learning 및 Privacy-Preserving AI 확산

**조직적 변화:**
- AI 거버넌스의 C-level 우선순위화
- AI 윤리 위원회 및 CoE 확대
- 제3자 AI Audit 수요 증가

---

**문서 버전**: 1.0
**최종 업데이트**: 2025-11-23
**작성자**: AI Research Team
