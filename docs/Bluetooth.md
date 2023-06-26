
## Jevil.bleCallback

해당 블루투스와 연결되었을때, 해제 되었을때, 응답이 왔을때 콜백으로 호출된다

- Jevil.bleCallback(command, callback)

#### parameter

- command `string` `require` 어떤 콜백을 받을지 종류를 가리킨다
connected : 블루투스가 연결되었을때, 
disconnected : 블루투스가 연결해제되었을때, 
notify : 블루투스(characteristic)로부터 바이트 응답이 왔을때, 


- callback `function` `require` 
    - res `json` `require` 콜백
- udid 
- value read시에만 호출되는 값으로 byte가 hexstring으로 표시된다 
예) 블루투스 실제 응답 aaa 는 value : 616161 로 온다
a의 ascii코드는 0x61이다
- list : 전체 블루투스 리스트

#### Example code
```javascript
Jevil.bleCallback('connected', function(res){
  Jevil.toast('connected ' + res.udid)
  data.list = make(res.list)
  Jevil.update()
})
Jevil.bleCallback('disconnected', function(res){
  Jevil.toast('disconnected ' + res.udid)
  data.list = make(res.list)
  Jevil.update()
})
Jevil.bleCallback('notify', function(res){
  Jevil.toast('notify ' + res.udid + ' / ' + res.value)
})
```




## Jevil.bleConnect

해당 블루투스 기기와 통신한다

- Jevil.bleConnect(udid)

#### parameter

- udid `string` `require` 블루투스 udid

#### Example code
```javascript
Jevil.bleConnect(thisData.udid)
```




## Jevil.bleDisconnect

해당 블루투스 기기와 연결을 해제한다

- Jevil.bleDisconnect(udid)

#### parameter

- udid `string` `require` 해당 블루투스 기기의 UDID

#### Example code
```javascript
Jevil.bleDisconnect(udid)
```




## Jevil.bleList

주변 블루투스 목록을 비동기로 가져온다.
블루투스 권한이 없다면 권한을 요청하고, 블루투스가 꺼져있다면 블루투스를 키도록 가이드한다


- Jevil.bleList(param, callback)

#### parameter

- param `json` `require` 블루투스를 찾기 옵션 
    - sec `float` `require` 몇초간 블루투스를 찾을 지를 가리킨다. Default 10 (10초)
새로운 블루투스 기기를 찾을 때마다 전체목록을 갱신하여 콜백함수를 호출한다
- callback `function` `require` 
    - res `json` `require` 응답
r : 블루투스 리스트 성공 여부
list : 블루투스 리스트
list의 각 JSON구조는 다음과 같다
{
 name : 블루투스명
 udid :  블루투스 고유한 구분자(안드로이드는 MAC Address를 반환 아이폰은 폰에서 부여한 UDID)
 status : 'connected' | 'disconnected'
}

#### Example code
```javascript
Jevil.bleList({sec:10}, function(res) {
    if(res.r) {
      data.list = res.list
      Jevil.update()
    }
})
```




## Jevil.bleRead

해당 블루투스 기기로부터 바이트를 읽는다

- Jevil.bleRead(param, callback)

#### parameter

- param `json` `require` read 
    - characteristic `string` `require` characteristic의 udid
- callback `function` `require` 
    - res `json` `require` 결과
read 요청에 대한 callback함수이다 
읽은 바이트가 바로 온다
hex, 
text,
characteristic
name

#### Example code
```javascript
Jevil.bleRead({
          udid:data.udid, 
          service:s.udid, 
          characteristic:c.udid, 
        }, function(res) {
          Jevil.stopLoading()
          Jevil.toast('read')
        })    
```




## Jevil.bleRelease

모든 블루트스 연결을 끊고 모든 자원을 제거한다

- Jevil.bleRelease()

#### parameter


#### Example code
```javascript
Jevil.bleRelease()
```




## Jevil.bleWrite

해당 블루투스 기기로 바이트를 보낸다.

- Jevil.bleWrite(param, callback)

#### parameter

- param `json` `require` write param
    - characteristic `string` `require` characteristic의 udid
    - hex `string`  예) aaa 는 616161 로 온다
a의 ascii코드는 0x61이다
    - text `string` `require` 예) text:'aaa' 라면 실제 616161로 보낸다

- callback `function` `require` 성공여부 콜백
    - res `json` `require` 성공 여부 콜백
{
 r: true or false
}

#### Example code
```javascript
Jevil.bleWrite({
          udid:ble_udid, 
          service:service_udid, 
          characteristic:c_udid, 
          text:'hello'
        }, function(res) {
          Jevil.stopLoading()
        })    
```



