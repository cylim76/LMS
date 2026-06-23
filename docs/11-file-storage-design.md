# File Storage Design

# LMS 文件存储设计

## 设计目标

保证：

* 文件长期保存
* 易于备份
* 易于迁移
* 易于扩展

---

# 原则

数据库保存：

元数据

---

文件系统保存：

实际文件

---

禁止：

大量图片存入数据库。

---

# 文件分类

系统文件分为：

Exam Files

Question Images

Student Answers

Reference Files

Report Files

---

# V1 存储结构

storage/

├── exams/

├── questions/

├── students/

├── references/

├── reports/

└── temp/

---

# exams

原始试卷

---

示例：

storage/exams/

2026/

高中/

数学/

高一上/

2026-09-15-第一次月考/

---

保存：

原始PDF

原始图片

扫描件

---

# questions

题目图片

---

示例：

storage/questions/

question_id/

---

例如：

storage/questions/5001/

question.png

question_original.png

---

保存：

题目裁切图

题目原图

---

# students

学生答案

---

示例：

storage/students/

student_id/

question_id/

---

保存：

学生答题图片

学生手写过程

补充资料

---

# references

参考资料

---

保存：

教材

真题

标准答案

教师资料

---

示例：

storage/references/

高中数学/

导数/

---

# reports

学习报告

---

保存：

PDF报告

导出文件

分析结果

---

# temp

临时目录

---

用于：

PDF转图片

AI处理中间文件

缓存

---

定期清理。

---

# 文件命名原则

禁止：

中文文件名

禁止：

空格

---

推荐：

UUID

或

系统生成文件名

---

例如：

question_5001.png

student_answer_3001.jpg

exam_1001.pdf

---

# 数据库存储原则

数据库只保存：

file_path

file_name

file_size

file_hash

mime_type

---

禁止：

保存文件二进制内容。

---

# file_hash

必须保存。

---

用途：

重复文件检测

文件完整性校验

备份校验

---

推荐：

SHA256

---

# 删除策略

默认：

逻辑删除

---

文件先进入：

Recycle Bin

---

保留：

30天

---

再彻底删除。

---

# 图片处理原则

保留：

原图

---

允许生成：

缩略图

压缩图

裁切图

---

原图不得覆盖。

---

# PDF处理原则

保留：

原始PDF

---

允许生成：

页面图片

OCR结果

AI分析结果

---

原始PDF不得覆盖。

---

# V1 存储位置

本地磁盘

---

例如：

Linux

/storage

或

/data/lms

---

Windows

D:\LMSData

---

Mac

/Users/lms/storage

---

路径配置化。

禁止写死。

---

# V2

对象存储

---

支持：

S3

MinIO

OSS

COS

---

# 备份原则

数据库备份

*

文件备份

同时进行

---

数据库恢复后

必须能找到对应文件。

---

# 数据迁移原则

迁移服务器时：

数据库

*

storage目录

一起迁移

---

恢复后：

系统立即可运行。

---

# V1 最终原则

原始资料最重要。

---

永久保留：

原始PDF

原始图片

学生答案图片

---

AI结果允许重算。

原始资料不得丢失。
