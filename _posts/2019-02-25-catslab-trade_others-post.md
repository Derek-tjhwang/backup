---
title: "A.10. 부가적인 기능의 함수들과 사용 예시"
date: 2019-02-25 16:15:21 -0400
categories: catslab trade others
---

## A.10. 부가적인 기능의 함수들과 사용 예시

거래소별 API를 사용하는 함수에 접근하고, 거래소별 자산, 주문 현황, 체결 현황과 같은 정보에 접근하기 위해서는 Bot을 생성할 때 입력한 거래소의 명칭을 key값으로 가지는 exchanges class에 접근하여 사용이 가능합니다. 
 
전략을 구현하고, Bot을 가동하는 과정에서 실시간으로 사용자의 Bot에 저장되어 있는 정보를 불러오는 함수들과 사용 예시들은 다음과 같습니다.

다음 예시는 “XRP”와 “MIOTA”를 각각 2개씩 매수주문을 넣은 상태에서 각각의 함수를 조회한 예시입니다.

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex1.png" | absolute_url}})



__A.10.1. get_balance 함수__

거래소의 자산 보유량을 실시간으로 조회하는 함수입니다. 다음 예시는 현재의 ‘coinone’ 거래소의 자산 현황을 조회한 결과입니다. 초기 투입금액에서 “XRP”와 “MIOTA”를 각각 2개씩 매수주문을 넣은 상태에서의 자산 변화를 볼 수 있습니다.

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex2.png" | absolute_url}})



__A.10.2. get_time 함수__

현재 시간을 datetime 타입으로 불러오는 get_time 함수입니다.

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex3.png" | absolute_url}})



__A.10.3. get_order_list 함수__

현재 거래소의 미체결 주문 정보를 실시간으로 불러오는 함수입니다.

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex4.png" | absolute_url}})



__A.10.4. get_orders 함수__

Order 객체를 사용하여 set_order 함수(A.7. set_orders 참고)를 사용하게 되면, 생성한 주문들을 내부 함수를 이용하여 거래소로 전송하기 이전에 orders라는 list에 임시적으로 저장을 해 둡니다. 1분마다 스케쥴링을 반복하면서 orders에 추가된 주문을 주문이 지정된 시간별로 거래소로 전송하여 처리하게 됩니다. 전송된 주문들은 orders list에서 빠지게 되고, 미체결된 주문은 order_list에서 관리하게 됩니다.

orders에 저장된 주문은 전송하는 시간을 기점으로 하여 이전의 주문들은 모두 전송하는 방식으로 처리됩니다. 즉, 주문을 생성할 때 현재 시간, 혹은 이전의 시간으로 지정한 경우 다음 스케쥴링에서 거래소로 주문이 전송되며, 주문 시간을 지정하여 나중에 주문이 전송되도록 설정할 수도 있습니다. 예를 들어, 현재 시간의 한 시간 뒤의 시간으로 주문을 지정하는 경우 1시간 뒤 스케쥴링에서 거래소로 전송됩니다. 

get_orders 함수는 현재 orders에 저장되어 있는 주문들의 list를 불러오는 함수입니다. 

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex5.png" | absolute_url}})



__A.10.5. calc_estimated 함수__

calc_estimated 함수는 현재 보유하고 있는 모든 자산의 현금 평가가격을 계산하여 반환해주는 함수입니다.

다음 예시는 “XRP”와 “MIOTA”를 각각 2개씩의 매수주문을 넣고, “XRP”의 주문이 모두 체결 된 상태에서 get_balance, get_order_list, calc_esimated 함수를 조회한 예시입니다. 주문이 체결 됬기 때문에 보유한 자산 목록에 avail이 증가한 것을 확인할 수 있고, 미체결 주문 리스트인 order_list에는 체결되지 않은 “MIOTA”의 주문이 남아 있는 상태입니다. 이때 calc_estimated 함수를 조회하여 조회 시점의 가상화폐의 가격을 기준으로 하여 계산한 현금 평가가격을 확인할 수 있습니다. 

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex6.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex7.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex8.png" | absolute_url}})
![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex9.png" | absolute_url}})



__A.10.6. clear_balance 함수__

clear_balance 함수는 현재 보유하고 있는 가상화폐들을 호가창의 정보를 이용하여 바로 청산을 하는 기능을 수행합니다. 보유하고 있는 가상화폐의 호가창의 가장 높은 금액으로 매도 주문을 넣습니다.

위의 예시에 이어지는 상황으로, “XRP” 주문이 체결된 후 clear_balance 함수를 호출하면 보유하고 있던 1.998개의 “XRP”를 바로 청산 주문을 하여 체결이 된 것을 확인할 수 있습니다.  

![My helpful screenshot]({{"/assets/A.10. 부가적인 기능의 함수 ex10.png" | absolute_url}})


