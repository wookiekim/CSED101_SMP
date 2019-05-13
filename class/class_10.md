# Class 10
Current/Most recent session:
> 2019/05/13

## 개요
1. 함수 포인터 Function Pointer VS 포인터 함수 Pointer Function
2. Linked List
3. Stack
4. Queue

* [Online C Compiler](https://www.jdoodle.com/c-online-compiler)

### 함수 포인터 Function Pointer vs 포인터 함수 Pointer Function
함수 포인터란?
* 특정 함수의 메모리 주소를 담을 수 있는 포인터 변수
  * 함수 주소가 아닌, 함수 자체를 담을 수도 있음

사용하는 이유?
* 코드가 간결해짐 (일반 포인터 또한)
  * 중복 코드를 줄일 수 있음 
* 함수 포인터를 배열에 담아서도 사용할 수 있음
* 상황에 따라 필요한 함수를 호출할 수 있음

모양 (Declaration):
```c
int (*FuncPtr) (int, int)
//함수의 주소를 담을 수 있는 FuncPtr라는 포인터 변수
//int를 반환하고, int형인자 2개를 받는 함수를 가르키는 포인터 

int add(int first, int second);
double div(double first, double second);

FuncPtr = add // O
FuncPtr = &add // O
FuncPtr = div // X
FuncPtr = add() // X

//자료형///////////////////////////////////////

typedef int (*FuncPtr) (int, int); // 사용하기 쉽도록 아예 FuncPtr라는 자료형으로 만듦
FuncPtr testFP = NULL;
testFP = add;


//사용법///////////////////////////////////////

void fun(int a){
    printf("Value of a is %d\n");
}

void (*FuncPtr)(int) = &fun;
(*fun_ptr)(10);

void (*FuncPtr)(int) = fun;
fun_ptr(10);
```

### Linked List
### Stack
### Queue
