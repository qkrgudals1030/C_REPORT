* 용어 정리 

차수 - 자식 노드의 개수

잎 - 자식 노드가 0인 노드

서브트리(sub Tree) - 트리 내부의 작은 트리

포리스트(Forest) - 트리가 여러 개 모인 것.

레벨(level) - 루트에서 그 노드까지의 거리를 말함.(루트레벨 :1)

높이 - 트리의 최대 레벨.

경로 - 특정 노드에서 특정 노드까지 가는 길. 트리의 경로는 1가지만 존재하는 특징이 있음.

(참고 : 그래프의 경로는 여러가지 가능)

1. 리스트의 종류와 설명

(1) 설명
    
   리스트 : 리스트(list)는 컴퓨터 과학에서 같은 값이 한 번 이상 존재할 수 있는 일련의 값이 모여있는 추상적 자료형이다. 시퀀스(sequence)라고             도 부른다.
   
(2) 종류 
    
   연결 리스트(linked list) : 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조이다.
   
   인접 리스트(adjacency list) : 그래프 이론에서 그래프를 표현하기 위한 방법 중 하나이다.
   
   메일링 리스트(mailing list) : 수많은 인터넷 사용자들에게 정보를 널리 퍼뜨릴 수 있도록 전자 우편을 이용하는 특별한 방법이다.

(3) 코드예제

#include <stdio.h>

#include <stdlib.h>

typedef struct list {

 int d;
 
 struct list* p;
 
} LIST;

LIST* root = NULL;

LIST* last = NULL;

void AddList(int a){

 LIST* r = (LIST*)malloc(sizeof(LIST));
 
 r->d = a;
 
 r->p = NULL;
 
 if(root==NULL) root = r;
 
 else           last->p = r;
 
 last = r;
 
}

int main(void){

 AddList(35);
 
 AddList(40);
 
 AddList(45);
 
 while(root){
 
  printf("%d\n", root->d);
  
  root = root->p;
  
 }
}


2. 트리의 종류 및 설명

(1) 설명

   트리는 여러 노드가 한 노드를 가리킬 수 없는 구조이다
   트리란 ‘나무를 닮은 자료구조’ 를 말합니다. 컴퓨터 과학에서 무궁무진한 응용을 하고 있는 대표적인 자료구조 입니다.
   
(2) 종류
   
  이진 트리 : 이진 트리란 컴퓨터 과학에서 아주 활발히 응용되는 분야 중 하나입니다. 앞서 살펴보았던 트리와는 달리 모든 모드가 최대 2개의 자식을 가질 수 있는 트리입니다.
  
  포화 이진 트리 : 잎 노드를 제외한 모든 노드가 자식을 둘씩 가지고 있는 트리입니다.
  
  완전 이진 트리: 잎 노드들이 왼쪽 부터 차근차근 채워진 것이 특징입니다.
  
  높이 균형 트리: 루트 노드를 기준으로 왼쪽 하위트리와 오른쪽 하위 트리가 1이상 차이 나지 않는 이진 트리입니다.
  
(3) 코드예제 
  
  레벨오더
  
#include<stdio.h>

#include <stdlib.h>  

typedef struct Tree {

struct Tree* l, * r;

int d;

} T;

void print(T* p) {

printf("%d\n", p->d);

if (p->l) print(p->l);

if (p->r) print(p->r);

}

T* mem() {

T* p = (T*)malloc(sizeof(T));

p->l = p->r = NULL;

return(p);

}

int main(void) {

T* r, * r1, * r2, * l1;

l1 = (T*)mem(); l1->d = 3;

r2 = (T*)mem(); r2->d = 8;

r1 = (T*)mem(); r1->d = 7; r1->r = r2;

r = (T*)mem(); r->d = 5; r->l = l1;  r->r = r1;

print(r);

}

프리오더

#include<stdio.h>

#include <stdlib.h>  

typedef struct Tree {

struct Tree* l, * r;

int d;

} T;

void print(T* p) {

if (p->l) print(p->l);

  printf("%d\n", p->d); 

if (p->r) print(p->r);

}

T* mem() {

T* p = (T*)malloc(sizeof(T));

p->l = p->r = NULL;

return(p);

}

int main(void) {

T* r, * r1, * r2, * l1;

l1 = (T*)mem(); l1->d = 3;

r2 = (T*)mem(); r2->d = 8;

r1 = (T*)mem(); r1->d = 7; r1->r = r2;

r = (T*)mem(); r->d = 5; r->l = l1;  r->r = r1;

print(r);

} 

포스트오더

#include<stdio.h>

#include <stdlib.h>  

typedef struct Tree {

struct Tree* l, * r;

int d;

} T;

void print(T* p) {

if (p->l) print(p->l);

if (p->r) print(p->r);

  printf("%d\n", p->d);

}

T* mem() {

T* p = (T*)malloc(sizeof(T));

p->l = p->r = NULL;

return(p);

}

int main(void) {

T* r, * r1, * r2, * l1;

l1 = (T*)mem(); l1->d = 3;

r2 = (T*)mem(); r2->d = 8;

r1 = (T*)mem(); r1->d = 7; r1->r = r2;

r = (T*)mem(); r->d = 5; r->l = l1;  r->r = r1;

print(r);

}
  

3. 그래프에 대한 설명

(1) 그래프의 종류와 설명

   유방향 그래프(Directed Graph) — 간선의 방향이 존재하는 그래프
   무방향 그래프(Undirected Graph) — 모든 간선이 방향을 가지지 않는 그래프
   비가중치 그래프 — 모든 간선에 가중치가 없는 그래프
   그래프는 사물을 정점(Vertex)과 간선(Edge) 으로 표현하기 위한 도구 입니다.
   
(2) 구현방법
   
   인접 행렬(Adjacency Matrix) — 2차원 배열을 사용하는 방식
   인접 리스트(Adjacency List) — 리스트를 사용하는 방식
   
(3) 코드예제

무방향 비 가중치 그래프를 인접 행렬로 표현하기

int a[1000][1000];
// 노드가 1000개 존재한다고 가정 1000 * 1000

int n, m;
// n = 노드의 갯수, m = 간선의 갯수

int main(void) 
{
  scanf_s("%d %d", &n, &m);
  // 노드의 갯수과 간선의 갯수를 입력 받습니다.
  
  for (int i = 0; i < m; i++) 
  // 간선의 갯수만큼 반복
  {
    int x, y;
    scanf_s("%d %d", &x, &y);
    // 서로 이어져 있는지 상태를 입력 받는다.
    // ex) 1 2 로 입력할 경우 1 과 2 는 서로 연결이 됐다는 뜻
    
   a[x][y] = 1;
   a[y][x] = 1;
    // 방향성이 없기 때문에 서로 이어져 있음을 1 로 표시합니다.
    
 }
 for (int i = 0; i <= n; i++) 
 {
   for (int j = 0; j <= n; j++) 
   {
        printf("%d ", a[i][j]);
	}
	    printf("\n");
	}
    // 연결되어 있는지 출력하여 확인합니다.
  
   system("pause");
}

소감 
수업시간에 듣고 기억한 내용을 다시한번 카페와 인터넷을 이용하여 정리해보면서 리스트, 트리, 그래프에대해 쉽게 이해하고 기억에도 더 잘남을 수 았었던것같습니다. 또한 이해가 되지 않았던 부분에 대해서는 그냥 넘어가는것이 아니라 친구들과 함께 고민해 보면서 서로가 이해되지 않는 부분에 대해서 설명해주면서 부족한부분을 채울수 있었던것같습니다. 이런 활동을 통해 조금더 프로그래밍에 대해 흥미를 느낄 수 있었고 언젠가 저도 다양한 언어를 열심히 공부하여 저만의 프로그램을 만들어 보고 싶다고 생각하였습니다. 지금보다 더 열심히 c언어를 공부해보겠습니다. C언어 공부파이팅!! 
