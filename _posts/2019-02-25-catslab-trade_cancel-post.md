---
title: "A.9. set_cancel 함수의 사용과 사용 예시"
date: 2019-02-25 16:15:21 -0400
categories: catslab trade others
---

## A.9. set_cancel 함수의 사용과 사용 예시

거래소에 전송한 주문 중 미체결 주문들을 취소할 때 사용할 수 있는 함수입니다. 

```python
def set_cancel(self, exchange, currency=None, order_id=None, qty=None):
```

__A.9.1 exchange (str)__

Bot에서 사용하는 거래소의 명칭을 입력합니다.


__A.9.2. currency (str)__

취소할 주문의 가상화폐를 입력합니다. 
(예: “btc”, “eth”, “xrp”, … )


__A.9.3. order_id (str)__

취소할 주문의 order_id를 입력합니다. 

order_id를 입력하여 주문을 취소하는 경우 currency를 함께 입력해야 합니다.


__A.9.4. qty (float)__

주문 취소할 수량을 입력합니다. 

수량을 입력하지 않는 경우 입력한 currency 또는 currency의 order_id에 남아 있는 주문 수량 전체를 취소합니다.


다음은 주문을 취소하는 4가지 방법에 대한 예시입니다. 



![My helpful screenshot]({{"/assets/A.9. set_cancel ex1.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex2.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex3.png" | absolute_url}})

![My helpful screenshot]({{"/assets/A.9. set_cancel ex4.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex5.png" | absolute_url}})

![My helpful screenshot]({{"/assets/A.9. set_cancel ex6.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex7.png" | absolute_url}})


4개의 ‘XRP’ 주문이 들어간 상태에서 거래소의 미체결 주문 현황과 Bot의 order_list에 저장되어 있는 주문들에 대한 정보입니다.


__cancel #4__

```python
set_cancel(exchange=EXCHANGE_NAME, currency=CURRENCY, order_id=ORDER_ID, qty=QUANTITY)
```

입력 받은 거래소의 해당 가상 화폐와 order_id를 갖는 주문을 입력받은 수량 만큼 부분 취소합니다. 입력한 qty가 미체결 수량보다 많은 경우 전체 수량을 취소하고, 적은 경우에는 부분 취소합니다. 

![My helpful screenshot]({{"/assets/A.9. set_cancel ex8.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex9.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex10.png" | absolute_url}})

주문 수량이 1이었던 주문을 0.5 수량만큼을 부분 취소하는 경우 order_list에서 해당 order_id의 remain_qty가 0.5로 남아 있는 것과, 거래소 미체결 주문 현황에 주문잔량이 0.5000으로 저장되어 있는 것을 확인할 수 있습니다.


__cancel #3__

```python
set_cancel(exchange=EXCHANGE_NAME, currency=CURRENCY, order_id=ORDER_ID)
```

qty를 입력하지 않는 경우 해당 가상화폐의 order_id를 갖는 주문의 미체결 수량 전체를 취소합니다.


![My helpful screenshot]({{"/assets/A.9. set_cancel ex11.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex12.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex13.png" | absolute_url}})


__cancel #2__

```python
set_cancel(exchange=EXCHANGE_NAME, currency=CURRENCY)
```

order_id를 입력하지 않고 가상화폐에 대한 정보만 입력한 경우 입력한 거래소의 currency에 해당하는 주문을 전부 취소합니다.

![My helpful screenshot]({{"/assets/A.9. set_cancel ex14.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex15.png" | absolute_url}})

거래소 명칭과 전체 취소할 가상화폐만을 입력한 경우, order_list와 거래소 미체결 주문 현황에 저장되어 있던 이전의 ‘XRP’ 주문들이 순차적으로 취소되어 모두 취소된 것을 확인할 수 있습니다.


__cancel #1__

```python
set_cancel(exchange=EXCHANGE_NAME)
```

거래소의 명칭만 입력한 경우, 입력 받은 거래소에 전송된 주문에 대하여 가상화폐의 종류, 남은 수량과 관계 없이 모든 미체결 주문을 전체를 취소합니다.

![My helpful screenshot]({{"/assets/A.9. set_cancel ex16.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex17.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex18.png" | absolute_url}})

![My helpful screenshot]({{"/assets/A.9. set_cancel ex19.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex20.png" | absolute_url}})

![My helpful screenshot]({{"/assets/A.9. set_cancel ex21.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex22.png" | absolute_url}})

![My helpful screenshot]({{"/assets/A.9. set_cancel ex23.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.9. set_cancel ex24.png" | absolute_url}})

‘XRP’와 ‘MIOTA’가 각각 수량 1 씩 주문된 상태에서, 거래소 명칭(예시에서는 ‘coinone’)만을 입력하여 set_cancel 함수를 호출한 경우 두 가상화폐의 미체결 주문들이 모두 취소 된 것을 확인할 수 있습니다.


