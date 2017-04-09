# Helmet

Help secure Express apps with various HTTP headers

[https://helmetjs.github.io/](https://helmetjs.github.io/)

---

Helmet 是一系列幫助增強 Node.js 之 Express/Connect 等 JavaScript Web 應用安全的中間件。一些著名的對 Web 攻擊有 XSS 跨站腳本， 腳本注入 clickjacking 以及各種非安全的請求等對 Node.js 的 Web 應用構成各種威脅，使用 Helmet 能幫助你的應用避免這些攻擊。

**安裝方法：**

```
npm install helmet --save
```

or

```
yarn add helmet
```



**使用方法：**

make sure these middlewares are listed before `app.router`.

```js
import Express from 'express';
import helmet from 'helmet';
const app = Express();

app.use(helmet());

// 也可以單獨使用它們的部分功能
app.use(helmet.noCache());
app.use(helmet.frameguard());

// 也可以使用設定檔的方式
app.use(helmet({
  frameguard: {
    action: 'deny'
  }
}))
```



