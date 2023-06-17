
## Jevil.consumeStandardReserveUrl


push 혹은 firebase deeplink로 받은url

Url형식의 데이터를 처리한다
앱별로 따로 코딩하지 않고 기본적인 기능을 제공한다.

- 화면이동
/screen/{screen_name}?{data의 프로퍼티로 전달될 queryString}




- Jevil.consumeStandardReserveUrl()

#### parameter


#### Example code
```javascript
Jevil.consumeStandardReserveUrl()
```




## Jevil.createDeepLink

파이어베이스 딥링크를 생성한다

iOS에서는 해야할게 많아

1. provisioning 생성할때 associate domain 포함

2. Xcode > Info.plist >  Url Typs에 https 스킴추가 
                <dict>
			<key>CFBundleTypeRole</key>
			<string>Editor</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>https</string>
			</array>
		</dict>

3. Xcode > target > Signing & Capavilities에 associate domain도메인 추가 
  예시) applinks:fluttermobile2.page.link

4. 위 도메인으로 파이어 베이스 dynamic link 생성



- Jevil.createDeepLink(json)

#### parameter

- json `json` `require` 딥링크 파라미터
    - url `string` `require` url은 풀 URL일수도 있고 (http://로 시작하는)
path(/path/abc)일수도있다

path일 경우 project 설정의 Web Host가 앞에 자동으로 붙는다.

    - title `string` `require` 링크에 표시될 제목
    - desc `string` `require` 링크에 표시될 설명
    - package_android `string` `require` 링크 클릭시 안드로이드로 연결될 패키지명
    - package_ios `string` `require` 링크 클릭시 아이폰으로 연결될 패키지명
    - image_url `string`  링크 preview 이미지 풀 URL이어야한다
    - prefix `string` `require` firebase dynamic link에서 생성하는 https://xxx.page.link 형태의 링크

    - appstore_id `string` `require` 앱스토어 아이디 
아이폰 딥링크 만들 시 필수 

#### Example code
```javascript
  let url = '/gift/coupon' + code
  Jevil.startLoading()
  Jevil.createDeepLink({
    url:url,
    prefix:'https://fluttermobile2.page.link',
    title:'쿠폰 선물하기 ',
    desc:'플러터',
    package_android :'com.toobplus.fluttermobile2',
    package_ios :'com.toobplus.fluttermobile2',
    image_url : 'http://www.tutorialsface.com/wp-content/uploads/2015/08/11954620_10153574159971543_7746758011460724864_n.jpg',
    appstore_id : '1571601921'
  }, function(res){
    Jevil.stopLoading()
    if(res && res.r) {
      Jevil.share(res.url)
    } else {
      Jevil.alert(res.msg)
    }
  })
```




## Jevil.getReserveUrl

push 클릭 시 혹은 firebaseDeeplink 클릭시 그 푸시나 firebaseDeeplink 에 담긴 full url이 singleton으로 저장된다. 

그 URL을 가져온다. 
popReserveUrl과 다른건 그 URL을 가져오기만하고 지우지 않는다.

popReserveUrl은 그 url을 가져오고 폰에 저장된 url을 삭제한다



푸시 패턴
   도착타입(show)
     1. 앱이 무조건 띄우는 푸시(default) - force
     2. 앱이 켜져있을때는 안띄우는 푸시 - hide
     3. 특정 조건에만 띄우는 푸시 - cond_show, cond:{screen_id:'chat', data_condition:'data>chat_room_id=='3''}
     4. 특정 조건에만 안띄우는 푸시 - cond_hide, cond:{screen_id:'chat', data_condition:'data>chat_room_id=='3''}
     
     클릭타입(action)
       1. first : 다 지우고 처음부터시작
       2. current : 기존 화면을 지우지않고 특정화면을 추가한다.  
 
     목표화면 
      개념적으로 모든 푸시는 목표화면이 있고, 이 것은 url에 녹여야한다. 
      하지만 이걸 consume하는 것은 무조건 하면 안되고 app javascript에 맡겨야한다.
      로그인이 안되어있는데 목표화면으로 보내버릴수도 있기 때문이다
      따라서, consume은 모든 화면의 onResume 에서 url을 보고 처리해야한다

     
예시) 채팅 푸시 서버 송신 시 
await push.send(db, him, 'chat', d.text, '', host + '/screen/chat/'+ chat_room_id, {
            project_id:1752507297, 
            messageId:300,
            show:'cond_hide', 
            action:'current',
            cond:{
                screen_name:'chat', 
                data_condition:`chat_room_id=='${chat_room_id}'`,
            },

           inapp:true,
           showType:'custom',
           block:'blockName',
});

inapp : 앱이 전면일때 인앱푸시로 화면에 토스트 형태로 뜬다.
showType : 'alert' | 'confirm' | 'custom' | 'default'
default = 데빌앱이 제공하는 기본 뷰로 뜬다
alert, confirm = devil-alert(confirm)-template 이나 Alert창으로 뜬다
custom = 커스텀 블록으로 뜬다



예시) 앱에서 수신시

Jevil.standardConsumeUrl(Jevil.popReserveUrl())
혹은 
Jevil.popReserveUrl() 커스텀 처리










- Jevil.getReserveUrl()

#### parameter


#### Example code
```javascript
if(Jevil.getReserveUrl()) {
    let url = Jevil.popReserveUrl()
    Jevil.alert('URL 처리해야함 ' + url)
}
```




## Jevil.standardUrlProcess

consumeStandardReserveUrl가 처리하는대로 URL을 처리한다

- Jevil.standardUrlProcess(url)

#### parameter

- url `string` `require` standard url

#### Example code
```javascript
Jevil.standardUrlProcess('http://host.com/screen/main?tab=2')
```



