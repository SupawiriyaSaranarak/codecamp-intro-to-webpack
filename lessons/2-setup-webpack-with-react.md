### Setup Webpack With React

0. ทำการ Install Dependencies ดังนี้

```
npm install -D babel-loader @babel/core @babel/preset-env @babel/preset-react
```

1. ทำการ install react และ react-dom

```
npm install -S react react-dom
```

2. สร้างไฟล์ .babelrc แล้วเขียน Config ลงไปดังนี้

```javascript
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ]
}
```

3. ทำการแก้ไฟล์ dist/index.html เป็นแบบนี้

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello Webpack</title>
  </head>
  <body>
    <div id="root"></div>
    <script src="./bundle.js"></script>
  </body>
</html>
```

4. ทำการแก้ไฟล์ src/index.js เป็นแบบนี้

```javascript
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(
  <h1>Hello React with Webpack from scratch</h1>,
  document.getElementById("root")
);
```

5. ทำการแก้ Config Webpack เป็นแบบนี้

```javascript
const path = require("path");

module.exports = {
  entry: path.resolve(__dirname, "./src/index.js"),
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["babel-loader"],
      },
    ],
  },
  resolve: {
    extensions: ["*", ".js", ".jsx"],
  },
  output: {
    path: path.resolve(__dirname, "./dist"),
    filename: "bundle.js",
  },
  devServer: {
    contentBase: path.resolve(__dirname, "./dist"),
  },
};
```

6. ทำการ Run Project ด้วย `npm run start`

ึ7. ทำการลอง import css ไฟล์แล้วลองรันดู
