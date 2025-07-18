# HTML / CSS / JavaScript 学习笔记

## 🔧 HTML 基础

### 1. 安装插件
- 在 IDE（如 IntelliJ IDEA）中安装 HTML 支持插件。

### 2. HTML 基本结构
- 输入 `!` + `Tab` 可快速生成 HTML5 基本结构。

### 3. 标签说明
- `head`：与展示无关的元素（如 `<title>`）。
- `body`：页面主要展示内容区域。
- 单标签不需要结束符，例如：
  - `<br>`：换行
  - `<hr>`：分割线
  - `<img src="路径">`：图片标签，可用 base64 编码

### 4. 常见标签
- 标题：`<h1>` ~ `<h6>`，表示 1~6 级标题。
- 段落：`<p>` 段落文本。
- 无序列表：`<ul><li>内容</li></ul>`
- 有序列表：`<ol><li>内容</li></ol>`
- 超链接（Anchor）：
  ```html
  <a href="链接地址">超链接文本</a>
  <a href="#top">回到顶部</a>
  <p id="top">页面顶部</p>
  ```
- 音视频：
  ```html
  <video src="路径" controls></video>
  <audio src="路径" controls></audio>
  ```

### 5. 表单 `<form>`
- 用于提交数据给服务器：
  ```html
  <form action="服务器地址" method="get/post" enctype="...">
      <input type="text" name="username">
      <input type="submit" value="提交">
  </form>
  ```
- 常见 `type`：
  - `text`：文本框
  - `submit`：提交按钮
  - `file`：上传文件
- `name` 属性必须存在，数据才会被提交。
- `form` 默认用 GET，若需 POST 需手动设置。
- 发送 JSON 需配合 JavaScript。

### 6. 样式标签
- `<span>`：用于设置行内样式（如颜色等）。
- 引入外部 CSS：
  ```html
  <link rel="stylesheet" href="style.css">
  ```

### 7. 其他
- `<div>`：容器标签，用于布局。
- `<template>`：需配合 JS 使用。
- HTML 的 `id` 属性不能重复。

---

## 🎨 CSS 基础

### 1. 选择器类型
- **类型选择器**：如 `p { color: red; }`
- **类选择器**：如 `.my-class { font-size: 14px; }`
- **ID 选择器**：如 `#header { background: black; }`

### 2. 使用方式
- 在 HTML 元素中使用：
  ```html
  <p class="my-class"></p>
  ```
- 样式写法：
  ```css
  .my-class {
    color: blue;
    font-size: 16px;
  }
  ```

### 3. 选择器优先级
- `id > class > type`

---

## 🧠 JavaScript 基础

### 1. 引入方式
- 内联：
  ```html
  <script>
    // js代码
  </script>
  ```
- 外部文件：
  ```html
  <script src="main.js"></script>
  ```

### 2. 变量定义
- `let`：块级作用域，推荐使用。
- `const`：常量，不可重新赋值。
- `var`：函数作用域，不推荐。

### 3. 获取元素
```javascript
document.getElementById("id名")
```

### 4. 操作文本
```javascript
element.innerText = "新文本";
```

### 5. 数据类型与操作
- `nullish` 合并：`undefined` 和 `null`
- 字符串拼接：
  - `"a" + "b"`
  - \`hello ${name}\`
- 类型转换：
  ```javascript
  parseInt("123"); // => 123
  ```
- 大整数：
  ```javascript
  let big = 12345678901234567890n;
  ```

### 6. 函数
- 普通函数：
  ```javascript
  function add(a, b) {
    return a + b;
  }
  ```
- 匿名函数（立即执行）：
  ```javascript
  (function(a, b){ return a + b; })(1, 2);
  ```
- 箭头函数：
  ```javascript
  (a, b) => a + b;
  ```

- 函数也是对象，可以赋值给变量，作为参数传递。
- 函数作用域：每个函数内部都是独立作用域。

### 7. 异常处理
```javascript
try {
  // 可能出错的代码
} catch (err) {
  console.log(err.message);
} finally {
  // 总会执行的代码
}
```

---

## 📚 JavaScript 数据结构

### 1. 数组 Array
- `push()`：尾部添加元素
- `shift()`：移除首位元素
- `splice(start, count)`：删除指定索引范围（左闭右开）
- `join("-")`：使用连接符将数组转字符串
- `map(fn)`：对数组所有元素执行函数并返回新数组
- `filter(fn)`：筛选符合条件的元素组成新数组
- `forEach(fn)`：遍历数组（不返回新数组）

> 这些方法不会改变原数组。

### 2. 对象 Object
- 创建对象：
  ```javascript
  const person = {
    name: "Tom",
    age: 25,
    greet: function() {
      return "Hello " + this.name;
    }
  };
  ```
- 访问属性：`obj.name` 或 `obj["name"]`
- 修改/添加属性：`obj.newProp = value`
- 删除属性：`delete obj.prop`
- Getter/Setter：
  ```javascript
  const obj = {
    _name: "Jack",
    get name() {
      return this._name;
    },
    set name(val) {
      this._name = val;
    }
  };
  ```

### 3. 对象遍历与 this
- `for in` 遍历对象属性：
  ```javascript
  for (let key in obj) {
    console.log(obj[key]);
  }
  ```
- `this` 指向规则：
  - 普通函数：调用者决定 `this`
  - 箭头函数：继承外部作用域的 `this`
  - 方法中的 `this` 指向所属对象

- 改变 `this`：
  ```javascript
  someFunction.call(newThis, arg1, arg2);
  ```

> 注意：使用 `.call` 会破坏封装，应尽量避免。

### 4. 展开运算符 ...
```javascript
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged = [...arr1, ...arr2];
```

---

## 📎 补充建议

- HTML 标签查询推荐使用 [MDN Web Docs](https://developer.mozilla.org/)
- 学习网络请求时深入理解 HTTP 协议和请求方法（GET、POST 等）
- 建议搭配 DevTools 观察 HTML/CSS/JS 的实际效果
