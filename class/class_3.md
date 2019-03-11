# Class 3
Current/Most recent session:
> 2019/03/qq

## 개요

1. 실습/프로그래밍 환경에 대해
2. 랩 과제 질의응답/ 설명 
3. 이론
4. Visual Studio 시도 ㄱㄱ

## 실습/프로그래밍 환경에 대해
PuTTY? XShell? Visual Studio?

### 왜 아직도 Visual Studio를 사용하지 않지??
> 그냥 제가 알려드리겠습니다 ㅎㅎ

[다운로드 설명 링크](https://note0913.tistory.com/84) \
[프로젝트 생성 방법 링크](https://studyc.tistory.com/m/27) \
[컴파일 방법 링크](https://dojang.io/mod/page/view.php?id=8)

## 랩 과제 질의응답 / 설명
**Lab 3-1**

두 정수를 입력 받아 합과 평균 구하여 출력하는 프로그램을 작성하시오. \
아래의 사용자 정의 함수를 반드시 정의하고 사용할 것

add()        : 두 정수의 합을 계산하여 반환 \
average() : 두 정수의 평균을 계산하여 반환 \
printResults(int x, int y, int sum, float avg) : 결과 출력  \
평균은 소수 첫째 자리까지 나타낼 것

2개의 정수를 입력 받아 몫과 나머지를 구하여 아래와 같이 출력하는 프로그램을 작성하시오.
아래의 사용자 정의 함수를 반드시 정의하고 사용할 것
void divide (int dividend, int divisor, int *quotient, int *remainder)
void printResults (int quotient, int remainder)

**Lab 3-2**

2개의 정수를 입력 받아 몫과 나머지를 구하여 아래와 같이 출력하는 프로그램을 작성하시오. \
아래의 사용자 정의 함수를 반드시 정의하고 사용할 것 \

> void divide (int dividend, int divisor, int *quotient, int *remainder) \
void printResults (int quotient, int remainder)

**Lab 3-3**

5~80 사이의 4개의 임의 정수(random number)를 2번 생성하여 그 숫자들에 아래와 같이 사칙연산을 수행하고 연산결과를 출력한다. \
첫 번째 임의 생성 정수를 (A1, A2, A3, A4), 두 번째 임의 생성 정수를 (B1, B2, B3, B4) 라고 할 때, 사칙연산은 아래와 같이 수행된다.

>  ( A1+ B1,  A2 – B2,  A3 * B3,  A4 / B4 )

요구사항
아래의 사용자 정의 함수를 반드시 정의하고 사용할 것 \

> void randData(int *, int *, int *, int *) – random data 생성

사칙연산(덧셈, 뺄셈, 곱셈, 나눗셈)을 수행하는 함수 add, subtract, multiply, divide 를 각각 구현하고 사용할 것 \
“calc.h” 와 “calc.c”에는 덧셈, 뺄셈, 곱셈, 나눗셈 함수를 작성


## 이론
### 연산자
* 산술연산자
  * +,-, *, /, % 
* 대입연산자
  * =, +=, -=, *=, /=, %=, <<=, >>=, &=, ^=, |= 
* 관계(비교) 연산자
  * />, <, >=, <=, ,!= 
* 논리연산자
  * &&, ||, ! 
* 증가/감소 연산자
  * ++, --
* 비트연산자
  * &, |, ^, ~ 
* 시프트연산자
  * <<, >>
* 주소 연산자
  * &, *

### 포인터

```c
int a = 14;
int *p = &a;

printf(“%p %d %d”, p, *p, a); 
a = 20; 
printf(“%p %d %d”, p, *p, a);

Results: 
00135760 14 14 
00135760 20 20
```

### 함수
* 함수란?
* 함수를 왜 쓰죠?
  * 반복, 분할, 재사용
* 함수 선언과 정의
* 아무것도 반환하지 않는 함수
* 값을 반환하는 함수
* Call by value | Call by reference
  * swap 함수
* 사용자 정의 함수 vs Library 함수
  * 예시) math.h --> abs, floor, ceil, round, pow, sqrt...


