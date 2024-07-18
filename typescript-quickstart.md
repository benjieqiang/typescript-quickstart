<!--
 * @Author: benjie
 * @Date: 2024-07-18 09:50:04
 * @LastEditTime: 2024-07-18 17:33:15
 * @LastEditors: benjie
 * @Description: https://www.runoob.com/typescript/ts-install.html
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

# 2. 易混点
## 字符串
```typescript
let name: string = "Runoob"; 
let years: number = 5;
let words: string = `您好，今年是 ${ name } 发布 ${ years + 1} 周年`; // 反引号（`）来定义多行文本和内嵌表达式。
```
## null和undefined

// 启用 --strictNullChecks
let x: number | null | undefined;
x = 1; // 编译正确
x = undefined;    // 编译正确
x = null;    // 编译正确

## never类型
never 类型的变量只能被 never 类型所赋值，在函数中它通常表现为抛出异常或无法执行到终止点（例如无限循环）


## 声明变量
var [变量名] : [类型] = 值;


## swtich注意点
switch 语句中的 expression 是一个要被比较的表达式，可以是任何类型，包括基本数据类型（如 number、string、boolean）、对象类型（如 object、Array、Map）以及自定义类型（如 class、interface、enum）等。
在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号。
case 的 constant-expression 必须与 switch 中的变量 expression 具有相同或兼容的数据类型

## 函数入参
可选参数使用问号标识 ？,表示可有可无；

```typescript
function buildName(firstName: string, lastName: string) {
    return firstName + " " + lastName;
}
 
let result1 = buildName("Bob");                  // 错误，缺少参数
let result2 = buildName("Bob", "Adams", "Sr.");  // 错误，参数太多了
let result3 = buildName("Bob", "Adams");         // 正确

function buildName(firstName: string, lastName?: string) {
    if (lastName)
        return firstName + " " + lastName;
    else
        return firstName;
}
 
let result1 = buildName("Bob");  // 正确
let result2 = buildName("Bob", "Adams", "Sr.");  // 错误，参数太多了
let result3 = buildName("Bob", "Adams");  // 正确
```

## 剩余参数
一种情况，我们不知道要向函数传入多少个参数，这时候我们就可以使用剩余参数来定义。

剩余参数语法允许我们将一个不确定数量的参数作为一个数组传入。

```TypeScript
function buildName(firstName: string, ...restOfName: string[]) {
    return firstName + " " + restOfName.join(" ");
}
  
let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

## 类型断言 
在 TypeScript 中，`var drummer = <Musician>{};` 是一种类型断言 (Type Assertion) 的语法，用于告诉 TypeScript 编译器将一个对象视为特定的类型。在这个例子中，我们将一个空对象 `{}` 断言为类型 `Musician`。具体解释如下：

1. **`var`**: 用于声明一个变量。`var` 是一种变量声明的方式，范围在函数作用域内。现代 TypeScript 和 JavaScript 更推荐使用 `let` 或 `const`。

2. **`drummer`**: 这是变量的名称。我们将创建一个名为 `drummer` 的变量。

3. **`<Musician>`**: 这是类型断言的语法，表示我们断言（强制转换）这个对象为类型 `Musician`。类型断言告诉 TypeScript 编译器你比它更了解这个变量的类型。这里假设 `Musician` 是已经定义的一个接口或类。

4. **`{}`**: 这是一个空对象字面量。我们将这个空对象断言为 `Musician` 类型。

### 示例代码

假设我们有一个 `Musician` 接口，定义如下：

```typescript
interface Musician {
  name: string;
  instrument: string;
}
```

然后，我们可以使用类型断言来创建一个 `Musician` 类型的对象：

```typescript
var drummer = <Musician>{}; // 使用类型断言将空对象视为 Musician 类型
drummer.name = "John Bonham";
drummer.instrument = "Drums";
```

也可以使用另一种类型断言的语法：

```typescript
var drummer = {} as Musician; // 另一种类型断言的语法
drummer.name = "John Bonham";
drummer.instrument = "Drums";
```

### 解释
- **类型断言**：类型断言不会真的改变对象的结构或类型，它只是告诉编译器如何看待这个对象。在这个例子中，尽管 `{}` 是一个空对象，通过 `<Musician>` 或 `as Musician` 进行断言后，编译器会认为 `drummer` 具有 `Musician` 类型。
- **用途**：类型断言主要用于情况明确知道一个变量的类型，但编译器无法推断出来时。它能帮助避免不必要的类型错误提示，但也需要谨慎使用，因为错误的类型断言可能导致运行时错误。

总结：`var drummer = <Musician>{};` 使用类型断言将一个空对象视为 `Musician` 类型，使得编译器认为 `drummer` 是一个 `Musician` 类型的对象，这样就可以给它赋值 `name` 和 `instrument` 属性。
## 数组
```
var array_name[:datatype] = [val1,val2…valn]
var numlist:number[] = [2,4,6,8]

var sites:string[] = new Array("Google","Runoob","Taobao","Facebook") 
 
for(var i = 0;i<sites.length;i++) { 
        console.log(sites[i]) 
}
```

## Map
```typescript
let nameSiteMapping = new Map();
 
// 设置 Map 对象
nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);
 
// 获取键对应的值
console.log(nameSiteMapping.get("Runoob"));     // 2
 
// 判断 Map 中是否包含键对应的值
console.log(nameSiteMapping.has("Taobao"));       // true
console.log(nameSiteMapping.has("Zhihu"));        // false
 
// 返回 Map 对象键/值对的数量
console.log(nameSiteMapping.size);                // 3
 
// 删除 Runoob
console.log(nameSiteMapping.delete("Runoob"));    // true
console.log(nameSiteMapping);
// 移除 Map 对象的所有键/值对
nameSiteMapping.clear();             // 清除 Map
console.log(nameSiteMapping);

let nameSiteMapping = new Map();
 
nameSiteMapping.set("Google", 1);
nameSiteMapping.set("Runoob", 2);
nameSiteMapping.set("Taobao", 3);
 
// 迭代 Map 中的 key
for (let key of nameSiteMapping.keys()) {
    console.log(key);                  
}
 
// 迭代 Map 中的 value
for (let value of nameSiteMapping.values()) {
    console.log(value);                 
}
 
// 迭代 Map 中的 key => value
for (let entry of nameSiteMapping.entries()) {
    console.log(entry[0], entry[1]);   
}
 
// 使用对象解析
for (let [key, value] of nameSiteMapping) {
    console.log(key, value);            
}
```

## 存储不同类型元素，使用元组

var mytuple = [10,"Runoob"]; // 创建元组
console.log(mytuple[0]) 
console.log(mytuple[1])

## 声明联合类型
var val:string|number 
val = 12 
console.log("数字为 "+ val) 
val = "Runoob" 
console.log("字符串为 " + val)

## 接口（特有）
需要注意接口不能转换为 JavaScript。 它只是 TypeScript 的一部分。
继承使用关键字 extends。多接口继承使用，分割；

```typescript
interface IPerson { 
    firstName:string, 
    lastName:string, 
    sayHi: ()=>string 
} 
 
var customer:IPerson = { 
    firstName:"Tom",
    lastName:"Hanks", 
    sayHi: ():string =>{return "Hi there"} 
} 
 
console.log("Customer 对象 ") 
console.log(customer.firstName) 
console.log(customer.lastName) 
console.log(customer.sayHi())  
 
var employee:IPerson = { 
    firstName:"Jim",
    lastName:"Blakes", 
    sayHi: ():string =>{return "Hello!!!"} 
} 
 
console.log("Employee  对象 ") 
console.log(employee.firstName) 
console.log(employee.lastName)
```

## 类
注意方法的声明；
```ts
class Car { 
   // 字段
   engine:string; 
   
   // 构造函数
   constructor(engine:string) { 
      this.engine = engine 
   }  
   
   // 方法
   disp():void { 
      console.log("函数中显示发动机型号  :   "+this.engine) 
   } 
} 
 
// 创建一个对象
var obj = new Car("XXSY1")
 
// 访问字段
console.log("读取发动机型号 :  "+obj.engine)  
 
// 访问方法
obj.disp()
```

TypeScript 不支持继承多个类，但支持多重继承，类继承后，子类可以对父类的方法重新定义，这个过程称之为方法的重写。

## 对象：包含一组键值对的实例
值可以是标量、函数、数组、对象等，如下实例：

```ts
var object_name = { 
    key1: "value1", // 标量
    key2: "value",  
    key3: function() {
        // 函数
    }, 
    key4:["content1", "content2"] //集合
}

var sites = {
    site1: "Runoob",
    site2: "Google",
    sayHello: function () { } // 类型模板,想在对象中添加方法
};
sites.sayHello = function () {
    console.log("hello " + sites.site1);
};
sites.sayHello();
```

## 范型
TypeScript 中的泛型（Generics）是让函数、类或接口能够处理不同类型的一种方式，而无需指定具体的类型。泛型提供了一种在编写代码时可以在不同的类型之间进行复用的方法。下面是一些使用泛型的例子：

### 泛型函数

创建一个泛型函数，它可以处理任何类型的数据：

```typescript
function identity<T>(arg: T): T {
  return arg;
}

// 使用泛型函数
let output1 = identity<string>("Hello, TypeScript");
let output2 = identity<number>(123);

console.log(output1); // 输出: "Hello, TypeScript"
console.log(output2); // 输出: 123
```

在这个例子中，`identity` 函数接受一个类型参数 `T`，它表示传入参数的类型和返回值的类型是相同的。

### 泛型接口

可以使用泛型来定义接口：

```typescript
interface Pair<T, U> {
  first: T;
  second: U;
}

// 使用泛型接口
let pair: Pair<string, number> = { first: "Hello", second: 42 };

console.log(pair.first); // 输出: "Hello"
console.log(pair.second); // 输出: 42
```

在这个例子中，`Pair` 接口接受两个类型参数 `T` 和 `U`，它们分别表示 `first` 和 `second` 属性的类型。

### 泛型类

定义一个泛型类，用于创建能够处理不同类型数据的类：

```typescript
class Box<T> {
  contents: T;
  constructor(value: T) {
    this.contents = value;
  }

  getContents(): T {
    return this.contents;
  }
}

// 使用泛型类
let stringBox = new Box<string>("Hello, World");
console.log(stringBox.getContents()); // 输出: "Hello, World"

let numberBox = new Box<number>(123);
console.log(numberBox.getContents()); // 输出: 123
```

在这个例子中，`Box` 类接受一个类型参数 `T`，它表示 `contents` 属性的类型。

### 泛型约束

可以使用泛型约束来限制类型参数的类型：

```typescript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);
  return arg;
}

// 使用泛型约束的函数
logLength("Hello, TypeScript"); // 输出: 17
logLength([1, 2, 3]); // 输出: 3
// logLength(123); // 错误: 数字类型不具有 length 属性
```

在这个例子中，`logLength` 函数要求类型参数 `T` 必须具有 `length` 属性。

### 泛型与类型推断

TypeScript 能够根据传入的参数自动推断类型：

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity("Hello, TypeScript");
console.log(output); // 输出: "Hello, TypeScript"
```

在这个例子中，尽管没有显式指定类型参数，TypeScript 仍然能够推断出 `T` 的类型为 `string`。

### 泛型在数组中的使用

泛型可以用于数组的类型定义：

```typescript
function logArray<T>(arg: T[]): void {
  console.log(arg.length);
  arg.forEach(element => console.log(element));
}

// 使用泛型函数处理数组
logArray([1, 2, 3]); // 输出: 3, 1, 2, 3
logArray(["Hello", "World"]); // 输出: 2, "Hello", "World"
```

在这个例子中，`logArray` 函数接受一个类型参数 `T` 的数组，并打印数组的长度和每个元素。

## 命名空间
在 TypeScript 中，命名空间（Namespace）是一种将代码组织成逻辑组的方法，可以防止全局命名冲突。命名空间通常用于较大的应用程序中，用来将代码分离成不同的模块。以下是如何在项目中使用命名空间的示例：

### 创建和使用命名空间

#### Step 1: 定义命名空间

在一个单独的文件中定义命名空间，例如 `shapes.ts`：

```typescript
// shapes.ts
namespace Shapes {
  export class Circle {
    constructor(public radius: number) {}
    getArea(): number {
      return Math.PI * this.radius * this.radius;
    }
  }

  export class Square {
    constructor(public sideLength: number) {}
    getArea(): number {
      return this.sideLength * this.sideLength;
    }
  }
}
```

#### Step 2: 使用命名空间

在另一个文件中使用上述定义的命名空间，例如 `app.ts`：

```typescript
// app.ts
/// <reference path="shapes.ts" />

let circle = new Shapes.Circle(5);
console.log(`Circle area: ${circle.getArea()}`);

let square = new Shapes.Square(10);
console.log(`Square area: ${square.getArea()}`);
```

#### Step 3: 编译并运行

使用 `tsc` 编译 TypeScript 文件：

```bash
tsc --outFile app.js app.ts shapes.ts
```

上面的命令将 `app.ts` 和 `shapes.ts` 文件编译成一个单一的 `app.js` 文件。然后在 HTML 文件中引用生成的 `app.js` 文件。

### 示例项目结构

假设项目结构如下：

```
project/
├── app.ts
├── shapes.ts
└── index.html
```

`index.html` 文件内容：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>TypeScript Namespaces</title>
</head>
<body>
    <script src="app.js"></script>
</body>
</html>
```

### 示例完整代码

#### shapes.ts

```typescript
namespace Shapes {
  export class Circle {
    constructor(public radius: number) {}
    getArea(): number {
      return Math.PI * this.radius * this.radius;
    }
  }

  export class Square {
    constructor(public sideLength: number) {}
    getArea(): number {
      return this.sideLength * this.sideLength;
    }
  }
}
```

#### app.ts

```typescript
/// <reference path="shapes.ts" />

let circle = new Shapes.Circle(5);
console.log(`Circle area: ${circle.getArea()}`);

let square = new Shapes.Square(10);
console.log(`Square area: ${square.getArea()}`);
```

### 编译和运行

在命令行中执行以下命令编译 TypeScript 文件：

```bash
tsc --outFile app.js app.ts shapes.ts
```

然后打开 `index.html` 文件，你应该可以在浏览器控制台中看到以下输出：

```
Circle area: 78.53981633974483
Square area: 100
```

### 说明

1. **定义命名空间**：`shapes.ts` 文件中定义了 `Shapes` 命名空间，并在其中导出了 `Circle` 和 `Square` 类。
2. **使用命名空间**：在 `app.ts` 文件中，通过 `/// <reference path="shapes.ts" />` 引用 `shapes.ts`声明文件，并使用 `Shapes.Circle` 和 `Shapes.Square` 来创建对象。
3. **编译**：通过 `tsc` 编译器将 TypeScript 文件编译成一个 JavaScript 文件。
4. **运行**：在 HTML 文件中引用编译后的 JavaScript 文件，并在浏览器中查看结果。

命名空间在大型应用程序中非常有用，可以帮助组织和管理代码，同时避免全局命名冲突。

## 声明文件
在 TypeScript 中，模块（Module）是一种将代码组织成独立文件的方法，每个文件都是一个模块。模块可以导出类、函数、变量和接口，其他模块可以通过导入这些导出来使用。

以下是如何在项目中使用 TypeScript 模块的示例：

### Step 1: 创建和导出模块

创建一个名为 `shapes.ts` 的文件，定义和导出一些类：

```typescript
// shapes.ts
export class Circle {
  constructor(public radius: number) {}
  getArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

export class Square {
  constructor(public sideLength: number) {}
  getArea(): number {
    return this.sideLength * this.sideLength;
  }
}
```

### Step 2: 导入并使用模块

在另一个文件中导入并使用这些类，例如 `app.ts`：

```typescript
// app.ts
import { Circle, Square } from './shapes';

let circle = new Circle(5);
console.log(`Circle area: ${circle.getArea()}`);

let square = new Square(10);
console.log(`Square area: ${square.getArea()}`);
```

### Step 3: 编译并运行

使用 `tsc` 编译 TypeScript 文件。首先，确保你的 `tsconfig.json` 文件正确配置：

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es5",
    "outDir": "./dist"
  },
  "include": ["./src/**/*"]
}
```

将源文件放在 `src` 文件夹中，编译输出到 `dist` 文件夹。目录结构如下：

```
project/
├── src/
│   ├── app.ts
│   └── shapes.ts
├── dist/
│   └── (compiled JavaScript files)
├── tsconfig.json
└── index.html
```

编译 TypeScript 文件：

```bash
tsc
```

在 `index.html` 文件中引用生成的 JavaScript 文件：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>TypeScript Modules</title>
</head>
<body>
    <script src="dist/app.js"></script>
</body>
</html>
```

### 示例完整代码

#### src/shapes.ts

```typescript
export class Circle {
  constructor(public radius: number) {}
  getArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

export class Square {
  constructor(public sideLength: number) {}
  getArea(): number {
    return this.sideLength * this.sideLength;
  }
}
```

#### src/app.ts

```typescript
import { Circle, Square } from './shapes';

let circle = new Circle(5);
console.log(`Circle area: ${circle.getArea()}`);

let square = new Square(10);
console.log(`Square area: ${square.getArea()}`);
```

#### tsconfig.json

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es5",
    "outDir": "./dist"
  },
  "include": ["./src/**/*"]
}
```

#### index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>TypeScript Modules</title>
</head>
<body>
    <script src="dist/app.js"></script>
</body>
</html>
```

### 说明

1. **创建和导出模块**：`shapes.ts` 文件中定义了 `Circle` 和 `Square` 类，并使用 `export` 关键字导出它们。
2. **导入模块**：在 `app.ts` 文件中，通过 `import { Circle, Square } from './shapes';` 导入 `shapes.ts` 文件中导出的类。
3. **编译**：通过 `tsc` 命令将 TypeScript 文件编译成 JavaScript 文件，并输出到 `dist` 文件夹。
4. **运行**：在 HTML 文件中引用编译后的 JavaScript 文件，并在浏览器中查看结果。

这种模块化的代码组织方式有助于提高代码的可维护性和可重用性，同时避免了全局命名冲突。


# react prop
在 React 中，**prop** 是指用于在组件之间传递数据的一种机制。它是从父组件向子组件传递数据的方式之一。

### 概述

1. **什么是 Prop：**
   - Prop 是 React 中组件之间通信的一种方式，用于从一个组件（父组件）向另一个组件（子组件）传递数据。

2. **用法：**
   - 在使用组件时，可以像使用 HTML 属性一样传递 props 给组件。

3. **传递数据：**
   - 父组件可以通过 props 向子组件传递任何类型的数据，包括字符串、数字、对象、函数等。

### 示例

假设有一个简单的父组件和子组件的例子，演示如何使用 prop 传递数据：

```jsx
// ParentComponent.js

import React from 'react';
import ChildComponent from './ChildComponent';

function ParentComponent() {
  const data = {
    name: 'John',
    age: 30,
  };

  return (
    <div>
      <h1>Parent Component</h1>
      <ChildComponent data={data} />
    </div>
  );
}

export default ParentComponent;
```

```jsx
// ChildComponent.js

import React from 'react';

function ChildComponent(props) {
  // props.data 包含父组件传递过来的数据
  const { name, age } = props.data;

  return (
    <div>
      <h2>Child Component</h2>
      <p>Name: {name}</p>
      <p>Age: {age}</p>
    </div>
  );
}

export default ChildComponent;
```

### 解释

- **ParentComponent：**
  - 定义了一个名为 `data` 的对象，包含 `name` 和 `age` 字段。
  - 将 `data` 作为 prop 传递给 `ChildComponent`。

- **ChildComponent：**
  - 接收一个 `props` 参数，其中包含从父组件传递过来的数据。
  - 使用解构赋值从 `props.data` 中提取 `name` 和 `age`。
  - 渲染 `name` 和 `age`。

### 要点

- **单向数据流：** Prop 是单向传递的，即只能从父组件向子组件传递数据，子组件不能直接修改 props。
- **命名约定：** 通常，props 的名称在组件中以对象的形式传递，并按照惯例使用 `props` 这个名称。
- **动态传递：** Props 可以是动态的，这意味着你可以根据需要在父组件中更改数据，并将新的数据传递给子组件。

在 React 中，props 是非常重要的概念，它允许你构建可复用、灵活和可组合的组件，从而更好地管理和组织你的应用程序。

#  React 中的 `useState` 钩子

这段代码使用了 React 中的 `useState` 钩子来创建一个名为 `squares` 的状态变量以及一个名为 `setSquares` 的函数，用于更新这个状态变量。让我们逐步解释这段代码的含义：

### 解释

1. **useState 钩子：**
   - `useState` 是 React 提供的一个钩子，用于在函数组件中添加状态管理能力。
   - 它接收一个初始状态作为参数，并返回一个包含当前状态值和更新状态的函数的数组。

2. **初始状态：**
   - `Array(9).fill(null)` 创建了一个包含 9 个元素的数组，并将每个元素初始化为 `null`。
   - 这个数组作为 `useState` 的初始状态，因此 `squares` 的初始值为 `[null, null, null, null, null, null, null, null, null]`。

3. **解构赋值：**
   - `const [squares, setSquares] = useState(Array(9).fill(null));` 使用了解构赋值语法，将 `useState` 返回的数组中的第一个元素赋值给 `squares`，将第二个元素赋值给 `setSquares`。
   - `squares` 是当前的状态值，即包含 9 个 `null` 的数组。
   - `setSquares` 是一个函数，用于更新 `squares` 的值。

### 使用场景

这段代码常用于游戏开发中，如井字棋（Tic-Tac-Toe）游戏的初始化。通过使用 `useState`，可以在组件中管理游戏板的状态，使得每个方格的状态（如为空、被玩家 X 或玩家 O 占据）可以动态地更新和渲染。

### 示例

以下是一个简单的示例，展示了如何在 React 中使用 `useState` 来管理井字棋游戏的方格状态：

```jsx
import React, { useState } from 'react';

function TicTacToe() {
  const [squares, setSquares] = useState(Array(9).fill(null));

  const handleClick = (index) => {
    if (squares[index] === null) {
      const newSquares = [...squares]; // 创建一个副本，确保不直接修改原始数组
      newSquares[index] = 'X'; // 在点击的方格上放置 'X'
      setSquares(newSquares); // 更新状态
    }
  };

  return (
    <div className="board">
      {squares.map((value, index) => (
        <button key={index} onClick={() => handleClick(index)}>
          {value}
        </button>
      ))}
    </div>
  );
}

export default TicTacToe;
```

### 总结

使用 `useState(Array(9).fill(null))` 初始化了一个包含 9 个方格状态的数组，并提供了一个 `setSquares` 函数来更新这些状态。这种模式是 React 中常见的状态管理方式，非常适合用于动态更新和渲染 UI。