# SMP 예측
SMP란 System Margin Price의 줄임말로, 
전기발전사업자로부터 생산된 전기를 한국전력이 구매할 때 설정된 가격입니다.
<br>
데이터셋은DACON의 '공공 데이터 활용 전력수요 및 SMP 예측 AI 경진대회'에서 다운 받아 재가공했습니다.
https://dacon.io/competitions/official/235606/overview/
<br>
LSTM모델은 28일간의 SMP(최댓값, 최솟값, 평균), weather(온도 최댓값&최솟값, 습도 최댓값&최솟값)을 속성으로 사용합니다.
ARIMA모델은 장기간의 SMP평균을 입력으로 사용합니다.
둘의 평균을 구해, hybrid ARIMA-LSTM 모델로 미래의 SMP 평균값을 예측합니다.

실행 환경
-
- Python 3.5.2
- tensorflow 1.11.0
- statsmodels 0.11.1
- pandas 0.24.2
- numpy 1.18.4
- matplotlib 3.0.3
- sklearn

파일 설명
-
- RKNN : rknn 모델로 구동
- Tensorflow : tensorflow모델로 구동

코드 실행
-
Tensorflow모델은 각각 LSTM, arima 모델을 따로 작성했습니다.

```
cd Tensorflow
python LSTM.py
python arima.py
```

RKNN모델은 hybrid ARIMA-LSTM모델로 두 모델을 합쳐 작성했습니다.
```
    cd RKNN
    python run.py
```

rknn을 변환하는 코드입니다.
```
    cd RKNN
    python convert.py
```

결과
-
hybrid ARIMA-LSTM모델의 예측값과 실제값을 비교한 그래프입니다.
<img src="/RKNN/output(hybrid2).png">
빨간선: 예측값, 파란선: 실제값
<br>

LSTM, ARIMA, hybrid ARIMA-LSTM 모델의 예측값과 실제값을 비교한 그래프입니다.
<img src="/RKNN/output(hybrid).png">
빨간선: LSTM, 초록선: ARIMA, 노란선: hybrid ARIMA-LSTM, 파란선: 실제값

