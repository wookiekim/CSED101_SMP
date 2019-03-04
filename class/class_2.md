# Class 2
Current/Most recent session:
> 2019/03/04

## 몰라도 되는 부분
* 컴퓨터란 무엇인가?
* 프로그램이란 무엇인가?
* 하드웨어는 무엇이며 소프트웨어는 무엇인가?
* 컴파일러?어셈블러?기계어?

위와 같은 이론적인 부분은 굳이 몰라도 됩니다 ㅎ.ㅎ
> 간혹 수업 중에 진행되는 퀴즈에 이론적인 질문이 많이 나오긴 하지만,\
퀴즈에 뭐가 나오는지 다 말씀해주셔서 ~~직전에만 대강 읽고 가면 된다는 점~~

## 컴퓨터 및 프로그래밍 소개

저번주 질문: "_프로그래밍을 배우면 어디에 쓸 수 있나요..?_"\
--> "_왜 배우나요?_"와 비슷한 질문

* 윤은영 교수님의 역사 수업: 컴퓨터의 역사
  * Imitation Game
* 인간이 하기에는 너무 시간이 오래 걸리거나, 귀찮거나, 어려운 일을 "대신 해주는 역할"
* 다양한 개념이 있지만 결국 해당 개념의 연장선임

컴퓨터가 "굳이" 2진수를 사용하는 이유?

## 개요

1. Bit?
2. Byte?

```
KB 킬로바이트 : 2^10 = 1024 
MB 메가파이트 : 2^20
GB 기가바이트 : 2^30

어쨌든 다른 과학에서 사용되는 단위랑은 다름
``` 
**sizeof()**
```c
int main() 
{ 
    printf("%d\n",sizeof(char)); //1
    printf("%d\n",sizeof(int)); //4
    printf("%d\n",sizeof(float)); //4
    printf("%d", sizeof(double)); //8

    int a = 0; 
    double d = 10.21; 
    printf("%d", sizeof(a+d)); //8

    return 0; 
}  
```

3. 왜 바이트를 사용하는가?
4. 바이트로 할 수 있는 것들 (ASCII)
5. 주석

```c
#include <stdio.h>

int main(){

  printf("Hello World!\n");

  //한줄주석
  /* 여러
   * 줄
   * 주
   * 석
   */

  return 0;
}
```

6. 예약어

```c
#include <stdio.h>

#define pi 3.14 // 변수처럼
#define square(x) x*x // 짧은 함수처럼

int main(){
  int a = 5;
  int b = square(a);
  
  printf("%d %f", b, pi);
  return 0; 
}
```

7. 식별자 (변수명?)

```c
int a; // ok
int dfghj; // ok
int a_b_c; // ok
int a1b2; //ok
int 1a; // wrong
int a!; // wrong
int _ab// ok
```

8. 연산자
* Primary
* Postfix
* Prefix
* Unary
* Binary
* Ternary

9. 전처리기

```c
#include <stdio.h>
```

직접 만들 수 있음 (custom header라고도 부름)
```c
파일명: myheader.h

#include <stdio.h>

//code1
//code2
//code3
...
..
```
```
#include <stdio.h>
#include "myheader.h"
```

10. Scope (변수 범위)
* Preprocessor Directives
* Global Declarations
* int main(){}
  * Local Declaration
  * Statements
* Other functions as required

11. 자료형
* void
* integral
  * boolean
  * character (1byte = 2^8 bits = 256)
  * integer (short, int, long int, long long int....)
* floating-point
  * real
  * imaginary
  * complex
* derived (?)

형 변환
* Implicit Conversion
  * 자동으로 이루어지는 형변환
```c
int a = 3.14 // a = ?
```
* Explicit Conversion (casting)
```c
double a = 3/4 // a = ?
double b = (double)3/4 // b = ?
```

bool < char < integer < real number

> 각 자료형마다 표현 범위가 있음

12. 변수
* const keyword?
* pointer 변수?

> auto, double, int, break, else, long, switch, case, register, char, extern, return...등 
C언어에서 이미 기능이 정해져있어서 변수명으로 사용할 수 없는 **표쥰 키워드**들이 있음

13. 출력
### printf()
```c
printf("Hello Worlddddddddddddd\n");

int a=1,b=2,c=3;
printf("a b c"); // wrong
printf("%d %d %d\n", a, b, c); // correct
```

Format String:

|출력형식|설명|
|--------|----|
|%d|10진수 정수형|
|%o|8진수 정수형|
|%x, %X| 16진수 정수형|
|%u|부호 없는 10진수 정수형|
|%c|한 문자|
|%s|문자열|
|%f|10진수 방식의 부동소수점 실수형 (float, double)|
|%Lf|10진수 방식의 부동소수점 실수형 (long double)|
|%e, %E|e방식의 부동소수점 실수형|
|%g, %G|%f 와 %e 중에서 출력 자릿수를 덜 차지하는 형태로 출력|

특수문자:

|특수문자|설명|
|-------|----|
|\n|개행|
|\t|탭|
|\'|작은 따옴표 출력|
|\"|큰 따옴표 출력|
|\?|물음표 출력|
|\\|역슬래시 출력|

```c
printf의 다른 예시/기능들

printf(“%10d \n”,123); // 오른쪽정렬 
printf(“%-10d \n”,123); // 왼쪽 정렬 
printf(“%10.2f \n”,123.456789); // 왼쪽 정렬 ****123.46(*은 빈칸) 
```

14. 입력
### scanf()

```c
scanf(“%c %f”, &code, &price);
```
* scanf(“Format string”, variable a, b, …); 
* printf의 %d처럼, scanf도 받는 데이터에 맞춰서 format string을 넣어줘야함
* 변수에 값을 넣기위해서는 변수의 **주소!** 를주어야 한다
  * 변수 a | 변수 주소 &a
* 공백, 서식문자를 제외한 문자가 있으면 입력시 형태를 맞춰줘야 한다. 
  * “%d-%d” --> 1-2 
* Format string 마지막에 공백이 있으면 안됨! 
  * "%d %d " X --> "%d %d" O

printf와 scanf 합치기!
```
#include <stdio.h>

int main(void) { 
  int num1, num2, num3; 

  printf("세 개의 정수 입력: "); 
  scanf("%d %o %x", &num1, &num2, &num3); //12 12 12

  printf("입력된 정수 10진수 출력: "); 

  printf("%d %d %d\n", num1, num2, num3); // 12 10 18 

  return 0;
}
```


