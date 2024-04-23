# 투자자 심리에 따른 테마주 주가 변동 예측 모델
- 2023 2학기 창의적종합설계 팀프로젝트
- 팀원 : 5명

# 1. 프로젝트 기간
- 2023.09.14 - 2023.12.21

# 2. 기획 배경 및 목적
- 코스피 시장의 기업 중심으로 주가 예측이 주를 이루었던 선행 연구와 달리, 코스닥 시장의 테마주 특성에 초점을 맞춘 연구를 진행
- 투자자 심리를 나타내는 감성지표를 반영할 떄, 주가 예측 성능에 크게 영향을 미치는 데이터의 조합을 검토

# 3. 프로젝트 소개 
<img src="https://github.com/MINJAEKH/Stock-Prediction-With-Sentiment-Analysis/assets/109459615/933e8bc0-4a0f-4372-b91e-3ac6ae87419c" alt="scheme" align="center">
![image](https://github.com/MINJAEKH/Stock-Prediction-With-Sentiment-Analysis/assets/109459615/5da21aee-6495-4b7c-8d6f-f77ba09647bc)

- 분석 대상 : 코스닥 테마주에 주목하여 해당 테마에 속하는 대표 종목 (에스엠, 에코프로)
- 텍스트 데이터 : 뉴스, 주식 커뮤니티 (종토넷, 팍스넷)
- 분석 범위 : 각 종목에 대해 활발하게 논의가 오간 기간을 중심으로 6개월
- 모델 : KcElectra (5가지로 세분화하여 분류), conv1D-LSTM 모델

###**실험 결과**
<img src="https://github.com/MINJAEKH/Stock-Prediction-With-Sentiment-Analysis/assets/109459615/4a2127ba-1d27-415a-a64c-19438d089d23" alt="scheme" align="center"> ![image](https://github.com/MINJAEKH/Stock-Prediction-With-Sentiment-Analysis/assets/109459615/4a859004-c33e-428f-bf8b-28ee2eb2d84d)

- 에스엠과 달리 에코프로는 감성분석 반영 여부 자체가 모델 성능에 큰 영향을 미친다.
- 에스엠과 에코프로 모두 **뉴스와 종토넷의 감성지표를 반영**한 결과가 가장 좋은 예측 성능을 보였다.
- 작은 window size 내에서 주가 예측 성능이 우수한 것으로 나타났다.
  - 단기간으로 주가 변동이 심한 테마주의 특성을 고려했을 때, 본 연구에서 제시하는 모델은 **단기적인 움직임**에 빠르게 대응할 수 있음을 시사한다.

# 4. 역할
- 뉴스 데이터 수집
- 텍스트 데이터 전처리, 뉴스 데이터 요약
- 주가 예측 모델링
- 
