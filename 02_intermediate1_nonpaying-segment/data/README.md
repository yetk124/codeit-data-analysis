# 데이터 설명

코드잇에서 제공한 교육용 구독 서비스 데이터(SQL 덤프)로, **데이터 제공 정책상 원본과 가공 CSV는 공개하지 않습니다.**

## 처리 흐름

```
subscription_dump.sql → MariaDB 복원 → 분석 기간 필터 테이블(*_filtered) 생성 → CSV 변환 → pandas 분석
```

## 이벤트 테이블

공통 컬럼: `user_id`, `client_event_time` (+ 이벤트별 속성)

| 테이블 | 의미 | 주요 속성 |
|---|---|---|
| enter_main_page | 메인 페이지 진입 | |
| enter_signup_page / complete_signup | 회원가입 페이지 진입 / 완료 | |
| enter_content_page | 콘텐츠 상세 페이지 진입 | content_id |
| click_content_page_start_content_button | 수강 버튼 클릭 | |
| click_content_page_more_review_button | 후기 더보기 클릭 | |
| start_content / end_content | 콘텐츠 시작 / 완료 | |
| enter_lesson_page | 레슨 페이지 진입 | lesson.id, content.id, is_trial |
| complete_lesson | 레슨 완료 | |
| click_lesson_page_related_question_box | 레슨 내 질문 기능 클릭 | |
| enter_payment_page | 결제 페이지 진입 | |
| complete_subscription / renew_subscription / resubscribe_subscription | 구독 결제 / 갱신 / 재구독 | coupon.discount_amount |
| click_cancel_plan_button | 구독 취소 버튼 클릭 | |
| start_free_trial | 무료체험 시작 (**분석 제외**) | |

## 분석 단위

| 단위 | 키 | 용도 |
|---|---|---|
| 사용자 | user_id | 결제/비결제 구분, 세그먼트 분류 |
| 이벤트 | 테이블 각 행 | 행동 횟수 |
| 콘텐츠 / 레슨 | content_id / lesson.id | 고유 탐색·수강 수 |
| 시간 | client_event_time | 가입 후 경과 시간, 행동 순서 |
