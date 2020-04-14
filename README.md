/* # sunshine
something about data structure，I am a Green hand！*/
#include<stdio.h>
#include<malloc.h>
typedef int ElemType;
typedef struct LNode
{
	ElemType data;
	struct LNode *next;
}LinkNode;
void CreateListR(LinkNode *&L,ElemType a[ ],int n)
  {     LinkNode *s,*r;int i;
        L=(LinkNode  *)malloc(sizeof(LinkNode)); 
        L->next=NULL;
        r=L;    
        for (i=0;i<n;i++)
        {    s =  (LinkNode*)malloc(sizeof(LinkNode));
              s->data=a[i];
              r->next=s;  
              r=s;
        }
        r->next=NULL;
  }
void Reverse(LinkNode *&L){
	LinkNode *p,*q;
	p=L->next;
	L->next=NULL;
	while(p!=NULL){
		q=p->next;
		p->next=L->next;
		L->next=p;
		p=q;
	}
}
void DispList(LinkNode *L)
{
	LinkNode *p=L->next;
	while (p!=NULL)
	{
		printf("%d ",p->data);
		p=p->next;
	}
	printf("\n");
}
void DestroyList(LinkNode *&L){
	LinkNode *pre,*p=L->next;
	while(p!=NULL){
		free(pre);
		pre=p;
		p=pre->next;
	}
	free(pre);
}
int main(){
	int a[]={1,3,5,7,9};
	int n=5;
	LinkNode *L;
	CreatlistR(L,a,n);
	Reverse(L);
	DispList(L);
	DestroyList(L);
	return 0;
} 





