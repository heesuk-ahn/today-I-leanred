# [React] React 란? (2)

```
<React 문서 중..>

We built React to solve one problem: building large applications with data that changes over time.
번역: 우리는 지속해서 데이터가 변화하는 대규모 애플리케이션을 구축하기 위해 React를 만들었습니다
```

* 변화하는 대규모 애플리케이션을 구축하기 위해 React 를 만들었다는 것은 무슨 의미일까
* React 이전에도 다양한 프레임워크들은 존재하였다. (Angular, Backbone, Knockout.js, Ember..)
* 이러한 프론트엔드 프레임워크들의 동일한 공통점은 __데이터가 변하면, 화면에서도 바뀐다.__ 라는 점이다.
* 하지만, 데이터가 변할 때, 화면이 변한다는 것은 간단해보이지만 또 간단하지 않은 문제다.
* __특정 이벤트가 발생했을 때, 모델에 변화를 일으키고, 이 변화를 어떤 DOM 에서 가져와서 업데이트를 해주는
로직들이 필요하다.__
* 페이스북에서는 `Mutaion (변경)`이 일어날 때 마다 위와 같은 로직들이 일어나는 것은 __비효율적__
이라고 생각했고, 변화가 생기면 새롭게 그 화면 자체를 새로운 뷰로 만드는 것을 고려했다.
* 그러면 업데이트라기 보다는 생성에만 초점을 맞추면 되기 때문에 좀 더 문제가 간단해진다.
* 하지만, __매번 새로운 뷰를 그린다는 것은 그만큼 성능 이슈가 생길 수 있다__ 는 것이 문제다.
* 그래서 이를 해결 하기 위해 DOM 을 직접 수정하는 것이 아니라, `Virtual Dom` 개념을 만들었다.
* 만약에 우리가 10개의 컴포넌트로 이루어진 하나의 화면을 갖고 있다고 생각해보자.
* 만약 1개의 컴포넌트에 변화가 발생하면, 기존방식은 10개의 컴포넌트가 모두 새롭게 그려져야한다.
* 하지만 Virtual Dom 을 이용하면, 가상 돔에 먼저 렌더링을 하고, 렌더링된 가상 돔 view 와 실제 Dom view
를 비교해서, 변화가 일어난 부분만 업데이트를 하는 방식이다.
* 즉, 이렇게 모델에 변화가 생기면, 변화가 생긴 뷰는 새로 그리고, 그 후 실제 돔과 비교해서 업데이트를
해주는 것이다.
* React 에서 성능 문제를 이런 방식으로 해결하자, Vue, Marko, Maquette, Mithril 등에서도 이런
가상 돔 방식을 채택하여 사용하게 되었다.

## 리액트의 장점

* 생태계가 크다
* 자유도가 높다
  * 라이브러리이기 때문에, 자신이 원하는 라이브러리를 사용하여 구축할 수 있다.
  * 이를테면 Router 라이브러리 경우에도, React-router, 그리고 Next.js, After.js 같은
  다양한 라이브러리가 존재한다.
  
### 참고)

* https://medium.com/react-native-seoul/react-%EB%A6%AC%EC%95%A1%ED%8A%B8%EB%A5%BC-%EC%B2%98%EC%9D%8C%EB%B6%80%ED%84%B0-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90-01-react-js%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-ad8ba252ee28
