
## Jevil.parseUrl

Uri 문자열을 받고 query를 map으로 반환한다

- Jevil.parseUrl(url)

#### parameter

- url `string` `require` Url을 받고 query를 map으로 반환한다

#### Example code
```javascript
Jevil.parseUrl('http://m.google.co.kr/path?a=1&b=2')

return값 
{
  a: 1,
  b: 2
}
```



