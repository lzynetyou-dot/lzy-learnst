# TypeScript 语法要点总结

TypeScript 是 JavaScript 的超集，主要为 JS 增加了静态类型系统和现代 ECMAScript 特性。以下是 TypeScript 的核心语法与关键特性总结。

---

## 1. 基础类型与类型声明

### 1.1 原始类型与常见类型
```typescript
// 基础原始类型
let isDone: boolean = false;
let age: number = 30;
let name: string = "Alice";
let u: undefined = undefined;
let n: null = null;
let s: symbol = Symbol("key");
let big: bigint = 100n;

// 数组 (Array)
let list1: number[] = [1, 2, 3];
let list2: Array<number> = [1, 2, 3]; // 泛型写法

// 元组 (Tuple): 固定长度和类型的数组
let tuple: [string, number] = ["hello", 10];

// Any, Unknown, Void, Never
let randomValue: any = 4; // 禁用类型检查
let unknownValue: unknown = 4; // 安全的 any，使用前必须进行类型缩小

function logMessage(): void { // 无返回值
  console.log("Log");
}

function throwError(): never { // 永不返回（抛出异常或死循环）
  throw new Error("Error");
}
```

### 1.2 枚举 (Enum)
```typescript
// 数字枚举（默认从 0 开始自增）
enum Direction {
  Up = 1,
  Down,
  Left,
  Right
}

// 字符串枚举
enum Status {
  Success = "SUCCESS",
  Fail = "FAIL"
}
```

---

## 2. 接口与类型别名

### 2.1 接口 (Interface)
用于定义对象的结构与契约。

```typescript
interface User {
  readonly id: number; // 只读属性
  name: string;
  age?: number;        // 可选属性
  [key: string]: any;  // 字符串索引签名（允许任意额外属性）
}

// 接口继承
interface VIPUser extends User {
  vipLevel: number;
}
```

### 2.2 类型别名 (Type Alias)
为类型创造新名字，支持联合类型、元组等复杂类型。

```typescript
type ID = string | number;

type Point = {
  x: number;
  y: number;
};
```

### 2.3 `interface` vs `type`
*   **Interface：** 声明合并（多次声明自动合并），擅长描述对象结构和 OOP 继承。
*   **Type Alias：** 支持联合类型、交叉类型、元组、基本类型别名，更为灵活。

---

## 3. 高级类型与类型运算符

### 3.1 联合类型与交叉类型
```typescript
// 联合类型 (Union Types): 或
type Status = "pending" | "fulfilled" | "rejected";

// 交叉类型 (Intersection Types): 与
type Person = { name: string };
type Employee = { id: number };
type Staff = Person & Employee;
```

### 3.2 字面量类型与类型守卫
```typescript
// 字面量类型
type Action = "click" | "hover";

// 类型守卫 (Type Guards)
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // 此分支下 id 类型缩小为 string
  } else {
    console.log(id); // 此分支下 id 类型缩小为 number
  }
}

// 自定义类型守卫 (is 关键字)
function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}
```

### 3.3 类型断言 (Type Assertion)
```typescript
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
// 尖括号语法（与 JSX 冲突，较少使用）
const someValue = <string>"this is a string";
```

---

## 4. 函数 (Functions)

```typescript
// 函数声明与类型注记
function add(x: number, y: number): number {
  return x + y;
}

// 可选参数与默认参数
function buildName(firstName: string, lastName?: string, prefix = "Mr."): string {
  return `${prefix} ${firstName} ${lastName ?? ""}`;
}

// 剩余参数
function sum(...numbers: number[]): number {
  return numbers.reduce((total, n) => total + n, 0);
}

// 函数重载 (Overloads)
function makeDate(timestamp: number): Date;
function makeDate(m: number, d: number, y: number): Date;
function makeDate(mOrTimestamp: number, d?: number, y?: number): Date {
  if (d !== undefined && y !== undefined) {
    return new Date(y, mOrTimestamp, d);
  } else {
    return new Date(mOrTimestamp);
  }
}
```

---

## 5. 类与面向对象编程 (Classes)

```typescript
class Animal {
  // 修饰符: public (默认), private (私有), protected (受保护)
  public name: string;
  private age: number;
  protected species: string;

  constructor(name: string, age: number, species: string) {
    this.name = name;
    this.age = age;
    this.species = species;
  }
}

// 参数属性简写语法
class Person {
  constructor(public name: string, private secret: string) {}
}

// 抽象类与抽象方法
abstract class Shape {
  abstract getArea(): number;
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }
  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
}
```

---

## 6. 泛型 (Generics)

泛型允许在定义接口、类或函数时不预先指定具体类型，而在使用时再指定。

```typescript
// 泛型函数
function identity<T>(arg: T): T {
  return arg;
}

// 泛型接口
interface GenericIdentityFn<T> {
  (arg: T): T;
}

// 泛型类
class GenericNumber<T> {
  zeroValue!: T;
  add!: (x: T, y: T) => T;
}

// 泛型约束 (Generic Constraints)
interface Lengthwise {
  length: number;
}
function loggingIdentity<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);
  return arg;
}

// 在泛型约束中使用 keyof
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}
```

---

## 7. 工具类型 (Utility Types)

TS 内置了许多开箱即用的类型工具：

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

// 1. Partial<T>: 将所有属性变为可选
type PartialTodo = Partial<Todo>;

// 2. Required<T>: 将所有属性变为必填
type RequiredTodo = Required<PartialTodo>;

// 3. Readonly<T>: 将所有属性变为只读
type ReadonlyTodo = Readonly<Todo>;

// 4. Pick<T, K>: 挑选部分属性
type TodoPreview = Pick<Todo, "title" | "completed">;

// 5. Omit<T, K>: 排除部分属性
type TodoInfo = Omit<Todo, "description">;

// 6. Record<K, T>: 构建键为 K、值为 T 的映射类型
type PageInfo = Record<"home" | "about", { title: string }>;

// 7. Extract<T, U> / Exclude<T, U>: 联合类型的交集与差集
type T0 = Exclude<"a" | "b" | "c", "a">; // "b" | "c"
type T1 = Extract<"a" | "b" | "c", "a" | "f">; // "a"

// 8. ReturnType<T>: 获取函数返回值的类型
type Func = () => number;
type R = ReturnType<Func>; // number
```

---

## 8. 高级类型编程技巧

### 8.1 映射类型 (Mapped Types) & 条件类型 (Conditional Types)
```typescript
// 条件类型
type IsString<T> = T extends string ? true : false;

// 映射类型
type Flags<T> = {
  [K in keyof T]: boolean;
};

// infer 关键字（在条件类型中推断类型）
type UnpackArray<T> = T extends (infer U)[] ? U : T;
type Num = UnpackArray<number[]>; // number
```

### 8.2 模板字面量类型 (Template Literal Types)
```typescript
type Event = "click" | "hover";
type EventHandler = `on${Capitalize<Event>}`; // "onClick" | "onHover"
```