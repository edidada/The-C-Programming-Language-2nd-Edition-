# 第 4 章 函数与程序结构（Functions and Program Structure）

> K&R 第 4 章学习笔记。代码路径均以仓库根目录为基准。

## 4.1 函数基础
- 返回值类型 + 函数名 + 形参表 + 函数体；调用前需要声明（原型）或定义。
- 旧式 C 默认返回 `int`（GCC 14 起会报错，本仓库构建已用 `-Wno-*` 兼容老代码）。
- 对应代码
  - `chapter-4-functions-and-program-structure/2.strrindex.c` —— 练习 4-1：返回模式串在字符串中最右出现位置

## 4.2 返回非整型的函数
- 返回 `double` 等类型必须显式声明；`atof` 是标准示例，强调“声明先于使用”。
- 对应代码
  - `chapter-4-functions-and-program-structure/3.atof-test.c` —— 练习 4-2：扩展 `atof`，支持科学计数法（`123.45e-6`）

## 4.3 外部变量 External Variables
- 多个函数通过共享外部变量协作；经典案例：逆波兰计算器。
- 对应代码
  - `chapter-4-functions-and-program-structure/4.reverse-polish-calculator.c` —— 练习 4-3~4-6：主循环 + 栈 + 运算符（`%`、`sin/exp/pow`、变量等）

## 4.4 作用域规则
- 变量作用域从声明处到文件尾；跨文件使用需 `extern` 声明。

## 4.5 头文件 Header Files
- 公共声明集中到头文件，多个 `.c` 用 `#include` 共享，避免声明不一致。
- 对应代码：`chapter-4-functions-and-program-structure/` 下 `getop.h` 之类头文件与源码分文件组织（逆波兰计算器多文件工程）

## 4.6 静态变量 Static Variables
- 文件内 `static` 限定外部链接为内部；函数内 `static` 变量跨调用保持值。
- 对应代码
  - `chapter-4-functions-and-program-structure/getch.c` —— 练习 4-7/4-8：`ungetch` 缓冲、回推一字符
  - `chapter-4-functions-and-program-structure/5.getop-with-static.c` —— 练习 4-11：`getop` 用 `static` 保存读入的多余字符

## 4.7 register 变量
- `register` 建议把变量放寄存器（现代编译器基本自动处理，保留语义为“不能取地址”）。

## 4.8 程序块结构 Block Structure
- C 无嵌套函数；程序块可声明局部变量，遮蔽外层同名变量。

## 4.9 初始化 Initialization
- 数组/变量初始化规则：不初始化时外部与 `static` 自动为 0，自动变量未初始化值不定。

## 4.10 递归 Recursion
- 函数直接/间接调用自身；递归必须有终止条件；与迭代互为补充。
- 对应代码
  - `chapter-4-functions-and-program-structure/9.itoa-recursive.c` —— 练习 4-12：递归实现 `itoa`
  - `chapter-4-functions-and-program-structure/10.reverse.recursive.c` —— 练习 4-13：递归实现字符串反转

## 4.11 C 预处理器
- `#include` 文件包含、`#define` 宏替换与带参宏、条件包含 `#if`/`#ifdef`/`#ifndef`。
- 带参宏注意括号与副作用，如 `#define max(A,B) ((A)>(B)?(A):(B))`。
- 对应代码
  - `chapter-4-functions-and-program-structure/11.swap-macro.c` —— 练习 4-14：定义 `swap(t,x,y)` 宏交换两变量
  - `chapter-4-functions-and-program-structure/12.conditional-inclusion.c` —— 条件编译示例

---

✍️ 个人补充/疑问：
