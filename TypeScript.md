# TypeScript

## TypeScript 教程 - 阮一峰

## Enum

Enum 结构的特别之处在于，它既是一种类型，也是一个值。绝大多数 TypeScript 语法都是类型语法，编译后会全部去除，但是 Enum 结构是一个值，编译后会变成 JavaScript 对象，留在代码中。(很大程度上，Enum 结构可以被对象的 as const 断言替代。)

Enum 结构比较适合的场景是，成员的值不重要，名字更重要，从而增加代码的可读性和可维护性。

Enum 成员默认不必赋值，系统会从零开始逐一递增，按照顺序为每个成员赋值，比如 0、1、2……
Enum 成员值都是只读的，不能重新赋值。

多个同名的 Enum 结构会自动合并。

## 类型断言

TypeScript 提供了“类型断言”这样一种手段，允许开发者在代码中“断言”某个值的类型，告诉编译器此处的值是什么类型。TypeScript 一旦发现存在类型断言，就不再对该值进行类型推断，而是直接采用断言给出的类型。

类型断言并不是真的改变一个值的类型，而是提示编译器，应该如何处理这个值。

类型断言的一大用处是，指定 unknown 类型的变量的具体类型。

类型断言要求实际的类型与断言的类型兼容，实际类型可以断言为一个更加宽泛的类型（父类型），也可以断言为一个更加精确的类型（子类型），但不能断言为一个完全无关的类型。

如果真的要断言成一个完全无关的类型，也是可以做到的。那就是连续进行两次类型断言，先断言成 unknown 类型或 any 类型，然后再断言为目标类型。因为 any 类型和 unknown 类型是所有其他类型的父类型，所以可以作为两种完全无关的类型的中介。

```js
// 或者写成 <T><unknown>expr
expr as unknown as T
```

## TypeScript 入门教程 - xcatliu

### 简介

TypeScript 的核心设计理念：在完整保留 JavaScript 运行时行为的基础上，通过引入静态类型系统来提高代码的可维护性，减少可能出现的 bug。

#### 什么是 TypeScript？

> - TypeScript 是添加了类型系统的 JavaScript，适用于任何规模的项目。
> - TypeScript 是一门静态类型、弱类型的语言。
> - TypeScript 是完全兼容 JavaScript 的，它不会修改 JavaScript 运行时的特性。
> - TypeScript 可以编译为 JavaScript，然后运行在浏览器、Node.js 等任何能运行 JavaScript 的环境中。
> - TypeScript 拥有很多编译选项，类型检查的严格程度由你决定。
> - TypeScript 可以和 JavaScript 共存，这意味着 JavaScript 项目能够渐进式的迁移到 TypeScript。
> - TypeScript 增强了编辑器（IDE）的功能，提供了代码补全、接口提示、跳转到定义、代码重构等能力。
> - TypeScript 拥有活跃的社区，大多数常用的第三方库都提供了类型声明。
> - TypeScript 与标准同步发展，符合最新的 ECMAScript 标准（stage 3）。

### 原始数据类型

- **原始数据类型**包括：布尔值、数值、字符串、null、undefined 以及 ES6 中的新类型 Symbol 和 ES10 中的新类型 BigInt。

- JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 **void** 表示没有任何返回值的函数。

```ts
function alertName(): void {
  alert("My name is Tom");
}
```

- **undefined 和 null** 是所有类型的子类型
- **任意值**（Any）用来表示允许赋值为任意类型。声明一个变量为任意值之后，对它的任何操作，返回的内容的类型都是任意值。
- TypeScript 会在没有明确的指定类型的时候推测出一个类型，这就是**类型推论**。如果定义的时候没有赋值，不管之后有没有赋值，都会被推断成 any 类型而完全不被类型检查。
- **联合类型**（Union Types）表示取值可以为多种类型中的一种,使用 | 分隔每个类型。

### 对象的类型 —— 接口

在 TypeScript 中，我们使用接口（Interfaces）来定义对象的类型。

在面向对象语言中，接口（Interfaces）是一个很重要的概念，它是对行为的抽象，而具体如何行动需要由类（classes）去实现（implement）。

TypeScript 中的接口是一个非常灵活的概念，除了可用于对类的一部分行为进行抽象以外，也常用于对「对象的形状（Shape）」进行描述。赋值的时候，变量的形状必须和接口的形状保持一致。

```ts
interface Person {
  name: string; // 确定属性
  age?: number; // 可选属性
  [propName: string]: any; // 任意属性，确定属性和可选属性的类型都必须是它的类型的子集
  readonly id: number; // 只读属性，只读的约束存在于第一次给对象赋值的时候，而不是第一次给只读属性赋值的时候
}

let tom: Person = {
  name: "Tom",
  gender: "male",
};
```

### 数组的类型

「类型 + 方括号」表示法:

```ts
let fibonacci: number[] = [1, 1, 2, 3, 5]; //数字类型的数组
```

我们也可以使用数组泛型（Array Generic） Array<elemType> 来表示数组：

```ts
let fibonacci: Array<number> = [1, 1, 2, 3, 5];
```

### 函数的类型

函数声明的类型定义较简单，输入多余的（或者少于要求的）参数，是不被允许的。

```ts
function sum(x: number, y: number): number {
  return x + y;
}
```

函数表达式类型定义较复杂，`=>` 用来表示函数的定义，左边是输入类型，需要用括号括起来，右边是输出类型。

```ts
let mySum: (x: number, y: number) => number = function (
  x: number,
  y: number
): number {
  return x + y;
};
```

### 用接口定义函数的形状

我们也可以使用接口的方式来定义一个函数需要符合的形状：

```ts
interface SearchFunc {
  (source: string, subString: string): boolean;
}

let mySearch: SearchFunc;
mySearch = function (source: string, subString: string) {
  return source.search(subString) !== -1;
};
```

采用函数表达式|接口定义函数的方式时，对等号左侧进行类型限制，可以保证以后对函数名赋值时保证参数个数、参数类型、返回值类型不变。

```ts
// 参数默认值，可选参数，剩余参数
function buildName(
  firstName: string,
  lastName: string = "Cat",
  age?: number,
  ...items: any[]
) {}
```

### 类型断言

类型断言（Type Assertion）可以用来手动指定一个值的类型,语法：`值 as 类型` 或 `<类型>值`

- 将一个联合类型断言为其中一个类型
- 将一个父类断言为更加具体的子类
- 将任何一个类型断言为`any`
- 将 `any` 断言为一个具体的类型

### 声明文件

- declare var 声明全局变量
- declare function 声明全局方法
- declare class 声明全局类
- declare enum 声明全局枚举类型
- declare namespace 声明（含有子属性的）全局对象
- interface 和 type 声明全局类型
- export 导出变量
- export namespace 导出（含有子属性的）对象
- export default ES6 默认导出
- export = commonjs 导出模块
- export as namespace UMD 库声明全局变量
- declare global 扩展全局变量
- declare module 扩展模块
- /// <reference /> 三斜线指令

声明文件必需以 .d.ts 为后缀。一般来说，ts 会解析项目中所有的 _.ts 文件，当然也包含以 .d.ts 结尾的文件。所以当我们将 jQuery.d.ts 放到项目中时，其他所有 _.ts 文件就都可以获得 jQuery 的类型定义了。

### 类型别名

类型别名用来给一个类型起个新名字。

```ts
type Name = string;
type NameResolver = () => string;
type NameOrResolver = Name | NameResolver;
function getName(n: NameOrResolver): Name {
  if (typeof n === "string") {
    return n;
  } else {
    return n();
  }
}
```

上例中，我们使用 type 创建类型别名。，别名常用于联合类型。

### 字符串字面量

字符串字面量类型用来约束取值只能是某几个字符串中的一个。

```ts
type EventNames = "click" | "scroll" | "mousemove";
function handleEvent(ele: Element, event: EventNames) {
  // do something
}

handleEvent(document.getElementById("hello"), "scroll"); // 没问题
handleEvent(document.getElementById("world"), "dblclick"); // 报错，event 不能为 'dblclick'
```

注意：类型别名与字符串字面量类型都是使用 type 进行定义。

### 元组

数组合并了相同类型的对象，而元组（Tuple）合并了不同类型的对象。

```ts
// 定义一对值分别为 string 和 number 的元组
let tom: [string, number] = ["Tom", 25];
```

### 枚举
