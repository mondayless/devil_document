
## Jevil.localPush

서버를 거치지 않은 로컬 푸시를 보낸다

- Jevil.localPush(param)

#### parameter

- param `json` `require` 파라미터
    - title `string` `require` 푸시 제목
    - msg `string` `require` 푸시내용
    - url `string` `require` 클릭시 url

#### Example code
```javascript
Jevil.localPush({
  title : '최초 가입 100만 샤베트를 받으셧습니다', 
  msg : '최초 가입 100만 샤베트', 
  url : 'http://m.on-bab.com/screen/my',
})
```



