
## Jevil.focus

Start Editing Text Input
onResume 함수에서 사용해야함

- Jevil.focus(node)

#### parameter

- node `string` `require` TextInput Node Name

#### Example code
```javascript
Jevil.focus('TextInputNodeName')
```




## Jevil.getViewPagerSelectedIndex

뷰페이저의 현재 인덱스를 가져온다

- Jevil.getViewPagerSelectedIndex(node)

#### parameter

- node `string` `require` 뷰페이저 노드명

#### Example code
```javascript
let index = Jevil.getViewPagerSelectedIndex('myViewPagerNodeName')
            
```




## Jevil.hideKeyboard

키보드를 내린다

- Jevil.hideKeyboard(null)

#### parameter
null

#### Example code
```javascript
Jevil.hideKeyboard()
```




## Jevil.resetTimer

Reset Timer to begining

- Jevil.resetTimer(node)

#### parameter

- node `string` `require` 타이머 노드명

#### Example code
```javascript
let index = Jevil.resetTimer('myTimerNodeName')
```




## Jevil.scrollDragged

스크롤이 멈췄을때 호출된다

- Jevil.scrollDragged(node, callback)

#### parameter

- node `string` `require` 스크롤 노드 이름
- callback `function` `require` 

#### Example code
```javascript
Jevil.scrollDragged('list', function(){
  //...
})

```




## Jevil.scrollEnd

스크롤되는 반복뷰(List, HList)의 스크롤에 마지막이 되면 함수가 콜된다

- Jevil.scrollEnd(node, callback)

#### parameter

- node `string` `require` List node name 
반복되는 아이템 말고 그 부모 노드 이름을 줘야한다
- callback `function` `require` 

#### Example code
```javascript
Jevil.scrollEnd('list', function(){
  ... do something
})
```




## Jevil.scrollTo

리스트의 스크롤을 특정 인덱스로 이동한다

- Jevil.scrollTo(node, index, param)

#### parameter

- node `string` `require` 리스트 노드 
null일경우 화면리스트를 가리킨다
- index `int` `require` 행인덱스
- param `json` `optional` 스크롤 옵션
  - offset `int` `optional` cell이 top을 기준으로 얼마나 아래로 이동하느냐
  - animation `boolean` `optional` 스크롤 이동 애니메이션 여부 default - true


#### Example code
```javascript
Jevil.scrollTo('list', index)

Jevil.scrollTo(null, index, {animation:true})
```




## Jevil.scrollUp

리스트를 최상단으로 스크롤한다

- Jevil.scrollUp(node)

#### parameter

- node `string` `require` 리스트 노드명 
null 이면 화면 리스트를 의미한다

#### Example code
```javascript
Jevil.scrollUp(null)

Jevil.scrollUp('list')
```




## Jevil.setText

스캐치의 textNode의 텍스트를 바꾼다
onResume함수에서 사용해야함

- Jevil.setText(node, text)

#### parameter

- node `string` `require` 노드명
- text `string` `require` 설정한 텍스트

#### Example code
```javascript
Jevil.setText('textNode', 'hello')
```




## Jevil.setViewPagerSelectedIndex

ViewPager의 index를 지정한다
다음 Jevil.update()에서 반영된다

- Jevil.setViewPagerSelectedIndex(nodeName, index)

#### parameter

- nodeName `string` `require` View Pager Node Name
- index `int` `require` View Pager Index

#### Example code
```javascript
Jevil.setViewPagerSelectedIndex('vp_list', 1)
```




## Jevil.textChanged

Input이 변경될때 호출된다호출된다

원 블록 함수
onResume이나 비동기로 호출요망

- Jevil.textChanged(nodeName, callback)

#### parameter

- nodeName `string` `require` Input 노드 명
- callback `function` `require` 
    - text `string` `require` 변경되는 텍스트

#### Example code
```javascript
Jevil.textChanged('input1', function(text) {
  //...
})
```




## Jevil.textFocusChanged

Input에 포커스가 변경 될때 호출된다

원 블록 함수
onResume이나 비동기로 호출요망

- Jevil.textFocusChanged(nodeName, callback)

#### parameter

- nodeName `string` `require` 노드명
- callback `function` `require` 
    - focus `boolean` `require` 포커스 설정 여부

#### Example code
```javascript
Jevil.textFocusChanged('input1', function(focus) {
  //...
})
```




## Jevil.timer

Timer 블록을 특정 초부터 다시 시작하게 한다

- Jevil.timer(node, sec)

#### parameter

- node `string` `require` Timer Node 이름
- sec `int` `require` 다시 시작할 초

#### Example code
```javascript
Jevil.timer('remain', 60*5)
```




## Jevil.update

Update blocks in screen
Javascript variable data affects this

- Jevil.update(null)

#### parameter
null

#### Example code
```javascript
data.text = 'Hello'
Jevil.update()
```




## Jevil.videoViewAutoPlay

눈에 보이고 autoplay설정된VideoView중 하나를 autoplay하고 나머지는 pause한다

- Jevil.videoViewAutoPlay(null)

#### parameter
null

#### Example code
```javascript
Jevil.videoViewAutoPlay()
```




## Jevil.webLoad

webview에서 urlload할때  마다 호출된다. 이 함수는 단일 블록 스크린에서만 실행 가능하다
그리고 최초 스크립트에서 실행할 수 없고 비동기로 실행 되어야 한다

두번째 파라미터는 반드시 true 나 false를 반환해야하며, true를 반환할 시 그 url을 로드되지 않는다

- Jevil.webLoad(node, callback)

#### parameter

- node `string` `require` WebView 노드 명
    - url `string` `require` 로드될 url
- callback `function` `require` 
    - url `string` `require` webView에 로드되는 url

#### Example code
```javascript
Jevil.webLoad('web', function(url){
     if(url.includes('bookplay.do')){
   return true;
}
      return false;
})
```



