---
title: "A.6. Order객체 생성 및 사용 예시"
date: 2019-02-25 15:48:58 -0400
categories: catslab trade
---

##A.6. Order 객체 생성 및 사용 예시
거래소에 주문을 전송하기 전에 Order 객체를 생성하여 list에 저장을 한 뒤, 거래소 API를 이용하는 함수를 사용하여 list에 저장되어 있는 주문들을 한 번에 처리합니다.

class Order(currency, order_type, quantity, price, fiat):

__A.6.1. currency (str)__
거래소에 주문을 넣을 가상 화폐의 명칭을 입력합니다. 
(예: “btc”, “eth”, “xrp”, … )


__A.6.2. order_type (str)__
매수와 매도를 구분하기 위한 parameter입니다. 매수 주문의 경우 “BUY”, 매도 주문의 경우 “SELL” 타입으로 입력합니다.


__A.6.3. quantity (float)__
주문할 가상화폐의 수량을 입력합니다.


__A.6.4. price (int)__
주문할 가상화폐의 가격을 입력합니다.


__A.6.5. fiat (str)__
거래소에서 사용하는 기축화폐를 입력합니다.
(예: “krw”, “usd”, … )


Order 객체의 사용 예시는 다음과 같습니다.

매수주문 (현재 가격으로 주문): 
```python
from coza.objects import Order

price = data[f’{currency]_{int(interval)}’][‘close’].loc[data[f’{currency]_{int(interval)}’].index[-1]]
buy_order = Order(currency=’xrp’, order_type=’BUY’, fiat=’krw’, price=price, quantity=1.2345)
```

매도주문 (지정가 주문): 
```python
from coza.objects import Order

sell_order = Order(currency=’xrp’, order_type=’SELL’, fiat=’krw’, price=342, quantity=5.4321)
```




