# 第 8 章 UNIX 系统接口（The UNIX System Interface）

> K&R 第 8 章学习笔记。本章仓库中的文件主要是**书内示例程序**（非编号练习），代码路径以仓库根目录为基准。

## 8.1 文件描述符 File Descriptors
- 内核以非负整数（文件描述符）标识打开的文件；0=stdin、1=stdout、2=stderr。
- 对比第 7 章的缓冲流：描述符是底层接口，流在描述符之上加缓冲。

## 8.2 低级 I/O Low-level I/O
- `read`/`write` 系统调用：读写指定字节数，返回实际读写字节数（0 表示 EOF，-1 出错）。
- 缓冲大小影响性能：读写调用开销大，一次性读大块再处理。
- 对应代码
  - `chapter-8-the-unix-system-interface/sys-copy.c` —— 最小复制程序：循环 `read(0)` → `write(1)`

## 8.3 open、creat、close、unlink
- `open` 打开/创建文件（`O_RDONLY`/`O_WRONLY`/`O_CREAT` 等标志与权限位），失败返回 -1。
- `creat` 已过时（等价 `open` + `O_CREAT`）；`unlink` 删除文件。

## 8.4 随机访问 lseek
- `lseek` 设置文件偏移实现随机读写；`getc` 等缓冲接口之上也可配合。

## 8.5 实例：实现 fopen/getc
- 用缓冲思想实现标准库 `FILE`：结构含 `fd`、缓冲指针、`cnt`、`flag`；`_fillbuf` 读入整块。
- 对应代码
  - `chapter-8-the-unix-system-interface/fopen.c` —— 自定义 `FILE` 结构、`fopen`/`_fillbuf` 实现（含 `_READ`/`_WRITE` 等标志位）
- 对比命令 `cp.c`：
  - `chapter-8-the-unix-system-interface/cp.c` —— 用 `open`/`read`/`write` 复制文件 + 变长参数 `error` 统一报错

## 8.6 实例：目录列表 List Directories
- `stat` 读取文件元数据；遍历目录需 `opendir`/`readdir`/`closedir`。
- 目录项与 inode 概念；`DIR` 与 `dirent` 结构。
- 对应代码
  - `chapter-8-the-unix-system-interface/dirent.h` —— 自定义目录项头文件
  - `chapter-8-the-unix-system-interface/fsize.c` —— 递归遍历目录树打印各文件大小（`fsize`/`dirwalk`）

## 8.7 实例：存储分配器 Storage Allocator
- `malloc`/`free` 的空闲链表实现：块头记录大小与下一块，按对齐分配，用 `sbrk` 向系统要内存。
- `union` 保证块头对齐（`union header` 技巧）。
- 对应代码
  - `chapter-8-the-unix-system-interface/malloc.c` —— `malloc`/`free`/`morecore` 实现

---

✍️ 个人补充/疑问：
