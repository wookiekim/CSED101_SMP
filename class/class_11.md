# Class 11
Current/Most recent session:
> 2019/05/20

1. 다음 함수가 Linked List에 대해서 수행하는 것은?

```c
void fun1(struct Node* head) 
{ 
  if(head == NULL) 
    return; 
   
  fun1(head->next); 
  printf("%d  ", head->data); 
} 
```

2. 이번 함수는?
```c
void fun2(struct Node* head) 
{ 
  if(head== NULL) 
    return; 
  printf("%d  ", head->data);  
  
  if(head->next != NULL ) 
    fun2(head->next->next); 
  printf("%d  ", head->data);    
} 
```

