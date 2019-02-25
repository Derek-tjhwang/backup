---
title: "B.2. Backtest 실행"
date: 2019-02-25 17:08:34 -0400
categories: catslab backtest runbacktest
---

생성한 BacktestContext를 run 함수를 이용하여 백테스트를 실행시킵니다. 
결과를 저장할 RESULT_NAME을 지정합니다.


```python
RESULT_NAME = BACKTEST_NAME.run(start_date, end_date, exchange, init_budget, slippage_rate)
```

__B.2.1. start_date (datetime.datetime)__
백테스트를 실행할 기간 중 시작 시점의 datetime을 입력합니다.


__B.2.2. end_date (datetime.datetime)__
백테스트를 실행할 기간 중 종료 시점의 datetime을 입력합니다.


__B.2.3. exchange (str)__
백테스트를 실행할 때에 사용할 거래소의 명칭을 입력합니다.


__B.2.4. init_budget__
백테스트의 초기 투입 자산을 입력합니다.


__B.2.5. slippage_rate__
백테스트를 실행할 때 고려할 슬리피지 비율을 입력합니다. 실제 거래와 달리 백테스트에서는 주문한 매수주문/매도주문은 즉시 체결된 것으로 간주하여 결과를 반영하기 때문에, 실제 거래에서 발생할 수 있는 주문 미체결의 문제와 호가의 차이를 고려한 것이 슬리피지 비율입니다.








