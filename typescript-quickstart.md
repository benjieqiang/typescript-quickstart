<!--
 * @Author: benjie
 * @Date: 2024-07-18 09:50:04
 * @LastEditTime: 2024-07-18 09:58:10
 * @LastEditors: benjie
 * @Description: 
-->
 # 1. intall
```
npm install -g typescript

benjie@MacBook-Pro ~ % tsc -v                   
Version 5.5.3


新建一个 app.ts 的文件，代码如下：

var message:string = "Hello World" 
console.log(message)

tsc app.ts
# app.ts -> app.js

benjie@MacBook-Pro test % tsc app.ts 
benjie@MacBook-Pro test % ls
app.js  app.ts
benjie@MacBook-Pro test % node app.js
Hello World
```