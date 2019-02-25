---
title: "A.5 make_orders 함수의 작성 및 예시"
date: 2019-02-25 15:44:30
categories: catslab trade
---

전략에서 사용하는 매수/매도 방식에 따라 매수주문/매도주문/주문취소를 진행합니다. 주문을 생성할 때는 Order 객체를 이용하여 생성하고, 생성한 주문들은 set_order 함수를 이용하여 주문 내역에 저장합니다. 주문 내역에 있는 주문들은 거래소 API를 이용하는 내부 함수를 사용하여 거래소로 전송됩니다. 주문 취소의 경우 set_cancel을 통해 거래소로 전송이 가능합니다.

주문을 생성하는 Order 객체 생성은 A.6.을 참고하시고, 생성한 주문을 거래소에 전송하기 위해 list에 추가하는 set_order 함수는 A.7.을 참고하시기 바랍니다. 또한, 체결 이전의 주문들의 정보를 저장하고 있는 order_list에 대한 내용은 A.8.에서, 주문 취소를 요청하는 set_cancel 함수에 대한 설명과 사용 방법은 A.9.을 참고하시기 바랍니다.

def make_orders(self, is_update, trade_info, update_len, data): 

__A.5.1. is_update (dict)__  
run_strategy 함수의 parameter와 동일합니다.


__A.5.2. trade_info (dict)__  
run_strategy 함수의 parameter와 동일합니다.


__A.5.3. update_len (dict)__  
run_strategy 함수의 parameter와 동일합니다.


__A.5.4. data (dict)__  
run_strategy 함수의 parameter와 동일합니다.


make_orders 함수의 사용 예시는 다음과 같습니다.
다음 예시는 위의 run_strategy를 기반으로 5일 이동평균선이 20일 이동평균선을 상향 돌파하는 순간 매수, 하향 돌파하는 순간 매도하는 전략입니다.
```python
def make_orders(self, is_update, trade_info, update_len, data):
    exchange = 'coinone'
    interval = 1
    
    total_fiat = self.exchanges[exchange].balance['fiat']
    
    for currency in trade_info['coinone']['currency']:
        current_index = data[f'{currency}_{int(interval)}'].index[-1]
        t = current_index
        
        if data[f'{currency}_{int(interval)}']['ema_20'].loc[current_index-timedelta(seconds=60)] \
        < data[f'{currency}_{int(interval)}']['ema_60'].loc[current_index-timedelta(seconds=60)] \
        and data[f'{currency}_{int(interval)}']['ema_20'].loc[current_index] \
        > data[f'{currency}_{int(interval)}']['ema_60'].loc[current_index]:
            order_type = 'BUY'
            price = data[f'{currency}_{int(interval)}']['close'].loc[current_index]
            quantity = math.floor( round (total_fiat*0.5 / price * 10**4, 4) )/(10**4)
            if quantity >= 1.0 and price * quantity <= self.exchanges[exchange].balance['fiat']:
                o = Order(currency=currency, order_type=order_type, fiat='krw', price=price, quantity=quantity)
                self.set_order(exchange=exchange, o=o, t=t)
                
        elif data[f'{currency}_{int(interval)}']['ema_20'].loc[current_index-timedelta(seconds=60)] \
        > data[f'{currency}_{int(interval)}']['ema_60'].loc[current_index-timedelta(seconds=60)] \
        and data[f'{currency}_{int(interval)}']['ema_20'].loc[current_index] \
        < data[f'{currency}_{int(interval)}']['ema_60'].loc[current_index]:
            order_type = 'SELL'
            price = data[f'{currency}_{int(interval)}']['close'].loc[current_index]
            quantity = math.floor(round(self.exchanges[exchange].balance[currency]['avail'] * 10**4, 4))/(10**4)
            if quantity >= 1.0:
                o = Order(currency=currency, order_type=order_type, fiat='krw', price=price, quantity=quantity)
                self.set_order(exchange=exchange, o=o, t=t)
```


