## Sketch로 UX구현
- Sketch 업로드 해서 UX로 변환
- Artboard(or Node) 가 DAB Screen과 DAB Block 이 된다
- 변환된 앱은 DAB App에서 확인

## Block Rule로 UX를 동적으로 변화시키기
- 약 10가지의 기본룰이 있어서, Image, Text 등이 동적으로 변환된다.
- 각 동적 요소들은 data 변수 안에서 참조하게된다

## 개발언어
- Javascript

## data와 thisData
- Screen에는 javascript를 포함하고, 그 Javascript는 모두 data라는 map객체에서 블록룰의 값을 참조한다

## Jevil로 기능 구현
 - Screen의 Javascript는 라이브러리를 import할 수 없고, 간단한 문법만 동작한다. 따라서 앱의 네이티브를 기능(사진첨부, 파일 읽기 쓰기, 네트워크 기능)을 이용하려면 Jevil이라는 class를 이용하여 개발해야한다.

다음은 http get방식으로 특정 데이터를 가져오는 코드이다
``` js
 Jevil.getThen('https://api.my.com/get/product/list', function(res) {
    if(res.success == true){
        data.list = res.list
        Jevil.update()
    }
 })
 ```

Jevil의 자세한 reference는 Jevil 메뉴를 참조하세요

