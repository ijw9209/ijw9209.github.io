---
title: "[자료구조] Linked List"
excerpt: "Linked List(연결리스트) - 자료구조"
toc: true
toc_sticky: true

categories:
  - etc
  - data structure
tags:
  - etc
  - data structure
last_modified_at: 2020-03-13T08:06:00-05:00
---

# LinkedList

LinkedList는 Array List와는 다르게 엘리먼트와 엘리먼트 간의 **연결(link)**을 이용해서
리스트를 구현한 것

## 연결

배열과는 다르게 Linked List는 그위치가 흩어져있기때문에 서로 연결되어 있어야 합니다.
Linked List와 같이 연결된 엘리먼트들은 **노드(node, 마디 교정의 의미) 혹은 버텍스(vertex , 정점 꼭지점의 의미)**라고 부릅니다. 이런 용어들은 연결성이 강조된 표현이라고 생각하면 됩니다.

## 구조 

Linked list의 구조를 살펴보면, 리스트는 노드(엘리먼트)들의 모임이고, 따라서 내부적으로노드를 가지고 있어야합니다. array list의 경우 엘리먼트가 배열의 엘리먼트였습니다. linked list는 배열 대신에 다른 구조를 사용합니다

노드는 최소한 두 가지 정보를 알고 있어야합니다. 노드의 값과 다음 노드입니다.
각각의 노드가 다음노드를 알고 있기 떄문에 하나의 연결된 값의 모임을 만들 수 있는 것입니다. 아래의 그림은 linked list 의 구조를 보여줍니다

![image5](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2939.png)

이것을 구현하는 방법은 여러가지입니다. 만약 자바와 같은 객체지향언어라면
객체에 데이터 필드와 링크필드를 만듭니다. 보통 데이터 필드는 value라는 이름의 변수, 링크필드는 next 변수를 사용합니다. value 에는 노드의 값이 저장되고 , next에는 다음 노드의 포인터나 참조값을 저장해서 노드와 노드를 연결시키는 방법을 사용합ㄴ디ㅏ

## Head

위의 그림을 보면 head라는 것이 있습니다. 건물에 비유하면 출입문에 해당하는것이 head입니다. linked list를 사용하기 위해서는 이 head가 가리키는 첫번째 노드를 찾아야합니다. 취향에 따라서는 first와 같은 이름을 사용하는 경우도 있습니다.


## 데이터의 추가

## 시작부분에 추가

노드를 첫 번째 위치에 추가해보려면

![image6](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2943.png)

우선 새로운 노드를 생성

```js
Vertex temp = new Vertex(input)

```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2944.png)

새로운 노드의 다음 노드로 첫번째 노드를 가리킵니다.

```js
temp.next = head
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2945.png)

새로 만들어진 노드가 첫번째 노드가 되도록 head의 값을 변경합니다.

```js
head = temp
```
위 작업에 대한 전체 소스
```js
Vertex temp = new Vertex(input)
temp.next = head
head = temp
```

## 중간에 추가

3번째 자리 (인덱스 2)에 90을 추가해봅니다.

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2930.png)

3번째자리는 붉은 화살표가 표시된 부분입니다.
6과 23사이에 90을 위치시켜보겠습니다. 우선 3번째자리를 찾아야합니다.'

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2919.png)

head를 참조해서 첫번째노드를 찾고,

```js
Vertex temp1 = head
```
![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2920.png)

23의 자리에 새로운 노드를 위치시키기 위해서는 6을 알고 있어야 합니다. 6의 next로 새로운 노드를 지정해야 하기때문. 아래는 6을 temp1로 지정하기 위한 반복문입니다.

```js
//현재 k의 값은 2
while(--k!= 0){
    temp1 = temp1.next
}
```

![ima](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2921.png)

6의 next를 이용해서 23을 찾아서 temp2로 지정합니다.

```js
Vertex temp2 = temp1.next
```

![iamge](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2922.png)

값이 90인 새로운 노드를 생성합니다

```js
Vertex newVertex = new Vertex(input)
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2923.png)

6의 다음 노드로 새로운 노드를 지정합니다

```js
temp1.next = newVertex
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2924.png)

새로운 노드의 다음 노드로 23번을 지정합니다

```js
newVertex.next = temp2
```
![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2926.png)

이렇게해서 90을 3번째자리에 위치시켰습니다.

전체코드
```js
Vertex temp1 = head
while (--k!=0)
  temp1 = temp1.next
Vertex temp2 = temp1.next
Vertex newVertex = new Vertex(input)
temp1.next = newVertex
newVertex.next = temp2
```


이것이 array list와 linked list의 핵심적인 차이점입니다. 배열의 경우는 엘리먼트를 중간에 추가/삭제할 경우 해당엘리먼트 뒤에있는 모든 엘리먼트를 자리 이동 시켰습니다.
그래서 배열은 추가/삭제가 느립니다.
하지만 linked list의 경우 추가/삭제가 될 엘리먼트의 이전, 이후 노드의 참조값(next)만 변경하면 되기때문에 속도가빠릅니다

## 데이터의 삭제

데이터를 제거하는 것도 추가하는것과 비슷 아래의 인덱스 2번째 항목을 삭제하겠습니다.


![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2932.png)


우선 head를 이용해 첫번째 노드를 찾습니다.

```js
Vertex cur = head
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2933.png)

그리고 두번째 노드로 이동합니다
```js
//k = 2
while(--k!=0){
  cur = cur.next
}

```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2934.png)

세번째 노드를 찾았습니다

```js
Vertex tobedelete = cur.next
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2935.png)


두번째 노드의 next를 23으로 변경합니다

```js
cur.next = cur.next.next
```

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2936.png)


90을 삭제해서 메모리에서 제거합니다
```
delete tobedeleted
```

아래는 전체 코드입니다
```js
Vertex cur = head
while(--k!=0){
  cur = cur.next
}  
Vertex tobedeleted = cur.next
cur.next = cur.next.next
delete tobedeleted
```

## 인덱스를 이용한 데이터 조회

인덱스를 이용해서 데이터를 조회할때 Linked list는 head가 가리키는 노드부터 순차적으로
노드를 찾아가는 과정을 거쳐야합니다. 만약 찾고자하는 엘리먼트가 가장끝에있다면 모든 노드를 탐색해야함.

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2937.png)

반면에 array를 이용해서 리스트를 구현하면 인덱스를 이용해서 해당 엘리먼트에 바로 접근 할 수있기 때문에 매우 빠릅니다.

![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2938.png)

## trade off

트레이드 오프는 장점이 있으면 단점이 있다 
우리가 자료구조를 배우는 이유중 하나는 이러한 트레이드 오프를 이해하기위해서입니다.
장점과 단점의 미묘한 균형을 이해할 수 있어야  올바른 선택을 할 수 있습니다.


![image](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2885.png)