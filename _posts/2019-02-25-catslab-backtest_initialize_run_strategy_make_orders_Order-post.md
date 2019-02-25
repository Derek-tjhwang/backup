---
title: "B.3. ~ B.6. initialize, run_strategy, make_orders, Order 작성"
date: 2019-02-25 17:08:34 -0400
categories: catslab backtest initialize, run_strategy, make_orders, Order 
---

# B.3. initialize의 작성

A. Trade의 initialize 함수와 동일합니다.


# B.4. run_strategy 작성

기본적으로 A. Trade의 make_orders 함수와 동일하나 1분 주기로 dataframe을 업데이트하고 그에 따른 기술적 지표를 업데이트하는 Trade에서와는 달리, Backtest에서는 dataframe의 업데이트가 발생하지 않고 처음 BacktestContext를 생성할 때 입력된 기간동안의 dataframe 및 기술적 지표를 한 번에 연산하여 저장합니다. 

백테스트를 실행하면 사용자가 입력한 가상화폐와 분봉들마다 저장해놓은 dataframe을 순차적으로 잘라서 가져오는 방식이기 때문에 1분 주기로 run_strategy를 실행하는 과정이 생략됩니다.


# B.5. make_orders 작성

A. Trade의 make_orders 함수와 동일합니다.


# B.6. Order 객체 생성

A. Trade의 Order 객체와 동일합니다.








