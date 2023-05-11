# Screen

Screen은 네이티브앱의 하나의 화면이다
DAB 콘솔에서 Screen을 생성한다 
Screen에는 Javascript 함수를 정의할 수 있으며, 이 Javascript 함수로 Screen의 다양한 로직을 처리한다
Screen에는 하나의 메인 블록을 포함할 수 있는데, Block은 Screen는 각각 UX와 로직을 담당하고 있다

#### Start Name

Screen에는 name이 있으며 이는 프로젝트 전체에서 고유해야 한다

#### Start Screen

첫 번째로 해야할 것은 여러 Screen중에 Start Screen을 선정하는 것이다
앱이 시작할 때 선정된 Screen이 처음으로 뜨게된다

## Screen Script

Screen에는 하나의 javascipt editor 창이 있다. 보통 하나의 앱 화면의 스크립트는 보통 100~300줄 내외로 유지된다

<img src="https://github.com/mondayless/devil_document/blob/master/docs/_images/screen.png?raw=true" width="70%"/>

다음과 같은 script가 들어 갈 수 있다.
button_click()의 경우 Block Rule에 의해() 지정되어 클릭시 호출된다

```js
let hello = 'Hello World'

//This show alert dialog when screen loaded
Jevil.alert(hello)

function button_click() {
    Jevil.go('other_screen_name')
}

```

## Header/Footer Frame

#### Header Block

#### Footer Block

#### Inside Footer Block