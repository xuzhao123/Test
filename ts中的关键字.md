---
title: ts中的关键字
categories: js
---

## 基础
* interface：接口
* type：类型别名，和interface不同的是可以作用于原始值，联合类型，元组以及其它任何你需要手写的类型。
* extends
	1. 用在接口，类之间表示接口，类之前的的继承关系
	2. 用在类型推断时候的约束关系
* keyof：索引类型查询操作符，keyof T的结果为 T上已知的公共属性名的联合
* T[K]：索引访问操作符，表示取T中K的属性
* in: P in K表示P是K中的一个属性，常用：P in keyof T
* &：交叉类型
* |： 联合类型
## Readonly
**Readonly\<T\>** 将T这个类型中的属性全都变成只读
```js
/**
 * Make all properties in T readonly
 */
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};
```
## Partial
**Partial\<T\>** 将T这个类型中的属性全都变成可选项
```js
/**
 * Make all properties in T optional
 */
type Partial<T> = {
    [P in keyof T]?: T[P];
};
```
## Pick
**Pick<T, K extends keyof T>** 在T中选取K作为子属性
```js
/**
 * From T, pick a set of properties whose keys are in the union K
 */
type Pick<T, K extends keyof T> = {
    [P in K]: T[P];
};
```
## Record
**Record<K extends keyof any, T>** 将K中所有的属性全都转化成T
```js
/**
 * Construct a type with a set of properties K of type T
 */
type Record<K extends keyof any, T> = {
    [P in K]: T;
};
```
## Exclude
**Exclude<T, U>** 从T中剔除可以赋值给U的类型
```js
/**
 * Exclude from T those types that are assignable to U
 */
type Exclude<T, U> = T extends U ? never : T;
```
## Extract
**Extract<T, U>**  提取T中可以赋值给U的类型
```js
/**
 * Extract from T those types that are assignable to U
 */
type Extract<T, U> = T extends U ? T : never;
```
## NonNullable
**NonNullable\<T\>**  从T中剔除null和undefined
```js
  /**
 * Exclude null and undefined from T
 */
type NonNullable<T> = T extends null | undefined ? never : T;
```
## ReturnType
**ReturnType\<T\>** 获取函数返回值类型
```js
/**
 * Obtain the return type of a function type
 */
type ReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any;
```
注：infer也是一个关键词，意思就是反解出的类型变量 R，上例中就是反解除了返回值的类型R
## InstanceType
**InstanceType\<T\>**  获取构造函数类型的实例类型。
```js
/**
 * Obtain the return type of a constructor function type
 */
type InstanceType<T extends new (...args: any) => any> = T extends new (...args: any) => infer R ? R : any;
```