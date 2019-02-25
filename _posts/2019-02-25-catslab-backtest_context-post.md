---
title: "B.1 BacktestContext의 생성"
date: 2019-02-25 17:08:34 -0400
categories: catslab backtest backtestcontext
---

## B.1. BacktestContext의 생성

BACKTEST_NAME을 지정하여 아래의 parameter를 입력하여 BacktestContext를 생성할 수 있습니다. 


```python
BACKTEST_NAME = BacktestContext(user_uuid, 
			initialize, 
			run_strategy, 
			make_orders, 
			use_data, 
			data_path, 
			save_result, 
			return_result)
```

__B.1.1. user_uuid__  
Cats Lab에서 발급 받은 사용자의 user_uuid를 입력합니다.


__B.1.2. initialize__  
A. Trade의 initialize 함수와 동일합니다.


__B.1.3. run_strategy__  
A. Trade의 run_strategy 함수와 동일합니다.


__B.1.4. make_orders__  
A. Trade의 make_orders 함수와 동일합니다.


__B.1.5. use_data (str, ‘LIVE’ 또는 ‘LOCAL’)__  
use_data = “LIVE”로 입력할 경우 거래소 API를 이용하여 입력한 기간만큼의 캔들 데이터를 실시간으로 호출하여 사용합니다.

use_data = “LOCAL”로 입력할 경우 지정한 경로(B.1.6. data_path)의 입력한 가상화폐와 분봉에 해당하는 CSV 파일을 로드하여 사용합니다.

![My helpful screenshot]({{"/assets/B.1. BacktestContext 생성 ex1.png" | absolute_url}}){: width="50%" height="50%"}



__B.1.6. data_path (str)__  
B.1.5. use_data에서 ‘LOCAL’ 모드로 입력하여 사용하는 경우, 캔들 데이터로 사용할 CSV 파일들의 경로를 입력합니다.


__B.1.7. return_result (bool)__  
백테스트의 결과를 반환할 것인지에 대한 여부를 bool 타입으로 입력합니다. 

로컬에서 백테스트를 실행할 경우 백테스트 결과를 확인하기 위해 True로 입력하여 반환 받은 result 객체로 접근이 가능합니다.










