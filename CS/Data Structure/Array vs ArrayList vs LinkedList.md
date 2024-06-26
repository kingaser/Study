# Array vs ArrayList vs LinkedList

### ArrayList

![image](https://github.com/kingaser/Study/assets/104209781/70bc877d-48cd-4cb7-9632-99b6c3f68dd3)

### LinkedList

![image](https://github.com/kingaser/Study/assets/104209781/79fb4852-e1a8-4447-8214-25ec496479e1)

- <b>Array</b>는 Index로 빠르게 값을 찾는 것이 가능
- <b>ArrayList</b>는 데이터의 삽입 및 삭제가 빠름
- <b>LinkedList</b>는 데이터를 찾는데 빠르지만, 삽입 및 삭제가 느림

### Array(배열)
- 선언할 때 크기와 데이터 타입을 지정해야 함
```Java
int arr[10];
String arr[5];
```
- <b>배열</b>은 메모리 공간에 할당할 사이즈를 미리 정해놓고 사용하느 자료구조
- 계속 데이터가 늘어날 때, 최대 사이즈를 알 수 없을 때는 사용하기 부적합
- 중간에 데이터를 삽입하거나 삭제할 때도 비효율적
- 4번째 Index 값에 새로운 값을 넣는다면, 원래 값을 뒤로 밀고 해당 Index에 덮어씌워야 함
- 기본적으로 사이즈를 정해놓은 배열에서는 해결하기에 부적합한 점이 많음
- <b>배열</b>은 Index가 존재하기 때문에 위치를 바로 알 수 있어 검색에 편한 장점이 있음

### ArrayList(List)
- <b>List</b>는 <b>배열</b>처럼 크기를 지정해주지 않아도 됨
- 순서가 중요함
- 크기가 정해져있지 않기 때문에, 중간에 데이터를 추가하거나 삭제하더라도 배열에서 갖고 있던 문제점을 해결 가능
- Index를 가지고 있으므로 검색도 빠름
- 중간에 데이터를 추가 및 삭제할 때 시간이 오래걸리는 단점은 여전히 존재
- 더하거나 뺄때마다 줄줄이 당겨지거나 밀려날 때 진행되는 연산이 추가, 메모리도 낭비

### LinkedList
- 연결리스트에는 단일, 다중 등 여러가지가 존재
- 종류가 무엇이든, 한 노드에 연결될 노드의 포인터 위치를 가리키는 방식으로 되어있음
- 단일은 뒤에 노드만 가리키고, 다중은 앞뒤 노드를 모두 가리키는 차이

- 이러한 방식을 활용하면서, 데이터의 중간에 삽입 및 삭제를 하더라도 전체를 돌지 않아도 이전 값과 다음값이 가르켰던 주소값만
수정하여 연결시켜주면 되기 때문에 빠르게 진행 가능
- 삽입, 삭제시에는 효율적, 검색에는 비효율적(주값을 통해 다음 값을 찾아가기 때문)

```
<b>Array</b>나 <b>ArrayList</b>에서 Index를 갖고 있기 때문에 검색이 빠르지만, <b>LinkedList</b>는 처음부터 살펴봐야하므로
검색에 있어서는 시간이 더 걸린다는 단점이 존재

상황에 맞게 자료구조를 잘 선택해서 사용하는 것이 중요
```
