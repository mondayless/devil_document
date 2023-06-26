
## Jevil.photo

전체 팝업으로 Photo를 디스플레이 한다

- Jevil.photo(param)

#### parameter

- param `json` `require` Photo뷰를 여는 파라미터
    - url `string` `require` 이미지 URL
    - urls `string` `require` 각 url들이 슬라이드됨

#### Example code
```javascript
Jevil.photo({
  url : 'http://m.google.com/player.mp4',
})

Jevil.photo({
  url : 'http://m.google.com/1.mp4'
  urls :['http://m.google.com/2.mp4','http://m.google.com/3.mp4','http://m.google.com/4.mp4']
})
```




## Jevil.video

새로운 화면으로 비디오를 플레이한다, 

- Jevil.video(param)

#### parameter

- param `json` `require` 비디오 플레이를 하기위한 파라미터
    - url `string` `require` 플레이할 Video URL
    - urls `array`  url이 끝나고 계속해서 플레이할 url

#### Example code
```javascript
Jevil.video({
  url : 'http://m.google.com/player.mp4',
})

Jevil.video({
  url : 'http://m.google.com/1.mp4'
  urls :['http://m.google.com/2.mp4','http://m.google.com/3.mp4','http://m.google.com/4.mp4']
})
```



