#include<stdio.h>
#include <malloc.h>
#define maxX 9
#define maxY 4
#define NSIZE 100
typedef struct{
	int X;
	int Y;
}Stats;
typedef struct{
	Stats stat;
	struct Node*parent;
	int id;
}Node;
typedef struct
{
	Node*Elements[NSIZE];
	int front,rear;
}Queue;
void makenull(Queue*Q)
{
	Q->front=0;
	Q->rear=-1;
}
void thempt(Queue*Q,Node* x)
{
	Q->rear++;
	Q->Elements[Q->rear]=x;
}
Node* laypt(Queue Q)
{
	return Q.Elements[Q.front];
}
void pop(Queue*Q)
{
	Q->front++;
}
int empty(Queue*Q)
{
	return Q->front>Q->rear;
}
int max(int a, int b){
	if(a>b)
	return a;
	else return b;
}
int min(int a, int b){
	if(a<b)
	return a;
	else return b;
}
Stats dodayX(Stats current){
	Stats a={-1,-1};
	if(current.X<maxX){
	a.Y=current.Y;
	a.X=maxX;
	}
	return a;
}
Stats dodayY(Stats current){
	Stats a={-1,-1};
	if(current.Y<maxY){
	a.X=current.X;
	a.Y=maxY;
	}
	return a;
}
Stats lamrongX(Stats current){
	Stats a={-1,-1};
	if(current.X>0){
	a.X=0;
	a.Y=current.Y;
	}
	return a;
}
Stats lamrongY(Stats current){
	Stats a={-1,-1};
	if(current.Y>0){
	a.Y=0;
	a.X=current.X;
	}
	return a;
}
Stats doXquaY(Stats current){
	Stats a={-1,-1};
	if(current.X>0&&current.Y<maxY){
			a.X=max(current.X-(maxY-current.Y),0);
			a.Y=min(current.X+current.Y,maxY);
	}
	return a;
}
Stats doYquaX(Stats current){
	Stats a={-1,-1};
	if(current.Y>0&&current.X<maxX){
			a.Y=max(current.Y-(maxX-current.X),0);
			a.X=min(current.Y+current.X,maxX);
	}
	return a;
}
int goalCheck(Stats stats,int n){
	return (stats.X==n||stats.Y==n);
}
void makenullStats(Stats*stats){
	stats.X=0;
	stats.Y=0;
}
int thaotac(Stats current, int opt){
	Stats a;
	switch(opt)
		case 1: 
			a=dodayX(current);
			if(a.x==-1)
			return 0;
			else return 1;
		case 2: 
			a=dodayY(current);
			if(a.x==-1)
			return 0;
			else return 1;
		case 3: 
			a=lamrongX(current);
			if(a.x==-1)
			return 0;
			else return 1;
		case 4: 
			a=lamrongY(current);
			if(a.x==-1)
			return 0;
			else return 1;
		case 5: 
			a=doXquaY(current);
			if(a.x==-1)
			return 0;
			else return 1;
		case 6: 
			a=doYquaX(current);
			if(a.x==-1)
			return 0;
			else return 1;
}
Node* BFS(Stats stat,int n)
{
	int i;
	Queue open;
	Queue close;
	makenull(&open);
	makenull(&close);
	Node*root=(Node*)malloc(sizeof(Node));
	root->stat=stat;
	root->parent=NULL;
	root->id=0;
	thempt(&open,root);
	while(empty(&open))
	{
		Node*c=laypt(&open); pop(&open);
		thempt(&close,c);
		if(goalCheck(c,n))
			return c;
		for(i=1;i<=n;i++)
			
	}
}
int main(){
	int X;
	Stats S;
	printf("nhap trang thai dau:\n");   
	printf("nhap X:");  //nhap x
	scanf("%d",&S.X);    
	printf("nhap Y:");   //nhap y
	scanf("%d",&S.Y);
	printf("nhap so luong mong muon:"); 
	scanf("%d",&X);
//	Stats a = dodayX(S);
//	printf("X: %d Y:%d",a.X,a.Y);
//	Stats b = dodayY(S);
//	printf("X: %d Y:%d",b.X,b.Y);
//	Stats b = doXquaY(S);
//	printf("X: %d Y:%d",b.X,b.Y);
//	b = doYquaX(S);
//	printf("X: %d Y:%d",b.X,b.Y);
//	Stats b = lamrongX(S);
//	printf("X: %d Y:%d",b.X,b.Y);
//	b = lamrongY(S);
	printf("X: %d Y:%d",b.X,b.Y);	
	return 0;
}
