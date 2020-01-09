# 2장 의미있는 이름 - 의도를 분명히 밝혀라

* __의도가 분명한 이름은 매우 중요하다.__
* 좋은 이름을 지으려면 시간이 걸리지만 좋은 이름으로 __절약하는 시간이 훨씬 많다.__
* 그러므로, 이름을 주의 깊게 살펴 더 나은 이름이 떠오르면 개선해야 한다.
* 변수의 이름은 나 혼자 읽는 것이 아니라, 팀원들도 읽게 되고, 팀원들이 코드를 이해하는데에 도움을
줄 수 있다.
* 변수나 함수 그리고 클래스 이름은 다음과 같은 굵직한 질문에 모두 답해야 한다.
  * 1) 변수(혹은 함수나 클래스)의 존재 이유는?
  * 2) 수행 기능은?
  * 3) 사용 방법은?
* 따로 주석이 필요하다면, 의도를 분명히 드러내지 못했다는 말이다.

```
int d; // 경과 시간 (단위: 날짜)
```

* 위와 같은 변수명은 __아무 의미도 드러나지 않는다__
* 아무 의미도 드러나지 않는 다는 것은 `d`만 봤을 때, 경과 시간 또는 날짜라는 의미 전달이 되지 않는다는
것이다.
* 만약, 주석이 없다면, 변수 d가 어떤 의도를 갖고 만들어진 변수인지, 존재 이유를 찾기 위해 개발자들은
코드를 읽어보며 __이 변수는 어떤 변수구나!!__ 하는 유레카를 찾기 위한 여정을 시작하게 될 것이다.. (끔찍)
* 위의 변수를 리팩토링해보자.

```

int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDats;
```  

* 의도가 드러나는 이름을 사용하면 코드 이해와 변경이 쉬워진다.
* 아래에서 좀 더 구체적인 예제를 살펴보자.

## 의도를 알 수 없는 단순한 코드는 유레카의 여정을 떠나게 한다..

```
public List<int[]> getThem() { //getThem..? method 이름부터 모호하다.
  List<int[]> list1 = new ArrayList<int[]>(); // 젠장..list1 이라니 무슨 list 인지 벌써부터 궁금해지잖아?

  for(int[] x: theList)
    if (x[0] == 4)
      list1.add(x)
  return list1;    
}
```

* 위의 코드는 몇줄인가? 10줄이 되지 않는다. __그럼 해당 코드는 쉽게 이해가 가능할까??__
* 그렇지 않다. 해당 함수가 어디에서 쓰여야 되고 무슨 의도로 만들어진 함수인지 의도가 드러나지않는다.
* 문제는 __코드의 단순성이 아니라, 코드의 함축성이다.__
* 다시 말해, __코드 맥락이 코드 자체에 명시적으로 드러나지 않는다.__
* 위의 코드는 코드를 보는 독자에게 아래와 같은  정보를 __알고 있다고 가정한다.__
  * `theList` 에 무엇이 들어있는가.
  * `theList` 에서 0번째 값이 무슨 값이길래 로직에 영향을 주는가?
  * 값 4는 무슨 의미인가. (매직 넘버...!ㅠㅠ)
  * 함수가 반환하는 리스트 list1을 어디서 어떻게 사용하는가
* 만약 위와 같은 정보들을 __미리 알고 있지 못하다면, 고작 10줄의 코드를 이해하기 위해 `유레카! 를 위한 여정을 떠나자`
가 시작될 것이다.. (끔찍)__
* 위의 코드에서는 우리가 궁금해하는 정보들이 제공은 되지 않는다. 해당 코드를 리팩토링 해보자.

## 코드를 리팩토링하여 코드의 함축성을 부여하자.

```
public List<int[]> getFlaggedCells() { //오호! 이름이 바꼈다. 플래그 cell 정보들을 가져오는 함수구나.
  List<int[]> flaggedCells = new ArrayList<int[]>();

  for(int[] cell: gameBoard)
    if (cell[STATUS_VALUE] == FLAGGED)
      flaggedCells.add(cell);
  return flaggedCells;    
}
```

* 위의 코드는 아까 전에 예제 코드와 같이 __코드의 단순성은 변하지 않았다.__
* 변한 것은 __이름을 리팩토링 하면서, 코드의 함축성이 좋아졌다는 것이다.__
* __이름만 바꿨을 뿐인데, 해당 함수가 `어떤 보드판에서 플래그된 정보들을 가져오는 함수구나.` 라는 이해도가
생기게 되었다.__
* 한 걸음 더 나아가면, int 배열을 간단한 클래스로 만들수도 있다.
* Cell 이라는 간단한 클래스를 만들고, 해당 객체의 메소드로 flag 검사를 하는 함수를 넣으면,
좀 더 코드가 명확해진다.

```
public List<Cell> getFlaggedCells() {
  List<Cell> flaggedCells = new ArrayList<Cell>();

  for (Cell cell: gameBoard)
    if (cell.isFlagged())
      flaggedCells.add(cell);
  return flaggedCells;    
}
```

## 결론

* 단순히 이름만 고쳐도 코드의 가독성은 좋아지며, 팀원의 시간을 아껴줄 수 있다.
* 유레카를 찾기 위한 여정을 떠나게 하지말자. :D

### 참고

* 클린코드 책 2장 - 의미있는 이름