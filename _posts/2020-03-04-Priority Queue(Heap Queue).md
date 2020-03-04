# Priority Queue (= Heap Queue) 


<br/>

## 1.  Priority Queue

- Queue 구조처럼 뒤쪽으로 원소를 삽입하고, 앞쪽에서 꺼낸다.  (FIFO, 선입선출)

- 그러나 내부적으로 논리적인 우선순위가 정해져 있다. 
    - 높은 우선순위를 갖는 원소가 앞쪽으로 온다. 
- Max/Min Queue , Heap Queue 

- 배열, 연결리스트, 힙으로 구현 가능하다.

</br>
</br>
## 2. Heap

- Complete Binary Tree(완전이진트리) 기반으로, 최댓값 및 최솟값 연산을 빠르게 하기 위해 고안된 구조 

- 루트 노드는 가장 우선순위가 높거나 혹은 가장 우선순위가 낮은 원소

- 파이썬의 경우, 리스트로 구현

- 힙 종류

    1. Max Heap(최대힙)
        - 부모 노드의 키 값이 항상 자식노드의 키 값보다 큼 

    2. Min Heap(최소힙)
        - 부모 노드의 키 값이 항상 자식노드의 키 값보다 작음 


</br>
</br>
## 3. heapq

- 파이썬의 heapq 모듈 : Complete Binary Tree 기반 Min Heap 자료구조 

- 루트 노드는 heapq에서 가장 작은 값 

- 가장 작은 값 알고 싶을 때 용이

<pre>
<code>
heap = []
heapq.heappush(heap, 1)

heap = [1,2,3,4]
heapq.heapify(heap) 
</code>
</pre>


</br>
</br>
## 4. heapq를 쓰는 알고리즘 문제 - 더 맵게 

- 섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)
- Leo는 모든 음식의 스코빌 지수가 K 이상이 될 때까지 반복하여 섞음 
- 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 섞어야 하는 최소 횟수를 return 

----
- 매번 가장 작은 수를 찾기 위해 sort 하는 것보다 heapq를 쓰는게 시간복잡도가 낮다. 





</br>
</br>

## *Reference*
 
<https://developer-alle.tistory.com/321>
</br>
<https://soooprmx.com/archives/5121>

