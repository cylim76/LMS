# Database Design

## 学习体系结构

Subject
↓
Stage
↓
Grade
↓
Semester
↓
Chapter
↓
Knowledge Point
↓
Question

---

## Subject

数学

物理

化学

英语

语文

---

## Stage

小学

初中

高中

---

## Grade

初一
初二
初三

高一
高二
高三

---

## Semester

上学期

下学期

---

# 核心表

students

subjects

stages

grades

semesters

exam_papers

exam_files

questions

question_images

question_references

student_question_answers

knowledge_points

question_knowledge_points

ai_analysis_results

wrong_question_records

study_reports

---

# 数据关系

exam_papers

↓

questions

↓

question_images

↓

question_references

↓

student_question_answers

↓

ai_analysis_results

↓

question_knowledge_points

---

# Question 设计原则

一题一记录。

Question 仅保存题目主体信息。

标准答案、解析、参考答案独立存储。

AI分析结果独立存储。

知识点关联独立存储。

---

# AI分析设计原则

AI分析结果属于衍生数据。

未来允许重新分析。

允许更换模型。

允许保留多个分析版本。

不得覆盖原始题目数据。

---

# 文件存储设计原则

原始文件永久保留。

题目裁切图片永久保留。

OCR文本允许重新生成。

AI分析允许重新生成。

原始数据作为系统最终依据。
