
## Jevil.getManyThen

여러 URL을 Get 한다
If 'x-access-token' variable exists, it automatically added to header

- Jevil.getManyThen(urls, callback)

#### parameter

- urls `array` `require` 동시에 실행할 url 배열이다
- callback `function` `require` 
    - results `json` `require` results.r은 모든 요청이 성공했을때 true이다. 하나라도 실패하면  false.



#### Example code
```javascript
let urls = ['/path/1', '/path/2']
  Jevil.startLoading()
  Jevil.getManyThen(urls, function(results){
    Jevil.stopLoading()
    if(!results || !results.r) {
      Jevil.alert('일시적 네트워크 오류입니다')
      return;
    }
    let res_first = results.res[0]
    let res_second = results.res[1]
 });


```




## Jevil.getThen

Send http request and get reponse json.
If you want to add http header, put it to project config.
Url could be path or whole url.
In case that url is path, host infomation should be put in project config.
Your API's response should be json, shouldn ot be others.
If 'x-access-token' variable exists, it automatically added to header

- Jevil.getThen(url, callback)

#### parameter

- url `string` `require` http url to call or path
- callback `function` `require` 
    - res `string` `require` res is json response body
if network failed, res is null

#### Example code
```javascript
Jevil.getThen('http://my.api.server.com/myapi?mykey='+'whatever', function(response) => {
    ...
})

Jevil.getThen('/myapi?mykey='+'whatever', function(response) {
    ...
})
          
```




## Jevil.http

Http 요청  


Get with Body는 동작 하지 않습니다.
RFC 7231 §4.3.1 states that a body "has no defined semantics", but that's not to say it is forbidden.

- Jevil.http(method, path, header, body, callback)

#### parameter

- method `string` `require` get post put delete 등 http 메소드
- path `string` `require` path
- header `json` `require` http header 
- body `json` `require` http body json
- callback `function` `require` 
    - res `json` `require` 응답

#### Example code
```javascript
Jevil.http('get', '/admin/ils-match', {}, {
    name : 'atr001',
    phone : '123456', 
    ils_id :'AA001',
}, function(res) {
    Jevil.alert('응답 ' + res)
})
```




## Jevil.postThen

Send http request and get reponse json.
If you want to add http header, put it to project config.
Url could be path or whole url.
In case that url is path, host infomation should be put in project config.
Your API's response should be json, shouldn ot be others.
If 'x-access-token' variable exists, it automatically added to header

- Jevil.postThen(url, json, callback)

#### parameter

- url `string` `require` http url or path
- json `json` `require` 
- callback `function` `require` 
    - res `json` `require` response body

#### Example code
```javascript
Jevil.postThen('http://my.api.server.com/myapi', {mykey:'whatever'}, function(response) => {
    ...
})

Jevil.postThen('/myapi', {mykey:'whatever'}, function(response) {
    ...
})

```




## Jevil.postThenWithHeader

Send http request and get reponse json.
If you want to add http header, put it to project config.
Url could be path or whole url.
In case that url is path, host infomation should be put in project config.
Your API's response should be json, shouldn ot be others.
If 'x-access-token' variable exists, it automatically added to header

- Jevil.postThenWithHeader(url, json, json, callback)

#### parameter

- url `string` `require` http url or path
- json `json` `require` 
- json `json` `require` 
- callback `function` `require` 
    - res `json` `require` res is json response body

#### Example code
```javascript
Jevil.postThenWithHeader('/myapi', {header1:'h1'}, {mykey:'whatever'}, function(response) {
    ...
})
     
```




## Jevil.putThen

Send http request and get reponse json.
If you want to add http header, put it to project config.
Url could be path or whole url.
In case that url is path, host infomation should be put in project config.
Your API's response should be json, shouldn ot be others.
If 'x-access-token' variable exists, it automatically added to header

- Jevil.putThen(url, json, callback)

#### parameter

- url `string` `require` url
- json `json` `require` json
- callback `function` `require` 

#### Example code
```javascript
Jevil.putThen('http://my.api.server.com/myapi', {mykey:'whatever'}, function(response) => {
    ...
})

Jevil.putThen('/myapi', {mykey:'whatever'}, function(response) {
    ...
})

```




## Jevil.saveFileFromUrl

URL을 다운받아 앱의 문서 폴더에 저장한다

- Jevil.saveFileFromUrl(param, callback)

#### parameter

- param `json` `require` 옵션 param
    - url `string` `require` 온라인 파일 URL
    - destFileName `string` `require` 저장될 파일 명
- callback `function` `require` 
    - res `json` `require` r : 성공여부
dest : 저장된 파일 path

#### Example code
```javascript
Jevil.saveFileFromUrl({url:res.floor.map_url, destFileName:'map_'+data.id+'.jpg'}, function(a) {
          if(a && a.r) {
            Jevil.save(key_my_map_version, res.floor.map_version)
            Jevil.save(key_my_map, a.dest)
          }
        })
```




## Jevil.sendPushKeyWithDevilServer

it calls /push/key api with push key and device udid
If logined, it also sends x-access-token

- Jevil.sendPushKeyWithDevilServer(null)

#### parameter
null

#### Example code
```javascript
Jevil.sendPushKeyWithDevilServer()
```




## Jevil.uploadS3

Upload file to s3.
It internally call '/api/media/url/put/jpg' or '/api/media/url/put/mp4' with Http Config Host Value of Project
and for getting S3 upload signed Url. It upload files and callback function with upload path
S3 and server should be prepared.


uploadS3Secure를 동일한 방법으로 사용하면, public이아닌 private영역에 파일이올라간다

- Jevil.uploadS3(files, callback)

#### parameter

- files `array` `require` local file path
- callback `function` `require` 
    - result `json` `require` s3 upload result

#### Example code
```javascript
//이 함수를 사용하려면 로그인 되어있어야함
Jevil.uploadS3(['/file/path1', '/file/path2'], function(result) {
    ...
    /*ex) result = {
        r : true,
        uploadedFile : [
            {
                original : '/file/path1',
                key : 'media/test/mp4',
                success : true
            }
        ]
    }*/
})

```



