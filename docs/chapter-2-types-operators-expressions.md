# 第 2 章 类型、运算符与表达式（Types, Operators and Expressions）

> K&R 第 2 章学习笔记。代码路径均以仓库根目录为基准。

## 2.1 变量名
- 标识符由字母/数字/下划线组成，不能以数字开头；关键字不可作变量名。
- 传统 C 中名称区分大小写，前 31 个字符有意义（标准并无强制，编译器相关）。

## 2.2 数据类型与大小
- 基础类型：`char`、`int`、`short`、`long`、`float`、`double`；`sizeof` 求大小（单位：字节）。
- 取值范围与机器相关，可查 `<limits.h>`、`<float.h>`。
- 对应代码
  - `chapter-2-types-operators-expressions/1.ranges-of-variables.c` —— 练习 2-1：确定并打印各类型取值范围

## 2.3 常量
- 整型/浮点/字符常量写法；字符常量是整数值；转义序列如 `\n` `\t`。
- 枚举常量（见第 4 章语法说明）、`#define` 命名的符号常量。

## 2.4 声明 Declarations
- 声明给出类型并可初始化，如 `int i = 0;`；建议声明时就近、初始化。

## 2.5 算术运算符
- `+ - * / %`；`%` 只能用于整型；除法的符号行为与机器有关。

## 2.6 关系与逻辑运算符
- 关系：`> >= < <=`；相等：`== !=`；逻辑：`&& || !`。
- `&&`、`||` 短路求值；表达式值非零即真。
- 对应代码
  - `chapter-2-types-operators-expressions/2.loop-without-logical-operators.c` —— 练习 2-2：不用 `&&`/`||` 重写循环条件

## 2.7 类型转换 Type Conversions
- 隐式转换与整型提升；赋值/表达式混合运算自动转换；`char`→`int` 常见陷阱（符号扩展）。
- 可显式 `(type)expr` 强制转换。
- 对应代码
  - `chapter-2-types-operators-expressions/3.atoi.c` —— 书本 atoi 示例：数字字符序列转整数（体现字符-整数转换）
  - 练习 2-3 要求扩展 `htoi`（十六进制字符串转整数），对比练习可自测

## 2.8 自增与自减
- `++i` 先增值后使用，`i++` 先用后增值；在表达式里的求值副作用需谨慎。

## 2.9 位运算符 Bitwise Operators
- 位运算符：`&`、`|`、`^`、`<<`、`>>`、`~`（单目取反）。
- 与逻辑运算符区分：`&` vs `&&`；移位、掩码、置位/清位/翻转是基础操作。
- 对应代码
  - `chapter-2-types-operators-expressions/11.setbits.c` —— 练习 2-6：`setbits` 把 n 位替换为另一数的位
  - `chapter-2-types-operators-expressions/12.invert.c` —— 练习 2-7：`invert` 翻转指定 n 位
  - `chapter-2-types-operators-expressions/13.rightrot.c` —— 练习 2-8：`rightrot` 循环右移
  - `chapter-2-types-operators-expressions/15.bitcount2.c` —— 练习 2-9：`x &= (x-1)` 快速统计 1 的位数

## 2.10 赋值运算符与表达式
- 复合赋值 `op=` 等价写法（如 `x *= 2`）；简洁且表达“更新”语义。

## 2.11 条件表达式 Conditional Expressions
- 三目运算符 `expr1 ? expr2 : expr3`；常与赋值/返回结合。
- 对应代码
  - `chapter-2-types-operators-expressions/16.lower2.c` —— 练习 2-10：用条件表达式改写 `lower`

## 2.12 优先级与求值顺序
- 优先级/结合性规则表；注意 `=` 与 `==`、`&` 与 `&&` 的优先级差异。
- 大多数运算符的求值顺序未定义，含副作用的表达式不要依赖顺序。

## 字符串处理练习
- `chapter-2-types-operators-expressions/8.squeeze2.c` —— 练习 2-4：删除 s1 中出现在 s2 的字符
- `chapter-2-types-operators-expressions/9.any.c` —— 练习 2-5：返回 s1 中任一 s2 字符首次出现位置

---

✍️ 个人补充/疑问：
