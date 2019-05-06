# Class 9
Current/Most recent session:
> 2019/05/06

## 개요

1. 동적할당 (복습)
2. enum
3. Struct & Union
4. String(문자열) - 下

* [Online C Compiler](https://www.jdoodle.com/c-online-compiler)

### 동적할당 (복습)

연습 문제:
* 입력받은 숫자 크기의 integer array를 할당
* array에 채울 숫자를 입력 받은 후 출력
* array 내의 가장 큰 수와 작은 수를 각각 출력
* 이후 inter array의 크기를 **다시** 받음
* 새로운 크기만큼 array를 **재할당** 함
* array에 채울 숫자를 입력 받은 후 출력
* array 내의 가장 큰 수와 작은 수를 각각 출력

**FREE 꼭 해주기**

예시 실행화면:
```
Input  array size: 5
2 1 5 4 3
Entered numbers are:
2 1 5 4 3
Maximum is 5
Minimum is 1

Input changed array size: 8
5 2 3 11 66 32 22 10
Entered numbers are:
5 2 3 11 66 32 22 10
Maximum is 66
Minimum is 2
```

### Enum
사용자 정의 자료형 (User-defined data type)중 하나!
* Enumeration의 약자
  * Enumeration : 열거
* 주로 항목 또는 선택지들을 관리할 때 사용됨
* 각 항목에 대해 하나의 **정수**가 identifier로서 할당됨 
  * enumeration constant라고 불림

예시 상황) 메뉴를 만든 뒤, 숫자를 입력받아 switch문으로 각기 다른 함수를 실행시켜야 함
* 메뉴를 애초에 0,1,2,3...처럼 switch문에 넣기 쉽도록 만들면 실행할 수는 있다
  * __**그러나 0,1,2,3이 각각 무엇을 의미하는지 나중에 헷갈리기 쉬움**__

사용 방법::
```c
//Declaration
enum days-of-week {Mon, Tue, Wed, Thu, Fri, Sat, Sun};
//첫 원소인 Mon은 자동으로 0이라는 숫자가 배정됨
//이후 1씩 증가하며 배정됨

//Instantiation
enum days-of-week day;
//즉 enum형 변수

//Operation
day = wed; // Wed는 3번째 위치에 있으므로 숫자 2를 의미함
```

다양한 코드 예시: [링크](https://www.geeksforgeeks.org/enumeration-enum-c/)

```c
enum MONTHS {JAN, FEB, MAR, APR};
// ? ? ? ?
enum MONTHS {JAN = 1, FEB, MAR, APR}; 
// ? ? ? ?
enum COLORS {RED, ROSE=0, CRIMSON=0, BLUE, AQUA=1};
//? ? ? ? ?
```

위와 같이 identifier를 지닌 항목들이 숫자/정수 역할을 하여 관리하기 쉬워짐
* `day = wed` 라는 코드를 보면 day라는 변수가 수요일을 지니고 있음을 알기 쉬움
* int 형과 자동으로 호환됨
  * `int x = Sun;`
  * 굳이 `enum days-of-week`과 같이 길게 길게 쓸 필요가 없어짐

중심적인 내용은 아니나 어싸인과 시험에 나올만 함

### Struct & Union 구조체 & 유니언
둘 다 또한 User-defined Data Type

**Structure 구조체** 
* 관련되는 element들의 집합
  * element라고 해서 별다른 게 있는 게 아니라 그냥 변수..배열..즉 요소들
* 그러나 구조체의 요소로 함수가 있을 수는 없다.

선언 
```c
//선언방법
struct STUDENT{
  int id;
  char name[26];
  char dept[3];
  int grade;
};

struct STUDENT a;
```
```c
typedef struct{
  int id;
  char name[26];
  char dept[3];
  int grade;
} STUDENT;

STUDENT a;
```

초기화
```c
typedef struct{
  int x;
  int y;
  float t;
  char u;
} SAMPLE;

SAMPLE sam1 = {2, 5, 3.2, 'A'};
SAMPLE sam2 = {7,3}; // 나머지는 각각 0과 \0 (NULL) 로 초기화
```

변수 접근/사용
```c
typedef struct{
  int x;
  int y;
  float t;
  char u;
} SAMPLE;

SAMPLE sam1;
SAMPLE* ptr;
ptr =  &sam1;


sam1.x = 10;
sam1.u = 'c';
(*ptr).x = 15;
ptr->x = 20;
ptr->u = 'd';
```

Nested구조 또한 가능!
* Struct내에 struct..

```c
typedef struct{
  int x;
  int y;
  SAMPLE sam1;
} SAMPLE2;
```

선언된 Struct(구조체)는 다른 자료형과 똑같이 사용될 수 있음
* 배열 선언
  * `SAMPLE a[10];`
  * `a[0].x = 10;`
* 동적 할당
  * `SAMPLE* a = (SAMPLE *) malloc(sizeof(SAMPLE) * 4);`
* 등등...
* **Linked List?**

**Union 유니언**
* 구조체와 비슷하다. 선언 및 사용도 동일함
  * struct 가 들어갈 자리에 union이 들어갈 뿐
* 그러나 모든 element들이 메모리를 **공유**
  * union내부의 가장 큰 변수의 크기만큼이 할당됨

```c
typedef union{
  short num;
  char chary[2];
} SHORTCHAR;

SHORTCHAR data;
data.num = 16706;
//100000101000010
//1000001 : 65, 'A'
//01000010: 66, 'B'

printf("Short: %d\n", data.num); //16706
printf("chary[0]: %c\n", data.chary[0]);//A
printf("chary[1]: %c\n", data.chary[1]);//B
```

* 헷갈리지만 않는다면 메모리 공간 절약 가능
* 하나의 유니언으로 여러 종류의 구조체 역할을 할 수도 있음

### String(문자열) - 下
* Refer to slide
