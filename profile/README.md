# 📊 자연어 기반 패널 추출 시스템 (Natural Language Based Panel Extraction System)

<div align="center">

> **"누구나 쉽고 빠르게"** > 복잡한 쿼리 없이 자연어 질문만으로 정확한 타겟 패널을 추출하고 인사이트를 도출하는 시스템

</div>

<br>

## 📅 프로젝트 개요 (Project Overview)

- **진행 기간**: 2025.09.14 ~ 2025.11.28
- **수행 조직**: PMI (자연어 기반 패널 인사이트 도출 기업)
- **개발 목적**:  
  기존 패널 추출 시스템은 복잡한 설정과 쿼리 지식이 필요하여 접근성이 낮았습니다. 이를 개선하기 위해 **자연어(Natural Language)를 이해하고, 의도에 맞는 패널을 자동으로 필터링 및 시각화**하는 시스템을 구축하였습니다.

<br>

| **기존 패널 추출 시스템** | **자연어 기반 패널 추출 시스템** |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/59cb8c9f-2254-4db4-b4d7-b5bd1b630bdc" width="400" alt="메인 검색 화면"> | <img src="https://github.com/user-attachments/assets/b2059e00-f907-4c7f-806a-78fa90db13dc" width="400" alt="검색 결과 및 시각화"> |
| 복잡한 조건 설정 필요 | **자연어 질문으로 자동 필터링** |

<br>

## 🖥️ 프로젝트 시연 (Demo)

사용자가 자연어로 질문을 입력하면, AI가 의도를 파악하여 조건에 맞는 패널을 추출하고 결과를 시각화합니다.

<table width="100%">
  <tr>
    <td width="50%" align="center">
      <b>📈 전체 데이터 시각화</b><br>
      <img src="https://github.com/user-attachments/assets/6a61bf87-814c-477f-a7cf-b111d5895c15" width="100%">
    </td>
    <td width="50%" align="center">
      <b>🔍 자연어 검색 시연</b><br>
      <img src="https://github.com/user-attachments/assets/bc6d8da5-93b5-4aaa-9aa9-39056aaacbce" width="100%">
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">
      <b>🧩 세부 프로세스 시연</b><br>
      <img src="https://github.com/user-attachments/assets/87024cc1-82ba-4b0c-9110-0e69eb8d2234" width="100%">
    </td>
  </tr>
</table>

<br>

## 🏗️ 시스템 아키텍처 (Architecture)

<p align="center">
  <img src="https://github.com/user-attachments/assets/cfef894c-fa82-463e-a2f8-fbcca8798b29" width="800" alt="시스템 아키텍처">
</p>

### 🛠️ 주요 기술 스택 및 리소스 (Tech Stack & Resources)

| Category | Stack | Version / Details |
| :--- | :--- | :--- |
| **Language & Framework** | ![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-0.111.0-009688?logo=fastapi&logoColor=white) | Python 3.11, FastAPI 0.111.0 |
| **Database & Search** | ![OpenSearch](https://img.shields.io/badge/OpenSearch-2.11-005EB8?logo=opensearch&logoColor=white) ![Qdrant](https://img.shields.io/badge/Qdrant-1.15.5-E91E63?logo=qdrant&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-8.2.3-DC382D?logo=redis&logoColor=white) | OpenSearch 2.11, Qdrant 1.15.5, Redis 8.2.3 |
| **AI & LLM** | ![Claude](https://img.shields.io/badge/Anthropic-Claude_3.7-D97757?logo=anthropic&logoColor=white) | Claude-3.7-Sonnet, Embedding: nlpai-lab/KURE-v1 |
| **Infra & DevOps** | ![Docker](https://img.shields.io/badge/Docker-29.0.0-2496ED?logo=docker&logoColor=white) ![Ubuntu](https://img.shields.io/badge/Ubuntu-25.04-E95420?logo=ubuntu&logoColor=white) ![DigitalOcean](https://img.shields.io/badge/DigitalOcean-Cloud-0080FF?logo=digitalocean&logoColor=white) | Ubuntu 25.04, Docker Engine 29.0.0 |

#### 💸 Infrastructure Specs & Cost
> **Total Infra Cost: $96/month** (LLM API usage excluded)

- **Search Node (OpenSearch/Qdrant)**: 2vCPU / 4GB RAM / 80GB SSD (x2 Instances) - **$48**
- **App Node (FastAPI/Redis)**: 4vCPU / 8GB RAM / 80GB SSD (x1 Instance) - **$48**
- **LLM Cost**: Claude-3.7-Sonnet (Avg. **$0.02** per request)

<br>

## ⚙️ 내부 동작 원리 (Internal Logic)

사용자의 질의는 **행동 패턴 사전**과 **인물 정보 사전**을 거쳐 엔티티가 추출되며, 이를 기반으로 최적의 검색 쿼리가 생성됩니다.

<p align="center">
  <img src="https://github.com/user-attachments/assets/af898299-93e2-4bd4-83a0-b4991952f0d3" width="700" alt="내부 동작 원리">
</p>

### 1. 사전 기반 분석 (Dictionaries)
정확한 의도 파악을 위해 두 가지 핵심 사전을 구축하여 활용합니다.

| **행동 패턴 사전 (Behavior Pattern)** | **인물 정보 사전 (Demographic)** |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/6f28f00e-89fb-475a-8fb1-e16958beeef4" width="400"> | <img src="https://github.com/user-attachments/assets/714d4c15-3350-4653-93c0-094095940a0b" width="400"> |
| 사용자 발화에서 패널의 **행동/의도**를 매핑 | 인구통계학적 **정보 및 속성** 매핑 |

### 2. 엔티티 추출 및 정확도 (Entity Extraction & Accuracy)
자연어 문장에서 핵심 검색 조건을 추출하고, 자체 검증 로직을 통해 높은 정확도를 유지합니다.

- **엔티티 추출 예시**:
<p align="center">
  <img src="https://github.com/user-attachments/assets/d75ba7e7-cf4e-42bb-a8e6-e509bfb093f5" width="700" alt="엔티티 추출">
</p>

- **정확도 측정 지표**:
<p align="center">
  <img src="https://github.com/user-attachments/assets/28849687-f719-4a86-960e-e6bdc98e22c1" width="700" alt="정확도 측정">
</p>

<br>

## 💾 데이터베이스 설계 (Database Design)

검색 성능과 시각화 효율성을 모두 잡기 위해 **OpenSearch 인덱스를 목적에 따라 이원화**하고 **Qdrant(Vector DB)**를 활용했습니다.

### OpenSearch 인덱스 구조
| **시각화 인덱스 (Visualization)** | **검색 인덱스 (Search)** |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/b0640ccd-f33d-40dc-b34d-015be6cde62b" width="350"> | <img src="https://github.com/user-attachments/assets/842f74e8-99af-4e28-b6ff-c9e2103b5cc1" width="350"> |
| 필드에 질문을 직접 삽입하여<br>**답변 비율 및 경향성 집계 최적화** | `Nested` 타입을 사용하여<br>**질문-답변 쌍을 묶어 정밀 검색 수행** |

### Vector DB (Qdrant) 컬렉션 구조
의미 기반 검색(Semantic Search)을 위해 Qdrant 컬렉션을 구성하여 문맥적 유사도를 분석합니다.
<p align="center">
  <img src="https://github.com/user-attachments/assets/ab57d6f0-722a-4796-91bc-764fa461220e" width="600" alt="Qdrant 컬렉션">
</p>

<br>

### RRF(Rank Fusion) 데이터 병합 알고리즘
서로다른 데이터 베이스에서 가져온 데이터를 서버에서 병합합니다.
<p align="center">
  <img src="https://github.com/user-attachments/assets/f88f26cc-fd7d-473a-887b-da5e66bace41" width="600" alt="Qdrant 컬렉션">
</p>

## 🚀 한계점 및 향후 개선 사항 (Limitations & Future Improvements)

현재 시스템 한계 및 개선 계획

### 1. 사전 업데이트 자동화 (Dictionary Automation)
- **Current Limitation**: 행동 패턴 사전과 인물 정보 사전이 정적으로 관리되어 최신 트렌드 반영이 늦음
- **Future Plan**: 유입 데이터를 감지하고, **사전을 자동으로 업데이트 및 확장**하는 파이프라인 구축 예정

### 2. 실시간 정확도 측정 시스템 (Real-time Evaluation)
- **Current Limitation**: 현재 정확도 측정은 사전에 기업에서 정의된 3가지 기준 쿼리를 통해 수동 검증 방식으로 진행
- **Future Plan**: **검색 정확도 점수(Scoring)를 실시간으로 대시보드에 시각화**하는 기능 도입
