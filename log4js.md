# Log4js

The Logging Framework for JavaScript

[http://stritti.github.io/log4js/](http://stritti.github.io/log4js/)

[https://github.com/nomiddlename/log4js-node](https://github.com/nomiddlename/log4js-node)

---

node 預設的日誌輸出中一旦應用中斷或者停止則記錄就會消失，儘管在生產環境中 pm2 也會為我們記錄一定的 logs，但是這些可能並不能夠滿足生產環境所需要的日誌信息，因此如果能夠將日常的​​日式保存到文件中是最為可靠的，log4js 滿足了我們日常的需要。

**安裝方法：**

```
npm install --save log4js
```

or

```
yarn add log4js
```

**使用方法：**

```js
const log4js = require('log4js');
log4js.configure({
  appenders: {
    cheese: {
      type: 'file',  //文件输出
      filename: 'cheese.log'
    }
  },
  categories: {
    default: {
      appenders: ['cheese'],
      level: 'error'
    }
  }
});

const logger = log4js.getLogger('cheese');
// 設置級別
logger.setLevel('ERROR');  

// log4js 有 6 個輸出級別
logger.trace('Entering cheese testing');
logger.debug('Got cheese.');
logger.info('Cheese is Gouda.');
logger.warn('Cheese is quite smelly.');
logger.error('Cheese is too ripe!');
logger.fatal('Cheese was breeding ground for listeria.');
```



