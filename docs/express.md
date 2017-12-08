## express
> Fast, unopinionated, minimalist web framework for node.

### Links
* https://expressjs.com
* https://github.com/expressjs/express

### Table of Contents
* [`next()` and `next('route')`](#`next()`-and-`next('route')`)

### Reference
* [express-route-tester](http://forbeslindesay.github.io/express-route-tester/)

---

### `next()` and `next('route')`

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
