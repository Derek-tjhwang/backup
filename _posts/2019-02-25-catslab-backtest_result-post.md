---
title: "B.8 plot 함수의 사용 방법 및 사용 예시"
date: 2019-02-25 17:08:34 -0400
categories: catslab backtest Result
---

## B.8. plot 함수의 사용 방법 및 사용 예시

Result 객체를 이용하여 사용할 수 있는 plot 함수는 백테스트에 이용한 가상화폐의 가격(종가 기준)의 변화와 백테스트 과정에서 거래가 발생한 시점마다 저장 되는 평가가격을 기반으로 자산의 변화를 도식화시켜주는 함수입니다. 이 함수의 사용 방법은 다음과 같습니다.

```python
def plot(add_marker, current_list, main_interval)
```


__B.8.1. add_marker (bool)__  
거래가 발생하는 시점을 매수와 매도를 구분하여 marker로 표시할지에 대한 여부를 입력합니다. 

plot 함수는 기본적으로 백테스트 기간 동안 거래에 이용한 가상화폐의 가격 변화 그래프를 보여주는데, add_marker=True로 입력하는 경우 거래가 발생한 매 시점의 가격이 매수주문과 매도주문을 구분하여 가격 변화 그래프 위에 표시됩니다.


__B.8.2. currenct_list__  
그래프를 그릴 때, 사용자가 도식화하고자 하는 가상화폐의 종류를 입력합니다. 

한 가지 가상화폐만 입력할 수도 있고, 여러 개를 입력하는 경우 여러 가상화폐의 가격 변화를 하나의 그래프에 동시에 나타낼 수도 있습니다.


__B.8.3. main_interval__  
입력한 가상화폐의 가격 변화를 종가를 기준으로 하여 그래프를 그리는데, 종가가격의 기준이 되는 분봉을 입력하는 parameter입니다.  

plot 함수의 사용 예시는 다음과 같습니다.


![My helpful screenshot]({{"/assets/B.8. plot 함수의 사용 ex1.png" | absolute_url}}){: width="80%" height="80%"}
![My helpful screenshot]({{"/assets/B.8. plot 함수의 사용 ex2.png" | absolute_url}}){: width="80%" height="80%"}


