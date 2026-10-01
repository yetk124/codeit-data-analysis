<div align="center">

# 📊 Codeit Sprint · AI 데이터 분석가 16기

**공공데이터 EDA → 행동 로그 세그먼트 분석 → 머신러닝 예측 모델링**
<br>
단계별로 분석 범위를 넓혀 온 팀 프로젝트 기록입니다.

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![SQL](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![CatBoost](https://img.shields.io/badge/CatBoost-FFCC00?style=flat-square&logoColor=black)
![Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat-square&logo=googlecolab&logoColor=white)

</div>

---

## 🗂️ Projects

### 🚇 01 · 초급 — [서울 지하철 무임승차 집중 구조와 이용 패턴 분석](./01_beginner_subway-free-ride)

> **무임승차는 어느 역에, 왜, 언제 몰리는가?**

- 무임승차 비율 상위 20역 vs 하위 20역 → **최대 10배 이상** 격차
- 고령인구 비율 상관계수 **0.58**, 상위역 반경 500m 경로당 **2.5배**
- 노인 이용은 출퇴근이 아닌 **평일 낮 시간대** 중심 → 피크타임 제한 정책과의 괴리 제시

`EDA` `상관분석` `공간분석` `GeoPandas` `Folium`

<br>

### 💳 02 · 중급 1 — [비결제자 행동 세분화를 통한 유료 전환 전략](./02_intermediate1_nonpaying-segment)

> **전체 회원의 92.5%인 비결제자, 행동 병목은 어디인가?**

- 콘텐츠·레슨·결제 페이지 진입 여부로 비결제자를 **5개 세그먼트**로 분류
- 결제 고민층은 결제 페이지 **1회 방문 후 이탈 50.2%** (결제자 13.3%)
- 세그먼트별 맞춤 개선안 3가지 제안 (관심사 추천 · 학습 알림 · 재방문 유도)

`SQL` `MariaDB` `세그먼테이션` `가설 검증`

<br>

### 🏢 03 · 중급 2 — [공유오피스 무료체험 고객의 결제 전환 예측](./03_intermediate2_shared-office-conversion)

> **체험 중 행동으로 결제할 고객을 구분할 수 있는가?**

- 타임존 보정 · 결측 시각 복원 · 자정 넘김 병합 등 **데이터 품질 검증**
- CatBoost Test ROC-AUC **0.648** (기준선 0.591), 누수 방지 파이프라인 설계
- SHAP 해석 → 재방문 유도 **A/B 테스트 설계**까지 연결

`Feature Engineering` `CatBoost` `SHAP` `A/B Test`

<br>

### 🔒 04 · 고급 — 진행 예정

---

## 📁 Structure

```
codeit-data-analysis/
├── 01_beginner_subway-free-ride/
├── 02_intermediate1_nonpaying-segment/
├── 03_intermediate2_shared-office-conversion/
└── 04_advanced/

📂 각 프로젝트 폴더
 ├── README.md     프로젝트 요약
 ├── notebooks/    분석 노트북 (Google Colab)
 ├── docs/         분석 보고서 · 발표자료 (PDF)
 ├── images/       주요 시각화
 └── data/         데이터 설명 (원본 비공개)
```

## 🔐 Data Notice

> 원본 데이터(CSV, SQL 덤프)는 **보안 및 데이터 제공처 정책상 포함하지 않았습니다.**
> 각 프로젝트의 `data/README.md`에 출처와 테이블·컬럼 구조를 정리했고,
> 노트북 출력 중 사용자 식별값(user_id 등)이 노출되는 표는 제거했습니다.

---

<div align="center">

**원예은** · Hansung University, Software Engineering

[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:919yeeun@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/yetk124)

</div>
