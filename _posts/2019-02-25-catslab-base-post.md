---
title: "A.0.Trade 기본"
date: 2019-02-25 10:48:59 -0400
categories: catslab trade
---

A.0. COZA package 및 필요한 모듈 및 함수 import
필수 
BotContext 생성을 위한 import 합니다.
```python
from coza.bot import BotContext
```

거래소에 주문을 넣기 위한 Order 객체 import 합니다.
```python
from coza.objects import Order
```

부가적으로 사용할 패키지 내의 객체나 함수 import
전략에서 이용할 TA들을 import 합니다.
```python
from coza.ta import (TA_NAME)
```
