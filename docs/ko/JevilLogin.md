
## JevilLogin.isLogin

Check user is logined or not

x-access-token을 본다

- JevilLogin.isLogin(null)

#### parameter
null

#### Example code
```javascript
let logined = JevilLogin.isLogin()
            
```




## JevilLogin.joinWithDevilServer

Join as new Member
/member/join and
/member/login and
save x-access-token

회원가입도 시키고 로그인도 한다음 x-access-token에 저장한다 
그럼 JevilLogin.isLogin()이 True로 나오고, 
이후 API의 x-access-token도 자동으로 담긴다


- JevilLogin.joinWithDevilServer(callback)

#### parameter

- callback `function` `require` 
    - result `json` `require` {r}
{type}
{email name, sex, age, identifier, profile, token}

#### Example code
```javascript
JevilLogin.joinWithDevilServer({
      age : data.age,
      gender : data.gender,
      identifier : data.identifier,
      name : data.name,
      email : data.email,
      profile : data.profile,
      token : data.token,
      type : data.type
    }
    , function(join){
      if(join.r) {
        Jevil.alertThen('회원가입이 완료되셨습니다', function(){
          Jevil.replaceScreen('main')
        })
      } else {
        Jevil.alert('일시적 오류가 발생하였습니다')        
      }
    })
```




## JevilLogin.kakaoProfileUpdateIfNeedWithDevilServer

kakao프로필이 업데이트 되었다면 devilserver의 /member/change/profile를 호출하여 프로필을 업데이트한다

- JevilLogin.kakaoProfileUpdateIfNeedWithDevilServer(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.kakaoProfileUpdateIfNeedWithDevilServer()
```




## JevilLogin.loginApple

JevilLogin.loginApple

- JevilLogin.loginApple(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginApple(function(result){

})
```




## JevilLogin.loginAppleWithDevilServer

JevilLogin.loginAppleWithDevilServer

- JevilLogin.loginAppleWithDevilServer(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginAppleWithDevilServer(function(result){
    /*ex) result = {
        newMember : true,
        r : true,
        type : 'apple',
        email : myaccount@gmail.com,
        name : 'Json Ko',
        ...
    }*/
})
```




## JevilLogin.loginFacebook

Sns Login

- JevilLogin.loginFacebook(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginFacebook(function(result){
    
})
   
```




## JevilLogin.loginFacebookWithDevilServer

JevilLogin.loginFacebookWithDevilServer

- JevilLogin.loginFacebookWithDevilServer(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginFacebookWithDevilServer(function(result){
    /*ex) result = {
        newMember : true,
        r : true,
        type : 'fb',
        email : myaccount@gmail.com,
        name : 'Json Ko',
        ...
    }*/
})
```




## JevilLogin.loginGoogle

Sns Login

- JevilLogin.loginGoogle(callback)

#### parameter

- callback `function` `require` 
    - result `json` `require` {r}
{type}
{email, name, sex, age, identifier, profile, token}

#### Example code
```javascript
JevilLogin.loginGoogle(function(result){
    /*ex) result = {
        r : true,
        type : 'google',
        email : myaccount@gmail.com,
        name : 'Json Ko',
        identifier:'googleuniquekey'
    }*/
})
```




## JevilLogin.loginGoogleWithDevilServer

Sns Login 을 하고
/member/check 데빌 API를 호출하여, 신규 유저인지 확인하고
신규유저라면 callback하고
기존유저라면 /member/login을 호출하여, Devil Server의 로그인 토큰을 받아온다
로그인 토큰은 Jevil.save('x-access-token', token) 에 저장한다.


-- Ejection시 필요한 내용 --
1. firebase설정 
https://console.firebase.google.com/u/0/project/lofi-84835/authentication/providers (해당 project로 url 교체) 에 구글 인증 추가

2. google cloud 설정
사용자 인증정보 > OAuth 2.0 클라이언트 ID 설정 에서 Web, iOS인증정보 설정 후 
client Id를 다음 세군데 복사
 - front
 - android
 - iOS

3. front
config.json의 googleAuthClientIdForIos와 googleAuthClientIdForAndroid에 각각, ios client Id, Web client ID를 복사(안드로이드는 Web을 사용함)

4. Android 
프로젝트 설정의 Android앱에 SHA1키 입력 
google-service.json을 재 다운로드
매니페스트에 추가
<meta-data
            android:name="devil.login.google.key"
            android:value="{Web client Id}" />

5. iOS
devil.plist에 GoogleLoginClientId 와 hasGoogleLogin Y 로 추가
info.plist에 CFBundleURLSchemes, 에 구글 스킴 추가 


- JevilLogin.loginGoogleWithDevilServer(callback)

#### parameter

- callback `function` `require` 
    - result `json` `require` {r}
{newMember} This user is new member or not
{type}
{email name, sex, age, identifier, profile, token}

#### Example code
```javascript
JevilLogin.loginGoogleWithDevilServer(function(result){
    /*ex) result = {
        newMember : true,
        r : true,
        type : 'google',
        email : myaccount@gmail.com,
        name : 'Json Ko',
        ...
    }*/
})

```




## JevilLogin.loginKakao

JevilLogin.loginKakao

- JevilLogin.loginKakao(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginKakao(function(result){
    
})
```




## JevilLogin.loginKakaoWithDevilServer

JevilLogin.loginKakao 는 카카오 플랫폼만 로그인하고
JevilLogin.loginKakaoWithDevilServer는 카카오 플랫폼+데빌 서버까지 로그인한다

sns 로그인과정은, sns 로그인 성공을 하면 user_id를 줍니다.
그 user_id를 가지고 데빌서버에 신규 유저인지를 물어보고,
기존 유저라면 데빌서버 로그인을 시도하고 데빌서버가 발급하는 토큰을 반환합니다
그 토큰이 앱에 저장되고 이후 모든 API에서 자신을 증명하는 인증수단이 됩니다


--Ejection 시 필요한 내용 --
iOS 세팅해야 할 것 
devil.info에 KakaoAppKey, hasKakaoLogin
info.plist에 카카오키 3군데 교체

Android 세팅해야할것
AndroidManifest.xml에 kakao_key 설정


- JevilLogin.loginKakaoWithDevilServer(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.loginKakaoWithDevilServer(function(result){
    /*ex) result = {
        newMember : true,
        r : true,
        type : 'kakao',
        email : myaccount@gmail.com,
        name : 'Json Ko',
        ...
    }*/
})
            
```




## JevilLogin.logout

로그아웃한다
remove x-access-token

- JevilLogin.logout(null)

#### parameter
null

#### Example code
```javascript
JevilLogin.logout()
```



