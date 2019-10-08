# Class 6
Current/Most recent session:
> 2019/10/08

## 개요

1. 배열  
2. 하노이탑 재귀
3. 시험대비 리뷰
4. 질의응답

### 배열 Array
연관성 있는 변수들을 하나로 묶어서 보관하는 데이터 타입
* ex) 정수 10개를 한 번에 보관하고싶다
  * `int temp[10];`
  * 변수 10개를 일일이 만들기는 좀..

선언:

(자료형) (배열의 이름)[(배열의 크기)]

```c
int scores[9];

char name[10];

float gpa[40];
```

초기화:

1. 기본 
  * `int numbers[5] = {1,2,3,4,5};`
2. Size 없이 초기화
  * `int numbers[] = {1,2,3,4,5};`
3. 부분 초기화
  * `int numbers[5] = {1,2} // 나머지 세 칸은 0으로 초기화`
4. 모두 0으로 초기화
  * `int lotsofnumbers[1000] = {0}`

배열의 원소(element)에 접근:

(배열의 이름)[(원소의 index)] : 배열의 index는 0에서부터 시작함
* `int arr[10];`으로 선언해서 10개의 칸이 있다면
* `arr[0]`부터 `arr[9]`까지존재함 (0에서 카운트 시작)
  * `오늘부터 0일`과 같은 되도 않는 드립의 시초

사용예시)

```c
for (i = 0; i < 10; i ++)
  scanf("%d", &scores[i]);

scores[4] = 23;
printf("%f", gpa[11]); // 배열 gpa의 '12번째' 실수 출력
```

함수로 넘기기:

```c
void fun0 (int x)
{
  //statement
}

void fun1 (int* x)
{
  //statement
}

void fun2 (int arr[])
{
  //statement
}

int a;
int ary[10];

fun0(a);
fun0(ary[3]);

fun1(&a);
fun1(&ary[3]);

fun2(ary);
```

어레이는 "주소값이다"
* 위 예시에서 `fun1(ary)`도 가능
  * ary는 ary의 첫 번째 원소의 주소값을 가지고 있음 
  * i.e. ary == &ary[0]

어레이는 주소값이다 의 예시
* `ary` == `&ary[0]`
* `ary + 1` == `&ary[1]`
* `*ary` == `ary[0]`
* `*(ary+1)` == `ary[1]`
* `*ary + 1` == `ary[0] + 1`

### 하노이탑 대비
```c
void towers (int n, char source, char dest, char auxiliary){
    //Local Declaration
    static int step = 0;

    //Statements
    printf("Towers (%d, %c, %c, %c)\n", n, source, dest, auxiliary);

    if(n==1)
        printf("Step %3d: Move from %c to %c\n", ++step, source, dest);

    else{
	towers(n-1, source, auxiliary, dest);
	printf("Step %3d: Move from %c to %c\n", ++step, source, dest);
	towers(n-1, auxiliary, dest, source);
    }
    return;
}
```
나머지는 칠판설명

### 시험대비 리뷰

* [week1](class_1.md)
* [week2](class_2.md)
* [week3](class_3.md)
* [week4](class_4.md)
* [week5](class_5.md)

### 질의응답
