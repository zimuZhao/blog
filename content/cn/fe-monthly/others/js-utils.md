---
title: "JS工具函数"
date: 2021-01-13T10:10:40+08:00
draft: false
enableToc: true
---

## Class A

### 检查是否为空

检查 String、Object、Array、Map、Set 是否为空。 

```javascript
function isEmpty(x) {
  if(Array.isArray(x)
    || typeof x === 'string'
    || x instanceof String
   ) {
    return x.length === 0;
  }

  if(x instanceof Map || x instanceof Set) {
    return x.size === 0;
  }

  if(({}).toString.call(x) === '[object Object]') {
    return Object.keys(x).length === 0;
  }

  return false;
}
```

### 类型检查

基于`typeof`来做判断。需要注意的是，对于数组和对象来说，它们都会被视为“对象”

```javascript
const isOfType = (() => {
  // create a plain object with no prototype
  const type = Object.create(null);

  // check for null type
  type.null = x => x === null;
  // check for undefined type
  type.undefined = x => x === undefined;
  // check for nil type. Either null or undefined
  type.nil = x => type.null(x) || type.undefined(x);
  // check for strings and string literal type. e.g: 's', "s", `str`, new String()
  type.string = x => !type.nil(x) && (typeof x === 'string' || x instanceof String);
  // check for number or number literal type. e.g: 12, 30.5, new Number()
  type.number = x => !type.nil(x)
    && (// NaN & Infinity have typeof "number" and this excludes that
      (!isNaN(x) && isFinite(x)
      && typeof x === 'number'
    ) || x instanceof Number);
  // check for boolean or boolean literal type. e.g: true, false, new Boolean()
  type.boolean = x => !type.nil(x) && (typeof x === 'boolean' || x instanceof Boolean);
  // check for array type
  type.array = x => !type.nil(x) && Array.isArray(x);
  // check for object or object literal type. e.g: {}, new Object(), Object.create(null)
  type.object = x => ({}).toString.call(x) === '[object Object]';
  // check for provided type instance
  type.type = (x, X) => !type.nil(x) && x instanceof X;
  // check for set type
  type.set = x => type.type(x, Set);
  // check for map type
  type.map = x => type.type(x, Map);
  // check for date type
  type.date = x => type.type(x, Date);

  return type;
})();
```

### 生成一定范围内的随机数

```javascript
function randomNumber(max = 1, min = 0) {
  if(min >= max) {
    return max;
  }

  return Math.floor(Math.random() * (max - min) + min);
}
```

### 生成简单的随机ID

三个方法分别支持了:
1. 当前时间（以毫秒为单位）
2. 特定的整数和增量开始生成
3. 从字母生成 ID

```javascript
// create unique id starting from current time in milliseconds
// incrementing it by 1 everytime requested
const uniqueId = (() => {
  const id = (function*() {
    let mil = new Date().getTime();

    while (true)
      yield mil += 1;
  })();

  return () => id.next().value;
})();
// create unique incrementing id starting from provided value or zero
// good for temporary things or things that id resets
const uniqueIncrementingId = ((lastId = 0) => {
  const id = (function*() {
    let numb = lastId;

    while (true)
      yield numb += 1;
  })()

  return (length = 12) => `${id.next().value}`.padStart(length, '0');
})();
// create unique id from letters and numbers
const uniqueAlphaNumericId = (() => {
  const heyStack = '0123456789abcdefghijklmnopqrstuvwxyz';
  const randomInt = () => Math.floor(Math.random() * Math.floor(heyStack.length))

  return (length = 24) => Array.from({length}, () => heyStack[randomInt()]).join('');
})();
```

### 创建数组

比如`range(200, 1000, 100)`生成的结果为：`[200, 300, 400, 500, 600, 700, 800, 900]`

```javascript
function range(maxOrStart, end = null, step = null) {
  if(!end) {
    return Array.from({length: maxOrStart}, (_, i) => i)
  }

  if(end <= maxOrStart) {
    return [];
  }

  if(step !== null) {
    return Array.from(
      {length: Math.ceil(((end - maxOrStart) / step))},
      (_, i) => (i * step) + maxOrStart
    );
  }

  return Array.from(
    {length: Math.ceil((end - maxOrStart))},
    (_, i) => i + maxOrStart
  );
}
```

### 轮询数据

适用于需要持续检查数据更新，但系统中未使用`WebSocket`的情况。

```javascript
async function poll(fn, validate, interval = 2500) {
  const resolver = async (resolve, reject) => {
    try { // catch any error thrown by the "fn" function
      const result = await fn(); // fn does not need to be asynchronous or return promise
      // call validator to see if the data is at the state to stop the polling
      const valid = validate(result);
      if (valid === true) {
        resolve(result);
      } else if (valid === false) {
        setTimeout(resolver, interval, resolve, reject);
      } // if validator returns anything other than "true" or "false" it stops polling
    } catch (e) {
      reject(e);
    }
  };
  return new Promise(resolver);
}
```

### 深度克隆对象

```javascript
const deepClone = obj => {
  let clone = obj;
  if (obj && typeof obj === "object") {
    clone = new obj.constructor();

    Object.getOwnPropertyNames(obj).forEach(
      prop => (clone[prop] = deepClone(obj[prop]))
    );
  }
  return clone;
};
```

