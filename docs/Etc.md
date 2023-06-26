
## Jevil.log

로그를 남긴다

- Jevil.log(log_text, json)

#### parameter

- log_text `string` `require` 로그 제목
- json `json` `require` 로그 json

#### Example code
```javascript
Jevil.log('send', {body:'text'})
```




## Jevil.removeTimer

타이머를 제거한다
타이머가 두개이상 일경우 아이폰 안드로이드 조금 동작이 다름

- Jevil.removeTimer(key)

#### parameter

- key `string` `require` 타이머 키

#### Example code
```javascript
Jevil.removeTimer('key')

```




## Jevil.setTimer

함수를 예약한다
몇 초 뒤 특정 함수를 실행한다

- Jevil.setTimer(key, sec, callback)

#### parameter

- key `string` `require` 예약된 함수키 이 키로 덮어쓰면 예전 함수를 사라진다
- sec `int` `require` 밀리 세컨드
- callback `function` `require` 

#### Example code
```javascript
Jevil.setTimer('key', 5, function(){
      Jevil.finish()
})

```




## Jevil.sha256ToHash

Jevil.sha256ToHash 문자열로 변환한다

- Jevil.sha256ToHash(text)

#### parameter

- text `string` `require` 인코딩 할 문자열

#### Example code
```javascript
let a = Jevil.sha256ToHash('password1234')
//a == 'b9c950640e1b3740e98acb93e669c65766f6670dd1609ba91ff41052ba48c6f3'
```




## Jevil.toJpg

해당 뷰를 이미지로 컨버팅하여 포토 앨범에 저장한다

- Jevil.toJpg(nodeName, callback)

#### parameter

- nodeName `string` `require` 뷰 이름
- callback `function` `require` 

#### Example code
```javascript
function save(){
  Jevil.toJpg('certificate', function(res) {
    if(res && res.r) {
      Jevil.alert('포토 앨범에 저장되었습니다')
    }
  })
}
```



