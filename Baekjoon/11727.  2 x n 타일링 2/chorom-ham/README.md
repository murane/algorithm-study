# 11727. 2 x n 타일링

## 풀이 방법

dp[i] : 2*i 직사각형을 1×2, 2×1과 2×2 타일로 채우는 방법의 수를 10007로 나눈 나머지

우선 작은 수(1, 2)에 대해서는 직접 그려 경우의 수를 파악했다. 

그다음 점화식을 찾으려고 했다. 

3이상의 i에 대해서 
```cpp
//dp[i]의 경우의 수는 
//2*(i-1) 타일링 경우의 수(dp[i-1]) * 1(이유: 1*2 타일 한가지만 사용 가능)
//2*(i-2) 타일링 경우의 수(dp[i-2]) * 2(이유: 2*2칸을 채우는 경우의 수 3 - 위의 경우 중복 1)
dp[i] = dp[i-1] + dp[i-2] * 2;
```
이라는 점화식을 세웠다.

## 어려웠던 부분 혹은 새로 알게 된 내용

문제의 예시 테스트 케이스에 대한 답은 잘 나오는데 백준에서 채점하니 틀렸다고 나와서 당황했다.

알고보니 숫자가 조금만 커져도 정수형이 담을 수 있는 수의 범위를 넘어가서 틀렸었던 것이다.

modulo 연산의 특성을 사용해 문제를 해결했다.