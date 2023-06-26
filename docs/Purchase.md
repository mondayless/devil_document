
## JevilBill.consume

1회성 아이템은 반드시 재구매 하기전에 JevilBill.consume을 해주어야한다
구매 -> 소비 

- JevilBill.consume(param, callback)

#### parameter

- param `json` `require` 파라미터
    - sku `string` `require` 소비할 sku
- callback `function` `require` 
    - res `json` `require` {
 r: true, 
 msg : 'Failed message'
}

#### Example code
```javascript
JevilBill.consume({sku:purchase.sku}, function(res) {
        if(res.r) {
          Jevil.alert('감사합니다 구매가 완료 되었습니다. ')
          update()
        }
})
```




## JevilBill.purchase

아이템 혹은 구독을 구매한다

- JevilBill.purchase(param, callback)

#### parameter

- param `json` `require` 구매 파라미터
    - sku `string` `require` 구독 혹은 구매할 sku
- callback `function` `require` 
    - res `json` `require` {
  r:  true,
  msg : '실패시 메세지'
}

#### Example code
```javascript
JevilBill.purchase({sku:'sku111'}, function(res) {
    Jevil.stopLoading()  
    if(res.r) {
      //purchaseReward(res)
    } else if(res.msg) {
      Jevil.alert(res.msg) 
    }
})
```




## JevilBill.requestProduct

구매 가능한 sku에 대한 정보를 가져온다

- JevilBill.requestProduct(param, callback)

#### parameter

- param `json` `require` 파라미터
    - skus `string` `require` 정보를 요청할 sku 배열을 넘긴다 

- callback `function` `require` 
    - res `json` `require` 응답값을 받는다
응답값 예시 

{
 r : true,
 list : [
  type : 'normal'  | 'subscribe', 
  sku : 'sku1', 
  title : '멤버쉽 아이콘',
  desc : '아이콘을 획득합니다', 
  price : '1000',
  price_text : '1000원',
  valid : true, //구독 시 true, 
  receipt : 'xx', // 구독시 영수증
  order_id : 'xx', //구독시 주문번호
 ]
}

#### Example code
```javascript
function loadSku() {
  Jevil.startLoading()
  JevilBill.requestProduct({skus:['membership5']}, function(res) {
    Jevil.stopLoading()  
    if(res && res.r) {
      data.sku_list = res.list
      update()
    }
  })  
}

```



