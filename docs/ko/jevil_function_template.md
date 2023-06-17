### Jevil.camera

Open camera for taking picture or video

- Jevil.camera(cameraOption, callback)

    - cameraOption(json)
        - hasPicture
            - type boolean
            - 갤러리에서 이미지 선택가능 여부
        - hasVideo `required`
        - minSec(int)
    - callback
        - type function
        - {r} boolean Complete or cancel {list} : [ {preview} String File path for video preview jpeg {video} String File path for video mp4 {image} String File path for image jpeg ]

#### Example code
```javascript
Jevil.camera({
    hasPicture : true,
    hasVideo : true,
    minSec : 3,
    maxSec : 10,
    ratio : 1.0
},
function(result){

})
```
