
## JevilAnimation.start

애니메이션을 시작한다

- JevilAnimation.start(nodeName, param)

#### parameter

- nodeName `string` `require` 노드명
- param `json` `require` 파라미터
    - type `string` `require` pulse - 영원히 커졌다 작아졌다한다
    - scale `float` `require` purlse - 최대로 커지는 크기

#### Example code
```javascript
JevilAnimation.start('recordIcon', {type:'pulse', scale:1.3})
```




## JevilAnimation.stop

에니메이션을 즉시 멈춘다

- JevilAnimation.stop(nodeName)

#### parameter

- nodeName `string` `require` nodeName

#### Example code
```javascript
JevilAnimation.stop('recordIcon')
```



