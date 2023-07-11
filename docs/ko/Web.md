
## Jevil.webLoad

webview에서 urlload할때  마다 호출된다. 이 함수는 단일 블록 스크린에서만 실행 가능하다
그리고 최초 스크립트에서 실행할 수 없고 비동기로 실행 되어야 한다

두번째 파라미터는 반드시 true 나 false를 반환해야하며, true를 반환할 시 그 url을 로드되지 않는다

- Jevil.webLoad(node, callback)

#### parameter

- node `string` `require` WebView 노드 명
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

## Jevil.webScript

앱에서 webview의 javascript를 호출할 때 실행된다

- Jevil.webScript(node, javascript, callback)

android 는 callback이 좀더 일찍 호출된다

#### parameter

- node `string` `require` WebView 노드 명
- javascript `string` `require` 웹페이지에 호출할 javascirpt 예)javascript:alert('hello')
- callback `function` `require` 자바스크립트가 호출되고 그 스크립트가 끝나고 나서 호출되는 콜백 함수

#### Example code
```javascript
Jevil.webScript('web', "javascript:alert('hello')", function(){
    Jevil.toast('script end')
})
```



## jevil://devil.com/popupAddress

이것은 Jevil 함수가 아닌 webpage에서 앱으로 스킴을 호출을 하는 방식이다
앱의 주소 검색 팝업을 호출한다

- jevil://devil.com/popupAddress(null)

#### parameter
null

#### Example code
```javascript
//주소 검색 버튼 클릭 

window.location.href = 'jevil://devil.com/popupAddress'

//callback function 
addressPopupCallback(address_name, load_address_name, address_detail, post) {
}
```




## jevil://devil.com/replaceScreen

이것은 Jevil 함수가 아닌 webpage에서 앱으로 스킴을 호출을 하는 방식이다

jevil://devil.com/replaceScreen


- jevil://devil.com/replaceScreen(null)

#### parameter
null

#### Example code
```javascript
jevil://devil.com/replaceScreen?screenName=main
```



