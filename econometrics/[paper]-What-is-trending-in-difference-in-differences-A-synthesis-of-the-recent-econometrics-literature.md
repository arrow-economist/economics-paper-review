# 논문리뷰 (DID survey)
# What's trending in difference-in-differences? A synthesis of the recent econometrics literature

오랜만에 논문리뷰를 올린다. 사실 그 이후로도 여러 논문을 읽긴 했지만, 뭔가 여기에 올리려면 대단하고 좋은 페이퍼면서도 내가 완벽히 이해했다고 생각되는 논문만 올려야할 것 같아서 그동안 올리는 것을 꺼려했다.
최근에 읽은 논문 중 괜찮았고, 또 역시 많이 cite 되고 있는 논문은 **Difference-in-Differences**에 대한 literature review paper다.  
의외로 *Journal of Econometrics*에 실린 논문인데, 왜 *Journal of economic literature*이라는 논문 말고 뭔가 theoretical한 페이퍼가 대부분인 *JoE*에 실렸는지는 의문이다. 아마 빅네임의 영향이기도 하고, 워낙 정리를 또 잘해서기도 하겠지?
  
## 소개
내 첫 리뷰 페이퍼는 **Synthetic Control Method**에 대한 논문인데, 이런 정책 분석을 하는 방법 중에서는 가장 전통적인게 *DID*다.  
Policy Intervention과 같은 어떠한 treatment의 영향을 추정할 수 있기 때문에 경제학 뿐만아니라 여타 다른 사회과학에서도 많이 쓰이고 있다.  
standard한 DID를 쓰기 위해서는 다소 강한 가정이 필요한데, 의외로 이를 만족하는 empirical example은 흔하지 않다.  
그런데도 많은 경우 이러한 assumption이 지켜지는지를 따지지 않고 무작정 쓰는데, 그러한 경우는 추정이 잘못되었다고 비판받기 쉽다.  
이 논문에서는 주요 가정을 소개하고 이게 violate(위배)되었을 때 어떤 다른 페이퍼를 통해서 해결할 수 있는지를 정리하여 Empirical analysis를 하는 연구자들에게 알려준다.
  
## Checklist for DID practitioners
논문의 초반에는 DID를 사용하는 연구자들을 위한 체크리스트가 소개되어있는데, 그 일부는 다음과 같다.

### 1. unit 들이 같은 시기에 treat를 받는가?
그렇다면, 또 여기에 더해 패널 데이터가 balanced인 경우는 간단한 two way fixed effect 모델로도 충분히 추정이 가능하다고 한다. 그러나 그렇지 않은 경우 staggered adoption이 들어간 estimator를 사용해야한다.

### 2. Parallel Trend Assumption을 만족하는가?
그렇다면 그 이유에 대한 justification이 필요할 것이다고 한다. 그렇지 않으면 여타 다른 방법을 통해 해결이 가능하다고 한다. (논문 속에 소개된 방법을 통해)

## Basic DID Setup
혹시 DID에 대해 잘 모르는 사람이 있을 수도 있기 때문에 이에 대해서 논문에서 설명한 방식에 따라 간략하게 설명해보고자 한다. 우선, time은 $t= 1,2$가 존재하고, 유닛은 $i = 1, 2, \cdots, N$으로 표기한다. 어떠한 intervention은 1기와 2기 사이에 일어난다고 가정하면, 1기는 pre-treatment period가 되고 2기는 post-treatment period가 된다.\
$Y_{i,t}(0,0)$는 두 period에서 모두 untreated인 unit $i$의 period $t$일 때 potential outcome으로 정의한다. 마찬가지로, $Y_{i,t}(0,1)$은 2기에서 treated가 되는 unit $i$의 period $t$일 때의 potential outcome이 된다. 그런데 notation을 단순화하기 위해서 $Y_{i,t}(0) = Y_{i,t}(0,0)$, $Y_{i,t}(1) = Y_{i,t}(0,1)$로 표현할 수 있다.\
이 때, Average Treatment Effect on the Treated (ATT)는 다음과 같이 정의된다.\
$\tau_2 = \mathbb{E}[Y_{i,2}(1) - Y_{i,2}(0) |D_i = 1]$

## References  
- Roth et al. (2023), "What's trending in difference-in-differences? A synthesis of the recent econometrics literature." *Journal of Econometrics* 235, 2218-2244.
- Callaway., Brantly, Sant’Anna., Pedro H.C., (2021), "Difference-in-Differences with multiple time periods." *Journal of Econometrics* 225 (2), 200–230.
## 참고할만한 다른 논문
- Doudchenko., Nikolay, Imbens., Guido W., (2016), "Balancing, Regression, Difference-In-Differences and Synthetic Control Methods: A Synthesis." *Working Paper* 22791, National Bureau of Economic Research.
- Rubin., Donald B., (1974), "Estimating causal effects of treatments in randomized and nonrandomized studies." *J. Edu. Psychol.* 66 (5), 670–688.
- Donald., Stephen G., Lang., Kevin, (2007), "Inference with Difference-in-Differences and Other Panel Data." *Rev. Econ. Stat.* 89 (2), 221–233.
