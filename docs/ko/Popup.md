
## Jevil.popup

Open popup with block content

- Jevil.popup(blockName, param, callback)

#### parameter

- blockName `string` `require` block name for popup
- param `json` `require` 팝업 파라미터
    - title `string`  Popup Title
    - yes `string`  Yes button text
    - no `string`  No button text
    - show `string`  Default is 'center'
'bottom' - show up from bottom
'top' - show up from top
    - cancelable `boolean`  뒷배경 클릭시 팝업 닫힘 여부
- callback `function` `require` 
    - answer `boolean` `require` yes or no button click

#### Example code
```javascript
Jevil.popup('password', 
    {title:'Change Password', 
    yes:'Change', 
    no:'Cancel'}, function(answer){
    ...
})
```




## Jevil.popupAddress

내장된 주소 선택 팝업을 연다

- Jevil.popupAddress(null)

#### parameter
null

#### Example code
```javascript
Web에서 사용하는법
window.location.href = jevil://devil.com/popupAddress

addressPopupCallback() 함수를 선언하여 콜백을 받는다

Vue의 경우 
async mounted() {
     ...
      window.addressPopupCallback = this.addressPopupCallback
},


Javascript에서 사용하는법

Jevil.popup('address-devil-template', {show:'bottom'}, function(yes) {
    if(yes) {
      Jevil.startLoading()
      Jevil.postThen('/api/my/address', {
        road_address_name: data.road_address_name,
        address_name: data.address_name,
        address_post : data.address_post,
        address_detail: data.address_detail,
      }, function(res) {
        if(res && res.r) {
          data.location = res.address1 +' '+ res.address2 +' '+res.address3 +' '+res.address4
          Jevil.update()
        }
      })
      Jevil.update()
    }
  })

```




## Jevil.popupClose

현재 열려있는 팝업을 없앤다

- Jevil.popupClose(yes)

#### parameter

- yes `boolean` `` popup이 닫히면서 팝업을 열었을때 지정한 callback이 실행되는데, 거기 yes or no 인자를 전달하기 위함

#### Example code
```javascript
Jevil.popupClose()

JevilpopupClose(true)
```




## Jevil.popupDate

날짜 선택 팝업을 연다

- Jevil.popupDate(optionJson, callback)

#### parameter

- optionJson `json` `require` 옵션 json
    - selectedKey `string`  선택된 Date
YYYYMMDD 형식 문자열
    - future `boolean`  true면 내일부터 선택가능
- callback `function` `require` 
    - selectedKey `string` `require` 선택된 Date
YYYYMMDD 형식 문자열

#### Example code
```javascript
Jevil.popupDate({selectedKey:'19810217'}, function(date){
})

Jevil.popupDate({selectedKey:'19810217', future:true}, function(date){
})
```




## Jevil.popupSelect

Open popup with selection list.
Each item of selectList should be json obejct that has key and value properties.


- Jevil.popupSelect(selectList, optionJson)

#### parameter

- selectList `array` `require` Selection Array of Map. It should be {key:'X',value:'X'}
- optionJson `json` `require` option for popup shape
    - title `string`  Popup Title
    - yes `string`  Yes button text
    - selectedKey `string`  Default Selected key
    - key `string`  Key column name of each json in selectList
    - value `string`  Value column name of each json in selectList
    - w `string`  Popup width. 360 is full width
    - h `string`  Popup height except title and button height
    - show `string`  Default is 'center'
'bottom' - show up from bottom
'top' - show up from top
'point' - show up from button click
    - textColorSelected `string` `require` 선택된 텍스트 색상 default(#5596E0)
    - textColorNormal `string` `require` 기본 텍스트 색상 default(#000000)
    - yesButtonTextColor `string` `require` 버튼 텍스트 색상 default(#5596E0)

#### Example code
```javascript
Jevil.popupSelect([
        {key:'key1',value:'pizza'},
        {key:'key2',value:'hamberg'},
        {key:'key3',value:'coke'},
    ], 
    {selectedKey:'key1'}, function(selectedKey){
    ...
})
         
```




## Jevil.popupTime

시간 선택 팝업을 연다

- Jevil.popupTime(optionJson, callback)

#### parameter

- optionJson `json` `require` 옵션 json
    - selectedKey `string`  선택된 Time
HHdd 형식 문자열
- callback `function` `require` function
    - selectedKey `string` `require` 선택된 Time
HHdd 형식 문자열

#### Example code
```javascript
Jevil.popupTime({selectedKey:'1513'}, function(date){
})
```



