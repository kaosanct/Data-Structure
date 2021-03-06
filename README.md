# 자료구조

* 자료구조의 필요성
  1. 데이터를 효과적으로 저장하고, 처리하는 방법에 대해서 바르게 이해할 필요가 있다.
  2. 자료구조를 제대로 이해하지 못하면 불필요하게 메모리와 성능을 낭비할 여지가 있다.
  3. 프로그램 내에서 int형 데이터가 100만개 가량 될때 원하는 데이터를 가장 빠르게 찾도록 해주는 자료구조를 찾기 위해서

---


## 기본적인 자료구조들
  * 선형 구조
    - 배열
    - 연결 리스트
    - 스택
    - 큐
  * 비선형 구조
    - 트리(Tree)
    - 그래프(Graph)

---

## 자료구조와 알고리즘
  - 효율적인 자료구조 설계를 위해 알고리즘 지식이 필요하다.
  - 효율적인 알고리즘을 작성하기 위해서는 문제 상황에 맞는 적절한 자료구조가 사용되어야 한다.
  - 따라서 자료구조론과 알고리즘 이론은 모두 동일선상에 놓을 수 있다.

---

## 프로그램의 성능 측정 방법론

1. 시간 복잡도(Time Complexity)란 알고리즘에 사용되는 연산 횟수를 의미한다.
2. 공간 복잡도(Space Complexity)란 알고리즘에 사용되는 메모리의 양을 의미한다.

> 효율적인 알고리즘을 사용한다고 가정했을 때 일반적으로 시간과 공간은 반비례 관계이다.

  * 시간 복잡도를 표현할 때는 최악의 경우를 나타내는 Big-O 표기법을 사용한다. 다음 알고리즘은 O(n)의 시간 복잡도를 가진다.

  ```cpp
    int main(void){
      int a,b;
      cin >> a >> b;
      int sum = 1;
      for (int i = 0 ; i < b ; i++){
        sum \*= a;
      }
      cout << sum;
    }
  ```

  * 다음 알고리즘은 O(n^2)의 시간복잡도를 가진다.
  ```cpp
    #include <iostream.h>

    using namespace std;

    int main(void){
      int n;
      cin >> n;
      for(int i = 0; i < n ; i++){
        for(int j = 0 ; j <= i ; j++){
          cout << "\*";
        }
        cout << '\n';
      }
    }
  ```

  * 다음 알고리즘은 1의 시간 복잡도를 가진다.

  ```cpp
    int main(void){
      int a,b;
      cin >> a >> b;
      cout << a + b;
    }

  ```

![Big-O](https://joshuajangblog.files.wordpress.com/2016/09/1.jpg?w=638)

  * [예시] : n이 1000일 때
    - n : 1000번의 연산
    - nlogn : 약 10000번의 연산 (1000 * log1000)
    - n^2 : 1,000,000번의 연산
    - n^3 : 1,000,000,000번의 연산

  > 보통 연산의 횟수가 10억을 넘어가면 1초 이상의 시간이 소요된다.

  * 시간 복잡도를 표기할 때는 항상 큰 항과 계수만 표시한다.
    - O(3n^2 + n) = O(n^2)
    - 현실적인 다양한 문제에서는 시간 제한이 1초 정도라고 생각하면 된다.

  * 공간 복잡도를 표기할 때는 일반적으로 MB 단위로 표기한다.
    - int a[1000] : 4 KB (int 는 4byte이므로)
    - int a[1000000] : 4 MB
    - int a\[2000\]\[2000\] : 16 MB

---

## 연결리스트

  * 연결 리스트의 필요성
    - 일반적으로 배열을 사용하여 데이터를 순차적으로 저장하고, 나열할 수 있다.
    - 배열을 사용하는 경우 메모리 공간이 불필요하게 낭비될 수 있다.

---

  * 배열 기반의 리스트
    - 데이터를 순차적으로 저장하고, 처리할 때는 배열 기반의 리스트를 간단히 이용할 수 있다.

  * 배열 기반 리스트의 특징
    - 배열로 만들었으므로 특정한 위치의 원소에 즉시 접근할 수 있다는 장점이 있다.
    - 데이터가 들어갈 공간을 미리 메모리에 할당해야 한다는 단점이 있다.
    - 원하는 위치로의 삽입이나 삭제가 비효율적이다. (하나하나 앞으로 밀어줘야 함)

---

## 연결 리스트
  * 일반적으로 연결 리스트는 구조체와 포인터를 함께 사용하여 구현한다.
  * 연결 리스트는 리스트의 중간 지점에 노드를 추가하거나 삭제할 수 있어야 한다.
  * 필요할 때마다 메모리의 공간을 할당 받는다.

---

## 단일 연결 리스트
  * 포인터를 이용해 단방향적으로 다음 노드를 가리킨다.
  * 일반적으로 연결 리스트의 시작 노드를 헤드(head)라고 하며 별도로 관리한다.
  * 다음 노드가 없는 끝 노드의 다음 위치 값으로는 NULL을 넣는다.
![단일연결리스트](https://t1.daumcdn.net/cfile/tistory/2115D641533FDD5E3A)
  * 삽입 및 삭제 기능에서의 예외 사항을 처리할 필요가 있다.
  * 삭제할 원소가 없는데 삭제하는 경우, 머리(head) 노드 자체를 잘못 넣은 경우 등을 체크해야 한다.

---
## 연결리스트의 특징
  - 삽입과 삭제가 배열에 비해서 간단하다는 장점이 있다.
  - 배열과 다르게 특정 인덱스로 즉시 접근하지 못하며, 원소를 차례대로 검색해야 한다.
  - 추가적인 포인터 변수가 사용되므로 메모리 공간이 낭비된다.
  - 기존에 배열을 이용했을 때보다 삽입과 삭제가 많은 경우에서 효율적이다.
  - 다만 특정한 인덱스에 바로 참조해야 할 때가 많다면 배열을 이용하는 것이 더 효율적이다.

---
## 양방향 연결 리스트
  * 양방향 연결 리스트는 머리(head)와 꼬리(tail)를 모두 가진다는 특성이 있다.
  * 양방향 연결 리스트의 각 노드는 앞 노드와 뒤 노드의 정보를 모두 저장하고 있다.
  * 삽입 및 삭제 기능에서의 예외 사항을 처리할 필요가 있다.
  * 더 이상 삭제할 원소가 없는데 삭제하는 경우 등을 체크해야 한다.
  * 양방향 연결 리스트를 이용하면 리스트의 앞에서부터 혹은 뒤에서부터 모두 접근할 수 있다.
    - 대신 포인터를 두개 사용함으로써 단일 연결 리스트보다 메모리가 조금 더 소모된다.
![양방향연결리스트](http://20tvni1sjxyh352kld2lslvc.wpengine.netdna-cdn.com/wp-content/uploads/sites/1/nggallery/data-structures/doubly-linked-list-2.png)
---
## 스택
  * 스택(Stack)은 한쪽으로 들어가서 한쪽으로 나오는 자료구조이다.
  * 이러한 특성 때문에 수식 계산 등의 알고리즘에서 다방면으로 활용된다.
    - PUSH : 스택에서 데이터를 넣는다.
    - POP : 스택에서 데이터를 빼낸다.
    - 맨 마지막으로 넣은 것이 처음으로 출력됨.
![스택](https://upload.wikimedia.org/wikipedia/commons/b/b4/Lifo_stack.png)
---
## 스택의 구현
  * 스택(Stack)은 배열을 이용한 구현 방법과 연결 리스트를 이용한 구현 방법으로 나누어 진다.
  * 가장 기본적인 형태의 자료구조로 구현 난이도가 낮다.

---
## 스택을 이용한 계산기 구현
  * 중위 표기법
    - 중위 표기법이란 일반적으로 사람이 수식을 표기할 때 사용하는 표기 방법
    - ex ) 7 * 5 + 3
  * 후위 표기법
    - 후위 표기법이란 컴퓨터가 계산하기 편한 수식의 형태
    - 후위 표기법에서 연산자는 뒤쪽에 위치
    - ex ) 7 5 * 3 +

  * 중위 -> 후위 표기법으로 바꾸는 방법
    - 피연산자가 들어오면 바로 출력한다.
    - 연산자가 들어오면 자기보다 우선순위가 높거나 같은 것들을 빼고 자신을 스택에 담는다.
    - 여는 괄호 '(' 를 만나면 무조건 스택에 담는다.
    - 닫는 괄호 ')' 를 만나면 '(' 를 만날 때까지 스택에서 출력한다.

  * 후위 표기법을 계산하는 방법
    - 피연산자가 들어오면 스택에 담는다.
    - 연산자를 만나면 스택에서 두 개의 연산자를 꺼내서 연산한 뒤에 그 결과를 스택에 담는다.
    - 연산을 마친 뒤에 스택에 남아있는 하나의 피연산자가 연산 수행 결과이다.

---
## Queue (큐)
  * 큐는 뒤쪽으로 들어가서 앞 쪽으로 나오는 자료구조이다.
  * 이러한 특성 때문에 스케줄링,탐색 알고리즘에서 다방면으로 활용된다.
  * 배열을 이용한 구현 방법과 연결 리스트를 이용한 구현 방법이 있다.

![queue](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTTpFXQdYj42wO508YtK4lS7nRLVGA1TyCOcM_Iau_EXFqnG6h4YQ)

---
## 선택정렬과 삽입정렬
  * 선택 정렬이란 가장 작은 것은 선택해서 앞으로 보내는 정렬 기법이다. 가장 작은 것을 선택하는 데에 N번, 앞으로 보내는 데에 N번의 연산으로 **O(N^2)** 의 시간 복잡도를 가진다.
  * 삽입 정렬이란 각 숫자를 적절한 위치에 삽입하는 정렬 기법이다. 들어갈 위치를 선택하는데 N번, 선택하는 횟수로 N번이므로 **O(N^2)** 의 시간 복잡도를 가진다.
  ![선택정렬](https://gmlwjd9405.github.io/images/algorithm-selection-sort/selection-sort.png)
  ![삽입정렬](https://gmlwjd9405.github.io/images/algorithm-insertion-sort/insertion-sort.png)
  > 출처 : https://jongmin92.github.io/2017/11/06/Algorithm/Concept/basic-sort/

---
## 퀵 정렬
  * 퀵 정렬이란 피벗을 기준으로 큰 값과 작은 값을 서로 교체하는 정렬 기법이다. 값을 서로 교체하는데에 N번, 엇갈린 경우 교체 이후에 원소가 반으로 나누어지므로 전체 원소를 나누는 데에 평균적으로 logN번이 소요되므로 평균적으로 **O(NlogN)** 의 시간 복잡도를 가진다.
  ![quickSort](http://interactivepython.org/courselib/static/pythonds/_images/partitionA.png)
  > 출처 :http://interactivepython.org/courselib/static/pythonds/SortSearch/TheQuickSort.html

  * 퀵 정렬은 편향된 분할이 발생할 때 연산의 양이 O(N^2)이다. 따라서 실제로 정렬을 함에 있어서는 퀵 정렬을 직접 구현하지 않는다. 따라서 C++의 algorithm 라이브러리를 사용한다. algorithm 라이브러리의 sort() 함수는 퀵 정렬을 기반으로 하되 O(NlogN)을 보장한다.

---
## 계수 정렬
 * 계수 정렬(Counting sort)는 크기를 기준으로 데이터의 개수를 세는 정렬 알고리즘이다. 각 데이터를 바로 크기를 기준으로 분류하므로 **O(N)** 이라는 시간 복잡도를 가진다.
 * 계수 정렬은 데이터의 크기가 한정적일때 사용할 수 있다.
 ![counting-sort](http://www.jidum.com/upload/ckeditor/2016/09/20160909101823110.png)
 > 출처 : http://www.jidum.com/jidums/view.do?jidumId=524

---
## 기수 정렬
  * 기수 정렬(Radix sort)는 자릿수를 기준으로 차례대로 데이터를 정렬하는 알고리즘이다. 각 데이터를 자릿수를 기준으로 분류하므로 가장 큰 자릿수를 D라고 했을 때 **O(DN)** 의 시간 복잡도를 가진다. 자릿수의 개수만큼 N번 반복한다. (일의 자리, 십의 자리등 자릿수가 작다면 사실상 계수 정렬만큼 빠르다고 볼 수 있다.)
  * 자료를 순서대로 일의 자리 값에 맞는 버킷에 넣고 해당하는 인덱스 값을 증가시킨다.
  * 각 버킷에 몇 개의 자료가 들어가는지와 누적수를 구한후 뒤에서부터 하나하나 누적수를 보고 재배열한다.
    - Ex) '46'숫자의 경우 6번 버킷의 누적수를 확인한다. 예를 들어 누적수가 13 이라면, 13번째에 46을 배치하고 6번 버킷의 누적수를 하나 빼준다.
    - 차례대로 뒤에서부터 숫자 하나하나씩 재배열 하면됨.
    - 십의 자리, 백의 자리도 마찬가지!
  ![Radix-sort](https://t1.daumcdn.net/cfile/tistory/22155249545489BE1E)
  * 일반적으로 기수 정렬은 계수 정렬보다 약간 더 느리지만, 숫자가 매우 큰 상황에서도 사용할 수 있다.
---
## 이진 트리
  * 트리(Tree)는 나무의 형태를 뒤집은 것과 같은 형태의 자료구조이다.
    - 일반적으로 트리의 최상단 노드를 루트 노드라고 하고, 루트 노드에서 가지로 각각의 노드로 연결된다. 끝에 연결 되어있는 노드를 리프 노드라고 한다.
    - 기본적으로 각각의 노드는 부모와 자식 관계를 가진다. 또 같은 레벨에 있다면 형제 노드라고 할 수 있다.
    - 길이(Length)란 출발 노드에서 목적지 노드까지 거쳐야 하는 가짓수를 의미한다.
    - 깊이(depth)란 루트 노드에서 특정 노드까지의 길이를 의미한다.
    - 트리의 높이(Height)란 루트 노드에서 가장 깊은 노드까지의 길이이다.

  * 이진 트리(Binary Tree)는 최대 2개의 자식을 가질 수 있는 트리이다.
    - 구현이 간단하여 다방면으로 활용된다.

  * 포화 이진 트리(Full Binary Tree)는 리프 노드를 제외한 모든 노드가 두 자식을 가지고 있는 트리이다.
  * 완전 이진 트리(Complete Binary Tree)는 모든 노드들이 왼쪽 자식부터 차근차근 채워진 트리이다.
  * 높이 균형 트리(Height Balanced Tree)는 왼쪽 자식 트리와 오른쪽 자식 트리의 높이가 1 이상 차이 나지 않는 트리이다.
  * 이진 트리는 많은 양의 노드를 낮은 높이에서 관리할 수 있다는 점에서 데이터 활용의 효율성이 높아진다.
  * 데이터 저장, 탐색 등의 다양한 목적에서 사용할 수 있다.

---
![binary_tree](https://t1.daumcdn.net/cfile/tistory/2321CB4951A467AC0B)
## 이진 트리의 전위 순회 알고리즘
  * 1. 자기 자신을 출력한다.
  * 2. 왼쪽 자식을 방문한다.
  * 3. 오른쪽 자식을 방문한다.
  * 10 - 5 - 1 - 6 - 17 - 14 - 21
---
## 이진 트리의 중위 순회 알고리즘(왼쪽에서부터 차례대로 방문)
  * 1. 왼쪽 자식을 방문한다.
  * 2. 자기 자신을 출력한다.
  * 3. 오른쪽 자식을 방문한다.
  * 1 - 5 - 6 - 10 - 14 - 17 - 21
---
## 이진 트리의 후위 순회 알고리즘
  * 1. 왼쪽 자식을 방문한다.
  * 2. 오른쪽 자식을 방문한다.
  * 3. 자기 자신을 출력한다.
  * 1 - 6 - 5 - 14 - 21 - 17 - 10

---
## 이진트리의 구현 및 순회
  * 이진 트리는 포인터를 이용해서 구현할 수 있다.
  * 이진 트리의 데이터를 방문하기 위해서 순회 알고리즘을 효과적으로 사용할 수 있다.

---
## 우선 순위 큐
  * 우선순위 큐는 '우선 순위' 를 가진 데이터들을 저장하는 큐를 의미한다. 데이터를 꺼낼 때 우선 순위가 높은 데이터가 가장 먼저 나온다는 특징이 있어 많이 활용되고 있다.
  * 우선순위 큐는 운영체제의 작업 스케줄링, 정렬, 네트워크 관리 등의 다양한 기술에 적용되고 있다.
  * 우선순위 큐와 큐의 차이점
    - 일반적인 형태의 큐는 선형적인 형태를 가지고 있지만 우선순위 큐는 트리(Tree) 구조로 보는 것이 합리적이다. 일반적으로 우선순위 큐는 최대 힙을 이용해 구현한다.
    - 최대 힙(Max Heap) : 최대 힙은 부모 노드가 자식 노드보다 값이 큰 완전 이진 트리를 의미한다.
      + 최대 힙의 루트 노드는 전체 트리에서 가장 큰 값을 가진다는 특징이 있다.

---
## 우선순위 큐의 삽입
  * 삽입할 원소는 완전 이진 트리를 유지하는 형태로 순차적으로 삽입된다.
  * 삽입 이후에는 루트 노드까지 거슬러 올라가면서 최대 힙을 유지할 수 있도록 구성한다.(상향식) 시간 복잡도: **O(logN)**
---
## 우선순위 큐의 삭제
  * 삭제를 할 때는 루트 노드를 삭제하고, 가장 마지막 원소를 루트 노드의 위치로 옮겨준다.
  * 삭제 이후에는 리프 노드까지 내려가면서 최대 힙을 구성한다. (하향식)

---
## 순차 탐색과 이진 탐색
  * 순차탐색(Sequential Search)는 특정한 원소를 찾기 위해 원소를 순차적으로 하나씩 탐색하는 방법이다. 데이터 정렬 유무와 상관 없이 가장 앞에 있는 원소부터 하나씩 확인해야 한다는 점에서 **O(N)** 의 시간 복잡도를 가진다.
  ![Sequential_search](https://t1.daumcdn.net/cfile/tistory/2133264853FDCD4C29)
  > 출처 : http://sw-tech.tistory.com/entry/%ED%83%90%EC%83%89%EC%88%9C%EC%B0%A8-%ED%83%90%EC%83%89

  * 이진탐색(Binary Search)는 배열 내부 데이터가 이미 정렬되어 있는 상황에서 사용 가능한 알고리즘이다. 탐색 범위를 절반씩 좁혀가며 데이터를 탐색하는 특징이 있다. 한 번 확인할 때마다 보아야 하는 원소의 개수가 절반씩 줄어든다는 점에서 탐색 시간이 **O(logN)** 의 시간 복잡도를 가진다.
  ![Binary_Search](https://t1.daumcdn.net/cfile/tistory/262CCF4657D6D0352E)
  >출처 : http://coderkoo.tistory.com/8

---
## 그래프
  * 그래프(Graph)란 사물을 정점(Vertex,Node)와 간선(Edge)으로 나타내기 위한 도구이다. 그래프는 두 가지 방식으로 구현할 수 있다.
    - 인접 행렬(Adjacency Matrix) : 2차원 배열을 사용하는 방식
    - 인접 리스트(Adjacency List) : 리스트를 사용하는 방식

    ![Adjacency_Matrix](https://cdn.filepicker.io/api/file/ASqFe9MSQXqzoZthyThq)
    > 출처 : https://www.zerocho.com/category/Algorithm/post/584b9033580277001862f16c

  * 무방향 비가중치 그래프와 인접 행렬
    - 모든 간선이 방향성을 가지지 않는 그래프를 무방향 그래프라고 한다.
    - 모든 간선에 가중치가 없는 그래프를 비가중치 그래프라고 한다.
    - 무방향 비가중치 그래프가 주어졌을 때 연결되어 있는 상황을 인접 행렬로 출력할 수 있다.

  * 방향 가중치 그래프와 인접 리스트
    - 모든 간선이 방향을 가지는 그래프를 방향 그래프라고 한다.
    - 모든 간선에 가중치가 있는 그래프를 가중치 그래프라고 한다.
    - 방향 가중치 그래프가 주어졌을 때 연결되어 있는 상황을 인접 리스트로 출력할 수 있다.
---    
## 그래프 개념과 구현
  * 인접 행렬은 모든 정점들의 연결 여부를 저장하여 O(V^2)의 공간을 요구하므로 공간 효율성이 떨어지지만 두 정점이 서로 연결되어 있는지 확인하기 위해 O(1)의 시간을 요구한다.
  * 인접 리스트는 연결된 간선의 정보만을 저장하여 O(E)의 공간을 요구하므로 공간 효율성이 우수하지만 두 정점이 서로 연결되어 있는지 확인하기 위해 O(V)의 시간을 요구한다.

---
## 깊이 우선 탐색
  * 깊이 우선 탐색(Depth First Search)은 탐색을 함에 있어서 보다 깊은 것을 우선적으로 하여 탐색하는 알고리즘이다. 깊이 우선 탐색은 기본적으로 전체 노드를 맹목적으로 탐색하고자 할 때 사용한다. 이 알고리즘은 스택(Stack) 자료구에 기초한다. 모든 경우의 수를 탐색하고자 할 때 쉽게 사용 가능!
    - 1. 탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.
    - 2. 스택의 최상단 노드에게 방문하지 않은 인접 노드가 하나라도 있으면 그 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.
    - 3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.
  ![DFS](https://gmlwjd9405.github.io/images/algorithm-dfs-vs-bfs/dfs-example.png)
  > 출처 : https://gmlwjd9405.github.io/2018/08/14/algorithm-dfs.html

  * 깊이 우선 탐색 알고리즘은 스택(Stack) 자료구조에 기초한다는 점에서 구현이 간단하다. 실제로는 스택을 쓰지 않아도 되며 탐색을 수행함에 있어서 **O(N)** 의 시간 복잡도를 가진다.
  * 참고 : https://blog.naver.com/ndb796/220702843478

---
## 너비 우선 탐색
  * 너비 우선 탐색(Breadth First Search)는 너비를 우선으로 하여 탐색을 수행하는 탐색 알고리즘이다. DFS와 마찬가지로 맹목적으로 전체 노드를 탐색하고자 할 때 자주 사용되며 큐(Queue) 자료구조에 기초한다. 너비 우선 탐색은 고급 그래프 탐색 알고리즘에서 자주 활용된다.
    - 1. 탐색 시작 노드를 큐에 삽입하고 방문 처리한다.
    - 2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은 노드들을 모두 큐에 삽입하고, 방문 처리한다.
    - 3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.
  * 너비 우선 탐색 알고리즘은 Queue자료구조에 기초한다는 점에서 구현이 간단하다. 또 실제로 구현함에 있어 큐 STL을 사용하면 좋으며 탐색을 수행함에 있어서 **O(N)** 의 시간 복잡도를 가진다. 일반적인 경우 실제 수행 시간은 DFS보다 좋은 편이다.
    ![BFS](https://cdn.filepicker.io/api/file/6sBaBZQVuci45KJTlGQ9)
    > 출처 : https://www.zerocho.com/category/Algorithm/post/5870153c37e1c80018b64eb0

  * 참고: https://blog.naver.com/ndb796/221230944971  
