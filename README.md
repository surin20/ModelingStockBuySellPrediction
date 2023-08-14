# 2023-1-PSAT-team-timeseries
2023년 1학기 통계분석학회 P-SAT 시계열자료분석팀 주제분석


## 💻 프로젝트 소개
<주식 초보자의 리스크 관리를 위한 매수/매도 추천 서비스>📈

주식 관련 정보 및 흐름을 이해하기 어려운 '주린이'😢를 위해, 주가에 영향을 줄 수 있는 요인에 대한 데이터로부터 모델이 매수/유지/매도를 학습하여 그 결과를 추천 -> 투자에 대한 쉽고 간단한 인사이트를 제공!😊

활용 데이터: 주식 시세 추이, 투자자별 거래 실적, 외국인 보유량, 공매도량, 국내 기사, 영문 기사, 네이버 증권 토론방 게시글, 네이버 검색량, 코스피, 비트코인 거래, 경제심리지수, 뉴스심리지수, 산업생산지수, 소비자물가지수, 소비자신뢰지수, 소비자심리지수, 실업률, 한국은행 기준금리, 환율

데이터 출처: 한국거래소, 한국은행 경제통계시스템, KOSIS, invest.com, 네이버 증권, 네이버 데이터랩, 빅카인즈, CNN

개발 기간: 23.04.16 ~ 23.05.19


## ❤️ 팀 구성 및 역할
- 김민(팀장): 데이터 수집, 데이터 전처리, Y~X EDA, 변수선택(KS검정), XGB, LSTM-CNN, LGBM
- 김동환: 등락률 라벨링, 데이터 전처리, Y~X EDA, 변수선택(인과관계검정), VAR, LGBM, SVM, log reg
- 서유진: 데이터 수집(+크롤링), 데이터 전처리, X변수 EDA, LSTM회귀(threshold자동화)
- 이수린: X변수 EDA, 변수선택(PCA, 요인분석, VIF, importance), 시계열 윈도잉, XGB, LGBM, NaiveBayes
- 장다연: 데이터 전처리, 한글/영문 기사 감성분석, randomforest, XGB, LGBM


## 🔍 분석 흐름
1. 데이터 수집
2. 데이터 전처리 (기사 데이터 감성분석, 데이터 병합, 결측치 보간, 자료형 수치형으로 통일, 시간 순 정렬)
3. EDA (X변수간 EDA, Y~X변수간 EDA)
4. 등락률(continuous) -> 매수/유지/매도(categorical) 라벨링
5. 변수 선택 (인과관계 검정, VIF, PCA, 요인분석, feature importance, KS검정 시도)
6. labeled y변수 예측 모델링 (with imbalanced class problem😭)
7. 예측 결과 시각화 및 결과 분석


## 📈 모델링 개요
![화면 캡처 2023-06-14 212644](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/ef628d73-e77e-4e37-a0ec-97bb7c19c735)


## 🚨 클래스 불균형 문제
매수/매도에 비해 예측 라벨의 수가 많아서 클래스 불균형이 심각 -> 매수/매도에 대한 예측 성능 저조

💡 해결을 위한 노력들
- 단순 정확도나 f1-score가 아닌 평가지표 커스텀을 통해 프로젝트 목적에 적합한 모델 선택 (ex. 매수, 매도의 정확도, 정밀도의 평균 / 매수, 매도, 유지 정확도의 평균 etc)
- 모델 학습 시 클래스별 샘플 가중치 반영
- 라벨 회귀 예측 -> 검증 set으로 분류 threshold 결정 -> 최종 분류


## 📃 결과
![화면 캡처 2023-06-14 212213](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/60fad7c1-5b94-4a24-a004-aaed0c71976c)
![화면 캡처 2023-06-14 212242](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/ab0a5ce1-e32e-4508-a379-f7543abe4bbd)
![화면 캡처 2023-06-14 212511](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/4a5403a3-b952-433f-bd1c-527da7ebc030)
![화면 캡처 2023-06-14 212533](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/e84f0203-acd0-4baa-9579-9108bd9abd88)
![화면 캡처 2023-06-14 212603](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/c36b4367-947a-4837-9d38-32889bfea767)
![화면 캡처 2023-06-14 212619](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/1206e5ed-a46d-47a9-b6d2-e7b03b96fd66)
