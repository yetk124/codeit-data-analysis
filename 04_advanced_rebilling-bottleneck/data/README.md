# 데이터 설명

코드잇에서 제공한 교육용 10대 익명 투표 SNS 데이터로, **청소년 사용자 데이터이자 데이터 제공 정책상 원본과 가공 CSV는 공개하지 않습니다.**
노트북 출력 중 개별 사용자를 식별할 수 있는 표는 제거했고, 팀 내부 저장소 경로는 placeholder로 바꿨습니다.

## 데이터셋

| 데이터셋 | 테이블 수 | 기간 | 비고 |
|---|---|---|---|
| 서비스 내부 DB (MySQL 덤프) | 21 | 2023.03.29 ~ 2024.05.09 | 원래 UTC → 전처리에서 KST로 변환 |
| Hackle 이벤트 로그 | 4 | 2023.07.18 ~ 08.10 | KST |

## 주요 테이블 (분석에 사용한 것)

| 영역 | 테이블 | 행 단위 | 비고 |
|---|---|---|---|
| 유저 | accounts_user, accounts_school, accounts_group | 유저 / 학교 / 반 | 유저 약 67.7만 명 |
| 친구 | accounts_friendrequest | 친구 요청 1건 | 약 1,715만 행 |
| 결제 | accounts_paymenthistory | 결제 1건 | 상품 4종 (heart.777 / 200 / 1000 / 4000) |
| 출석 | accounts_attendance | 출석 기록 | 2023.05.27부터 기록 |
| 투표 | polls_* , accounts_userquestionrecord, accounts_pointhistory | 투표 / 포인트 변동 | 투표를 시작한 약 5천 명만 포함 |
| 핵클 | hackle_events, hackle_properties, user_properties | 이벤트 1건 / 세션 속성 | 이벤트 약 1,144만 행 |

제외: 탈퇴 기록, 타임라인 신고, 기기 속성

## 결합 구조

```
accounts_user ─┬─ accounts_paymenthistory   (1:N, user_id → 첫 결제자 테이블로 집계)
               ├─ accounts_friendrequest    (1:N, send_user_id / receive_user_id)
               ├─ accounts_attendance       (1:N)
               └─ accounts_group ── accounts_school

hackle_events ── hackle_properties (session_id, 세션당 여러 행)
              → 세션별 숫자 user_id 하나로 정리한 매핑 표를 먼저 만든 뒤 accounts_user와 연결
```

- 서비스 DB와 핵클은 **기간과 범위가 다른 데이터셋**이라 투표 기록끼리가 아니라 **유저 단위**로 연결
- 조인 전후 행 수·유저 수를 비교해 행 증식 여부를 확인

## 노트북 산출물 (미포함)

- `data_csv/` — 정리된 DB(final_clean)에서 내보낸 테이블별 CSV
- 첫 결제자 테이블(유저 1명 = 1행), 핵클 방문 테이블(30분 공백 기준 방문 단위)
