# 데이터 설명

코드잇에서 제공한 교육용 공유오피스 데이터로, **데이터 제공 정책상 원본과 가공 CSV는 공개하지 않습니다.**

## 원본 테이블

| 테이블 | 원본 행 수 | 행 단위 | 주요 컬럼 |
|---|---|---|---|
| trial_register | 9,659 | 사용자 1명의 신청 | user_uuid, trial_date |
| trial_payment | 9,659 | 사용자 1명의 결제 결과 | user_uuid, is_payment |
| trial_visit_info | 11,477 | 사용자-지점-날짜 방문 | site_id, date, first_enter_time, last_leave_time, stay_time_second |
| trial_access_log | 63,708 | 출입 이벤트 1건 | id, checkin (1=입실, 2=퇴실), cdate, site_id |
| site_area | 9 | 지점 1개 | site_id, area_pyeong |

## 결합 구조

```
trial_register ─┬─ trial_payment          (1:1, user_uuid)
                ├─ trial_visit_info       (1:N → 사용자 단위 집계 후 left join)
                └─ trial_access_log       (1:N → 사용자 단위 집계 후 left join)
trial_visit_info / trial_access_log ── site_area (site_id)
```

## 노트북 산출물 (미포함)

- `shared_office_trial_model.csv` — 사용자 1명 = 1행, 36개 피처 + is_payment
- 제외 사용자 목록 (제외 사유 포함)
