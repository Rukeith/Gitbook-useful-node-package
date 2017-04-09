# Csurf

Node.js CSRF protection middleware.

Requires either a session middleware or cookie-parser to be initialized first.

[https://github.com/expressjs/csurf](https://github.com/expressjs/csurf)

---

CSRF（Cross-site request forgery），中文名稱：跨站請求偽造，也被稱為：one click attack/session riding，縮寫為：CSRF/XSRF。你這可以這麼理解 CSRF 攻擊：攻擊者盜用了你的身份，以你的名義發送惡意請求。CSRF 能夠做的事情包括：以你名義發送郵件，發消息，盜取你的賬號，甚至於購買商品，虛擬貨幣轉賬……造成的問題包括：個人隱私洩露以及財產安全。



**使用方法：**

```js
var cookieParser = require('cookie-parser')
var csrf = require('csurf')
var bodyParser = require('body-parser')
var express = require('express')

// setup route middlewares
var csrfProtection = csrf({ cookie: true })
var parseForm = bodyParser.urlencoded({ extended: false })

// create express app
var app = express()

// parse cookies
// we need this because "cookie" is true in csrfProtection
app.use(cookieParser())

app.get('/form', csrfProtection, function (req, res) {
  // pass the csrfToken to the view
  res.render('send', { csrfToken: req.csrfToken() })
})

app.post('/process', parseForm, csrfProtection, function (req, res) {
  res.send('data is being processed')
})
```



