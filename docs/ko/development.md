## 앱의 호스트 설정하기

앱의 API 호스트는 보통 하나이며, 이는 앱에 공통으로 설정하고 앱에서 API를 사용할 떄는 path만 첨부한다

```javascript
Jevil.getThe('/api/product/list', function(res) {
    ...
})
```

위와 같은 코드는 호스트 설정에 따라 다음과 같이 다양하게 호출 될 수 있다
 - 예시 
    - https://api.myservice.com/api/product/list
    - https://dev.myservice.com/api/product/list
    - http://localhost:8080/api/product/list


호스트를 설정하는 법은 다음과 같이 DAB Console > project > HTTP CONFIG 에서 API Host와 Web Host를 설정할 수 있다.

<img src="https://github.com/mondayless/devil_document/blob/master/docs/_images/host_select.png?raw=true" width="100%" />

- API Host는 다음과 같은 http 관련 함수에서 자동으로 설정된다
    - Jevil.getThen()
    - Jevil.postThen()
    - Jevil.sendPushKeyWithDevilServer()
    - 기타
- Web Host는 WebView block rule에서 자동으로 설정된다

## 앱의 호스트를 개발서버로 설정하기
서버와 앱을 개발하기 위해서는 앱이 개발 서버를 바라보도록 해야한다

앱의 서버 설정과 개발 서버 설정은 다음과 같다