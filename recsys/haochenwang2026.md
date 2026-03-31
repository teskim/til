# Self-Evolving Recommendation System: End-To-End Autonomous Model Optimization With LLM Agents
### Abstract
(1) proxy metric으로 가설들을 만들고, (2) live production에서 후보군들을 검증한다. 유튜브에서 여럿 런치했기에 효과적임을 검증함.

### Introduction
Training proxy와 유저의 long term user satisfaction은 간극이 있다. proxy를 maximize한다고 해결되는게 아니다. 

기존 autoML에서는 정해진 Reward를 정해진 search space에서 Maximize하는 방식이다.
여기에는 3개의 challenge가 있음
1. 모델의 아키텍처를 바꾸는것에는 automl의 한계가있음.
2. user satisfaction을 위한 reward은 복잡하고 계속 변할수 있고, 사람마다 다를수 있다. 결국 간극이 생기게 된다.
3. Human driven iteration은 unscalable하다.
 
이런것들을 해결하는 FRAMEWORK를 제안한다.