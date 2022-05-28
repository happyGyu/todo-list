# Todo-list

## 🎯 소개 및 목적
***
- TODOList 웹 서비스 만들기.
- Webpack과 Babel을 활용
- Drag and Drop를 API없이 직접 구현
- 함수형 프로그래밍

<br />

## 🔎 Points
***
<details>
<summary>Client단에서의 Store의 역할?</summary>
<div markdown="1">

- 일반적으로 디자인패턴에서는 Model(store)과 View를 분리합니다. 
- 그런데 이 미션의 경우 Model의 예상되는 Model의 생김새가 Server의 db와 굉장히 유사합니다. 즉, server에서 데이터를 잘 처리해주기만 하면, 굳이 Client단에 store를 두지 않아도 되지 않을까? 라는 생각을 했습니다.
- 그러나 '새 카드를 추가 중인 상태', '수정 중' 상태 등은 서버에 매번 알려주는 것은 비효율적입니다.
- 그러면, 서버에 알릴 필요가 없는 '상태'만 store에 저장하고, 나머지 서버에 매 이벤트마다 업데이트하는 상태는 store를 거치지 않고 서버로 부터 받아 이용하는 것은 어떨까 생각했습니다.
- 이 서비스를 계속 운영하며 확장한다고 가정했을 때, 위 방식은 좋지 않다고 생각했습니다. 만약 사용자와 서버의 연결이 원활하지 못할 경우 서비스 자체가 불가하기 때문입니다. client단에 store를 두는 것 만으로도 local환경에서 서비스가 가능하기 때문에, 큰 이점이 있다고 판단했습니다.
- 결론적으로 client단에도 store를 둬 현재 view를 구성하는 데이터를 저장하는 역할을 맡도록했고 추가적으로 서버로부터 데이터를 주고 받는 역할을 담당하게 했습니다.         
</div>
</details>

<details>
<summary>함수형 프로그래밍에 대한 생각</summary>
<div markdown="1"> 

- 함수를 최대한 순수하게 만들고 잘게 나눠 로직을 숨기고 선언적으로 프로그래밍 하고자 노력했습니다.
- 전체를 순수함수로 만드는 것은 어려웠습니다. 
- 특히 DOM 조작을 해야하는 경우 외부 환경에 영향을 받는 것이기 때문에 순수하다고 말할 수 없는 것 같습니다.
- 함수형 프로그래밍이 추구하는 가치(참조투명성, 순수성, 불변성 등)과 고차함수를 이용한 방식은 매력적이었습니다.
- 그런데 함수형 프로그래밍은 OOP와 반대되는 개념인가? 하는 생각을 했습니다.
- OOP는 Class를 정의하고, instance의 상태를 변경함으로서 조작하는데, 클래스는 그대로 만들고 상태를 조작하는 방식을 함수형 프로그래밍스럽게 만드는 것은 어떤가..?
</div>
</details>

<details>
<summary>API없이 드래그앤드롭을 구현하며..</summary>
<div markdown="1">

- HTML에는 드래그 앤 드롭 API이 있지만, 미션에서는 API없이 구현하는 것이 요구사항이었기 때문에, 드래그앤드롭 이벤트를 감지하는 것부터 시작했습니다.
- 드래그와 일반 클릭을 구분해야했는데, 처음 계획은 mousedown 이벤트로 일정시간을 기다리고(setTimeout), 그 시간 안에 해당 이벤트가 또 발생하면, 드래그앤드롭이 아닌 더블 클릭으로 판단하고자 했습니다.
- 위 방식은 더블클릭은 문제없이 잘 잡아내지만, 드래그를 하고자 할때는 다소 문제가 있었습니다.
- 사용자는 드래그를 하려고 할때 마우스를 누른채로 일정시간 기다렸다가 움직이지 않습니다.
- 즉, 사용자가 직관적으로 행동했을 때 의도하지 않았던대로 동작하기 때문에 나쁜 UX를 주는 로직이었습니다.
- 이것을 해결하기 위해 코드상으로는 비효율적으로 느껴지는 방식이지만, mousedown시 무조건 drag 로직을 활성화하고, drag로직이 활성화 된 채로 mouseup이 emit되면 드래그앤드롭을 종료하는 방싱으로 구현했습니다. 
- JS엔진이나 브라우저가 처리해야하는 양은 늘어난 것 같지만 UX적으로는 더 나은 선택이었다고 생각합니다. 

</div>
</details>

<details>
<summary>webpack, Babel 등 환경설정</summary>
<div markdown="1">

- 요즘 많이 사용되는 React 같은 라이브러리를 사용하면, 개발 환경 설정을 자동으로 해주기도 하지만, 직접 환경 설정을 하며 사용 목적과 방법을 이해하기 위해 노력했습니다.
- 너무 많은 설정과 플러그인이 있어 전부 알고 있는 것은 불가능하다고 생각합니다.
- 기본적인 설정 방법을 익힌 뒤 상황마다 필요한 것을 검색해서 적용하는 방법을 익히는 것이 합리적일 듯 합니다. 

</div>
</details>

<br />

## 📝 Record
***
[첫 팀프로젝트에서 고민했던 것 (Hard skill)](https://velog.io/@happygyu/%EC%B2%AB-%ED%8C%80%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EB%A5%BC-%EB%A7%88%EC%B9%98%EA%B3%A0)

<br />

## 👬 팀원
***
### Team28 - ver.alan
<table>
  <tr>
    <td align="center">
      <a href="https://github.com/lv0314">
        <img src="https://avatars.githubusercontent.com/u/95198109?v=4" width="100px;" alt="ver"/><br />
        <sub><b>ver</b><br></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/happyGyu">
        <img src="https://avatars.githubusercontent.com/u/95538993?s=400&u=142c62a8238fbfd3a3e46976651dbc991cafc088&v=4" width="100px;" alt="Alan"/><br />
        <sub><b>Alan</b><br></sub>
      </a>
    </td>
  </tr>
</table>

[Wiki](https://github.com/happyGyu/todo-list/wiki)

<br />

## 🎞 데모
***
<details>
<summary>CRUD</summary>
<div markdown="1">

https://user-images.githubusercontent.com/95538993/163117357-9b896708-1692-43ff-b4e0-ec2d031ca4be.mp4
  
</div>
</details>
<details>
<summary>드래그앤드롭</summary>
<div markdown="1">

https://user-images.githubusercontent.com/95538993/163532068-7321f7ac-6b08-4d6b-9025-960be30041e2.mp4       

</div>
</details>
