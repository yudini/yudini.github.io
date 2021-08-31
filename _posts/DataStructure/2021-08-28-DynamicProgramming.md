---
layout: post
title:  "[알고리즘] 다이나믹 프로그래밍 "
date: 2021-08-28
author: yudini
categories: DataStructure Study
comments: true
tags: DynamicProgramming DP DataStructure 
---

## Dynamic Programming(DP)
### 큰 문제를 작은 문제들로 쪼개어 푸는 방식(주로 Bottom-up 방식)
### 하나의 문제는 단 한번만 푼다.
- 작은 문제들이 중복될 때 한번 계산한 결과는 저장해두고 다시 사용한다.(즉 메모이제이션 기법을 이용한다.)

### 메모이제이션(Memoization)
- 동일한 계산을 반복해야 할 경우 한 번 계산한 결과를 메모리에 저장해 두었다가 꺼내 씀으로써 중복 계산을 방지 할 수 있게 하는 기법이다.
<h3 style="color:red">!다이나믹 프로그래밍의 핵심 기법!</h3>

### 조건
- 작은 문제가 반복해서 발생하는 경우
- 같은 문제는 구할 때마다 값이 동일

### 규칙을 찾아 점화식을 세워야한다.
(ex.DP[i]=DP[i-1]+DP[i-2])

<hr>

### 다이나믹 프로그래밍과 분할정복 비교 
![DP vs DaC](/assets/images/DP.png)

<hr>

![fibonacci](/assets/images/fibonacci1.png)

분할정복기법으로 메모이제이션 없이 푼 코드이다. 
~~~C++
#include <stdio.h> 
int fibo(int x){ 
   if(x==1) return 1; 
   if(x==2) return 1; 
   return fibo(x-1) + fibo(x-2); 
} 

int main(void){ 
   printf("%d",fibo(6)); 
} 
~~~

![fibonacci](/assets/images/fibonacci.jpg)

이렇게 재귀적으로 피보나치함수를 구현하게 되면 같은 함수를 여러번 중복하여 호출하게 된다. 특히 위 그림에서 두번째 항은 무려 5번이나 중복되는 것을 볼 수 있다. 재귀적으로 피보나치를 구현할 시 시간복잡도는 2^n이 되며 숫자가 작을 시 문제가 없겠지만 n=50인경우 이는 cpu가 감당하지 못하는 시간이된다.

<hr>

![fibonacci](/assets/images/fibonacci2.jpg)

이러한 단점을 해결하기위해 메모이제이션을 이용하는 다이나믹 프로그래밍 기법을 사용할 수 있다. 먼저 재귀호출을 사용하는 Top-down 방식이다. top-down 방식은 큰 문제를 작은 문제들로 나누어 푼 후 큰 문제를 푸는 방식이다. 처음부터 큰 문제를 방문 후 작은 문제를 호출하는 방식이라고 볼 수 있다. (예를들어 n번째 항을 구하기 위해서 n-1과 n-2로 문제를 나눠야한다. 
이런식으로 문제를 작게 나눈 후 작은 문제들을 다 풀었으면 결론적으로 마지막엔 n-1과 n-2의 값을 더해 n번째 항을 구한다.)

### DP(Top-down)
~~~c++
#include <stdio.h>                                                   
int d[100]; 

int fibo(int x){ 
  if(x==1) return 1; 
  if(x==2) return 1; 
  if(d[x]!=0) return d[x]; 
  return d[x] = fibo(x-1) + fibo(x-2); 
} 

int main(void){
  printf("%d",fibo(6)); 
} 

~~~
위 코드를 보면 재귀 함수를 호출하여 값을 구하고 구한 값을 배열에 저장하여 한번 구하여 배열에 값이 있는 경우는 함수 호출 없이 그 배열 값만 리턴해주는 코드이다.
여기서 이 **d**라는 배열이 DP테이블이 되어 이곳에 값들을 저장하는 것입니다. 
<hr>

다음으로는 bottom-up방식이다. DP는 주로 bottom-up 방식으로 구현하는데, bottom- up 방식은 문제를 크기가 작은 문제부터 차례대로 푼 후 조금씩 더 큰 문제를 푸는 방식이다. Top-down이 큰 문제부터 접근하여 나누는 방식이라면, botoom-up은 접근을 작은것부터 하는것이다. 주로 반복문을 사용하여 구현 할 수 있다. 

### DP(Bottom-Up, 점화식 필요)
~~~c++
#include <stdio.h>                                              
int d[100]; 
int fibo(int x){ 
  d[0]=0; 
  d[1]=1; 
  for(int i=2;i<=x;i++){ 
     d[i]=d[i-1]+d[i-2]; 
  } 
  return d[x]; 
}
 
int main(void){ 
  printf("%d",fibo(6)); 
} 
~~~

코드를 보면 먼저 배열에 작은 항부터 구하여 저장하고 점점 큰 항을 구해 원하는 x항까지 배열에 저장하여 리턴하는 것을 볼 수 있다. 이곳에서 점화식은 ***d[i]=d[i-1]+d[i-2]*** 고, 이 코드는  n까지만 반복하면 되므로 시간복잡도는 n이라고 볼 수 있다.



<hr>


<h4>&#8251;오류가 있다면 댓글로 알려주세요!</h4>