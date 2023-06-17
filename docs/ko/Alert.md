
## Jevil.alert

얼럿 창으로 메세지를 표시한다

- Jevil.alert(message)

#### parameter

- message `string` `require` 표시할 메세지

#### Example code
```javascript
Jevil.alert('Hello Alert')
```




## Jevil.alertFinish

얼럿창을 표시하고 확인버튼을 누르면 현재 화면이 finish 된다

- Jevil.alertFinish(message)

#### parameter

- message `string` `require` 얼럿창에 표시할 메세지

#### Example code
```javascript
Jevil.alertFinish('Hello Alert')
```




## Jevil.alertThen

얼럿 창을 표시한 후 확인을 누르면 함수를 실행한다

- Jevil.alertThen(callback)

#### parameter

- callback `function` `require` 

#### Example code
```javascript
Jevil.alertThen('Hello Alert', function(){
    ...
})
```




## Jevil.alertThenOption

Jevil.alertThen과 비슷하나, Option 변수로 얼럿창 모양을 베리에이션한다
(Android Only)

- Jevil.alertThenOption(option)

#### parameter

- option `json` `require` 옵션
    - msg `string` `require` 얼럿 메세지
    - yes `string` `require` 확인 부분에 표시될 글자
    - cancelable `boolean` `require` alert cancelable

#### Example code
```javascript
Jevil.alertThenOption({yes:'응대완료', msg:msg}, function() {
   ...     
}) 
```




## Jevil.confirm

컨펌창을 띄운다

- Jevil.confirm(message, yes, no, callback)

#### parameter

- message `string` `require` 컨펌 메세지
- yes `string` `require` Yes 버튼의 문구
- no `string` `require` No 버튼의 문구
- callback `function` `require` 
    - yes `boolean` `require` Yes 버튼을 눌렀는지 여부

#### Example code
```javascript
Jevil.confirm('Are you human?','Yes', 'No', function(ans){
    if(ans){
        ...
    }
})
        
```




## Jevil.startLoading

로딩 중 표시를 한다

- Jevil.startLoading(null)

#### parameter
null

#### Example code
```javascript
Jevil.startLoading()  
```




## Jevil.stopLoading

로딩 창을 숨긴다

- Jevil.stopLoading(null)

#### parameter
null

#### Example code
```javascript
Jevil.stopLoading()
```




## Jevil.toast

토스트로 메세지를 표시한다

- Jevil.toast(message)

#### parameter

- message `string` `require` 표시할 메세지

#### Example code
```javascript
Jevil.toast('Hello Toast')
```



