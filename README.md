# 🍅 도마도의 골목가게 (Tomato’s Alley Store)

> **멋쟁이사자처럼 데이터분석 6기 파이널 프로젝트 4팀**  
> **팀명:** 사과가 되지 말고 도마도가 되라 🍅  
> **팀원:** 정우정 · 구서정 · 권지예 · 박선유 · 이채연  

---

## 📘 프로젝트 개요 (Overview)

**‘도마도의 골목가게’**는 브라질 이커머스 플랫폼 **Olist**의 실제 데이터를 기반으로,  
**하위 판매자들이 상위 30% 판매자로 성장하기 위한 전략**을 도출한 데이터 분석 프로젝트입니다.  

브라질 전자상거래 시장은  
- 주마다 다른 세금 구조,  
- 복잡한 배송 체계,  
- 글로벌 기업(Amazon, Alibaba)의 낮은 점유율 등으로 인해  
중소 판매자에게 높은 진입 장벽이 존재합니다.  

이에 따라, **Olist 플랫폼 내 판매자 데이터를 분석하여**  
하위 70% 도마도들이 상위 30% 도마도로 성장할 수 있는  
**데이터 기반 맞춤형 전략과 추천시스템**을 제시했습니다.

---

## 🧭 분석 목표 (Main Objectives)
1. 리뷰·배송비·카테고리 관점에서 성공 요인 분석 
2. 머신러닝으로 상위 전환 요인 예측  
3. 데이터 기반 맞춤형 성장 전략 제시  

---

## 📊 데이터셋 (Dataset)

- **출처:** Olist E-Commerce Public Dataset (2016–2018)  
- **규모:** 약 10만 건의 주문 및 배송 데이터  
- **주요 테이블:**  
  - 주문 정보 (`orders.csv`)  
  - 배송 정보 (`order_deliveries.csv`)  
  - 리뷰 정보 (`order_reviews.csv`)  
  - 제품 정보 (`products.csv`)  
  - 판매자 정보 (`sellers.csv`)
  
<img width="600" height="800" alt="image" src="https://github.com/user-attachments/assets/bc1ece0e-6221-4e35-9dad-e30e7b8bc154" />

---

## 🔍 분석 과정 (Analysis Process)

### 1️⃣ 데이터 전처리 및 탐색 (EDA) 
- 결측치·이상치 처리 및 데이터셋 병합
- 판매자 지역 분포(상파울루 59.7%) 시각화  ->  약 59%의 판매자가 상파울루 지역에 거주함. 이후 분석은 상파울루 지역에 국한하여 진행
  <img width="400" height="300" alt="스크린샷 2025-10-14 오후 3 29 07" src="https://github.com/user-attachments/assets/41b582c1-32dd-4b13-8d55-a58c735b6ce0" />
---

### 2️⃣ 리뷰 분석 (Review Analysis)
- **3점 이하 리뷰 워드클라우드:** 배송 관련 문제 단어 다수  
  → ‘받지 못했습니다’, ‘지연’, ‘다른’, '기다리고 있습니다' 등
  <img width="717" height="358" alt="스크린샷 2025-10-14 오후 3 22 00" src="https://github.com/user-attachments/assets/cf0b0f04-c962-463f-8c67-bbd55bec7670" /> 
- **T-test 결과:** 배송 지연 시 리뷰 점수 급감 (p < 0.001)  
  - 정시 배송 평균 4.14점  
  - 지연 배송 평균 2.36점
  <img width="712" height="351" alt="스크린샷 2025-10-14 오후 3 22 51" src="https://github.com/user-attachments/assets/34b4c4d5-861a-4228-b20a-3484aa3c212c" />

- **Insight:** 배송문제는 택배사나 olist 기업 자체의 문제. 품질이 좋으면 배송 문제에도 긍정적 리뷰 가능  
  - 배송 문제가 있었지만, 리뷰 점수는 높았던 리뷰: 품질 관련 언급 많음
  - 높은 점수의 리뷰에서 약 32%가 상품 품질 키워드
  <img width="424" height="366" alt="스크린샷 2025-10-14 오후 3 24 11" src="https://github.com/user-attachments/assets/5ac38dbb-ed47-4add-bfab-ee1d1ccf32c9" />
  
---

### 3️⃣ 배송비 분석 (Shipping Cost Analysis)
- 거래의 대부분이 **25헤알 이하 구간**에서 발생

  <img align="left" width="450" height="350" alt="스크린샷 2025-10-14 오후 3 31 01" src="https://github.com/user-attachments/assets/bfa8798e-d65c-4c89-8dbc-c83b1df0dec1" />
  <br clear="left"/>
- **배송비 부담도**(배송비/상품가)가 낮을수록 매출이 높음

  <img align="left" width="400" height="300" alt="스크린샷 2025-10-14 오후 3 31 21" src="https://github.com/user-attachments/assets/d9f62871-ee31-49cc-a5fa-2eb461fdb2af" />
  <br clear="left"/>
- 최적 배송비 수준: **상품가의 약 10%** + **25헤알 이하**

> 💡 고객은 절대적인 금액보다 ‘상대적 부담감’에 더 민감하다.

---

### 4️⃣ 카테고리 분석 (Category Analysis)
- **ANOVA 검정 결과:** 카테고리에 따른 매출 차이 유의미 (p < 0.001)  
- 매출 상위 4개 대분류:
  1. 가구/인테리어  
  2. 취미/여가  
  3. 가전/전자  
  4. 생활용품  
  <img width="600" height="400" alt="스크린샷 2025-10-14 오후 3 33 00" src="https://github.com/user-attachments/assets/06e1cccf-778a-43d5-90bf-ef6fc69df14c" />

- 상위 30% 판매자 중 **1~3개 카테고리 조합** 보유 시 매출 비중 68%

  <img align="left" width="400" height="300" alt="스크린샷 2025-10-14 오후 3 32 46" src="https://github.com/user-attachments/assets/f3fc0b17-6d45-48cc-9d8c-5a98cf612222" />
  <br clear="left"/>
- **Insight:** 매출금액이 높은 대분류 카테고리 Top4중 3개 이하로 조합하여 판매
  
---

### 5️⃣ 머신러닝 모델링 (Machine Learning)
- **Model:** XGBoost Classifier  
- **Target:** 상위 30% 여부 (Top30_YN)  
- **Features:** 상품·배송·리뷰 관련 변수  

| Metric | Score |
|:--|:--:|
| Accuracy | 0.85 |
| Precision | 0.77 |
| Recall | 0.73 |
| F1-score | 0.75 |
| ROC-AUC | 0.92 |

**주요 요인**
- 상품 가격 전략  
- 응답 소요일(고객 문의 대응 속도)  
- 세부 카테고리 다양성  
<img width="437" height="153" alt="스크린샷 2025-10-14 오후 3 35 15" src="https://github.com/user-attachments/assets/35ea6151-2797-4404-83d6-31b999fb8fef" />

---

## 🚀 제안 및 전략 (Solutions)

| 구분 | 전략 제안 |
|:--|:--|
| 리뷰 | 배송 문제보단 **품질 관리 & 고객 응대 강화** |
| 배송비 | **25헤알 이하**, 상품가의 **10% 내외**로 설정 |
| 카테고리 | **상위 4개 대분류 중 3개 이하 조합**으로 집중 |
| 추천시스템 | 머신러닝 기반 **맞춤형 카테고리 추천** 도입 |
  <img width="1273" height="652" alt="스크린샷 2025-10-14 오후 3 36 10" src="https://github.com/user-attachments/assets/37e16473-6adf-433f-9e26-844ec71031e3" />

---

## 🧠 핵심 인사이트 (Key Findings)

- 배송지연은 리뷰 점수에 가장 큰 부정적 영향  
- 품질이 좋을 경우, 그 배송문제의 영향은 완화됨  
- 고객은 배송비 비율(부담도)에 더 민감  
- 소수 핵심 카테고리에 집중 시 효율적    

---

## 🛠 Tools & Skills

**Python:** pandas, matplotlib, seaborn, sklearn, XGBoost  
**Statistics:** t-test, ANOVA  
**Visualization:** Tableau, Matplotlib, WordCloud  
**Collaboration:** GitHub, Notion  

---

## 💬 한계점 & 추후 개선사항
- 파레토 분포 구조의 한계 (전체 결과의 80%가 상위 20%의 원인(또는 판매자)에 의해 발생한다는 원리) -> 상위 판매자의 독점구조는 자연스러운 현상
- 구글 자동 번역의 부자연스러움 : 포르투갈어를 한국어로 번역하는 과정에서 직역으로 부자연스러운 언어로 번역이 되었다.
- 지역 이름의 혼동성 : (지역 이름 오타, 동일한 지역의 다른 이름 등) 수작업으로도 통일화하기 어려운 작업이여서 못쓰는 데이터들도 많았다.
- 머신러닝의 활용 : 기존에 만든 Lumi로 만든 웹사이트 (머신러닝 적용 안됨)보다 머신러닝을 적용한 웹사이트를 만들어 완성도 높이기
  
