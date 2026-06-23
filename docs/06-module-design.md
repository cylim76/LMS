# Module Design

# LMS 模块设计

## 系统目标

LMS 以学生学习成长档案为核心。

所有数据围绕学生展开。

---

# 一级菜单

Dashboard

Students

Exams

Questions

Knowledge

Wrong Questions

Reports

Settings

---

# Dashboard

学习总览

显示：

* 学生人数
* 最近考试
* 最近上传试卷
* 错题数量
* 知识点掌握情况
* AI分析摘要

---

# Students

学生管理

---

功能：

学生列表

学生详情

学习档案

考试记录

错题统计

成长曲线

---

# Exams

试卷管理

---

功能：

上传试卷

试卷列表

试卷详情

AI分析状态

重新分析

---

试卷详情：

基本信息

↓

题目列表

↓

成绩统计

↓

知识点统计

---

# Questions

题目管理

---

功能：

题目查询

题目详情

题目搜索

题目标签

题目收藏

---

题目详情：

题目图片

题目文字

标准答案

解析

知识点

AI分析结果

---

# Knowledge

知识点管理

---

结构：

学科

↓

学段

↓

年级

↓

学期

↓

章节

↓

知识点

---

功能：

知识点树

知识点统计

知识点掌握情况

关联题目

---

# Wrong Questions

错题管理

---

功能：

错题列表

错因分类

知识点分类

复习状态

掌握状态

---

状态：

未复习

已复习

已掌握

---

# Reports

学习报告

---

支持：

学生报告

科目报告

知识点报告

阶段报告

---

内容：

正确率

错题率

知识点掌握率

成长趋势

AI建议

---

# Settings

系统配置

---

功能：

学科管理

知识点配置

AI模型配置

文件存储配置

系统参数配置

---

# V1 保留模块

Dashboard

Students

Exams

Questions

Wrong Questions

Reports

Settings

---

# V1 暂不开放模块

Knowledge

单独管理页面

暂缓

V1 阶段通过 AI 自动管理知识点。

---

# 页面设计原则

优先 PC 端。

兼容平板。

手机端后期适配。

---

# 用户角色

V1：

仅管理员

即家长账号

---

V2：

学生账号

---

V3：

教师账号

家庭账号

商业版账号
