
## Jevil.back

현재 화면을 종료한다

- Jevil.back(null)

#### parameter
null

#### Example code
```javascript
Jevil.back()
```




## Jevil.finish

현재 화면을 끝내고 부모화면에게 어떤 데이터를 전달한다
데이터를 전달하는 방식은 부모의 화면의 callback 함수를 호출한다


- Jevil.finish(undifined)

#### parameter

- undifined `json` `require` 

#### Example code
```javascript
Jevil.finish({
  searchResult:'ok'
})

//부모 화면
callback(callbackData){
  Jevil.alert(callbackData.searchResult)
}
```




## Jevil.finishThen

현재 화면을 끝내고 부모화면의 어떤 함수를 호출한다

- Jevil.finishThen(callback)

#### parameter

- callback `function` `require` 

#### Example code
```javascript
Jevil.finishThen(function(){...}})

(Example1)
//In screen A
function updateScreenA(){
    ...
}
Jevil.go('B')
//In screen B
Jevil.finishThen(function(){
    //this is screen A function
    updateScreenA()
}})
```




## Jevil.go

화면 이동을 한다
화면 스택에 쌓인다

- Jevil.go(screenName, undifined)

#### parameter

- screenName `string` `require` 이동할 화면명
- undifined `json` `` 

#### Example code
```javascript
Jevil.go('login')
Jevil.go('login', {title:'hello', 'auto':true})
   
```




## Jevil.replaceScreen

현재 화면을 종료하고, 새로운 화면을 시작한다

- Jevil.replaceScreen(screenName, undifined)

#### parameter

- screenName `string` `require` 이동할 화면
- undifined `json` `` 

#### Example code
```javascript
Jevil.replace('A')

(Example1)
//In screen A
Jevil.replaceScreen('B')
//In screen B
//B showed but, A is gone

        
```




## Jevil.rootScreen

모든 부모화면을 없애고, 지정한 화면으로 이동한다

- Jevil.rootScreen(screenName, undifined)

#### parameter

- screenName `string` `require` 화면 이름
- undifined `json` `` 

#### Example code
```javascript
Jevil.rootScreen('A')
```




## Jevil.tab

화면 이동 없이 현재 화면이 탭처럼 변경된다

- Jevil.tab(screenName)

#### parameter

- screenName `string` `require` 이동할 화면 명

#### Example code
```javascript
Jevil.tab('main')
```




## function onCreated

화면이 만들어지고 난 후에 1회 호출가능하다 

Screen에 onCreated() 함수가 선언되면, 화면을 만들고 난후 1회자동으로 호출한다

- function onCreated(null)

#### parameter
null

#### Example code
```javascript
'input1' 은 화면이 만들어져야 찾을 수 있다.


function onCreated(){
  Jevil.textChanged('input1', function(text) {
    if(text){
      data.nomore = false;
      data.page = 0
      append()
    } else {
      data.list = []
      Jevil.update()
    }
  })  
}
```




## function onResume

Android 의 onResume, 이나 iOS의 viewDidAppeared처럼 화면이 나타날 때, 호출된다, 
이는 자식화면이 finish되면서 부모화면이 나타날때도 호출한다


- function onResume(null)

#### parameter
null

#### Example code
```javascript
function onResume(){
    ...
}

```



