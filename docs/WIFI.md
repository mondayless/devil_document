
## Jevil.isWifi

Wifi 여부를 체크한다 iOS는 무조건 true를 반환한다

- Jevil.isWifi(callback)

#### parameter

- callback `function` `require` 
    - yes `boolean` `require` wifi 여부

#### Example code
```javascript
Jevil.isWifi(function(yes){
 ...
})
```




## Jevil.wifiIsOn

Check wifi is connected(In iOS case it always return yes, because we dont know)


- Jevil.wifiIsOn(null)

#### parameter
null

#### Example code
```javascript
let wifiIsConnected = Jevil.wifiIsOn()
```



