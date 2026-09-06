# 第 5 章 指针与数组（Pointers and Arrays）

> K&R 第 5 章学习笔记。代码路径均以仓库根目录为基准。

## 5.1 指针与地址 Pointers and Addresses
- 指针保存变量的地址；`&` 取地址，`*` 间接访问；`NULL`/0 表示空指针。
- 声明 `int *p;` 与使用 `*p` 的含义要分清。

## 5.2 指针与函数参数
- C 参数按值传递，想修改调用方变量必须传地址（指针），实现“引用”效果。
- 对应代码
  - `chapter-5-pointers-and-arrays/3.getint.c` —— 练习 5-1：`getint` 读入整数并回传（修正 `c = getch()` 边界）
  - `chapter-5-pointers-and-arrays/4.getfloat.c` —— 练习 5-2：扩展到 `getfloat`

## 5.3 指针与数组 Pointers and Arrays
- 数组名是常量指针（首元素地址）；`a[i]` 等价于 `*(a+i)`。
- 下标与指针可互换，但数组名本身不可再赋值。

## 5.4 地址算术 Address Arithmetic
- 指针加减整数按所指向类型大小步进；两指针相减得到元素个数差。
- 对应代码
  - `chapter-5-pointers-and-arrays/15.strcat-pointer.c` —— 练习 5-3：指针版 `strcat`
  - `chapter-5-pointers-and-arrays/16.strend.c` —— 练习 5-4：判断字符串是否以另一字符串结尾
  - `chapter-5-pointers-and-arrays/17.strncpy.c` / `18.strncat.c` / `19.strncmp.c` —— 练习 5-5：带长度限制的字符串库函数

## 5.5 字符指针与函数
- 字符串常量是字符数组；`char *p = "..."` 与 `char s[] = "..."` 的差异（是否可写）。

## 5.6 指针数组；指向指针的指针
- `char *lineptr[]` 是字符串指针数组；`**` 表示二级指针（如 `argv`）。
- 对应代码
  - `chapter-5-pointers-and-arrays/39.sort-with-r.c` —— 练习 5-14：排序支持 `-r` 逆序（函数指针做参数）
  - `chapter-5-pointers-and-arrays/40.sort-with-f.c` —— 练习 5-15：`-f` 忽略大小写
  - `chapter-5-pointers-and-arrays/41.sort-with-d.c` —— 练习 5-16：`-d` 仅比较字母数字（字典序）

## 5.7 多维数组 Multi-dimensional Arrays
- 二维数组按行存储；初始化、作为函数参数时列数必须给出。
- 对比“指针数组”与“二维数组”的布局差异。
- 对应代码
  - `chapter-5-pointers-and-arrays/24.pointer-arrays-without-alloc.c` —— 练习 5-7：用二维数组替代 `alloc` 存储文本行

## 5.8 指针数组的初始化
- 用指针数组组织一组字符串比二维数组更省空间、更灵活（`month_name` 例子）。
- 对应代码
  - `chapter-5-pointers-and-arrays/27.year-month-day-pointer.c` —— 练习 5-8/5-9：日期与年内第几天的互转（改用指针数组/指针算术）

## 5.10 命令行参数 Command-line Arguments
- `argc` 参数个数、`argv` 参数指针数组，`argv[0]` 是程序名。
- 对应代码
  - `chapter-5-pointers-and-arrays/32.expr.c` —— 练习 5-10：用命令行参数写逆波兰表达式求值
  - `chapter-5-pointers-and-arrays/33.detab.c` / `34.entab.c` —— 练习 5-11：命令行版 detab/entab
  - `chapter-5-pointers-and-arrays/35.detab-arg.c` / `36.entab-arg.c` —— 练习 5-12：带起止列表参数的版本
  - `chapter-5-pointers-and-arrays/37.tail.c` —— 练习 5-13：`tail` 打印最后 n 行

## 5.11 函数指针 Pointers to Functions
- 函数名是函数地址；`int (*cmp)(void*, void*)` 形式传递比较器实现通用排序。
- 对应代码：`39/40/41.sort-with-*.c`（`qsort` 与比较函数指针）

## 5.12 复杂声明 Complicated Declarations
- 用 `dcl` 程序解析声明；区分 `*p[]`（指针数组）与 `(*p)[]`（指向数组的指针）。
- 对应代码
  - `chapter-5-pointers-and-arrays/43.dcl-error-handle.c` —— 练习 5-18：`dcl` 增加错误处理
  - `chapter-5-pointers-and-arrays/44.undcl.c` —— 练习 5-19：`undcl` 反向转换声明文本

## 更多字符串/指针练习
- `chapter-5-pointers-and-arrays/20.getline-pointer.c` —— 练习 5-6：指针版 `getline`

---

✍️ 个人补充/疑问：
