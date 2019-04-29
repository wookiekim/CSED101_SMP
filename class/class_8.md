# Class 8
Current/Most recent session:
> 2019/04/29

## 개요

1. 문자열 (복습)
2. 포인터 (복습)
3. Storage Class
4. 동적할당

* [Online C Compiler](https://www.jdoodle.com/c-online-compiler)

### 문자열 (복습)

**캐릭터형 배열**
* 이지만 끝에 널 (NULL)문자 `\0`가 들어가있음
* 캐릭터형 배열과 다르게 **시작**부터 **NULL문자**까지 한 번에 출력하기 용이함
  * 캐릭터형 배열은 배열 내의 모든 원소를 한 번에 이어서 출력할 수 없음

```
|H| <-- char 'H'
|H|\0| <-- string "H"
|\0| <-- empty string ""

char str[11];
|G|o|o|d| |D|a|y|\0|?|?|
ㄴ ?? <-- 배열의 일부이나, 문자열의 일부는 아님
ㄴ 할당한 배열의 크기를 다 사용할 필요가 없는 것
```

문자열 사용 예시:
```c
char pid[100], sid[100]; 

printf(“Input your povis id: “); 

scanf(“%s”, pid); 
printf(“%s”, pid);

getchar();

scanf(“%s”, sid); 
printf(“%s”, sid);
```

실습 문제) 대<-> 소문자 변환

~~jdoodle.com/a/1aUV~~

```c
#include <stdio.h>

int main(void) { 

    char str[10]; 
    int i; 
    
    scanf("%s", str); //왜 &str이 아니지?
     
    for(i=0;i<10;i++){ 
    //logic
    }
    
    printf("%s\n", str); 
}
```

실습 문제 2) 회문 판정 (Palindrome)
* 12321
* 가나다라다나가

~~jdoodle.com/a/1aUT~~
```c
#include <stdio.h> 
#include <string.h> 

int main() { 
    char str[100]; 
    scanf("%s",str);
    
    int flag=0, i; 
    int n=strlen(str);
    
    for(/*logic*/) { 
       //logic     
    } 
    
    if(flag==1)  printf("회문 아님"); 
    else   printf("회문 맞음");
}
```

나중에 더 복잡하게 찾아뵙겠습니다...

### 포인터 (복습)

2014 봄 학기 기말고사 1번 문제

~~jdoodle.com/a/1aUZ~~
```c
#include <stdio.h>

int main() { 

    char arr[][6] = {"cs101","final","exam","is","easy"};    

    printf("%s\n", arr[2]);  // (1)  
    printf("%c\n", *(&arr[3][1]-1)); // (2)  
    printf("%c\n", (*(arr+4))[2]); // (3)  
    printf("%c\n", ((char *)arr)[6]); // (4)  
    printf("%s\n", arr[1]+1);  // (5)  
    printf("%c\n", *(*(arr+2)+1)); // (6)  
 
    return 0;
}
```
4번 문제:

```
아래의 프로그램은 배열의 원소 중 가장 작은 값을 찾아 그 값을 출력하는 프로그램이다. 
배열 arr 에서 pmin 이 가장 작은 값을 가리키도록 빈 칸을 채우시오. 
```

```c
#include <stdio.h> 
#define ARY_SIZE 10  

void set_min_prt (int *arr, int size, int **pmin);  

int main() {  
    
    int arr[ARY_SIZE] = {3, 4, 1, 7, 8, 9, 6, 10, 11, 15};  
    int *pmin; // 배열의 원소 중 가장 작은 값을 가리키기 위한 변수  
 
    set_min_ptr (arr, ARY_SIZE, _______);  //1 
    printf(“Minimum is %d,\n”, _______);  //2
 
    return 0; 
}
   
void set_min_prt (int *arr, int size, int **pmin) 
{  
    int i;  
    ____ = arr; //3 
 
    for(i = 1; i < size; i++)  {
        if(______ > _______){ //4  
            ________________; //5
        }  
    }  
    return; 
} 
```

딱히 몰라도 되지만 알아두면 좋은 사실:
* 포인터에 타입이 왜 필요한가? 어차피 다 주소값인데?
  * 역참조할 때 얼만큼 읽어야할 지 알려주기 위해
* 그러면 타입이 없는 void * 는 뭔가? 
  * 모든 종류의 주소값을 저장할 수는 있으나, 위의 이유로 역참조는 안 된다
  * 근데 casting을 하면 역참조 가능 i.e. `*(int*)p`
* 왜 포인터는 0이 아닌 NULL로 초기화 하나요?
  * 0도 하나의 존재하는 값이기 때문에, '아무것도 가르키고 있지 않다'라는 의미로
  * 사실 0이라는 주소값에 무언가가 존재하고 있을 수도!!

### Storage Class

Auto Variable 자동 변수
* 가장 일반적인 변수
* 일반적으로 지역 변수 == 자동 변수
* 초기화하지 않으면 쓰레기값 저장
* 해당 블록을 종료하는 순간 (중괄호 끝나는 지점) 메모리에서 자동으로 제거

Static Variable 정적 변수
* 정적 지역변수 vs 정적 전역변수
  * 정적 지역변수: 선언된 블록 내에서만 참조 가능
  * 정적 전역변수: 선언된 "파일" 내에서만 참조 가능
    * 그냥 전역 변수 : 다른 파일이어도 참조 가능
* 초기화하지 않으면 타입에 따라 0 혹은 '\\0' (null) 저장
* 블록이 종료돼도 프로그램 종료까지는 메모리에 남아있음

Extern Variable 한국어로 뭐지
* 전역 변수로 선언된 변수를 사용하고자 할 때
  * 근데 그 전역 변수가 다른 파일에 선언되어 있을 때!!!!(Static 전역 변수는 안되겠죠?)
* 초기화하지 않으면 타입에 따라 0 또는 '\\0' (null) 저장

Register Variable
* 어쨌든 더 빠름
* 초기화 안하면 쓰레기값 저장

2014 봄 학기 기말고사 2번 문제
~~jdoodle.com/a/1aVb~~
```c
#include <stdio.h>  

int g=0; 
void func (int *n);  

int main() {  
    int a=0;  
    func(&a);  
    func(&a);  
    
    printf("%d\n", a);  // (1)  
    printf("%d\n", g);  // (2)  
    {   
        int g=1;   
        printf("%d\n",g); //(3)  
    }  
    printf("%d\n", g);  //(4)  
    
    return 0; 
}  

void func( int *n) {  
    static int s = 1;  
    g = g + s;  
    (*n)++;  
    s++;
}
```

### 동적할당

종강까지 여러분을 가장 많은 버그와 오류로 괴롭히는 친구들
* 배열 (0으로 시작하는 게 어색하고 그래서..) 
* 포인터 (ㅎㅁㅎㅇ)
* 동 적 할 당

메모리 할당에는 두 가지 종류가 있습니다
* 정적 할당
  * 지금까지 우리가 해온 것
  * ex) `int arr[10];`
* 동적 할당
  * 배열의 크기를 입력받아 그 크기만큼의 배열을 만들고 싶을 때
  * 프로그램 실행 중에 메모리를 할당하여 저장할 공간을 생성하는 방법

```c
int main(void){
  int size;

  scanf("%d", %size);
 
  int array[size]; // COMPILE ERROR!
}
```

주요 함수 및 헤더:
* Header : `<stdlib.h>`
* Functions:
  * ` void* malloc (size_t size);`
  * ` void* calloc (size_t count, size_t size);`
  * ` void* realloc (void* ptr, size_t newSize);`
  * ` void free (void* ptr);`

`void* malloc(size_t size);`
* 지정하는 크기 (byte) 만큼 메모리를 할당
* `void*` 를 반환하기 때문에 casting을 해줘야 한다
* 할당에 실패한 경우 NULL 반환
  * ex) `int* p = (int *)malloc(sizeof(int) * 4); `
  * ex2) `char *str = (char *)malloc(sizeof(char) * 10);`

`void* calloc(size_t count, size_t size)`
* count X size 만큼의 메모리를 할당하고
  * **해당 영역을 0으로 초기화하여 반환**
* ex) `int *p = (int *)calloc(4, sizeof(int)); `
* ex) `char *str = (char *)calloc(10, sizeof(char));`
  * `malloc(sizeof(int)*4) <--> calloc(4, sizeof(int))`

`void* realloc (void* ptr, size_t newSize);`
* 할당받은 메모리 공간을 새로운 크기로 재할당
* example
  * `int *p = (int *)calloc(4, sizeof(int));`
  * `p = (int *)realloc(p, sizof(int) * 6);`
  * 4->6으로 길어졌다!
  * 기존 데이터는 그대로 유지됨
  * 새로 이어붙여진 부분은 초기화가 안 된 상태

`void free(void* ptr);`
* 사용이 끝난 동적할당 된 메모리 반환
  * 우리에게 반환하는 반환이 아니라 컴퓨터에게 반환
  * 사용하지 않을 때 & 프로그램의 마지막에 반드시 free 해줘야 함!!
* 해주지 않아도 프로그램이 도는 데에 문제는 없으나, 메모리 누수가 생김
  * 또한 이 메모리 누수가 있으면 어싸인 감점 ㅋㅋ

동적할당으로 2차원 배열 만들기 예시
```c
table = (int**) calloc (rowNum + 1, sizeof(int *))

table[0] = (int *) calloc (4, sizeof(int));
table[1] = (int *) calloc (7, sizeof(int));
..
..
..
```

동적할당 & 포인터를 사용할 때 생길 수 있는 부작용들:
* Unreachable Memory (이 공간이 가르키는 포인터가 없다)
  * free를 안 해줬을 경우 ==> 메모리 누수
* Dangling Pointer (어딘가 가르키고 있지만, 뭘 가르키고 있는지는 모른다)
  * 포인터가 가르키던 변수가 있던 블록이 끝나서 사라진 경우
* Buffer Overflow
  * 저장하려고 한 내용이 할당된 버퍼(메모리)의 영역 밖으로 넘치는 것
* 잘못된 연산 오류 Segmentation Fault
  * 지정된 영역 이외의 엉뚱한 위치 (주로 null 포인터, 혹은 쓰레기값)을 가르키는 포인터를 참조하려고 할 때 발생함
  * 각 포인터가 가르키는 위치가 유효한지 잘 확인해야함
* ex)
  * `int *p`
  * `*p = 123` <-- 초기화 되지 않은 포인터를 역참조...?
