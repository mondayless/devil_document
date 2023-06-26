
## Jevil.drawerCallback

This is counter part of Block Drawer Rule
Callback when Drawer status change

- Jevil.drawerCallback(nodeName, command, callback)

#### parameter

- nodeName `string` `require` Node Name
- command `string` `require` 'up' before popup move
'down' after popup down
- callback `function` `require` 

#### Example code
```javascript
Jevil.drawerCallback('detail_popup', 'up', function(){
  ...
})
```




## Jevil.drawerClose

This is counter part of Block Drawer Rule
Close Drawer

- Jevil.drawerClose(nodeName)

#### parameter

- nodeName `string` `require` Node Name

#### Example code
```javascript
Jevil.drawerClose('detail_popup')
```




## Jevil.drawerMove

This is counter part of Block Drawer Rule
Open Drawer Partial

- Jevil.drawerMove(nodeName, offset)

#### parameter

- nodeName `string` `require` Node Naame
- offset `int` `require` height or width which is able to visible

#### Example code
```javascript
Jevil.drawerMove('detail_popup', 260)
```




## Jevil.drawerOpen

This is counter part of Block Drawer Rule
Open Drawer

- Jevil.drawerOpen(nodeName, param)

#### parameter

- nodeName `string` `require` Node Name
- param `json` `require` blank

#### Example code
```javascript
Jevil.drawerOpen('detail_popup')
```




## Jevil.menuClose

현재 열려있는 메뉴를 닫는다

- Jevil.menuClose(null)

#### parameter
null

#### Example code
```javascript
Jevil.menuClose()
```




## Jevil.menuOpen

Jevil.menuReady에서 준비된 메뉴를 연다

- Jevil.menuOpen(null)

#### parameter
null

#### Example code
```javascript
Jevil.menuOpen('메뉴')
```




## Jevil.menuReady

좌측 메뉴, 혹은 우측 메뉴를 열연다, 하단 탑 drawer를 생성한다

- Jevil.menuReady(blockName, optionJson)

#### parameter

- blockName `string` `require` 메뉴로 사용할 블록
- optionJson `json` `` 옵션 json
    - show `string`  default는 'left'
right, bottom, top
    - offset `int`  메뉴가 약간 보여야한다면 얼만큼 보여야할지에 대한 sketch단위 넓이

#### Example code
```javascript
Jevil.menuReady('메뉴')

Jevil.menuReady('메뉴', {
  show:'right'
})

Jevil.menuReady('메뉴', {
  show:'right',
  offset:100
})
```



