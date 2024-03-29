---
title: "A.1 BotContext의 생성"
date: 2019-02-25 11:08:34 -0400
categories: catslab trade botcontext
---

## A.1. BotContext의 생성

BOT_NAME을 지정하여 아래의 parameter를 입력하여 BotContext를 생성할 수 있습니다. 
생성과 동시에 전략에서 사용할 가상화폐와 분봉들의 dataframe을 로드하여 저장합니다.


```python
BOT_NAME = BotContext(api_key, 
		secret_key, 
		init_budget, 
		exchange, 
		initialize, 
		run_strategy, 
		make_orders)
```

__A.1.1. api_key (str)__  
거래소로부터 발급 받은 사용자의 거래소 api key를 입력합니다.


__A.1.2. secret_key (str)__  
거래소로부터 발급 받은 사용자의 거래소 secret key를 입력합니다.


__A.1.3. init_budget (int)__  
사용자의 Bot에서 사용할 자산의 초기 투입 금액을 입력합니다.


__A.1.4. exchange (str)__  
Bot에서 가상 화폐 거래를 할 때 이용할 거래소의 명칭을 입력합니다. 
(해당 거래소에서 발급 받은 api key, secret key를 위의 입력 값으로 사용합니다.) 


__A.1.5. initialize__  
사용자가 Bot을 생성할 때 전략에서 사용할 가상화폐의 종류, 분봉, 거래소의 기축 화폐에 대한 정보와 safety setting에 대한 정보를 저장하는 함수입니다.

자세한 설명과 작성 예시는 A.3. initialize를 참고하시기 바랍니다.


__A.1.6. run_strategy__  
Bot에서 사용하는 전략에서 매수 및 매도를 위해 참고할 기술적 지표를 계산하여 저장하는 함수입니다. 
자세한 설명과 작성 예시는 A.4. run_strategy를 참고하시기 바랍니다.


__A.1.7. make_orders__  
사용자가 정한 방식에 따라 매수주문/매도주문/주문취소 등을 진행하는 함수입니다. 
자세한 설명과 작성 예시는 A.5. make_orders를 참고하시기 바랍니다.


dataframe에 접근하는 방식은 우선 BotContext를 생성할 때의 BOT_NAME class에서 exchanges로 접근하여 Bot에서 사용하는 거래소별 객체로 접근할 수 있습니다. 
각 거래소에서 data로 접근하여 ‘{currency}_{interval}’ 형태의  key값으로 가상화폐 별, 분봉 별 dataframe에 접근이 가능합니다.

생성된 dataframe의 형태는 다음과 같습니다.

![My helpful screenshot]({{"/assets/A.1. DataFrame ex1.png" | absolute_url}}){: width="50%" height="50%"}
![My helpful screenshot]({{"/assets/A.1. DataFrame ex2.png" | absolute_url}}){: width="50%" height="50%"}
![My helpful screenshot]({{"/assets/A.1. DataFrame ex3.png" | absolute_url}}){: width="50%" height="50%"}








