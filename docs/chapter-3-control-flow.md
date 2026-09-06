# 第 3 章 控制流（Control Flow）

> K&R 第 3 章学习笔记。代码路径均以仓库根目录为基准。

## 3.1 语句与程序块 Statements and Blocks
- 表达式后加分号即语句；`{ }` 把多条语句合成一个复合语句（程序块）。
- 声明可以出现在程序块开头，作用域限于块内。

## 3.2 if-else
- `else` 与最近的未配对 `if` 结合（悬挂 else 问题），必要时用 `{}` 明确归属。
- 分支内部尽量避免复杂的嵌套。
- 对应代码
  - `chapter-3-control-flow/01.binsearch.c` —— 练习 3-1：改进二分查找，循环内只测一次相等

## 3.3 else-if
- 用 `if / else if / else` 链表达多分支判定，优于深嵌套。
- 温度转换、字符分类等线性判断场景常用。

## 3.4 switch
- 按整型表达式值分发到 `case`；每个分支以 `break` 结束，否则贯穿（fall-through）。
- `default` 处理未匹配分支。
- 对应代码
  - `chapter-3-control-flow/03.escape.c`、`04.unescape.c` —— 练习 3-2：字符转义/还原（`\n` `\t` 等，switch 实现）

## 3.5 循环 Loops
- `while` / `for` / `do-while`：区别在“先判断”还是“先执行一次”。
- `for` 的三段表达式灵活；逗号运算符常用于初始化/更新多个变量。
- 对应代码
  - `chapter-3-control-flow/08.expand.c` —— 练习 3-3：展开 `a-z` 这类简写记法

## 3.6 break 与 continue
- `break` 立即退出最内层循环/switch；`continue` 跳到下一次循环。
- 用得好可减少标志变量（注意不要过度使用破坏可读性）。

## 3.7 goto 与标号
- `goto label` 提供无约束跳转；正常程序应避免，仅在跳出多层嵌套或统一收尾时偶尔有用。

## 数字转字符串练习
- `chapter-3-control-flow/09.itoa.c` —— 练习 3-4：`itoa` 正确处理 `INT_MIN`（绝对值溢出问题）
- `chapter-3-control-flow/10.itob.c` —— 练习 3-5：整数转任意进制（2–36）字符串
- `chapter-3-control-flow/11.itoa.c` —— 练习 3-6：`itoa` 支持最小宽度与右对齐填充

---

✍️ 个人补充/疑问：
