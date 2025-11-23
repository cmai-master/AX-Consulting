# 웹 리서치 항목 목록

> **목적**: 컨설팅 자산 110개 문서 작성을 위한 웹 기반 정보 수집 계획
> **작성일**: 2025-11-23
> **총 리서치 항목**: 80개 (High: 35개, Medium: 30개, Low: 15개)

---

## 📋 목차

1. [우선순위 개요](#우선순위-개요)
2. [High Priority - 즉시 리서치](#high-priority---즉시-리서치)
3. [Medium Priority - 2차 리서치](#medium-priority---2차-리서치)
4. [Low Priority - 추가 리서치](#low-priority---추가-리서치)
5. [리서치 방법론](#리서치-방법론)

---

## 우선순위 개요

| Priority | 항목 수 | 예상 소요 | 목적 |
|----------|---------|-----------|------|
| **High** | 35개 | 40-60시간 | 핵심 방법론 및 기술 문서 작성 기반 |
| **Medium** | 30개 | 30-40시간 | 템플릿 및 가이드 작성 기반 |
| **Low** | 15개 | 20-30시간 | 참고 자료 및 보완 정보 |
| **Total** | **80개** | **90-130시간** | |

---

## HIGH PRIORITY - 즉시 리서치

### 🎯 1. RAG (Retrieval-Augmented Generation) 시스템

#### 1.1 RAG 아키텍처 및 설계 패턴
- **리서치 내용**:
  - RAG 시스템 전체 아키텍처 (Naive RAG, Advanced RAG, Modular RAG)
  - 구성 요소별 설계 패턴
  - End-to-end 파이프라인 구조

- **주요 소스**:
  - Anthropic 공식 문서 및 Cookbook
  - LangChain RAG 가이드
  - arXiv 최신 RAG 논문 (2024-2025)
  - Pinecone, Weaviate 기술 블로그

- **관련 문서**:
  - A4-1: RAG System Design Methodology
  - C2-2: RAG System Implementation Guide
  - B3-3: Context Model Canvas

- **예상 시간**: 6-8시간
- **산출물**: RAG 아키텍처 패턴 가이드, 설계 의사결정 트리

#### 1.2 Chunking 전략
- **리서치 내용**:
  - Fixed-size chunking
  - Semantic chunking
  - Recursive chunking
  - Context-aware chunking
  - 각 전략의 장단점 및 적용 시나리오

- **주요 소스**:
  - LlamaIndex 문서
  - LangChain Text Splitters
  - Greg Kamradt의 Chunking 연구
  - Unstructured.io 블로그

- **관련 문서**:
  - A4-1: RAG System Design Methodology
  - C2-2: RAG System Implementation Guide
  - D2-1: Technical Best Practices

- **예상 시간**: 3-4시간
- **산출물**: Chunking 전략 비교표, 의사결정 플로우차트

#### 1.3 Embedding 모델 비교
- **리서치 내용**:
  - OpenAI (text-embedding-3-small/large)
  - Cohere (embed-v3)
  - Voyage AI
  - 오픈소스 모델 (BGE, E5, Instructor)
  - MTEB 벤치마크 결과
  - 모델별 특성 (차원, 다국어, 도메인 특화)

- **주요 소스**:
  - MTEB Leaderboard
  - 각 제공사 공식 문서
  - HuggingFace Model Hub

- **관련 문서**:
  - A4-1: RAG System Design Methodology
  - B3-2: Technology Stack Assessment Matrix
  - D4-1: Technology Landscape

- **예상 시간**: 4-5시간
- **산출물**: Embedding 모델 비교 매트릭스, 선정 가이드

#### 1.4 Vector Database 비교
- **리서치 내용**:
  - Pinecone, Weaviate, Qdrant, Milvus, ChromaDB, Faiss
  - 성능 벤치마크 (QPS, latency, recall)
  - 기능 비교 (필터링, 하이브리드 검색, 스케일링)
  - 가격 비교
  - 배포 옵션 (클라우드, 온프레미스, 하이브리드)

- **주요 소스**:
  - 각 Vector DB 공식 문서
  - VectorDBBench
  - 독립적 벤치마크 리포트

- **관련 문서**:
  - B3-2: Technology Stack Assessment Matrix
  - D4-1: Technology Landscape
  - A3-1: Enterprise AI Platform Reference Architecture

- **예상 시간**: 5-6시간
- **산출물**: Vector DB 비교표, 선정 의사결정 트리

#### 1.5 Retrieval 전략 및 최적화
- **리서치 내용**:
  - Similarity search (cosine, euclidean, dot product)
  - Hybrid search (keyword + semantic)
  - Re-ranking 기법
  - Query transformation (HyDE, Multi-query, Step-back)
  - Contextual compression
  - Maximum Marginal Relevance (MMR)

- **주요 소스**:
  - LangChain Retrieval 가이드
  - Anthropic Contextual Retrieval
  - Cohere Re-ranking 문서

- **관련 문서**:
  - A4-1: RAG System Design Methodology
  - C2-2: RAG System Implementation Guide
  - D2-1: Technical Best Practices

- **예상 시간**: 4-5시간
- **산출물**: Retrieval 전략 플레이북, 최적화 체크리스트

#### 1.6 RAG Evaluation 메트릭
- **리서치 내용**:
  - Retrieval 메트릭 (Precision@k, Recall@k, MRR, NDCG)
  - Generation 메트릭 (Faithfulness, Answer Relevancy, Context Precision/Recall)
  - End-to-end 메트릭
  - RAGAS, TruLens, DeepEval 프레임워크

- **주요 소스**:
  - RAGAS 문서
  - TruLens 가이드
  - arXiv RAG evaluation 논문

- **관련 문서**:
  - A5-2: AI System Evaluation Framework
  - B4-3: Evaluation Dataset Template
  - C2-2: RAG System Implementation Guide

- **예상 시간**: 4-5시간
- **산출물**: RAG 평가 메트릭 가이드, 평가 프로토콜

---

### 🤖 2. Agent & Multi-Agent Systems

#### 2.1 Agent 아키텍처 패턴
- **리서치 내용**:
  - ReAct (Reasoning + Acting)
  - Plan-and-Execute
  - Reflection/Self-Critique
  - Tree of Thoughts
  - Agent 구성 요소 (Memory, Tools, Planning, Execution)

- **주요 소스**:
  - Anthropic Agent 가이드
  - LangChain Agents
  - arXiv Agent 논문

- **관련 문서**:
  - A1-3: Agent Orchestration Framework
  - B3-4: Agent Design Canvas
  - C2-3: Agent Development Guide

- **예상 시간**: 5-6시간
- **산출물**: Agent 패턴 카탈로그, 설계 가이드

#### 2.2 Multi-Agent Orchestration
- **리서چ  내용**:
  - Multi-agent 패턴 (Hierarchical, Sequential, Parallel, Network)
  - Communication protocols
  - Coordination strategies
  - Conflict resolution
  - LangGraph, CrewAI, AutoGen 비교

- **주요 소스**:
  - LangGraph 문서
  - CrewAI 문서
  - Microsoft AutoGen
  - Multi-agent 연구 논문

- **관련 문서**:
  - A1-3: Agent Orchestration Framework
  - C2-3: Agent Development Guide
  - D2-1: Technical Best Practices

- **예상 시간**: 6-7시간
- **산출물**: Multi-agent 패턴 가이드, 프레임워크 비교표

#### 2.3 Agent Memory Architecture
- **리서치 내용**:
  - Short-term memory (conversation buffer, window)
  - Long-term memory (vector store, knowledge graph)
  - Semantic memory vs Episodic memory
  - Memory retrieval strategies
  - Memory management 패턴

- **주요 소스**:
  - LangChain Memory
  - Mem0 (memory framework)
  - Agent memory 연구 논문

- **관련 문서**:
  - A1-3: Agent Orchestration Framework
  - B3-4: Agent Design Canvas
  - C2-3: Agent Development Guide

- **예상 시간**: 3-4시간
- **산출물**: Memory 아키텍처 패턴, 구현 가이드

#### 2.4 Tool Integration & Function Calling
- **리서치 내용**:
  - Function calling 메커니즘
  - Tool definition 베스트 프랙티스
  - Error handling
  - Tool orchestration
  - Security considerations

- **주요 소스**:
  - Anthropic Tool Use 가이드
  - OpenAI Function Calling
  - LangChain Tools

- **관련 문서**:
  - B3-4: Agent Design Canvas
  - C2-3: Agent Development Guide
  - D2-1: Technical Best Practices

- **예상 시간**: 3-4시간
- **산출물**: Tool Integration 가이드, 베스트 프랙티스

---

### 🏗️ 3. Enterprise AI Platform & Architecture

#### 3.1 Enterprise AI Platform 참조 아키텍처
- **리서치 내용**:
  - Layered architecture (Data, Model, Application, User)
  - 필수 컴포넌트 (Model Serving, Vector Store, Orchestration)
  - 선택 컴포넌트 (Feature Store, Experiment Tracking)
  - Integration patterns
  - Security layer

- **주요 소스**:
  - AWS AI/ML Reference Architecture
  - Google Cloud AI Platform
  - Azure AI Platform
  - Databricks AI Platform

- **관련 문서**:
  - A3-1: Enterprise AI Platform Reference Architecture
  - C1-3: Enterprise AI Platform Playbook
  - B3-2: Technology Stack Assessment Matrix

- **예상 시간**: 6-8시간
- **산출물**: 참조 아키텍처 다이어그램, 컴포넌트 가이드

#### 3.2 Semantic Layer & Knowledge Graph
- **리서치 내용**:
  - Semantic layer 개념 및 설계
  - Ontology 모델링 기법
  - Knowledge graph 구축 방법론
  - Graph database (Neo4j, Amazon Neptune, TigerGraph)
  - Query 최적화

- **주요 소스**:
  - Neo4j 문서 및 Graph Academy
  - W3C Semantic Web 표준
  - Knowledge Graph 논문

- **관련 문서**:
  - A1-2: Context Engineering Methodology
  - C2-1: Context Engineering Implementation Guide
  - B3-3: Context Model Canvas

- **예상 시간**: 6-7시간
- **산출물**: Semantic Layer 설계 가이드, KG 모델링 패턴

#### 3.3 MLOps 파이프라인 및 도구
- **리서치 내용**:
  - MLOps 단계 (Data, Training, Serving, Monitoring)
  - CI/CD for ML
  - Model versioning & registry
  - Experiment tracking
  - MLflow, Kubeflow, Weights & Biases 비교

- **주요 소스**:
  - MLOps 커뮤니티 가이드
  - Google MLOps Maturity Model
  - 각 도구 공식 문서

- **관련 문서**:
  - A3-2: MLOps Reference Architecture
  - C2-4: MLOps Pipeline Setup Guide
  - D4-1: Technology Landscape

- **예상 시간**: 5-6시간
- **산출물**: MLOps 파이프라인 가이드, 도구 비교표

#### 3.4 Model Serving & Deployment 패턴
- **리서치 내용**:
  - Deployment 패턴 (Blue-Green, Canary, A/B)
  - Scaling strategies
  - API Gateway patterns
  - Rate limiting & throttling
  - Cost optimization

- **주요 소스**:
  - AWS SageMaker
  - Kubernetes for ML
  - Model serving 프레임워크 (TorchServe, TensorFlow Serving)

- **관련 문서**:
  - A3-1: Enterprise AI Platform Reference Architecture
  - C2-4: MLOps Pipeline Setup Guide
  - D2-1: Technical Best Practices

- **예상 시간**: 4-5시간
- **산출물**: Deployment 패턴 가이드, 최적화 체크리스트

---

### 📊 4. Prompt Engineering & Optimization

#### 4.1 Prompt Engineering 기법
- **리서치 내용**:
  - Zero-shot, Few-shot, Many-shot
  - Chain-of-Thought (CoT)
  - Tree of Thoughts
  - ReAct prompting
  - System prompts vs User prompts
  - Prompt 구조 및 템플릿

- **주요 소스**:
  - Anthropic Prompt Engineering Guide
  - OpenAI Prompt Engineering
  - Prompt Engineering Guide (dair.ai)

- **관련 문서**:
  - A4-2: Prompt Engineering Framework
  - B4-4: Prompt Library Template
  - D2-1: Technical Best Practices

- **예상 시간**: 4-5시간
- **산출물**: Prompt 패턴 카탈로그, 작성 가이드

#### 4.2 Prompt Optimization 프로세스
- **리서치 내용**:
  - Prompt iteration 방법론
  - A/B testing for prompts
  - Prompt versioning
  - Performance 측정
  - DSPy, PromptPerfect 등 자동화 도구

- **주요 소스**:
  - DSPy 프레임워크
  - Prompt optimization 연구
  - 실무 케이스 스터디

- **관련 문서**:
  - A4-2: Prompt Engineering Framework
  - B4-4: Prompt Library Template
  - C2-3: Agent Development Guide

- **예상 시간**: 3-4시간
- **산출물**: Optimization 프로세스 가이드, 템플릿

---

### 🎯 5. AI Maturity & Assessment

#### 5.1 AI Maturity Models
- **리서치 내용**:
  - Gartner AI Maturity Model
  - McKinsey AI Maturity
  - Forrester AI Maturity
  - 5-level maturity framework
  - 평가 차원 (Strategy, Data, Technology, People, Process, Governance)

- **주요 소스**:
  - Gartner 리포트
  - McKinsey Analytics
  - Forrester Research
  - 학술 논문

- **관련 문서**:
  - A2-1: AI Maturity Model
  - B1-1: AI Maturity Assessment Questionnaire
  - C1-1: AI Strategy & Readiness Playbook

- **예상 시간**: 5-6시간
- **산출물**: Maturity Model 프레임워크, 평가 기준

#### 5.2 Use Case Prioritization 프레임워크
- **리서치 내용**:
  - Value vs Effort 매트릭스
  - RICE (Reach, Impact, Confidence, Effort)
  - Weighted scoring models
  - Risk-adjusted prioritization
  - AI 특화 평가 기준 (데이터 가용성, 기술 성숙도)

- **주요 소스**:
  - Product management 프레임워크
  - AI 전략 컨설팅 방법론
  - McKinsey, BCG 케이스

- **관련 문서**:
  - A2-2: Use Case Prioritization Framework
  - B2-2: Use Case Prioritization Scorecard
  - C3-2: Use Case Prioritization Guide

- **예상 시간**: 3-4시간
- **산출물**: Prioritization 프레임워크, 스코어카드

---

### ⚠️ 6. AI Risk & Compliance

#### 6.1 AI Risk Taxonomy
- **리서치 내용**:
  - NIST AI Risk Management Framework
  - AI 리스크 분류 (Technical, Operational, Ethical, Legal)
  - Likelihood × Impact 평가
  - Risk mitigation strategies

- **주요 소스**:
  - NIST AI RMF
  - ISO/IEC 23894 (AI Risk Management)
  - EU AI Act

- **관련 문서**:
  - A2-3: Risk Assessment Framework
  - B6-1: Risk Register
  - B6-2: Risk Assessment Worksheet
  - C3-3: Risk Assessment Execution Guide

- **예상 시간**: 5-6시간
- **산출물**: Risk Taxonomy, 평가 프레임워크

#### 6.2 AI 규제 및 컴플라이언스
- **리서치 내용**:
  - EU AI Act (High-risk systems, prohibited practices)
  - GDPR (AI 관련 조항)
  - 한국 개인정보보호법
  - ISO/IEC 42001 (AI Management System)
  - 산업별 규제 (금융, 의료, 공공)

- **주요 소스**:
  - EU 공식 문서
  - ISO 표준
  - 금융위원회, 개인정보보호위원회 가이드라인

- **관련 문서**:
  - B6-3: Compliance Checklist
  - C1-6: AI Risk & Compliance Playbook
  - D4-1: Technology Landscape

- **예상 시간**: 6-8시간
- **산출물**: 규제 요구사항 매핑, 컴플라이언스 체크리스트

#### 6.3 Fairness & Bias Assessment
- **리서치 내용**:
  - Bias 유형 (Selection, Measurement, Algorithm)
  - Protected attributes
  - Fairness 메트릭 (Demographic Parity, Equal Opportunity, Equalized Odds)
  - Bias detection 도구 (AI Fairness 360, Fairlearn)
  - Mitigation 기법

- **주요 소스**:
  - IBM AI Fairness 360
  - Microsoft Fairlearn
  - Google PAIR (People + AI Research)
  - 학술 논문

- **관련 문서**:
  - B6-5: Fairness Assessment Template
  - C1-6: AI Risk & Compliance Playbook
  - D2-1: Technical Best Practices

- **예상 시간**: 4-5시간
- **산출물**: Fairness 평가 가이드, Mitigation 플레이북

#### 6.4 Model Governance & Documentation
- **리서치 내용**:
  - Model Card 표준 (Google)
  - Model lifecycle management
  - Stage-gate 프로세스
  - Approval workflow
  - Model drift detection

- **주요 소스**:
  - Google Model Cards
  - Microsoft Responsible AI
  - MLOps 거버넌스 프레임워크

- **관련 문서**:
  - A4-3: Model Governance Methodology
  - B5-5: Model Card Template
  - B5-3: Stage-gate Review Checklist

- **예상 시간**: 4-5시간
- **산출물**: Governance 프로세스, Model Card 템플릿

---

### 💰 7. ROI & Business Value

#### 7.1 AI 프로젝트 ROI 계산 모델
- **리서치 내용**:
  - Cost structure (인프라, 인력, 라이선스, 데이터)
  - Benefit 측정 (비용 절감, 매출 증대, 리스크 감소)
  - ROI 계산 공식
  - Payback period
  - NPV, IRR
  - 민감도 분석

- **주요 소스**:
  - McKinsey AI ROI 연구
  - Gartner TCO 모델
  - AWS, GCP 비용 계산기

- **관련 문서**:
  - A5-1: AI Project ROI Model
  - B2-4: Investment Plan & Budget Template
  - E2-3: ROI Calculator

- **예상 시간**: 4-5시간
- **산출물**: ROI 계산 모델, 템플릿

#### 7.2 AI 투자 벤치마크
- **리서치 내용**:
  - 산업별 AI 투자 현황
  - 프로젝트 규모별 비용 범위
  - 평균 ROI 데이터
  - 성공률 통계

- **주요 소스**:
  - Gartner, Forrester 리포트
  - McKinsey State of AI
  - 산업 리포트

- **관련 문서**:
  - A5-1: AI Project ROI Model
  - E2-2: Pricing Guide & Calculator

- **예상 시간**: 3-4시간
- **산출물**: 벤치마크 데이터, 비교 자료

---

### 🎨 8. LLM Platforms & Models

#### 8.1 LLM 플랫폼 비교
- **리서치 내용**:
  - Claude (Sonnet, Opus, Haiku)
  - GPT-4, GPT-4 Turbo, GPT-4o
  - Gemini (Pro, Ultra)
  - 오픈소스 (Llama, Mistral, Qwen)
  - 모델별 특성 (context window, capabilities, pricing)

- **주요 소스**:
  - Anthropic, OpenAI, Google 공식 문서
  - Artificial Analysis 벤치마크
  - HuggingFace Leaderboards

- **관련 문서**:
  - D4-1: Technology Landscape
  - B3-2: Technology Stack Assessment Matrix

- **예상 시간**: 4-5시간
- **산출물**: LLM 비교표, 선정 가이드

#### 8.2 Context Window 최적화
- **리서치 내용**:
  - Long context handling
  - Context compression 기법
  - Sliding window
  - Prompt caching
  - Cost optimization

- **주요 소스**:
  - Anthropic Prompt Caching
  - LongLLMLingua
  - Context optimization 연구

- **관련 문서**:
  - D2-1: Technical Best Practices
  - A4-2: Prompt Engineering Framework

- **예상 시간**: 3-4시간
- **산출물**: Context 최적화 가이드

---

### 📈 9. Monitoring & Observability

#### 9.1 LLM Observability 플랫폼
- **리서치 내용**:
  - LangSmith, Arize, WhyLabs, Helicone 비교
  - Tracing & debugging
  - Performance monitoring
  - Cost tracking
  - User feedback 수집

- **주요 소스**:
  - 각 플랫폼 공식 문서
  - LLMOps 가이드

- **관련 문서**:
  - A3-2: MLOps Reference Architecture
  - D4-1: Technology Landscape

- **예상 시간**: 4-5시간
- **산출물**: Observability 플랫폼 비교, 구축 가이드

#### 9.2 Model Performance Monitoring
- **리서치 내용**:
  - Drift detection (data drift, concept drift)
  - Performance degradation
  - Alerting strategies
  - Retraining triggers

- **주요 소스**:
  - MLOps 모니터링 가이드
  - Evidently AI, NannyML

- **관련 문서**:
  - A4-3: Model Governance Methodology
  - C2-4: MLOps Pipeline Setup Guide

- **예상 시간**: 3-4시간
- **산출물**: Monitoring 전략, 구현 가이드

---

### 🏢 10. AI Operating Model & Organization

#### 10.1 AI CoE (Center of Excellence) 모델
- **리서치 내용**:
  - Centralized vs Federated vs Hybrid
  - Hub & Spoke model
  - 각 모델의 장단점
  - 적용 조건 및 전환 경로
  - 성공 사례

- **주요 소스**:
  - McKinsey, BCG 조직 설계 연구
  - Gartner AI CoE 가이드

- **관련 문서**:
  - A3-3: Operating Model Patterns
  - C1-2: AI Operating Model Playbook

- **예상 시간**: 4-5시간
- **산출물**: Operating Model 패턴 가이드

#### 10.2 AI 거버넌스 구조
- **리서치 내용**:
  - Governance committee 구조
  - 의사결정 권한 (RACI)
  - Policy framework
  - Compliance monitoring

- **주요 소스**:
  - ISO/IEC 38500 (IT Governance)
  - AI 거버넌스 프레임워크

- **관련 문서**:
  - A3-3: Operating Model Patterns
  - B5-2: RACI Matrix Template
  - B5-4: Policy Document Template

- **예상 시간**: 3-4시간
- **산출물**: Governance 구조, 템플릿

---

## MEDIUM PRIORITY - 2차 리서치

### 📝 11. Templates & Standards

#### 11.1 Architecture Decision Record (ADR)
- **리서치 내용**:
  - ADR 표준 포맷 (MADR, Nygard)
  - 작성 가이드
  - 예시

- **주요 소스**:
  - ADR GitHub
  - adr.github.io

- **관련 문서**:
  - B3-1: Architecture Decision Record (ADR)

- **예상 시간**: 2시간
- **산출물**: ADR 템플릿

#### 11.2 API Specification 표준
- **리서치 내용**:
  - OpenAPI/Swagger 3.0
  - API 문서화 베스트 프랙티스
  - Authentication/Authorization
  - Rate limiting 표준

- **주요 소스**:
  - OpenAPI Specification
  - REST API 베스트 프랙티스

- **관련 문서**:
  - B3-5: API Specification Template

- **예상 시간**: 2-3시간
- **산출물**: API Spec 템플릿

#### 11.3 Test Case Documentation
- **리서치 내용**:
  - Test case 작성 표준
  - AI 시스템 테스팅 전략
  - Unit, Integration, E2E 테스트

- **주요 소스**:
  - Software testing 표준
  - ML testing 가이드

- **관련 문서**:
  - B4-2: Test Case Template

- **예상 시간**: 2시간
- **산출물**: Test Case 템플릿

#### 11.4 Technical Documentation 표준
- **리서치 내용**:
  - 기술 문서 구조
  - Diagrams as Code (Mermaid, PlantUML)
  - Versioning 전략

- **주요 소스**:
  - Docs as Code 방법론
  - Technical writing 가이드

- **관련 문서**:
  - B8-2: Technical Documentation Template

- **예상 시간**: 2-3시간
- **산출물**: Documentation 표준

---

### 🚀 12. Project Management & Delivery

#### 12.1 Agile for AI/ML 프로젝트
- **리서치 내용**:
  - AI 프로젝트 특성에 맞는 Agile 적용
  - Sprint 구조
  - Experimentation vs Development
  - Backlog management

- **주요 소스**:
  - Agile for ML
  - Scrum Guide

- **관련 문서**:
  - F1-1: Project Initiation Process
  - B7-1: Project Plan (Gantt Chart)

- **예상 시간**: 3-4시간
- **산출물**: Agile 프로세스 가이드

#### 12.2 Risk & Issue Management
- **리서치 내용**:
  - 프로젝트 리스크 관리
  - Issue tracking
  - Escalation 프로세스

- **주요 소스**:
  - PMI PMBOK
  - 프로젝트 관리 표준

- **관련 문서**:
  - B7-3: Risk & Issue Log

- **예상 시간**: 2-3시간
- **산출물**: Risk Management 프로세스

#### 12.3 Change Management
- **리서치 내용**:
  - Kotter 8-step
  - ADKAR model
  - Stakeholder engagement

- **주요 소스**:
  - Kotter International
  - Prosci ADKAR

- **관련 문서**:
  - F1-2: Kickoff & Stakeholder Alignment
  - B7-4: Change Request Form

- **예상 시간**: 3-4시간
- **산출물**: Change Management 가이드

---

### 🎓 13. Training & Capability Building

#### 13.1 AI 역량 모델
- **리서치 내용**:
  - AI 관련 역할 정의
  - 역할별 필요 스킬
  - 학습 경로

- **주요 소스**:
  - LinkedIn Skills
  - Kaggle Learning Paths
  - 산업 표준

- **관련 문서**:
  - G1-1: AI Roles & Responsibilities
  - G1-2: AI Competency Framework

- **예상 시간**: 3-4시간
- **산출물**: 역량 모델, 스킬 매트릭스

#### 13.2 교육 프로그램 설계
- **리서치 내용**:
  - 성인 학습 이론
  - Hands-on lab 설계
  - Assessment 방법

- **주요 소스**:
  - Instructional design
  - Technical training 베스트 프랙티스

- **관련 문서**:
  - C1-5: AI Capability Building Playbook
  - G2-1: Training Curriculum

- **예상 시간**: 2-3시간
- **산출물**: 프로그램 설계 가이드

---

### 💼 14. Sales & Marketing

#### 14.1 Value Proposition 프레임워크
- **리서치 내용**:
  - Value Proposition Canvas
  - Pain-Solution 매핑
  - Differentiation 전략

- **주요 소스**:
  - Strategyzer
  - Sales methodology

- **관련 문서**:
  - E2-1: Value Proposition Deck
  - C5-1: Sales Conversation Guide

- **예상 시간**: 2-3시간
- **산출물**: Value Prop 프레임워크

#### 14.2 Discovery Question 기법
- **리서치 내용**:
  - SPIN Selling
  - Solution Selling
  - Consultative selling

- **주요 소스**:
  - SPIN Selling (Neil Rackham)
  - 컨설팅 영업 방법론

- **관련 문서**:
  - C5-1: Sales Conversation Guide
  - B1-2: Interview Guide Set

- **예상 시간**: 2-3시간
- **산출물**: Discovery 질문 가이드

#### 14.3 Proposal Writing
- **리서치 내용**:
  - 제안서 구조
  - Storytelling 기법
  - Pricing 전략
  - Win theme

- **주요 소스**:
  - Proposal writing 가이드
  - 컨설팅 제안서 베스트 프랙티스

- **관련 문서**:
  - C5-2: Proposal Development Guide
  - E2-5: Proposal Template

- **예상 시간**: 3-4시간
- **산출물**: Proposal 가이드

#### 14.4 Objection Handling
- **리서치 내용**:
  - 일반적인 objection 유형
  - 대응 전략
  - AI 특화 objections (비용, 데이터, 신뢰)

- **주요 소스**:
  - Sales training 자료
  - AI 영업 케이스

- **관련 문서**:
  - C5-1: Sales Conversation Guide
  - E2-4: Common Objections & Responses

- **예상 시간**: 2-3시간
- **산출물**: Objection Handling 가이드

---

### 🔧 15. Data & Infrastructure

#### 15.1 Data Architecture Patterns
- **리서치 내용**:
  - Data Lake, Lakehouse, Data Mesh
  - Data pipeline 패턴
  - Data governance

- **주요 소스**:
  - Databricks Lakehouse
  - Data Mesh (Zhamak Dehghani)

- **관련 문서**:
  - A3-1: Enterprise AI Platform Reference Architecture
  - B4-1: Data Requirements Sheet

- **예상 시간**: 4-5시간
- **산출물**: Data Architecture 가이드

#### 15.2 Cloud Provider 비교
- **리서치 내용**:
  - AWS AI/ML 서비스
  - GCP AI Platform
  - Azure OpenAI Service
  - 가격 비교

- **주요 소스**:
  - 각 클라우드 공식 문서
  - 독립적 비교 리포트

- **관련 문서**:
  - D4-1: Technology Landscape
  - B3-2: Technology Stack Assessment Matrix

- **예상 시간**: 4-5시간
- **산출물**: Cloud 비교표

#### 15.3 보안 베스트 프랙티스
- **리서치 내용**:
  - AI 시스템 보안 위협
  - Prompt injection 방어
  - Data privacy
  - Access control

- **주요 소스**:
  - OWASP Top 10 for LLM
  - Cloud security 베스트 프랙티스

- **관련 문서**:
  - D2-1: Technical Best Practices
  - F2-2: Security & Privacy Guidelines

- **예상 시간**: 4-5시간
- **산출물**: Security 가이드

---

### 📊 16. Evaluation & Testing

#### 16.1 LLM Evaluation 프레임워크
- **리서치 내용**:
  - Human evaluation
  - Automated evaluation
  - LLM-as-judge
  - Benchmark datasets

- **주요 소스**:
  - Anthropic Evals
  - OpenAI Evals
  - 학술 논문

- **관련 문서**:
  - A5-2: AI System Evaluation Framework
  - B4-3: Evaluation Dataset Template

- **예상 시간**: 4-5시간
- **산출물**: Evaluation 프레임워크

#### 16.2 A/B Testing for AI
- **리서치 내용**:
  - A/B test 설계
  - 통계적 유의성
  - Multi-armed bandit

- **주요 소스**:
  - Experimentation 플랫폼 (Optimizely, LaunchDarkly)
  - A/B testing 방법론

- **관련 문서**:
  - A5-2: AI System Evaluation Framework

- **예상 시간**: 3-4시간
- **산출물**: A/B Testing 가이드

---

### 🌍 17. Industry-Specific Insights

#### 17.1 금융 산업 AI 활용
- **리서치 내용**:
  - 금융권 use cases (fraud detection, credit scoring, chatbot)
  - 규제 요구사항
  - 사례 연구

- **주요 소스**:
  - 금융권 AI 리포트
  - 규제 기관 가이드라인

- **관련 문서**:
  - D1-2: Financial Services Case Studies

- **예상 시간**: 3-4시간
- **산출물**: 금융 산업 인사이트

#### 17.2 통신 산업 AI 활용
- **리서치 내용**:
  - 통신사 use cases (network optimization, customer service)
  - 기술적 특성
  - 사례 연구

- **주요 소스**:
  - 통신 산업 리포트
  - 케이스 스터디

- **관련 문서**:
  - D1-3: Telecom Case Studies

- **예상 시간**: 2-3시간
- **산출물**: 통신 산업 인사이트

#### 17.3 제조 산업 AI 활용
- **리서치 내용**:
  - 제조업 use cases (예지보전, 품질관리)
  - IoT 통합
  - 사례 연구

- **주요 소스**:
  - 제조 산업 리포트

- **관련 문서**:
  - D1-4: Manufacturing Case Studies

- **예상 시간**: 2-3시간
- **산출물**: 제조 산업 인사이트

---

### 🎯 18. Workshop & Facilitation

#### 18.1 Workshop 설계 및 진행
- **리서치 내용**:
  - Workshop 구조
  - Facilitation 기법
  - Engagement 전략
  - Output 정리

- **주요 소스**:
  - Facilitation 가이드
  - Design Thinking 방법론

- **관련 문서**:
  - F1-2: Kickoff & Stakeholder Alignment
  - C3-2: Use Case Prioritization Guide

- **예상 시간**: 3-4시간
- **산출물**: Workshop 가이드

#### 18.2 Stakeholder Interview 기법
- **리서치 내용**:
  - Interview protocol
  - 질문 설계
  - Note-taking
  - Insight 도출

- **주요 소스**:
  - User research 방법론
  - 컨설팅 인터뷰 기법

- **관련 문서**:
  - B1-2: Interview Guide Set
  - C3-2: Use Case Prioritization Guide

- **예상 시간**: 2-3시간
- **산출물**: Interview 가이드

---

### 📚 19. Knowledge Management

#### 19.1 지식 관리 시스템
- **리서치 내용**:
  - KM 플랫폼 (Confluence, Notion, SharePoint)
  - 분류 체계 (taxonomy)
  - 검색 최적화

- **주요 소스**:
  - KM 베스트 프랙티스
  - 플랫폼 공식 문서

- **관련 문서**:
  - H1-1: Knowledge Repository Structure
  - H1-2: Documentation Standards

- **예상 시간**: 2-3시간
- **산출물**: KM 시스템 가이드

#### 19.2 Lessons Learned 프로세스
- **리서치 내용**:
  - Retrospective 방법
  - 학습 포착 및 공유
  - Continuous improvement

- **주요 소스**:
  - Agile retrospectives
  - KM 방법론

- **관련 문서**:
  - D3-1: Lessons Learned Template
  - F1-4: Project Closure & Handover

- **예상 시간**: 2시간
- **산출물**: Lessons Learned 프로세스

---

### 🎨 20. Visualization & Reporting

#### 20.1 Executive Reporting
- **리서치 내용**:
  - Executive summary 작성법
  - Data visualization 원칙
  - Storytelling with data

- **주요 소스**:
  - McKinsey communication
  - Data visualization 베스트 프랙티스

- **관련 문서**:
  - B8-1: Executive Report Template

- **예상 시간**: 2-3시간
- **산출물**: Reporting 가이드

#### 20.2 Dashboard & Metrics
- **리서치 내용**:
  - KPI dashboard 설계
  - Real-time vs batch reporting
  - Visualization 도구

- **주요 소스**:
  - BI 베스트 프랙티스
  - Dashboard design

- **관련 문서**:
  - H2-3: Reporting & Analytics Setup

- **예상 시간**: 2-3시간
- **산출물**: Dashboard 가이드

---

## LOW PRIORITY - 추가 리서치

### 📖 21. Advanced Topics

#### 21.1 Constitutional AI & Alignment
- **리서치 내용**:
  - Constitutional AI 개념
  - RLHF (Reinforcement Learning from Human Feedback)
  - AI alignment 연구

- **주요 소스**:
  - Anthropic 연구 논문
  - AI safety 연구

- **관련 문서**:
  - D4-2: Research Paper Library

- **예상 시간**: 3-4시간
- **산출물**: Advanced topics 요약

#### 21.2 Multimodal AI
- **리서치 내용**:
  - Vision-Language models
  - Document understanding
  - Multimodal RAG

- **주요 소스**:
  - Claude Vision
  - GPT-4V
  - 연구 논문

- **관련 문서**:
  - D4-2: Research Paper Library

- **예상 시간**: 3-4시간
- **산출물**: Multimodal 가이드

#### 21.3 Fine-tuning & PEFT
- **리서치 내용**:
  - Fine-tuning 전략
  - LoRA, QLoRA
  - When to fine-tune vs prompt engineering

- **주요 소스**:
  - HuggingFace PEFT
  - Fine-tuning 연구

- **관련 문서**:
  - D2-1: Technical Best Practices

- **예상 시간**: 3-4시간
- **산출물**: Fine-tuning 가이드

---

### 🌐 22. Emerging Trends

#### 22.1 AI Trends & Hype Cycle
- **리서치 내용**:
  - Gartner Hype Cycle for AI
  - 최신 트렌드 (2025)
  - 기술 성숙도

- **주요 소스**:
  - Gartner
  - Forrester

- **관련 문서**:
  - D4-3: Industry Reports & Trends

- **예상 시간**: 2-3시간
- **산출물**: Trends 리포트

#### 22.2 Research Paper 큐레이션
- **리서치 내용**:
  - arXiv 주요 논문
  - Conference papers (NeurIPS, ICML)
  - 실무 적용 가능성

- **주요 소스**:
  - arXiv
  - Papers with Code

- **관련 문서**:
  - D4-2: Research Paper Library

- **예상 시간**: 지속적 (분기 4-6시간)
- **산출물**: Paper 라이브러리

---

### 🛠️ 23. Tooling & Automation

#### 23.1 Code Generation & Copilot
- **리서치 내용**:
  - GitHub Copilot, Cursor
  - AI 코딩 어시스턴트 활용
  - Best practices

- **주요 소스**:
  - 각 도구 문서
  - 활용 사례

- **관련 문서**:
  - D2-1: Technical Best Practices

- **예상 시간**: 2-3시간
- **산출물**: Tooling 가이드

#### 23.2 No-code/Low-code AI
- **리서치 내용**:
  - LangFlow, FlowiseAI
  - No-code 플랫폼
  - 적용 시나리오

- **주요 소스**:
  - 플랫폼 문서

- **관련 문서**:
  - D4-1: Technology Landscape

- **예상 시간**: 2-3시간
- **산출물**: No-code 가이드

---

### 🌏 24. Localization & Regional

#### 24.1 한국 AI 생태계
- **리서치 내용**:
  - 한국 AI 정책
  - 주요 플레이어
  - 투자 동향

- **주요 소스**:
  - 과기정통부
  - KISTEP

- **관련 문서**:
  - D4-3: Industry Reports & Trends

- **예상 시간**: 2-3시간
- **산출물**: 한국 시장 인사이트

#### 24.2 글로벌 AI 규제 동향
- **리서치 내용**:
  - 국가별 규제
  - Cross-border 이슈

- **주요 소스**:
  - OECD AI Policy Observatory

- **관련 문서**:
  - D4-3: Industry Reports & Trends

- **예상 시간**: 2-3시간
- **산출물**: 규제 동향 리포트

---

### 💡 25. Innovation & R&D

#### 25.1 AI Innovation 프로세스
- **리서치 내용**:
  - Innovation framework
  - PoC/Pilot 방법론
  - Fail-fast 전략

- **주요 소스**:
  - Innovation 방법론

- **관련 문서**:
  - F1-3: Quality Assurance Process

- **예상 시간**: 2-3시간
- **산출물**: Innovation 가이드

---

## 리서치 방법론

### 🔍 리서치 접근법

#### 1. 웹 검색 전략
```
✓ 공식 문서 우선 (Anthropic, OpenAI, Google 등)
✓ 학술 논문 (arXiv, Papers with Code)
✓ 산업 리포트 (Gartner, Forrester, McKinsey)
✓ 기술 블로그 (각 플랫폼 공식 블로그)
✓ GitHub repositories (인기 프로젝트)
✓ 커뮤니티 (Reddit, HackerNews, LinkedIn)
```

#### 2. 정보 품질 검증
```
✓ 출처 신뢰성 확인
✓ 최신성 (2024-2025 정보 우선)
✓ 다수 소스 교차 검증
✓ 실무 적용 가능성 평가
```

#### 3. 문서화 기준
```
✓ 출처 명시
✓ 최종 업데이트 날짜 기록
✓ 실무 적용 팁 포함
✓ 예시 및 템플릿 첨부
```

---

## 다음 단계

### Phase 1: High Priority 리서치 (Week 1-2)
- RAG 시스템 (20시간)
- Agent Systems (15시간)
- Enterprise Platform (15시간)
- **Total: 50시간**

### Phase 2: Medium Priority 리서치 (Week 3-4)
- Templates & Standards (10시간)
- Project Management (10시간)
- Sales & Marketing (10시간)
- **Total: 30시간**

### Phase 3: Low Priority 리서치 (Week 5+)
- Advanced Topics (10시간)
- Emerging Trends (10시간)
- Localization (10시간)
- **Total: 30시간**

---

## 진행 상황 추적

| 카테고리 | 항목 수 | 완료 | 진행중 | 미시작 |
|---------|--------|------|--------|--------|
| RAG Systems | 6 | 6 | 0 | 0 |
| Agent Systems | 4 | 0 | 0 | 4 |
| Enterprise Platform | 4 | 0 | 0 | 4 |
| Prompt Engineering | 2 | 0 | 0 | 2 |
| Maturity & Assessment | 2 | 2 | 0 | 0 |
| Risk & Compliance | 4 | 4 | 0 | 0 |
| ROI & Business | 2 | 0 | 0 | 2 |
| LLM Platforms | 2 | 0 | 0 | 2 |
| Monitoring | 2 | 0 | 0 | 2 |
| Operating Model | 2 | 0 | 0 | 2 |
| **High Priority Total** | **35** | **12** | **0** | **23** |

---

**마지막 업데이트**: 2025-11-23
