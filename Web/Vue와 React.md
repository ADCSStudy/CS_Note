# Vue와 React

### **React는 라이브러리이고 Vue는 프레임워크이다.**

흔히들 **리액트는 비교적 자유도가 높고, 뷰는 기능이 이미 다 정해져 있다** 라고들 얘기 하는데 이것은 각자의 태생적 특성에서도 영향을 받지 않았나 생각한다.

**라이브러리**는 사용자가 필요할 때에 가져다 썼다가 뺐다가 할 수 있고 부분적으로 사용이 가능하다.**프레임워크**는 부분적 사용이 불가능하고 프레임 워크의 안으로 들어가서 프레임 워크가 지원해주는 문법에 따라서 작성해줘야 제대로 동작한다.

이런 태생적 특성 때문에 리액트는 리액트만의 대체 불가능한 문법이 지정되어있기 보다는 자바스크립트 문법을 응용해서 개발자가 자유롭게 개발할 수 있는 환경이고, 뷰는 뷰에서 지정해준 문법 방식으로만 개발 할 수 있다.

### **자유도가 높은 React, 한 가지 방식대로만 하면 되는 Vue**

예를 들어 조건에 따라 button을 보였다가 안보였다가 해야 되는 상황이라면 리액트는 개발자가 자바스크립트 문법을 쓰고 싶은대로 써서 재량껏 구현하면 된다. 자바스크립트의 삼항연산자를 쓰든 && 연산자를 쓰든 미리 만들어둔 함수 호출로 랜더링을 하든 그건 개발자의 선택이다.

```
// && 연산자 방식
<div>
	{isVisible && <button>조건에 따라 사라질 버튼</button>}
</div>

// 삼항 연산자 방식
<div>
	{isVisible ? <button>조건에 따라 사라질 버튼</button> : null}
</div>
```

뷰에서 보이고 안보이고를 제어할 수 있는 방법은 뷰에서 제공해주는 v-if 단 한가지 방법밖에 없다.

```
<div>
	<button v-if="isVisible">조건에 따라 사라질 버튼</button>
</div>
```

비슷한 사례로 배열을 돌면서 리스트를 랜더링 해줘야 하는 상황일때에 리액트는 자바스크립트의 문법중 map을 선택하든 forEach를 선택하든 for 문을 선택하든 개발자의 맘이지만, 뷰는 뷰에서 제공해주는 문법인 v-for 로만 구현이 가능하다.

### **컴포넌트 분리, 재사용 측면에서 React의 효율성**

컴포넌트를 분리할 시에 리액트는 한개의 파일에서 새로운 함수형 컴포넌트를 쉽고 깔끔하게 정의해서 만들수 있으며, 부모에서 자식으로 props 를 전달해주는 과정이 **함수에 인수 전달하듯이** 매우 매끄럽게 진행된다.

하지만 **뷰에서 새로운 컴포넌트를 분리하려면 일단 새로운 파일을 하날 더 만들어야 하고, 그에 따라 하나의 파일에 해당하는 template script style 도 작성해야 할 것이다.** 또 props를 전달하는 과정도 2개의 파일을 오가며 해야 한다.

컴포넌트를 작은 단위로 분리하고 재사용 하는 프로세스에 있어서는 React가 더 효율성이 높다고 생각한다.

### **각각의 장단점에 대한 이모저모**

앞서 말했듯이 뷰는 뷰에서 제공해주는 문법으로만 코딩이 가능하기 때문에 개발자간에 코딩 스타일에도 통일성이 생긴다. 이에 반해 **리액트는 자유도가 높아서 개발자마다 코딩 스타일을 통일하는데에 커뮤니케이션 비용이 든다.**

**러닝 커브는 뷰가 리액트에 비해 많이 낮은 편이다.**일단 template style script 의 [싱글 파일 컴포넌트](https://kr.vuejs.org/v2/guide/single-file-components.html) 구조로 개발하는 방식이 기존의 html css js 로 나눠서 개발하던 방식과 유사하여 js 나 제이쿼리로 개발하던 개발자, 개발을 배워보려는 퍼블리셔, 서버에서 서버사이드 랜더링을 해봤던 서버개발자 들에게 익숙하게 다가올 수 있다.

**반면 리액트는 모든것이 다 자바스크립트이다.** jsx라고 불리는 html 역할을 하는 코드도 js의 확장된 문법이며 js 안에서 쓰는것이고, css도 css 파일을 분리해서 따로 만드는 방식 말고 한 파일안에서 사용하려면 css-in-js 결국은 자바스크립트로 써야한다.

뷰는 자바스크립트의 문법을 정확히 몰라도 뷰에서 제공해주는 문법만 배우면 잘 동작하는 것을 확인할 수 있어서 **생산성**도 빠른 편이다.

**리액트의 진입장벽**으로는 redux, 라우팅.. 등이 있을 수 있는데 뷰가 리액트의 고충을 보고나서 만들어진 언어라 그런지 vuex, vue-routing 로 같은 기능을 하더라도 문법이 훨씬 쉬운편이다.

**속도 이슈**는 아주 미세한 차이라 유의미하게 느낄정도 까지는 아니지만 뷰가 조금 더 빠르다고 한다. 그래서 속도이슈에 민감한 코인거래 사이트에서도 vue를 가끔 사용한다고 한다.

**타입스크립트**는 리액트가 더 결합이 잘된다. 개인적으로는 뷰에서 타입스크립트를 써본적은 없어서 잘 모르지만, 2.x버전에서는 타입스크립트 지원이 완벽하지 않다고 한다.

**리액트는 변화가 빠르고 혁신적이다.** 프론트엔드의 변화를 선두하고있다고 볼 수 있다. 리액트에서 새로운 기능이 나오면 추후에 뷰에서 비슷한 기능이 나오는 편..(예를들어 리액트의 hook이 나오고 나서 뷰에 composition이 나온다든지)

리액트는 자체적으로 지원해주는 기능이 제한적이고 프로그래밍의 **자유도**가 많이 보장된다. 그만큼 모든 상황에 대해서 대처하기에 더 유연할 수 있다.

### React, Vue 누구에게 잘 맞을까

아래는 개인적인 의견입니다.

> 규모가 작고 가벼운 프로젝트를 빠르게 만들고 싶다.
속도 이슈에 매우 민감한 사이트이다.
자바스크립트 문법에 미숙하다.
회사에 퍼블리셔가 따로 존재한다.
기존 html css js 구조로 작성된 코드를 SPA로 옮기고 싶다.
개발자간 코드 통일성을 위한 커뮤니케이션 비용을 줄이고 싶다.
백엔드 개발자다.
> 

=> Vue를 추천합니다.

> 프로젝트의 규모가 크다. 
점점 더 확장 될 것이다.
자바스크립트 문법에 능숙하다.
컴포넌트를 작은 단위로 나누어 비슷한 UI 재사용을 많이 할 예정이다.
커스터마이징 및 자유도가 높은 개발 환경을 좋아한다.
타입스크립트를 사용할 것이다.
넓은 커뮤니티 및 개발 인력시장의 혜택을 보고싶다.
> 

=> React를 추천합니다.

[https://velog.io/@leehaeun0/React-vs-Vue-장단점-비교](https://velog.io/@leehaeun0/React-vs-Vue-%EC%9E%A5%EB%8B%A8%EC%A0%90-%EB%B9%84%EA%B5%90)
