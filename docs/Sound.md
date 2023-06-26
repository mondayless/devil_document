
## Jevil.recordCancelCallback

앱이 백그라운드로 가거나 녹음이 취소될때 호출된다

- Jevil.recordCancelCallback(null)

#### parameter
null

#### Example code
```javascript
Jevil.recordCancelCallback(function () {
  data.record_status = '녹음 취소'
    data.record_btn_text = '녹음 시작'
    Jevil.update()
})
```




## Jevil.recordStart

녹음을 시작한다

- Jevil.recordStart(param, callback)

#### parameter

- param `json` `require` 녹음 옵션 - 아직 옵션은 없다
- callback `function` `require` 
    - res `json` `require` 시작 결과 - 아직 결과값은 없다

#### Example code
```javascript
data.record_status = '녹음 대기'
data.record_btn_text = '녹음 시작'

function record() {
  if(Jevil.recordStatus() == 'none') {
    data.record_status = '녹음 준비 중'
    data.record_btn_text = '클릭 불가'
    Jevil.update()
    Jevil.recordStart({}, function(res){
      data.record_status = '녹음 중'
      data.record_btn_text = '녹음 중지'
      Jevil.update()

      Jevil.recordCancelCallback(function () {
        data.record_status = '녹음 취소'
          data.record_btn_text = '녹음 시작'
          Jevil.update()
      })
    })
  } else if(Jevil.recordStatus() == 'recording') {
    data.record_status = '녹음 마감 중'
    data.record_btn_text = '클릭 불가'
    Jevil.update()
    Jevil.recordStop(function(res){
      data.record_status = '녹음 준비 중'
      data.record_btn_text = '녹음 시작'
      data.url = res.url
      Jevil.update()
    })
  } else if(Jevil.recordStatus() == 'changing') {
    
  }
}

```




## Jevil.recordStatus

현재 레코딩 상태를 가져온다.
'none' - 프리한 상태
'recording' - 녹음 중
'changing' - 상태가 변하고 있는 상태

- Jevil.recordStatus(null)

#### parameter
null

#### Example code
```javascript
if(Jevil.recordStatus() == 'none') {
...
}
```




## Jevil.recordStop

녹음을 중단한다
로컬 파일 url을 결과값으로 받는다
Jevil.sound({url:[그 url]) 로 녹음한 파일을 재생할 수 있다


- Jevil.recordStop(callback)

#### parameter

- callback `function` `require` 
    - res `json` `require` url - 녹음파일이 저장된 파일 경로

#### Example code
```javascript
Jevil.recordStop(function(res) {
  Jevil.alert(res.url)
})
```




## Jevil.recordTick

녹음이 재생중이라면 매초마다 해당 함수를 call한다

- Jevil.recordTick(callback)

#### parameter

- callback `function` `require` 
    - sec `int` `require` 진행중인 초

#### Example code
```javascript
Jevil.recordTick(function(sec) {
  //Jevil.toast(sec)
})
```




## Jevil.sound

음악을 재생한다

- Jevil.sound(param)

#### parameter

- param `json` `require` 파라미터
    - url `string` `require` 재생할 사운드의 http url
    - start `int`  재생할 사운드의 시작점(초)
    - title `string`  락스크린에 표시할 음악 명
    - artist `string`  락스크린에 표시할 아티스트 명
    - notification `boolean`  안드로이드만 해당하며 미디어 플레이어 노티피케이션이 나온다 
default는 false다
    - keep `boolean`  activity가 끝나도 음악이 계속 재생된다 
default true
    - artwork `string`  음악재생에 표시할 비트맵 이미지 URL
    - notification_url `string`  Android에서 notification 을 클릭했을 때 이동할 url

    - music `boolean`  music이면 안드로이드의 ongoing player 락스크린의 플레이어가 뜬다.

default : true

#### Example code
```javascript
Jevil.sound({
url:'http://.../mp3',start:3
})

Jevil.sound({url:url,start:sec, title:data.title, artist:data.author})

Jevil.sound({
      url:music.mp4,
      notification:true,
      notification_url : '/screen/player?id=' + data.id + '&isplayer=Y',
      title:music.title,
      artist:res.album.name,
      artwork:res.album.image,
      keep:true,
})
```




## Jevil.soundControlCallback

음악 플레이는 외부에서 컨트롤 가능하다 

외부에서 컨트롤하거나, 음악파일이 끝날때 호출된다

대표적으로 잠금화면에서 play/pause forward, reward가 있습니다.

또한 Android의 경우 notification에서도 컨트롤 가능하다

- Jevil.soundControlCallback(callback)

#### parameter

- callback `function` `require` 
    - command `string` `require` command 이름, 

자세한건 예제 참조

#### Example code
```javascript
function controlCallback() {
  Jevil.soundControlCallback(function(command){
    if(command == 'prev') {
      
    } else if(command == 'next') {
      
    } else if(command == 'stop') {
      pauseState()
    } else if(command == 'resume') {
      playState()
    } else if(command == 'pause') {
      pauseState()
    } else if(command == 'complete') {

    }
  })
}
```




## Jevil.soundCurrentInfo

현재 재생중인 사운드가 있으면 그 정보를 가져온다

- Jevil.soundCurrentInfo(null)

#### parameter
null

#### Example code
```javascript
let info = Jevil.soundCurrentInfo()
info = {
 ...
}
```




## Jevil.soundIsPlaying

현재 세션에 사운드가 플레잉중인지 반환한다

- Jevil.soundIsPlaying(null)

#### parameter
null

#### Example code
```javascript
if(Jevil.soundIsPlaying())
   Jevil.soundPause()
else
   Jevil.soundResume()
```




## Jevil.soundMove

현재 재생중인 지점에서 N초간 이동한다

- Jevil.soundMove(sec)

#### parameter

- sec `int` `require` 이동할 N초며 마이너스 값이 될 수 있다

#### Example code
```javascript
Jevil.soundMove(10);
Jevil.soundMove(-3);
```




## Jevil.soundPause

현재 재생중인 음성이 있다면 pause한다.


- Jevil.soundPause()

#### parameter


#### Example code
```javascript
Jevil.soundPause()
```




## Jevil.soundResume

현재 Pause 중인 음성이 있다면 다시 재생한다

- Jevil.soundResume(null)

#### parameter
null

#### Example code
```javascript
Jevil.soundResume()
```




## Jevil.soundSeek

해당 초로 이동한다

- Jevil.soundSeek(sec)

#### parameter

- sec `int` `require` 이동할 초

#### Example code
```javascript
Jevil.soundSeek(10)
```




## Jevil.soundSpeed

현재 재생중인 음성의 재생 속도를 설정한다

- Jevil.soundSpeed(speed)

#### parameter

- speed `float` `require` 음성의 재생속도 1.0은 기본, 2.0은 두배 1.5는 1.5배

#### Example code
```javascript
Jevil.soundSpeed(1.6)
```




## Jevil.soundStop

현재 재생중인 음성이 있다면 Stop한다. pause와 다른점은 pause는 잠시스톱이며, resume으로 복구가가능하지만, Stop은 완전히 메모리에서 내려간다

- Jevil.soundStop(null)

#### parameter
null

#### Example code
```javascript
Jevil.soundStop()
```




## Jevil.soundTick

음성이 재생중이라면 매초마다 해당 함수를 call한다

- Jevil.soundTick(callback)

#### parameter

- callback `function` `require` 
    - sec `string` `require` 현재 재생중인 음성의 진행 시점(초)
    - totalSec `int` `require` 총 길이(초)

#### Example code
```javascript
Jevil.soundTick(function(sec, totalSec) {
  //alert(sec, totalSec)
})
```




## Jevil.speechRecognizer

음성 인식을 한다

- Jevil.speechRecognizer(param, callback)

#### parameter

- param `json` `require` 음성 인식 옵션
    - streaming `boolean`  말하는 중간에 결과를 스트리밍으로 받을지 
default : false
- callback `function` `require` 
    - text `string` `require` 인식 결과 텍스트

#### Example code
```javascript
Jevil.speechRecognizer({streaming:true}, function(result){
  if(result && result.r) {
    let text = result.text
    if(result.end) {
      ... 마지막 여부
    } else {
      ....중간 인식 결과
    }
  }
  

})
```




## Jevil.stopSpeechRecognizer

현재 음성인식중이라면 멈춘다

- Jevil.stopSpeechRecognizer(null)

#### parameter
null

#### Example code
```javascript
stopSpeechRecognizer()
```



