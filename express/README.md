# express
> Fast, unopinionated, minimalist web framework for node.

* [expressjs.com](https://expressjs.com)
* [github.com/expressjs/express](https://github.com/expressjs/express)

## Table of Contents
* [next() and next('route')](#next()-and-next('route'))
* [gzip 압축](#gzip-압축)
* [에러 핸들러에서의 req.params 소멸](#에러-핸들러에서의-reqparams-소멸)

## Reference
* [Express Middleware](http://expressjs.com/en/resources/middleware.html)
  * expressjs팀에서 관리하는 미들웨어 목록입니다.
* [express-route-tester](http://forbeslindesay.github.io/express-route-tester/)

---

### next() and next('route')

`next()`로 호출하면 해당 라우터의 다음 스택을 실행하여 `first`를 응답한다.

`next('route')`로 호출하면 해당 라우터의 스택을 건너뛰고 다음 라우터로 제어권을 넘긴다.

```javascript
app.get('/user/:id', (req, res, next) => {
  if (req.params.id == 1) {
    // print 'second'
    next('route');
  } else {
    // print 'first'
    next();
  }
}, (req, res, next) => {
  res.send('first');
});

app.get('/user/:id', (req, res, next) => {
  res.send('second');
});
```

### gzip 압축

express 사용시 주로 [compression](https://github.com/expressjs/compression) 미들웨어를 사용한다.

* `nginx` vs `compression`의 성능 차이가 있는지 리서치 해본 결과 무시해도 될 만한 수준의 차이가 있는 것으로 보인다.
* `compression`의 gzip 압축 레벨의 기본값은 6이다.
* `compression`의 gzip 압축 대상 최소 사이즈는 기본값이 1kb 이상이다.

### 에러 핸들러에서의 req.params 소멸

참고: https://github.com/expressjs/express/issues/2577

특정 라우팅 미들웨어 스택을 진행하는 도중 에러가 발생함으로써 에러 핸들러로 제어권이 넘어가는 경우  
에러 핸들러에서의 req.params은 빈값이 나온다.  
이유인 즉슨 에러 핸들러 내에서의 req.params는 더 이상 의미가 없는 값이라고 한다.

```javascript
// e.g.  POST /user/myid
router.route('/user/:id')
  .post((req, res, next) => {
    console.log('req.params', req.params); // { id: "myid" }
    if (req.params.id === 'myid') { return next(new Error('Test Error!'); }
    next();
  })
  .post((req, res, next) => {
    res.send('test');
  });

...

function errorHandler(err, req, res, next) {
  console.log('req.params', req.params); // {}
  res.send('Error');
}
```
