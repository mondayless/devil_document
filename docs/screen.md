# Screen

Screen은 네이티브앱의 하나의 화면이다
DAB 콘솔에서 Screen을 생성한다 
Screen에는 Javascript 함수를 정의할 수 있으며, 이 Javascript 함수로 Screen의 다양한 로직을 처리한다
Screen에는 하나의 메인 블록을 포함할 수 있는데, Block은 Screen는 각각 UX와 로직을 담당하고 있다

첫 번째로 해야할 것은 여러 Screen중에 Start Screen을 선정하는 것이다
앱이 시작할 때 선정된 Screen이 처음으로 뜨게된다

### Screen Script

<img src="https://github.com/mondayless/devil_document/blob/master/docs/_images/screen.png?raw=true" width="100%"/>

```js
let hello = 'Hello World'

//This show alert dialog when screen loaded
Jevil.alert(hello)

function button_click() {
    Jevil.go('other_screen_name')
}

```

### Header Block

### Footer Block

#### Inside Footer Block