---
title: "笔记"
date: 2020-08-02T14:08:56+08:00
draft: false
enableToc: true
---

## JS

### 使用 ^ 切换变量 0 或 1

```javascript
// --- before ---
// if 判断
if (toggle) {
    toggle = 0;
} else {
    toggle = 1;
}
// 三目运算符
togle = toggle ? 0 : 1;

// --- after ---
toggle ^= 1;
```

### void 0 比写 undefined 快

```javascript
let d = void 0;
console.log(d); // undefined
```

### 使用 Array.length = 0 来清空数组

## VUE

[VUE笔记](https://www.processon.com/view/link/5f9b8ee35653bb3730921646)

