# Revenue Forecasting with Time Series & ML

## 1. 프로젝트 개요
본 프로젝트는 소규모 노선(또는 단위 시장)의
매출(Revenue)을 예측하여,
의사결정에 활용 가능한 인사이트를 도출하는 것을 목표로 한다.

### 문제 정의
- 과거 판매/공급 데이터를 기반으로
  향후 기간의 매출을 예측
- 단일 모델이 아닌 여러 모델을 비교하여
  가장 실용적인 접근 방식 도출

### 분석 목표 (KPI)
- 예측 정확도 향상
- Revenue 관점의 의사결정 지원
- 모델 간 성능 및 해석력 비교

### 사용 모델
- ARIMA / SARIMA (시계열 모델)
- RandomForest Regressor
- XGBoost Regressor

---

## 2. 데이터 구조 및 특성
실무와 비슷한 Synthetic Data(가상 항공/수요 데이터) 사용

### 주요 컬럼
- date: 기준 날짜
- capacity (ASK): 공급 좌석
- demand (PAX): 수요
- load_factor (LF): 탑승률 (0~1)
- avg_revenue (AR): 평균 운임
- revenue (REV): 총 매출

### 데이터 특성
- LF는 0~1 범위
- AR은 합리적인 범위 내 분포
- 계절성(seasonality), 요일 효과, 휴일 효과 존재

### 예측 문제 유형
- 회귀(Regression)
- 시계열(Time Series)

---

## 3. 전처리 전략 (1차)
- 결측치 처리
  - 비정기 운항/결항 구간 제거 또는 대체
- 이상치 처리
  - LF < 0 또는 > 1 제거
  - 비정상 AR/REV 제거
- 데이터 타입 정합성 확보
- 파생변수 생성
  - RPK, ASK, Yield, RASK

---

## 4. 탐색적 데이터 분석 (EDA)
- 주요 변수 분포 확인
- Revenue와 설명 변수 간 관계 분석
- 상관관계 분석
- 시계열 패턴 및 도메인 인사이트 도출

---

## 5. 전처리 전략 (2차)
- 스케일링
- 범주형 변수 인코딩
- Train / Validation / Test 분리

---

## 6. 모델링 접근
### 6-1. RandomForest
- 비선형 관계 학습
- Feature importance 확인

### 6-2. XGBoost
- Gradient Boosting 기반 예측
- 성능 중심 모델

### 6-3. ARIMA / SARIMA
- 시계열 기반 예측
- 계절성 반영 여부 비교

---

## 7. 모델 평가
- 회귀 성능 지표
  - MAE, RMSE, MAPE
- 예측 결과 시각화
- Feature importance 비교 (RF, XGB)

---

## 8. 모델 비교
- 모델별 성능 비교 테이블
- 해석 가능성 vs 성능 비교
- 실무 적용 관점에서의 장단점 정리

---

## 9. 결론 및 비즈니스 적용
- 최적 모델 선정
- Revenue 관점 시사점
- 실제 운영 적용 시 고려사항

---

## 10. 한계점 및 개선 방향
- 완전 자동화의 한계
- 외생 변수 미반영 이슈
- 추가 데이터 확보 시 개선 가능성
