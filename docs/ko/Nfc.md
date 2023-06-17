
## JevilNfc.Stop

NFC 리딩을 멈춘다

- JevilNfc.Stop()

#### parameter


#### Example code
```javascript
JevilNfc.stop()
```




## JevilNfc.start

NFC를 읽고, NFC가 ndef방식이면 write에 해당하는 text 혹은 hex를 쓴다

- JevilNfc.start(param, callback)

#### parameter

- param `json` `require` nfc를 읽었을때의 다양한 행동을 명시한다
    - write `json` `require` text 혹은 hex 로 무엇을 쓸지를 전달한다
write : {
   text : 'hello',
}

write : {
   hex : '31313030',
}
    - writeAndReadTermMs `int`  write를 할 경우, 직후 read를 하는데 몇ms후에 할지에 대한 변수이다. default는 500ms이다
- callback `function` `require` 
    - res `json` `require` r - 읽었는지 여부 
id - nfc id hex string
tech_list : nfc 종류
record_list : nfc로부터 읽어들인 내용
s : id 를 string으로 변환한값

#### Example code
```javascript
JevilNfc.start({write:{
    text:'100125  홍길동      01011112222 1\r'
}, writeAndReadTermMs:100}, function(res) {
    data.text2 = 'Tag id Hex = ' + res.id
   /* res 예시 
   let res = { 
      r:true,   
      id : "028467150cb35", 
      tech_list:[{
         name:'android.nfc.tech.IsoDep'
      }],
      record_list : [{ //NFC로 부터 읽은값 배열
         payload_hex :'aa001의 hex 문자열',
         payload_text :'aa001'
      }]
   }
*/
})


```



