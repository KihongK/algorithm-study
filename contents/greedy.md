# 탐욕법(Greedy) 알고리즘 요약설명 

- 문제를 작은 단위로 쪼개 반복적으로 진행하며 접근하는 방식이다.
- 탐욕법은 각 단계마다 현재에 충실한 선택을 한다.
- 미래의 선택, 최종 결과는 고려하지 않는다.
- 반드시 최적의 해를 보장하는건 아니다.

### 탐욕법 문제 풀이 순서
1. 해 선택 
    - 현재 단계에 가장 최적의 해를 구해서 부분해 집합에 포함시킨다.
2. 적절성 검사
    - 포함시킨 부분해 집합이 문제의 조건을 만족하는지 검사한다.
    - 만족하지 않을 경우, 한 단계 전으로 돌아가 다른 해를 구해 부분해 집합에 포함한다
3. 해 검사
    - 포함시킨 부분해 집합이 문제의 해가 되는지 검사한다. 
    - 아직 문제의 해가 완성되지 않았다면 1번부터 다시 시작한다.

### 탐욕법을 활용한 문제
- 동전을 최소 개수로 거슬러주기
- [체육복](https://github.com/TheCopiens/algorithm-study/blob/ohhako/source/ohhako/200202_greedy.md)