# 투자자 심리에 따른 테마주 주가 변동 예측 모델
- 2023 2학기 창의적종합설계 팀프로젝트
- 팀원 : 5명

# 1. 프로젝트 기간
- 2023.09 - 2023.12.21

# 2. 기획 배경 및 목적
- 기업의 실적뿐만 아니라 시장 투자자들이 해당 기업을 어떻게 평가하고 있는지에 대한 투자자 반응에 따라 주가가 변동할 수 있다고 분석
- 코스피 시장의 기업 중심으로 주가 예측이 이루어졌던 선행연구가 주를 이룸

- 코스닥 시장의 테마주의 특성에 초점을 맞춘 연구 진행
- 뉴스와 커뮤니티에서 수집된 텍스트 데이터를 활용하여 투자자 심리가 주식의 미래 가격의 변동에 미치는 영향을 조사
- 가장 좋은 주가 예측 결과를 나타내는 데이터의 조합을 검토

# 3. 프로젝트 소개 
<img src="https://github.com/MINJAEKH/Stock-Prediction-With-Sentiment-Analysis/assets/109459615/933e8bc0-4a0f-4372-b91e-3ac6ae87419c" alt="scheme" align="center">

분석 대상의 주식을 선정하기 위해 시가총액, 거래량, 그리고 1년 미만의 짧은 기간 내에 특정한 이슈로 인해 커뮤니티에서 활발한 논의가 이루어진 종목을 중점으로 고려했다. 코스닥 테마주에 주목하여 해당 테마에 속하는 대표 종목, 에스엠과 에코프로를 선정하였다. 텍스트 데이터로는 감성 지표를 파악할 수 있는 뉴스 데이터와 주식 커뮤니티 데이터를 수집하였다. 주식 커뮤니티는 사용자가 많고, 커뮤니티가 활발한 사이트를 중심으로 종토넷과 팍스넷을 선정하였다.

요약된 기사 본문과 주식 커뮤니티 게시글의 데이터를 기반으로 KcElectra모델을 이용하여 감성분석 지표를 도출한다. 0과 1로 긍부정으로 분류하는 문제를 5가지로 세분화하여 분류한다. KcElectra 모델에 전처리된 데이터셋을 적용한 결과, 감성분석 확률이 0.5를 기준으로 대부분 밀집된 형태를 띠고 있다. 커뮤니티의 성향과 그에 대한 의견을 분리시키기 위해 min-max scaling을 진행하여 감성 분석 결과를 주가 예측에 반영하였다. 

휴장일을 제외한 총 124일의 일별 데이터를 사용하여 주가 예측에 활용한다. 이때, 감성분석 결과의 영향과 각 변수의 설명력을 파악하기 위해 변수들의 조합을 사전에 구성하여 Huber Loss로 성능을 비교한다. t-N ~ t-1기까지의 데이터로 t기의 데이터를 예측하는 **conv1D-LSTM 모델**을 구축하였다. 모델의 하이퍼파라미터를 조정하여 주가 데이터만을 입력했을 때 가장 좋은 성능을 보이는 모델의 구조를 채택하였다.

**실험 결과**
- 감성 분석 여부에 따른 결과를 비교했을 때, 에스엠은 감성분석 반영 여부 자체가 실제 LSTM 모델 성능에 영향을 크게 미치지 않는다. 반면, 에코프로는 감성분석 반영 여부 자체가 모델 성능에 큰 영향을 미치고 있으며, 이는 감성분석이 특정 주식의 주가 예측에서 큰 효과를 낼 수 있음을 방증한다.
- 모든 데이터의 조합 결과를 비교했을 때, 에스엠과 에코프로 모두 **뉴스와 종토넷의 감성지표를 반영**한 결과가 가장 좋은 예측 성능을 보였다.
- 데이터 양의 제한으로 더 다양한 window size를 사용하지 못한 관계로, 기존 선행 연구에 비해 작은 window size를 두고 실험을 진행하였다. 다른 조건들에 비해 상대적으로 모델이 window size에 민감하지 않음을 확인하였다. 테마주는 짧은 시기에 주가가심하게 변동하는 특징을 갖는 투자 상품임을 고려할 때 본 연구에서 제시하는 모델은 **단기적인 움직임**에 빠르게 대응할 수 있음을 시사한다.


# 4. 담당 역할
- 뉴스 데이터 크롤링
- 텍스트 데이터 전처리 및 뉴스 본문 요약
- LSTM 모델링 및 성능 비교
