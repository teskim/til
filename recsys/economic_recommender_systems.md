# Economic Recommender System survey

- 한 줄 요약: price sensitivity를 고려하면 interest를 높힐수 있다.
- 날짜: 2026-03-17

- 한 줄 요약: utility modeling은 유저는 가격대비 효용이 가장 높은 것을 구매한다는 가정으로 효용성을 모델링할수 있다. 구매한 제품의 갯수, 대체제, 보완재에 따라서 모델링할 수 있다.
- 날짜: 2026-03-18

- 한 줄 요약: profitablity는 플랫폼 수익성과 유저의 연관성을 잘 밸런싱하는것이 중요하다.
- 날짜: 2026-03-19

- 한 줄 요약: 추천의 형태가 바뀌기도 한다. 할인율을 정할수도 묶음추천으로 확장하여 AOV를 늘리기도 한다. LTV를 예측하기도 한다.
- 날짜: 2026-03-24(1)

- 한 줄 요약: 추천으로 수익성을 내기 위해서는 연관성과 tradeoff가 발생한다. 하지만 추천의 신뢰도가 올라갈수록 구매할 확률이 올라가긴 할것 이다.
- 날짜: 2026-03-24(2)

## Introduction

ESRS에서는 5가지 관점을 고려한다.
- 고객 관점: 관련도가 높으면서 그중에 가격이 높은것을 더 추천해보자.
    - => 이상적으로는 이부분을 계속 고민하는것이 가장 좋은 방법이라고 생각함.
    - Price sensitivity: 가격에 민감하니 이를 더 활용하여 추천하자.
        - => CVR에 대한 accuracy에 가까운듯.
    - Economic Utility Modeling: 핸드폰같은 것을 근래에 구매한 경우 재구매할확률이 낮다. 이런 것을 economic utility라고 하는데 이를 이용해서 모델링하자.
        - => true negative를 늘려가는 방식중 하나.
- 조직 관점: 조직의 KPI를 직접적으로 활용하여 추천하자ㅏ.
    - => 이게 좀더 KPI를 늘리는데는 쉬울수도 있다.
    - 조직의수익기반: 조직의 KPI를 직접적으로 활용하여 추천하자ㅏ.
    - 프로모션: 프로모션 상품들을 의도적으로 자주 노출시킨다. 이는 고객이 충동적으로 살 수 있도록 유도할 수 있다. 고객이 발견하지 못한 프로모션을 추가로 보여줄수도 있다.
    - 장기적 가치 지속가능성: 더많은 상품/구매를 하여 고객의 lifetime value를 높힐수도 있을것이다.

## Price Sensitibility Method
### 모델링
Matrix Factorization은 user-item dot product을 통해 item을 추천하는것.
  - 여기에 **cost**를 objective function에 추가하면 더 정확도가 올라간다.
  - unseen user-category에 대해서 cost preference를 첨가하면 정확도가 방어된다.
    - 기존에 잘 안되었던것에 cost signal을 추가한 느낌.
  - context aware recsys에서 구매하는데 필요한 것들 (가격, 할인, seller 평판)이 정확도에 영향을 준다.
  - price를 피처로 추가했더니 성능이 올랐다.
### 후처리
price sensitivity를 score로 두고, interest와 price sensitivity를 고려한다.

## Economic Utility Modeling Methods
- 효용이라는건 추상적이다. Ranking model의 score를 utility로 볼수도 있다. utility_user_item
- 상품의 속성별로 효용성을 나눠볼수도 있다. sum_attribute(impartance_user_attribute * utility_item_attribute)
- 구매한 횟수에 따라서 상품의 효용성이 달라지기도 한다. 컴퓨터는 한번 구매하면 새로운 컴퓨터에 대한 효용성이 더 커지지 않는다. 기저귀는 갯수가 늘어날수록 효용성이 커진다.
- 상품간의 관계도 있다. 보완제 대체제에 따라서 효용성이 달라진다 이를 모델링 하기도 한다.

## Profit Aware Method
### Modeling
- 이익을 통해 추천모델을 고도화. Pareto optimization으로 CTR, GMV를 모두 최적화하는 방법도 있음
- 대부분 전통적인 방식이고, 실제 우리랑 관련이 커보이지 않는다.

### Postprocessing -> user interest와 profit이 적절히 밸런싱 되어야함.
- pCTCVR*V(item)은 relevance가 심하게 깨지진 않지만, 2개의 밸런싱을 찾기가 어려움. 
  - 내생각에는 가격차이가 심한 상품은 비싼게 높게 랭킹될 가능성이 있음.
  - the organization could risk losing loyal customers should they feel dissatisfied with overly biased recommendations toward higher-value items and decide to leave the platform.
- 구매할 확률이 어느정도 높은것 + 가격이 어느정도 낮은것에 대해서 sum(v)를 맞춘다.

## Promotional
- 할인되는것을 추천 혹은 가격을 맞추는것에 대한 연구들이 있지만 실용적인지 검증이 되지 않음.
- 묶음으로 판매하는 것은 연관된 묶음을 잘 추천하여 aov를 증가시킬수 있다.
- LTV를 예측하는것도 있는데, 결국 추천퀄리티가 좋아야 그만큼 수익성있는것을 추천할때 효과가 좋다는 직관도 있다.

# Evaluation
## Offline eval
- profit@k, pNDCG@k, expectedProfit@k 이런걸 주로 본다고 함.

# Future work
- Profitability - recommendation 의 퀄리티는 purchase propensity가 연관있다. Profit과 relevance간에 밸랜스가 중요하다