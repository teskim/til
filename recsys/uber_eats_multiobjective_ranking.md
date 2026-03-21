# 한줄요약
- 20260320: retention, profit, diversity가 적정이상이면서 conversion을 최대화로 최적화하는 문제는 weighted sum으로 문제를 풀수 있다.
- 20260321: weighted sum은 random ranking을 적용한 데이터를 기반으로 offline replay를 해서 평가했다. off-policy, position bias 문제를 해결하기 위함이다.

# TODO
- constrained optimization을 어떻게 linear weighted sum으로 표현할수 있는것일까?
- 논문에서 각 term별로 weight은 어떻게 찾았을까?
- 오프라인에서는 어떤 메트릭을 보았을까?