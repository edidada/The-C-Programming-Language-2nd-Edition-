# 第 7 章 输入与输出（Input and Output）

> K&R 第 7 章学习笔记。本章仓库中的文件主要是**书内示例程序**（非编号练习），代码路径以仓库根目录为基准。

## 7.1 标准输入输出 Standard Input/Output
- `getchar()`/`putchar()` 面向标准输入输出；`EOF` 标志文件结束。
- 文本流与二进制流；行缓冲/全缓冲概念了解即可。

## 7.2 格式化输出 Formatted Output
- `printf` 的格式串与转换说明：`%d %f %s %c %x` 等；宽度、精度、`-`/`0` 标志。
- 对应代码
  - `chapter-7-input-and-output/scanf-sample.c` —— 输出格式化示例（`%f` 对齐与精度）

## 7.3 变长参数表 Variable-length Argument Lists
- 自定义变参函数：`<stdarg.h>` 的 `va_list`、`va_start`、`va_arg`、`va_end`。
- 类型不能自动提升的注意点（`char`/`short` 提升为 `int`，`float` 提升为 `double`）。
- 对应代码
  - `chapter-7-input-and-output/minprintf.c` —— 最小版 `printf`（用 `va_arg` 逐个取参数）

## 7.4 格式化输入 Formatted Input
- `scanf`/`sscanf`：按格式读入，返回成功匹配的项数；地址参数需传指针（`&v`）。
- 对应代码
  - `chapter-7-input-and-output/scanf-sample.c` —— 循环用 `scanf("%lf", &v)` 读入并累加

## 7.5 文件访问 File Access
- `FILE *` 流；`fopen` 打开（"r"/"w"/"a" 等模式），`fclose` 关闭；失败返回 `NULL`。
- `getc`/`putc`/`fprintf` 面向文件流版本。
- 对应代码
  - `chapter-7-input-and-output/cat-v1.c` —— 版本 1：`fopen` + `getc`/`putc` 复制文件（`filecopy`）

## 7.6 错误处理 Error Handling
- 错误信息写 `stderr`，用 `exit` 返回状态；`ferror` 检测流错误。
- 对应代码
  - `chapter-7-input-and-output/cat-v2.c` —— 版本 2：改用 `fprintf(stderr,...)`、`exit`、并检查 `ferror(stdout)`

## 7.7 行输入与输出
- `fgets`/`fputs` 按行读写（书中 `getline` 改良思路源于此）。

## 7.8 其他函数
- 字符串函数、字符分类 `<ctype.h>`、`ungetc`、`system`、存储管理 `malloc/free` 等，具体实现见第 8 章笔记。

---

✍️ 个人补充/疑问：
