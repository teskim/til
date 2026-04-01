# Self-Evolving Recommendation System: End-To-End Autonomous Model Optimization With LLM Agents
## TIL
- 20260401: 추천고도화에 필요한 작업들을 문서화하고, agent로 분리한것을 보면서 내가 일하던 방식을 다시한번 리마인드 할 수 있어서 좋았고, 일단 내가 이렇게 일을 해봐야겠다 라는 생각이 들었다. 그리고 reward를 정했다면 이걸 어떻게 모델에 녹일수 있는지도 궁금한데, 이부분도 더 찾아봐야겠다.

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

### 문제 정의
Loss Function은 최종 비즈니스 메트릭의 proxy이다. 그러므로 우리가 사용하는 모델은 주어진 optimizer, architecture, reward definition에서 proxy loss를 최소한을 만드는 모델이다.
어떤 구성으로 모델을 만들었냐도 중요하다. 결국 최종 온라인 지표가 가장 좋은 모델이 학습된 configuration을 찾는것이 최종 목표인 것이다.
configuration에는 optimizer, architecture, reward가 주어지고 reward는 training labels를 결정한다.

Q. reward라는게 아직 완전히 와닿지 않는다. reward를 바로 모델이 학습한다면 어떻게 학습하는것인가..?

### 방법론

Offline loop과 Online loop을 나눴다. 그리고 context, 실험 히스토리들을 공유한다.

Offline에서는 reward, optimizer, architecture를 정하는 agent가 각각 있고, 이를 기반으로 코드를 만들고 학습하는 것이다.
Optimizer, architecture는 정해진 Loss를 minimize하는것고, reward는 얼마나 실 로그랑 correlation이 있는지 보는것이다.
