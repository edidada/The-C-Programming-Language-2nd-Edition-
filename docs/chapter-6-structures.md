# 第 6 章 结构（Structures）

> K&R 第 6 章学习笔记。代码路径均以仓库根目录为基准。

## 6.1 结构基础
- 结构把相关数据聚合：`struct point { int x, y; };`
- 用 `.` 访问成员；结构可整体赋值、作参数（按值拷贝）、作返回值。
- 对应代码
  - `chapter-6-structures/1.structures-and-functions.c` —— 结构与函数的示例（矩形/点运算）

## 6.2 结构与函数 Structures and Functions
- 结构作参数按值传递，函数内修改不影响调用方；大结构建议传指针。
- 示例函数：`makepoint`、`addpoint`、`ptinrect`。

## 6.3 结构数组 Arrays of Structures
- 结构数组常见于“键值表”，如关键字计数：`struct key { char *word; int count; }`
- 对应代码
  - `chapter-6-structures/2.keywords-count.c` —— C 关键字计数（结构数组 + 二分查找/线性查找）

## 6.4 结构指针 Pointers to Structures
- 用 `->` 访问结构指针成员；结构数组二分查找常用指针算术（`keytab + mid`）。
- 对应代码
  - `chapter-6-structures/4.keywords-count-pointer.c` —— 指针版关键字计数（与 2 对比）

## 6.5 自引用结构 Self-referential Structures
- 结构成员可指向自身类型，构成二叉树等动态结构；递归遍历。
- 对应代码
  - `chapter-6-structures/5.words-count-binary-tree.c` —— 二叉树统计单词出现次数（`addtree/treeprint`）
  - `chapter-6-structures/3.getword.c` —— 练习 6-1：增强 `getword`（跳过注释/预处理指令，处理下划线）

## 6.6 表查找 Table Lookup
- 哈希表 + 链表解决冲突；`lookup` / `install` 经典实现。
- 对应代码
  - `chapter-6-structures/8.table-lookup.c` —— 练习 6-5：表查找并实现 `undef`（删除定义）

## 6.7 typedef
- 为类型起别名，提高可读性/可移植性，如 `typedef struct tnode *Treeptr;`

## 6.8 联合 Unions
- 联合的所有成员共享同一存储，大小取最大成员；一次只保存一种成员。

## 6.9 位字段 Bit-fields
- 结构内按位分配字段：`unsigned int is_keyword : 1;`，紧凑表示标志位（受机器相关限制）。

## 综合练习
- `chapter-6-structures/6.variables-group.c` —— 练习 6-2：按变量名分组统计（综合 getword + 树）
- `chapter-6-structures/7.words-appear-lines.c` —— 练习 6-3：交叉引用——打印每个单词出现的行号
- `chapter-6-structures/getch.c` —— `getword` 依赖的字符读入辅助实现

---

✍️ 个人补充/疑问：
