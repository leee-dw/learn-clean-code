# 이름에 정보 담기

## 특정한 단어 고르기

### '무의미한 단어'를 피하자

```python
// Not Good
def GetPage(url):
  
  
// Good

def FetchPage():

```

위 코드에서 `get` 은 별 의미를 전달하지 않는다. 이 메서드를 보고는 로컬 캐시, 데이터 베이스, 인터넷 중 어디서 페이지를 가져오는지 알 수 없다. 만약 인터넷에서 가져오는 것이라면 `FetchPage()` 혹은 `DownloadPage()` 가 더 의미 있는 이름이 될 것이다.



```typescript
// Not Good
class BinaryTree {
  int Size();
}

// Good
class BinaryTree {
  int Height();
}
```

Size() 메서드는 무엇을 반환할까? 트리의 높이, 노드의 갯수, 트리의 메모리 사용량? 문제는 Size()라는 이름이 우리가 의도한 정보를 전달하지 못하는 데, 있다. `Height()`, `NumNodes()` 혹은 `MemoryBytes()` 등이 더 의미있는 이름이 될 것이다.



또 다른 예로 다음과 같은 Thread 클래스가 있다고 해보자.

```typescript

// Not Good
class Thread {
  void Stop();
}

// Good
class Thread {
  void Kill();
}
```



### 더 화려한 단어를 고르기

| 단어  | 대안                                              |
| ----- | ------------------------------------------------- |
| send  | deliver, dispatch, announce, distribute, route    |
| find  | search, extract, locate, recover                  |
| start | launch, create, begin, open                       |
| make  | create, setup, build, generate, compose, add, new |



## tmp나 retval같은 보편적인  이름 피하기

```js
// Not Good
var euclideanNorm = function(v) {
  var retval = 0;
  for (var i = 0; i < v.length; i++) {
    retval += v[i] * v[i];
  }
  return Math.sqrt(retval);
}

// Good
var euclideanNorm = function(v) {
  var sumSquares = 0;
  for (var i = 0; i < v.length; i++) {
    sumSquares += v[i] * v[i];
  }
  return Math.sqrt(retval);
}


// retval이라는 이름은 정보를 제대로 담고 있지 않다. 변수값을 설명하는 이름을 사용해라
```



## 추가적인 정보를 이름에 추가하기

### 단위를 포함하는 값들

```js
// Not Good
var start = (new Date()).getTime(); 
var elapsed = (new Date()).getTime() - start;
document.writeln('Load Time was: ' elapsed + 'seconds');


// Good
var startMs = (new Date()).getTime();
var elapsedMs = (new Date()).getTime() - startMs;
document.writeln('Load Time was: ' + elapsedMs / 1000 + "seconds");
```

단위를 포함하는 변수명의 마지막에는 단위를 추가하도록 한다.



## 요약

* 특정한 단어를 사용하라 - 상황에 따라 Get 대신 Fetch나 Download를 사용하는 것이 낫다.

* tmp나 retval 같은 보편적인 이름의 사용을 피하라

* 변수명에 중요한 세부정보를 덧붙여라 - 예를 들어 밀리초의 값을 저장하는 변수 뒤에 _ms를 붙이거나 이스케이핑을 수행하는 변수 앞에 `raw` 를 붙여라

  