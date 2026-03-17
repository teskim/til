# Economic Recommender System survey

- 한 줄 요약: price sensitivity를 고려하면 interest를 높힐수 있다.
- 날짜: 2026-03-17

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