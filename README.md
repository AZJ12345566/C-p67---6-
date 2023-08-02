# C-p67---6-
C语言学习笔记 p67 动态内存分配-总结(6)
#include<stdio.h>
#include<stdlib.h>
struct S
{
    int n;
    char c;
    int arr[0];//柔性数组成员
};
struct S
{
    int n;
    char c;
    int arr[];//柔性数组成员
};//这是第二种写法


int main()
{
    printf("%d\n",sizeof(struct S));
    int i=0;
    struct S* p = (struct S*)malloc(sizeof(struct S)+10*sizeof(int));
    p->n=100;
    for(i=0;i<10;i++)
    {
        p->arr[i]=i;
    }
    for(i=0;i<10;i++)
    {
        printf("%d\n",p->arr[i]);
    }
    free(p);
    p=NULL;
    return 0;
}

struct S
{
    int n;
    int* arr;
};
int main()
{
    int i=0;
    struct S* p= (struct S*)malloc(sizeof(struct S));
    p->n=100;
    p->arr=(int*)malloc(10*sizeof(int));
    for(i=0;i<10;i++)
    {
        p->arr[i]=i;
    }
    for(i=0;i<10;i++)
    {
        printf("%d ",p->arr[i]);
    }
    free(p->arr);
    p->arr=NULL;
    free(p);
    p=NULL;
    return 0;
}
