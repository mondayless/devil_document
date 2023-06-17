
## Jevil.camera

Open camera for taking picture or video

- Jevil.camera(cameraOption, callback)

#### parameter

- cameraOption `json` `require` Camera Option
    - startVideo `boolean`  Camera starts with video record. Default false
    - startFront `boolean`  Camera starts with front lence(self-camera). Default true
    - startFlash `boolean`  Camera starts with flash on. Default true
    - hasPicture `boolean`  Camera can take picture. Default true
    - hasVideo `boolean`  Camera can take video. Default false
    - hasGallery `boolean`  Camera can take video or picture from gallery. Default true
    - minSec `int`  If it has video, min sec for recording. Default 3
    - maxSec `boolean`  If it has video, max sec for recording. Default 10
    - ratio `float`  Height comparing width. Default 1.0
- callback `function` `require` 
    - result `json` `require` {r}	boolean	Complete or cancel
{preview}	String	File path for video preview jpeg
{video}	String	File path for video mp4
{image}	String	File path for image jpeg

#### Example code
```javascript
Jevil.camera(
    {
        hasPicture : true,
        hasVideo : true,
        minSec : 3,
        maxSec : 10,
        ratio : 1.0
    },
    function(result){

})
            
```




## Jevil.cameraQr

Qr코드 혹은 바코드를 인식한다

- Jevil.cameraQr(param, callback)

#### parameter

- param `json` `require` 카메라 옵션
    - blockName `string`  카메라 위에 덮을 블록명 
없으면 그냥 기본 제공 UI
    - startFront `boolean`  전면 카메라로 시작할지 여부
default - false
    - finish `boolean`  QR인식하면 카메라 화면을 중단할지 여부. default - true
- callback `function` `require` 
    - result `json` `require` 응답값 

#### Example code
```javascript
Jevil.cameraQr(
    {
      blockName:'qr',
      startFront:true,
    },
    function(result){
      if(result.r) {
        Jevil.startLoading()
        Jevil.getThen('/api/Coupon/Coup_inf_cd=' + result.code, function(res) {
          Jevil.stopLoading()  
          if(res && res.result == 1) {
            Jevil.toast('쿠폰이 사용처리 되었습니다')
          }
        })
      }
  })
```




## Jevil.cameraQrClose()

현재 열려있는 QR인식 화면을 닫는다

- Jevil.cameraQrClose()()

#### parameter


#### Example code
```javascript
Jevil.cameraQrClose()
```




## Jevil.gallery

갤러리로부터 사진 입력을 받는다

- Jevil.gallery(param, callback)

#### parameter

- param `json` `require` 파라미터
    - hasPicture `boolean` `require` 갤러리에서 이미지 선택가능 여부
    - hasVideo `boolean` `require` 갤러리에서 비디오 선택가능 여부
    - minSec `int`  비디오 선택시 최소 재생시간
    - maxSec `int`  비디오 선택시 최대 재생시간
    - min `int` `require` 갤러리 선택시 최소 선택 개수
    - max `int` `require` 갤러리 선택시 최대 선택 개수
    - title `string`  사진 선택시 상단에 나올 제목
- callback `function` `require` 
    - result `json`  {r}	boolean	Complete or cancel
{list} : [
{preview}	String	File path for video preview jpeg
{video}	String	File path for video mp4
{image}	String	File path for image jpeg
]

#### Example code
```javascript
Jevil.gallery(
      {
          min:1, //최소 선택
          max:1, //최대 선택
          //이하 Jevil.camera의 파라미터를 따름
          hasPicture : true,
          hasVideo : false,
          startFront : true,
          ratio : 1.0, 
      },
      function(result){
/*
result sampel
{
  r:true,
  list:[
 {
type:'image', //동영상인경우 video
image:'/storage/emulated/0/....jpg',//이미지일경우
preview:'/storage/emulated/0/....jpg', //동영상일경우
video:'/storage/emulated/0/....mp4',//동영상일경우
}
 ]
}
result.r true/false, 성공실패
result.list 
*/
        if(result.r) {
          data.image = result.list[0].image
          Jevil.update()
        }
  })
```




## Jevil.galleryList

겔러리의 이미지를 가져온다

- Jevil.galleryList(optionJson, callback)

#### parameter

- optionJson `json` `require` 파라미터
    - hasPicture `boolean` `require` 이미지 가져올지 여부
    - hasVideo `boolean` `require` 비디오 가져올지 여부
- callback `function` `require` 
    - res `json` `require` list

#### Example code
```javascript
Jevil.galleryList({}, function(res) {
    Jevil.stopLoading()
    if(res && res.r) {
      //res.list = [{url:'url1'}, {url:'url2'}]
      Jevil.update()
    }
  })
```



