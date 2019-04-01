# Class 5
Current/Most recent session:
> 2019/04/01

## 개요

1. 재귀 함수  
2. FILE I/O


### 재귀 함수 Recursion

함수가 **자기 자신**을 부르는 것!

```c
//Fibonacci

int fib(n){
    if ( n<=2){
        return 1;
    }
    else{
        return fib(n-1) + fib(n-2);
    }

}
```

필수조건:
* Base Case (주로 n=1, 혹은 n < m ...)
* 그 외의 Case

왜 쓰나요?
* 장점: 문제를 단순하게 풀 수 있다
* 단점: 메모리 소모가 많다

대표적인 문제:
* Tower of Hanoi
  * 오늘은 여기까지, 만일 추가적으로 배운다면 다음주에 ㄱㄱ

### FILE I/O

말 그대로 파일(.txt, .c, .py, .whatever)에서 **입출력** 하는 것

```
FILE* infile;
infile = fopen("text.txt","w");
~~
fclose(infile);
```

대표적 FILE I/O 함수들
* int fprintf(FILE \* out, const char \* format, ...) [설명](https://www.tutorialspoint.com/c_standard_library/c_function_fprintf.htm)
  * Filestream, out으로부터 format의 형태로 출력한다
  * 비교) int printf(const char \* format, ...)

```c
FILE * out; 
out = fopen(“test.txt”, “w”); 
fprintf(out, “%c %d\n”, ‘a’, 22); 
…
fclose(out);
```

* int fscanf(FILE \* in, const char * format, ...) [설명](https://www.tutorialspoint.com/c_standard_library/c_function_fscanf.htm)
  * File stream, in 으로 부터 format의 형태로 입력받는다
  * 비교) int scanf(const char \* format,...)

```c
int a; 
char b; 
FILE * in;

in = fopen(“text.txt”, “r”); 
fscanf(in, “%c %d”, &b, &a); 
printf(“%c %d\n”, b, a);
fclose(in);
```

```c
#include <stdio.h>

int main(void) 
{ 
    FILE *inFile; 
    FILE *outFile; 

    int a, b, c; 
    int sum; 
    float avg;

    inFile = fopen("input.txt", "r"); 
    outFile = fopen("output.txt", "w");

    if(inFile == NULL) 
    { 
        printf(“Input file open error\n"); 
        return 0;
    }

    while(fscanf(inFile, "%d %d %d", &a, &b, &c) != EOF) 
    { 
       sum = a + b + c; 
       avg = (float)(sum)/3.0; 
       fprintf(outFile, "%d %.3f\n", sum, avg); 
    }

    return 0;
}
```


* File pointer는 **1번** 열고, **반드시** 닫아줍니다
  * 안 그러면 별에 별 기괴한 문제가 생길 수 있습니다

그 외 I/O 관련 함수들
* int getchar(void) 
* int putchar(int out\_char)
* int fgetc(FILE\* in) 
* int fputc (int oneChar, FILE\* out) 
* int ungetc (int oneChar, FILE\* Data) 
* Int fgets (char \*str, int num, FILE \* in) 
* Int fputs(const char \*str, FILE \* out)

FLUSH
* 스트림 버퍼를 비우는 역할을 한다.
* scanf 등 입력받는 함수 사용시 주의
  * 근접한 scanf 두 번 사이에는 문제가 생길 수 있음

```c
int a;  
char b; 

scanf(“%d”, &a); 
scanf(“%c”,&b); 

printf(“%d %c\n”, a, b);
```
