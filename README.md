# Codeit Sprint AI 데이터 분석가 16기 — 프로젝트 모음

코드잇 스프린트 데이터 분석 부트캠프에서 진행한 팀 프로젝트 저장소입니다.
단계(초급 → 중급 → 고급)를 거치며 **공공데이터 EDA → 행동 로그 기반 세그먼트 분석 → 머신러닝 예측 모델링**으로 분석 범위를 넓혀 왔습니다.

## 프로젝트 목록

| 단계 | 프로젝트 | 핵심 질문 | 주요 기법 | 기술 스택 |
|---|---|---|---|---|
| 초급 | [서울 지하철 무임승차 집중 구조와 이용 패턴 분석](./01_beginner_subway-free-ride) | 무임승차는 어느 역에, 왜, 언제 몰리는가? | EDA, 상관분석, 공간분석(500m 반경), 시간대 패턴 정규화 | Python, pandas, GeoPandas, Folium |
| 중급 1 | [비결제자 행동 세분화를 통한 유료 전환 전략](./02_intermediate1_nonpaying-segment) | 92.5% 비결제자의 행동 병목은 어디인가? | 행동 기반 세그먼테이션, 가설 검증, 결제자 비교군 분석 | Python, SQL(MariaDB, pandasql) |
| 중급 2 | [공유오피스 무료체험 고객의 결제 전환 예측](./03_intermediate2_shared-office-conversion) | 체험 중 행동으로 결제 고객을 구분할 수 있는가? | 데이터 품질 검증, 피처 엔지니어링, CatBoost, SHAP | Python, scikit-learn, CatBoost, SHAP |
| 고급 | [진행 예정](./04_advanced) | - | - | - |

## 폴더 구조

```
codeit-data-analysis/
├── 01_beginner_subway-free-ride/
├── 02_intermediate1_nonpaying-segment/
├── 03_intermediate2_shared-office-conversion/
└── 04_advanced/
    각 프로젝트 폴더
    ├── README.md     프로젝트 요약
    ├── notebooks/    분석 노트북 (Google Colab)
    ├── docs/         분석 보고서 · 발표자료 (PDF)
    ├── images/       주요 시각화
    └── data/         데이터 설명 (원본 비공개)
```

## 데이터 관련 안내

원본 데이터(CSV, SQL 덤프)는 **보안 및 데이터 제공처 정책상 저장소에 포함하지 않았습니다.**
각 프로젝트의 `data/README.md`에 데이터 출처와 테이블·컬럼 구조를 정리했습니다.
노트북 출력 중 개별 사용자 식별값(user_id 등)이 노출되는 표는 제거했습니다.

## Author

**원예은** · Hansung University, Software Engineering
