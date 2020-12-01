### Setup Webpack From Scratch

1. สร้าง Folder ชื่อว่า `intro-to-webpack`

2. จากนั้นทำการใช้คำสั่ง `npm init -y` เพื่อจะได้จัดการ Packages ต่าง ๆ ได้ภายใน Project

3. ทำการ Install Dependencies ของ Webpack ดังนี้

```
npm install --save-dev webpack webpack-dev-server webpack-cli
```

4. สร้าง Folder และ Files ตามนี้

```
  - /dist
    - index.html
  - /src
    - helpers.js
    - index.js
```

5. ในไฟล์ index.html เขียน Code ตามนี้

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello Webpack</title>
  </head>
  <body>
    <h1>Hello Webpack</h1>
    <script src="./bundle.js"></script>
  </body>
</html>
```

6. ใน helpers.js เขียน Code ตามนี้

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

7. ทำการ import subtract และ add function เข้ามาลองใช้ดูในไฟล์ index.js

```javascript
import { add, subtract } from "./helpers";

const addResults = add(20, 1);
const subtractResults = subtract(20, 1);

console.log("hello word");
console.log("addResults: ", addResults);
console.log("subtractResults: ", subtractResults);
```

8. ทำการสร้างไฟล์ webpack.config.js ขึ้นมาแล้วเขียน Config ตามนี้

```javascript
const path = require("path");

module.exports = {
  entry: path.resolve(__dirname, "./src/index.js"),
  output: {
    path: path.resolve(__dirname, "./dist"),
    filename: "bundle.js",
  },
  devServer: {
    contentBase: path.resolve(__dirname, "./dist"),
  },
};
```

9. ทำการ Setup script ใน package.json

```json
...
  "scripts": {
    "start": "webpack serve --mode development",
    "build": "webpack --mode production"
  }
...
```

10. ทำการ Run Project ด้วยคำสั่งทั้งสองแล้วลองสังเกตผลดู

```
npm run start
```

และ

```
npm run build
```
