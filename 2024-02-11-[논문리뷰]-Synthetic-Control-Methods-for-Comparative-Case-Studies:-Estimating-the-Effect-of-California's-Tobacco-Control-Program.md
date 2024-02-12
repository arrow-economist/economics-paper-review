---
categories:
  - Paper Review
---

# #PaperReview #SyntheticControlMethod

앞으로는 내가 경제학과인만큼 내가 읽는 논문들에 대해서도 소개하고 정리하는 포스팅을 해보려고 한다.  
그 대망의 첫번째 논문은 나온지 10년 정도 된 따끈따끈한 Method인 **Synthetic Control Method**다.  
이 방법론은 *Journal of the American Statistical Association*이라는 통계학 탑 저널 중 하나에 2010년에 게재된 **Abadie et al. (2010), Synthetic Control Methods for Comparative Case Studies: Estimating the Effect of California's Tobacco Control Program**이라는 논문으로부터 시작한다.  
물론 더 이전에는 **Abadie and Gardeazabal (2003)** 이 논문도 존재하지만, 이 논문이 최초로 well-designed되었다고 여겨진다.  
  
## 소개
경제학뿐만 아니라 사회과학, 그 외의 여러 분야에서 treatment effect를 estimate하고싶어한다. 경제학에서는 policy intervention이 있었을 때, 사회과학에서도 어떤 treatment가 있었을 때 그 이전에 비해 무엇이 얼만큼 달라졌는가를 추정하는 문제는 오래 전부터 중요시 여겨져왔다.  
가장 유명한 method는 아마 **DID (Difference-in-differences)** 일 것이다. *Card and Krueger (1994)* 에서 minimum wage effect를 추정할 때 쓰였던 방법으로 유명한데, 아무래도 간단하고 파워풀하지만 단점이 있다.  
가장 치명적인 단점은 **parellel trend**를 만족해야한다는 것이다. DID에 대해서는 다음에 더 다뤄보기로 하겠다.  
무튼 이런 단점을 해결하기 위해(?) 나온 Synthetic Control Method는 그러한 가정이 필요없다는 점에서 더 쓰기 쉽다고 말할 수 있다. 그러면 이 메소드는 어떻게 추정을 하는 것일까?
  
## Synthetic Control Method
우선 이 논문에서 소개한 California Tobacco Program을 예시로 설명을 하겠다.  
우선 treated unit으로는 California 1개 주가 있고, controlled units로는 그 외의 38개 주가 있다.  
Pre-treatment period, 즉 policy intervention이 있기 전까지의 기간은 19년이고 post-treatment period는 12년이다.  
  
이 정책으로 인해 캘리포니아 주의 담배 소비량이 얼마나 달라졌는지를 연구자는 알고싶어한다.  
  
![캘리포니아 주와 다른 주의 담배소비량 그래프](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/f1.png)
  
이렇게 그래프를 그려보면 1989년을 기준으로 정책이 있고 없기 때문에 단순히 계산을 할 수는 없다.  
Synthetic Control Method는 여기에서 *"혹시 가상으로 treatment를 받지 않은 California주를 만든다면 두 값을 빼주어서 계산이 될 수 있지 않을까?"* 하는 아이디어를 제시한다.  
그렇게 synthetic California unit을 만들기 위해서는 38개주의 값을 하나의 값으로 만들어야하므로, 적절한 weight matrix가 필요할 것이다.  
  
담배 소비량에 대한 설명변수를 $X$라고 하고 이 때 California 주의 설명변수는 $X(1)$, 다른 주의 설명변수는 $X(0)$이라고 해보자.  
그렇다면 우리는 $||X(1)-X(0)W||$를 minimize하는 weight matrix $W$를 생각해볼 수 있다.  
