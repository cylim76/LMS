# System Architecture

## 总体架构

学生上传试卷

↓

试卷管理模块

↓

AI分析模块

↓

题目管理模块

↓

知识点管理模块

↓

错题管理模块

↓

学习报告模块

---

## 技术架构

Frontend

* Vue3
* Element Plus

Backend

* Flask

Database

* MySQL

Storage

* Local Storage（V1）
* Object Storage（未来）

AI

* Doubao Vision（默认）
* GPT（高级分析）

---

## 数据流

上传试卷

↓

保存原始文件

↓

PDF转图片

↓

AI识别

↓

自动拆题

↓

自动裁切题目

↓

知识点分析

↓

写入数据库

↓

生成学习报告

---

## 模块划分

### Student Module

学生管理

---

### Exam Module

试卷管理

---

### Question Module

题目管理

---

### Knowledge Module

知识点管理

---

### Wrong Question Module

错题管理

---

### AI Module

AI分析服务

---

### Report Module

学习报告

---

## 文件存储原则

原始文件永久保留：

* 原始PDF
* 原始图片

系统生成：

* 页面图片
* 题目裁切图片

所有AI分析结果均可重新生成。

原始数据不可丢失。
