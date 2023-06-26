
## Jevil.get

Get the value in the mobile phone disk with key
It has return value
Pre saved value is as following.
UDID - device UDID MODEL - device Model OS - Android / iOS OS_VERSION - Android Version APP_VERSION - App Version PROJECT_ID - DEVIL project id FCM - firebase push key

- Jevil.get(key)

#### parameter

- key `string` `require` Variable name

#### Example code
```javascript
let myname = Jevil.get('MyName')
//myname is maybe 'Json Ko' if you save the value
```




## Jevil.remove

Remove value in the mobile phone disk with key

- Jevil.remove(key)

#### parameter

- key `string` `require` 삭제할 키

#### Example code
```javascript
Jevil.remove('MyName')
```




## Jevil.save

Save in the mobile phone disk with key and value pair This keep until app removed

- Jevil.save(key, value)

#### parameter

- key `string` `require` Key to save
- value `string` `require` value

#### Example code
```javascript
Jevil.save('MyName', 'Json Ko')
```



