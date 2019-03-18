# Class 4
Current/Most recent session:
> 2019/03/18

## 개요

1. 회식시간 다시 잡기..ㅎㅎ
2. 랩과제/어싸인먼트 질의응답/ 설명
3. Visual Studio 사용해보았나
4. 조건문, 반복문

## 회식시간 다시 잡기
어제 진짜 코드 한 1000+ 줄은 짰을 듯
**알고리즘** 과제..ㅎㅎ
* 너네도 나중에 배우게 될 거야

우선 치킨 시킬까
[순수치킨](http://dorm.postech.ac.kr/dormunion/?mid=food&act=dispFoodRestaurantInfo&restaurant_srl=373544)

### 랩 과제/어싸인먼트 질의응답/설명??

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

**Assignment 1**
개인적인 생각에 위 랩 문제들이 어싸인먼트 1보다 어려움 ㅎㅎ
* math.h의 지수함수?
```c
#include <math.h>
#include <stdio.h>

int main(){
  int a = pow(2,3); //8
}
```
* 소수점 이하 반올림?
```c
...
printf("%0f",....);
...
```
* 입력한 소문자 알파벳 대문자 변환, 암호화 및 순번 구하기
  * ASCII 코드
  * 대문자 A, 소문자 a? 
  * 이정도는 외우고 있는게 좋음

## Visual Studio 사용해보았나
이번 수업이 끝나고 나면 본격적으로 투닥투닥 해볼 수 있음

**다음주**부터는 SMP 도중 이런저런 실습을 해 볼 예정 ㅎ.ㅎ

* 저번 주 과제 (숙제?)
  * temp 변수 없이 swap 짜는 법

```c
int x = 5;
int y = 10;

x = x + y; //15
y = x - y; //y = 15 - 10 = 5
x = x - y; // x = 15 - 5 = 10
```
막상 알고 보면 크게 어렵지 않
* 지만 그 자리에서 생각해보려고 하면 쉽지 않음
  * CSED101 시험에 이러한 문제들이 *간혹* 나옴

## 조건문, 반복문

### 조건문 (Conditional Statements)
조건에 따라서 선택적으로 프로그램을 진행
* 프로그램의 흐름(Flow)를 조종
* 2 way selection
  * 두 가지 선택지 중 하나

```c
if (조건)
{
 // 조건이 참True 일 때
}
else
{
 //조건이 거짓False일 때
}
```
* Else 가 없을 수도 있다.
  * 비와? 우산 챙겨. 
  * 안 오면 그냥 나가면 됨.
* Multiway Selection
  * 여러가지 가능성 중 하나

```c
...
int 잔고;

scanf("%d", &잔고);

if(잔고 > 7000){
    학생회관에서_먹기();
}
else if (잔고 < 7000 && 잔고 > 3500){ // 그냥 잔고 > 3500?
    지곡회관에서_먹기();
}
else{ // else if(잔고 < 3500)?
    굶기();
}

```

```c
...
if(condition){
    return 1;
}
return 0; //else return 0;
```

조건 안의 조건이 있을 수도 있다
* "만약" *비가 오고*, "만약" *우산이 있으면*, 우산을 챙긴다

```c
...
if(비가 온다){
    if(우산이 있다){
        우산을 챙긴다;
    }
}
```

조건 검사 (True/False)
* C언어에서는 0이면 False, 그 외에는 모두 True
* 논리 연산자를 응용하게 됨

**Truth Table:**

Not(!)

|x|!x|
|-|--|
|False|True|
|True|False|

And(&&) 

|x|y|x&&y|
|-|-|----|
|False|False|False|
|False|True|False|
|True|False|False|
|True|True|True|

Or (||) 

|x|y|x\|\|y|
|False|False|False|
|False|True|True|
|True|False|True|
|True|True|True|

괄호 잘 쓰기
* `if(a>=1 && a<= 100 && a%2 == 0)` --> `if((a>=1 && a <=100) && a%2 ==0)`

```c
int x = 1;
int y = 0;

if( x || y){
  printf("x || y is true\n");
}
else{
  printf("x || y is false\n");
}
```

**Nested IF statement**

```c
if(조건1){
  if(조건2){
    // 조건1과 조건2가 둘 다 참
  }
  else{
    //조건 1은 참, 조건 2는 거짓
  }
}
else{
  //조건 1이 거짓
}
```

> **주의사항!** \
if, else 다음에 실행할 명령이 "한 줄"이면 중괄호 필요 없음
```c
if(조건1)
  if(조건2)
    //조건 1,2 참
else 
  // 조건1이 거짓? 1은 참이지만 2가 거짓?
```
* 가장 가까운 if 랑 자동으로 matching되어버림
  * 그냥 읽기 쉽게 중괄호 사용하도록 합시다

**Multiway Selection**
* Else if 구문
* Switch 구문

**Else if 구문**
* if~else의 확장형

```c
if(조건문1){
  //조건문 1이 참일 때
}
else if(조건문 2){
  //조건문 2가 참일 때
}
else{
  //앞의 모든 조건문이 거짓일 때
}
```

**Switch 문**
* 검사하고자 하는 대상의 값(변수, 함수의 반환값)에 여러가지 선택지가 있을 때

```c
switch(검사대상)
{
  case 값1:
    statement_1_1;
    statement_1_2;
  case 값2:
    statement_2_1;
    statement_2_2;
  case 값3:
    statement_3_1;
    statement_3_2;
}
```
```c
switch(num){
  case 0: //num==0
    statement0;
    break;
  case 1: //num==1
    statement1;
    break;
  default: //else
    statementN;
    break;
}
```
* break를 쓰지 않는다면?
  * 쭉 내려감 (모두 실행)

ex)
학점 계산기 만들기

```c
#include <stdio.h>

int main(void) { 

  int score; 
  
  printf("Type your score.\n"); 
  scanf("%d", &score);

  if(score>=90) 
    printf("Grade : A\n"); 
  else if(score>=80) 
    printf("Grade : B\n"); 
  else if(score>=70) 
    printf("Grade : C\n"); 
  else printf("Grade : D\n");
}
```
```c
#include <stdio.h>

int main(void) { 
  int score; 
  
  printf("Input the score: "); 

  scanf("%d", &score); 
  
  switch(score/10) { 
    case 9: 
      printf("A grade\n"); 
      break; 
    case 8: 
      printf("B grade\n"); 
      break;
    case 7:
      printf("C grade\n"); 
      break;
    case 6:
      printf("D grade\n"); 
      break; 
    default: 
      printf("F grade\n"); 
      break; 
   }
return 0;
}
```
### 반복문 (Loop)
일련의 작업들을 반복해서 실행하게 하는 것
  ex) 1~50까지의 합 구하기, 자동 냉방 장치 시스템, 게임..

1. Initialization 초기화 //1부터!
2. Update 업데이트 //1 다음은 2!
3. Condition Check 조건 확인//50 까지 더했니?

* 위 조건들이 필요 없는 경우..?

### For 문

```c
for(initialization ; condition check ; update){
    //statements;
}

int i;
for( i = 0; i < 10; i ++){
  printf("%d ", i);
}

//결과: 0 1 2 3 4 5 6 7 8 9

int i, sum = 0;
for(i = 1; i <=50; i ++){
  sum = sum + i;
}
printf("%d", sum);
```

2중, 3중...n중 포문!!!
```c
for(..;...;...){
  for(...;...;...){
    for(...;...;..){
      //statement;
    } 
  } 
}

//구구단 전체 출력하기

#include <stdio.h>
int main(){
  int i,j;

  for(i=2;i<=9;i++){
    for(j=1;j<=9;j++){
      printf("%d * %d = %d\n", i, j, i*j);
    }
  }
}
```

### while문

```c
//initialization
while(condition check){
  //statement;
  //update
}
```
* 예시: 정수를 입력받아 더해 나가다가 0이 입력되면 모든 정수의 합을 출력하고 종료

```c
#include <stdio.h> 

int main() { 
  int sum=0; 
  int su=1; 

  while(su!=0) { 
    
    scanf(“%d”,&su); 
    sum += su; 
  } 
  
  printf(“sum=%d\n”, sum); 
}
```
* 마찬가지로 2중 while 가능

**do~while문**?

```c
do{
  //statement
} while(condition);
```
* while과 똑같지만
  * 최초 1 번은 무조건 실행됨

### 반복문의 조건이 필요없는 경우?
1. Initialization이 없는 경우
* 굳이 초기화가 필요 없는 경우
2. Condition이 없는 경우
* 무한루프 
```c
while(1){}
while(True){}
while(123456){}

for(a;b;c){} // a, b, c 중 필요한 것만 있다면? 다 없다면?
```
3. Update가 없는 경우
* 또한 무한루프..
* 혹은 그저 기다리는 용도
```c
while(1){
  //empty
}
```

* 언제 어떤걸 쓰나요?
  * 님 마음대로..
  * for문으로 가능한 건 while 문으로 가능하고..반대로도 성립

### 분기문
* break문
  * 오잉 아까 switch문에 있던거 아닌가요?
    * 맞습니다
  * 가장 "가까운" switch/loop문 한 개를 나간다
* continue문
  * loop 문에 사용됨
  * loop의 나머지 코드를 실행하지 않고, 바로 Condition으로 돌아감

```c
int i = 0;
while(1){
  i++;
  if (i > 1000)
    break; // i가 1000이 넘어가는 순간 while문을 빠져나감

}
printf("%d", i); //1001
```

```c
int i = 0;
while(i < 50){
  if(i % 2) // if(i % 2 == 1)
    continue;
  printf("%d ",i); //짝수만 출력
}
```

**만약에 한 번에 두 개의 Initialize/ Condition check/ Update를 하고 싶다면?**
" Comma쉼표 Expression"

for(a ; b ; c){} -> for (a1,a2;b1,b2;c1,c2);

```c
int sum, i;

for(sum = 0, i = 1; i <= 50; i ++){
  sum +=i;
}
```

조건문, 반복문은 모든 프로그램의 뼈대 역할을 함
* !!!!!!!고로 매우 중요!!!!!!!

Exercises:

조건문:

1. 입력받은 년도가 윤년(Leap year)인지 아닌지 판단하는 함수를 만들어라.
2. 입력받은 글자가 알파벳인지 아닌지 확인하라 (", - 와 같은 기호들도 %c 로 받음)
3. 입력받은 3 개의 정수 중 최대값을 반환하는 프로그램을 만들어라

반복문 :

1. 숫자를 입력받은 뒤, 각 자릿수의 합을 반환하는 프로그램을 만들어라.
2. 주어진 숫자가 회문 (palindrome)인지 확인하는 프로그램을 만들어라.
3. 주어진 숫자의 팩토리얼을 구하는 프로그램을 만들어라.

