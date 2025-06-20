# RUST特征小议

## 泛型小议

Rust是一门以泛型为基础的语言。其他语言不使用泛型也不会影响编程，泛型仅是这些语言的强大语法工具之一；而Rust离开泛型就无法编写程序，泛型与语法共生。

1. 强制使用泛型，需要在设计时考虑适配所有类型，这样才能具有良好的可扩展性。
2. 使用泛型约束，要求必须抽象出接口关系才能进行代码实现，这样才能产生更多的思考和更好的模块设计。

## Rust内存安全杂述



Rust是一门内存安全语言，但Rust的编译器仅提供了有限的安全特性。

- 明确的安全类型

1. 变量必须初始化之后才能使用。
2. 引用必须是内存对齐的，引用指向的变量必须已经初始化。
3. 模块成员默认为私有，结构成员对模块外代码默认为私有。
4. 严格的类型及类型无效值。
5. 基本类型都满足Copy、Send、Sync等AutoTrait。
6. 线程间转移变量必须支持Send，线程间共享变量必须支持Sync。
7. if及match必须覆盖所有分支条件。

- 明确的不安全特性

1. 裸指针解引用。
2. 支持所有FFI（调用C语言函数）调用、unsafe固有函数调用。
3. 对类型产生无效类型值。
4. 嵌入式汇编使用

- 为安全提供的语法工具

1. 编译器提供的特性包括所有权、生命周期、自动调用DropTrait。
2. 自动解引用。

## 获取封装类型变量的内部变量

### 使用“?”运算符解封装

实现`Try Trait`的封装类型，可以使用“？”运算符进行解封装并完成异常处理。



