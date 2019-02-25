---
title: "A.7 set_order 함수의 사용과 예시
date: 2019-02-25 16:20:02 -0400
categories: catslab trade
---

## A.7. set_order 함수의 사용과 사용과 예시

Order 객체를 이용하여 생성한 주문들을 거래소 API를 이용하여 거래소에 전송을 하기 위한 함수입니다. 

주문내역에 대한 정보를 저장하는 Order 객체와, 주문 시간을 지정하여 list에 추가한 뒤, 내부 함수를 이용하여 list 저장되어 있는 주문을 거래소로 전송을 합니다. 

거래소로 전송함과 동시에 자산의 보유량을 업데이트하여 변경된 정보를 저장합니다. 보유 자산을 업데이트할 때는 수수료를 고려하여 적용이 됩니다.

```python
def set_order(self, exchange, o, t=None):
```

__A.7.1. exchange (str)__  
Bot에서 사용하는 거래소의 명칭을 입력합니다.


__A.7.2. o (object)__  
make_orders에서 Order 객체를 사용하여 생성하며, 주문할 가상화폐의 종류, 주문 유형, 주문 수량, 주문 가격, 거래소에서 사용하는 기축화폐에 대한 정보를 포함합니다.


__A.7.3. t (datetime.datetime)__  
주문을 요청하는 시간을 입력합니다. 별도로 지정하지 않는 경우 현재시간을 이용하여 주문 시간이 정해집니다.

```python
from coza.objects import Order
from datetime import datetime

# 현재 시간으로 주문
price = data[f’{currency]_{int(interval)}’][‘close’].loc[data[f’{currency]_{int(interval)}’].index[-1]]
buy_order = Order(currency=’xrp’, order_type=’BUY’, fiat=’krw’, price=price, quantity=1.2345)
order_time = datetime.now()
set_order(exchange=’coinone’, o=buy_order, t=order_time)


# 주문 신호가 들어온 캔들의 시간으로 주문
sell_order = Order(currency=’xrp’, order_type=’SELL’, fiat=’krw’, price=342, quantity=5.4321)
t = data[f’{currency]_{int(interval)}’].index[-1]
set_order(exchange=’coinone’, o=sell_order, t=t)
```

![My helpfule screenshot]({{"/assets/A.7. Order 객체 ex1.png" | absolute_url}})
