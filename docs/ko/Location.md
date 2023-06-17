
## Jevil.getCurrentLocation

현재 위치 위경도를 구한다

- Jevil.getCurrentLocation(param, callback)

#### parameter

- param `json` `require` 현재는 빈값이다
- callback `function` `require` 
    - res `json` `require` {r} 성공 여부
{lat}
{lon}
{address1}
{address2}
{address3}
{address4}

#### Example code
```javascript
  Jevil.startLoading()
  Jevil.getCurrentLocation({}, function(res){
    Jevil.stopLoading() 
    if(res.r) {
      data.isthis = 'Y'
      
      let msg = '현재 위치는 ' + res.address2  + ' ' + res.address3 + ' 입니다\n이 위치로 선택하시겠습니까?'
      Jevil.confirm(msg , '예', '아니오', function(yes) {
        if(yes){
          data.location = res;
          select()
        }
      })
      
    } else 
      Jevil.alert(JSON.stringify(res))
  })
```




## Jevil.getCurrentPlace

현재 위치의 주소와 위경도를 가져온다

- Jevil.getCurrentPlace(parameter, callback)

#### parameter

- parameter `json` `require` 현재는 빈값이다
- callback `function` `require` 
    - res `json` `require` res

#### Example code
```javascript
  Jevil.startLoading()
  Jevil.getCurrentPlace({}, function(res){
    Jevil.stopLoading() 
    if(res.r) {
      data.isthis = 'Y'
      
      let msg = '현재 위치는 ' + res.address2  + ' ' + res.address3 + ' 입니다\n이 위치로 선택하시겠습니까?'
      Jevil.confirm(msg , '예', '아니오', function(yes) {
        if(yes){
          data.location = res;
          select()
        }
      })
      
    } else 
      Jevil.alert(JSON.stringify(res))
  })
```




## Jevil.searchPlace

동명 등 위치를 검색한다

- Jevil.searchPlace(param, callback)

#### parameter

- param `json` `require` 검색 옵션
    - keyword `string` `require` 검색어
- callback `function` `require` 
    - res `json` `require` {r} 성공 여부
{list} 결과 목록

#### Example code
```javascript
  Jevil.startLoading()
  Jevil.searchPlace({keyword:data.input1}, function(res){
    Jevil.stopLoading()
    if(res && res.r) {
      data.list = res.list
      Jevil.update()
    } else {
      Jevil.alert(res.msg)
    }
  })
```



