# 第 1 章 入门（Introduction）

> K&R 第 1 章学习笔记：先按书中小节记录知识点，再列出本仓库对应的练习代码。代码路径均以仓库根目录为基准。

## 1.1 起步 Getting Started
- C 程序由函数组成，执行入口是 `main`；语句以 `;` 结尾。
- `printf` 负责格式化输出；`#include <stdio.h>` 引入标准库声明。
- 对应代码
  - `chapter-1-introduction/1.hello.c` —— 练习 1-1：hello, world
  - `chapter-1-introduction/2.hello.c` —— 练习 1-2：输出 `\c`，观察未知转义序列的行为

## 1.2 变量与算术表达式 Variables and Arithmetic Expressions
- 数据类型 `int` / `float`；整型除法结果截断，混合类型运算发生自动转换。
- `while` 循环；`printf` 格式说明 `%d`、`%f` 与字段宽度。
- 对应代码
  - `chapter-1-introduction/5.celsius-fahrenheit-table.c` —— 练习 1-3/1-4：华氏-摄氏转换表（表头、浮点格式化对齐）
  - `chapter-1-introduction/7.fahrenheit-celsius-table-reverse.c` —— 练习 1-5：逆序输出转换表

## 1.3 for 语句 The For Statement
- `for (init; test; step)` 把循环控制集中在一行，比 `while` 更紧凑。
- 对应代码
  - 同上 `7.fahrenheit-celsius-table-reverse.c`（练习 1-5 用 `for` 实现逆序）

## 1.4 符号常量 Symbolic Constants
- `#define 名字 替换文本`：在编译前完成文本替换，避免“魔法数”。
- 经典写法 `#define LOWER 0`、`#define UPPER 300`、`#define STEP 20` 定义温度范围。

## 1.5 字符输入输出 Character Input and Output
- `getchar()` / `putchar()` 每次读写一个字符；文件结束返回 `EOF`。
- 复制输入的惯用法：`while ((c = getchar()) != EOF)`——`c` 需声明为 `int` 以容纳 `EOF`。
- 行计数、单词计数依赖“是否在一个单词内”这类状态变量（`in_word`）。
- 对应代码
  - `chapter-1-introduction/11.file-copying-3rd.c` —— 练习 1-6：验证 `getchar() != EOF` 的值
  - `chapter-1-introduction/12.print-eof.c` —— 练习 1-7：打印 `EOF` 的数值
  - `chapter-1-introduction/16.space-tab-line-counting.c` —— 练习 1-8：统计空格/制表符/换行
  - `chapter-1-introduction/17.repalce-multi-space.c` —— 练习 1-9：连续多个空格折叠为一个
  - `chapter-1-introduction/18.replace-tab-backspace-backslash.c` —— 练习 1-10：把不可见字符转成可见表示
  - `chapter-1-introduction/20.print-words.c` —— 练习 1-12：每行打印一个单词

## 1.6 数组 Arrays
- 用字符/整数作下标统计输入分布，是“数组作计数器”的典型场景。
- 对应代码
  - `chapter-1-introduction/22.words-length-histogram-horizontal.c`、`23.words-length-histogram-vertical.c` —— 练习 1-13：单词长度直方图（横/纵）
  - `chapter-1-introduction/24.characters-frequencies-histogram.c` —— 练习 1-14：字符频度直方图

## 1.7 函数 Functions
- 函数须先声明/定义再使用；练习 1-15 把温度转换改成函数调用。
- 对应代码
  - `chapter-1-introduction/26.fahrenheit-celsius-table-function.c` —— 练习 1-15：函数版温度表

## 1.8 参数——传值调用 Arguments: Call by Value
- C 函数参数按值传递；函数内修改形参不影响实参（除非传指针）。
- 对应代码
  - `26.fahrenheit-celsius-table-function.c`（参数按值传递的体现）

## 1.9 字符数组 Character Arrays
- 常用“读一行 + 拷贝 + 处理”的骨架：`getline` 负责读行，`copy` 负责保存。
- 对应代码
  - `chapter-1-introduction/28.print-input-line-and-text.c` —— 练习 1-16：打印最长行及长度
  - `chapter-1-introduction/29.print-length-80-line.c` —— 练习 1-17：打印超过 80 字符的行
  - `chapter-1-introduction/30.remove-line-end-space-and-tab.c` —— 练习 1-18：去掉行尾空格/Tab
  - `chapter-1-introduction/31.reverses.c` —— 练习 1-19：逐行反转字符顺序

## 1.10 外部变量与作用域 External Variables and Scope
- `extern` 声明引用其他位置定义的外部变量；合理使用文件作用域变量与函数。
- 本章文本工具类练习（综合前面知识点）：
  - `chapter-1-introduction/33.detab.c` —— 练习 1-20：制表符替换为空格
  - `chapter-1-introduction/34.entab.c` —— 练习 1-21：空格串替换为 Tab
  - `chapter-1-introduction/35.fold-line.c` —— 练习 1-22：超过 N 列折行
  - `chapter-1-introduction/36.remove-comments.c` —— 练习 1-23：删除 C 注释（字符串/字面量中除外）

---

✍️ 个人补充/疑问：
