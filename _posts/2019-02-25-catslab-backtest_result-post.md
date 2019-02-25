---
title: "B.7. Result 객체의 생성 및 사용 예시"
date: 2019-02-25 17:08:34 -0400
categories: catslab backtest Result
---

생성한 BacktestContext를 run 함수를 이용하여 백테스트를 실행시킨 뒤 그 결과를 Result 객체로 생성하여 저장 및 반환합니다. Result 객체에 저장되어 있는 정보는 아래와 같습니다. 

백테스트 결과를 도식화 하는 plot 함수의 기능은 B.8. plot을 참고하시기 바랍니다.

백테스트 결과를 저장하기 위해 지정한 RESULT_NAME을 이용하여 각각의 정보로 접근할 수 있습니다.


```python
RESULT_NAME = BacktestContext_NAME.run(start_date, end_date, exchange, init_budget, slippage_rate)
```



![My helpful screenshot]({{"/assets/B.7. Result 객체 ex1.png" | absolute_url}})
![My helpful screenshot]({{"/assets/B.7. Result 객체 ex2.png" | absolute_url}})



_B.7.1. created_time_
백테스트를 실행하여 Result 객체를 생성한 시간에 대한 정보입니다.


_B.7.2. elapsed_time_
백테스트를 수행할 때 전체 경과시간에 대한 정보입니다. 


_B.7.3. earning_rate_
백테스트 초기 투입 자산 대비 종료 시점의 자산의 수익률을 나타내는 정보입니다. 

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex3.png" | absolute_url}})



_B.7.4. final_balance_
백테스트 종료 후 최종 시점의 자산 보유량에 대한 정보입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex4.png" | absolute_url}})



_B.7.5. estimated_list_
백테스트를 진행하는 과정에서 매수 또는 매도가 발생했을 때의 거래 정보 및 그 시점에 보유한 모든 자산의 현금 평가가격에 대한 정보를 저장하고 있는 list입니다.

estimated_list에 저장되는 정보의 타입은 ‘datetime’이 key값이고 거래가 발생하는 시점의 datetime을 value값으로 갖는 정보와 ‘estimated’가 key값이고 그 시점의 현금 평가가격을 value값으로 가지는 dictionary 타입입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex5.png" | absolute_url}})


_B.7.6. total_fee_
백테스트를 진행하는 과정에서 일어난 거래들의 총 수수료를 나타내는 정보입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex6.png" | absolute_url}})



_B.7.7. total_slippage_
백테스트를 진행하는 과정에서 입력한 slippage_rate을 기반으로 계산한 총 슬리피지 비용을 나타내는 정보입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex7.png" | absolute_url}})



_B.7.8. max_profit_
백테스트를 진행하는 과정에서 최대로 얻은 이익의 수익률에 대한 정보입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex8.png" | absolute_url}})



_B.7.9. max_loss (float)_
백테스트를 진행하는 과정에서 최대로 손실을 보게 된 시점의 수익률에 대한 정보입니다.

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex9.png" | absolute_url}})



_B.7.10. trade_history (dict)_
백테스트 진행 과정에서 일어난 모든 거래에 대한 정보를 저장하고 있는 dictionary입니다. 

거래가 일어난 시점의 datetime을 key값으로 하고, 거래가 일어난 시점의 자산 보유 현황(‘balance’)과, 수익률(’earning_rate’), 평가가격(‘estimated’), Order 객체로 생성되어 저장되어 있는 ‘order_list’에 대한 정보가 포함되어 있습니다. 

![My helpful screenshot]({{"/assets/B.7. Result 객체 ex10.png" | absolute_url}})



