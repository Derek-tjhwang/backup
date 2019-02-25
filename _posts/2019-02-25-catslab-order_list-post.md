---
title: "A.8 Order_list"
date: 2019-02-25 15:57:08 -0400
categories: catslab trade
---

##A.8. order_list
Order 객체를 이용하여 생성된 주문은 내부 함수를 거쳐 거래소로 전송된 뒤에 BotContext의 exchanges 내부 order_list에 저장됩니다. 가상화폐 종류를 key값으로 하여 가상화폐 별로 다시 dictionary를 관리합니다. dictionary의 key값은 order_id로 하고, 해당 order_id의 주문 정보가 dictionary 타입의 value값으로 저장됩니다.

주문한 수량의 전체가 체결이 되거나, 전체가 취소될 경우 order_list에서 제거가 되며, 자산의 업데이트가 진행됩니다. 부분 체결 및 부분 취소가 발생한 경우에도 자산의 업데이트가 진행되며, 미체결 수량이 존재하는 경우에는 remain_qty에 그 수량을 저장합니다. 

order_list에 대한 예시는 다음과 같습니다. coinone_bot이라는 BotContext에 저장되어 있는 order_list로, ‘iota’와 ‘xrp’에 관련된 미체결 주문 정보가 저장되어 있는 것을 볼 수 있습니다. 
![My helpful screenshot]({{"/assets/A.8. order_list ex.png" | absolute_url}})

__A.8.1. currency__
주문한 가상화폐의 명칭을 저장합니다.


__A.8.2. fee__
주문한 수량을 기준으로 계산한 수수료에 대한 정보입니다. ‘order_type’이 ‘SELL’인 경우 ‘fee’에 저장된 값은 Bot에서 사용하는 거래소의 기축화폐에 해당합니다. 


__A.8.3. fiat__
Bot에서 사용하는 거래소의 기축화폐의 정보입니다.


__A.8.4. order_type__
매수 주문인지 매도 주문인지 구분하는 역할을 합니다.


__A.8.5. price__
주문 가격에 대한 정보입니다.


__A.8.6. quantity__
주문한 수량에 대한 정보입니다.


__A.8.7. remain_qty__
주문한 수량에서 부분 체결이나 부분 취소가 발생하고 난 뒤의 미체결 된 주문 수량에 대한 정보입니다.


__A.8.8. timestamp__
주문한 시간의 timestamp값에 대한 정보입니다.
