# Database Schema V1

# LMS 数据库设计 V1

## 设计原则

V1 优先保证：

* 简单
* 可扩展
* 不重复设计

避免过度设计。

允许未来扩展。

---

# students

学生表

## 用途

管理多个学生。

支持：

* 老大（高中）
* 老二（初中）

未来支持：

* 多家庭
* 多用户

## 字段

id

name

nickname

gender

birth_date

current_stage

current_grade

status

created_at

updated_at

---

# subjects

学科表

## 示例

数学

物理

化学

英语

语文

生物

政治

历史

地理

## 字段

id

name

sort_order

status

created_at

updated_at

---

# exam_papers

试卷表

## 用途

记录一次考试。

一张试卷对应一条记录。

## 字段

id

student_id

subject_id

stage

grade

semester

exam_name

exam_type

exam_date

total_score

student_score

status

created_at

updated_at

---

# exam_files

试卷文件表

## 用途

保存原始资料。

## 文件类型

question_paper

answer_sheet

solution

clean_pdf

student_work

## 字段

id

exam_paper_id

file_type

file_path

original_name

page_no

file_size

ocr_status

created_at

---

# questions

题目表

## 原则

一题一记录。

## 字段

id

exam_paper_id

subject_id

question_no

question_type

question_text

full_score

student_score

difficulty

source_type

status

created_at

updated_at

---

# question_images

题目图片表

## 用途

保存：

题目图

学生答案图

标准答案图

整页图

## 字段

id

question_id

image_type

file_path

page_no

bbox_json

created_at

---

# question_references

题目参考资料表

## 用途

保存：

标准答案

解析

评分标准

参考范文

AI讲解

## 字段

id

question_id

ref_type

title

content

source

sort_order

created_at

updated_at

---

# student_question_answers

学生答题表

## 用途

记录学生对题目的作答情况。

## 字段

id

student_id

question_id

exam_paper_id

answer_text

answer_image

score

is_correct

comment

created_at

updated_at

---

# knowledge_points

知识点表

## 用途

建立知识点树。

## 字段

id

subject_id

stage

grade

semester

chapter

parent_id

name

description

status

created_at

updated_at

---

# question_knowledge_points

题目知识点关联表

## 用途

支持一题多知识点。

## 字段

id

question_id

knowledge_point_id

is_primary

confidence

created_at

---

# ai_analysis_results

AI分析结果表

## 用途

保存AI分析记录。

允许多模型并存。

允许重新分析。

## 字段

id

question_id

analysis_type

ai_provider

model_name

prompt_version

result_json

confidence

created_at

---

# wrong_question_records

错题记录表

## 用途

记录学生错题。

## 字段

id

student_id

question_id

exam_paper_id

wrong_reason

ai_wrong_reason

review_count

is_mastered

next_review_date

created_at

updated_at

---

# study_reports

学习报告表

## 用途

保存历史学习报告。

## 字段

id

student_id

report_type

report_period

report_json

created_at

---

# V1 核心关系

students

↓

exam_papers

↓

questions

↓

question_images

question_references

student_question_answers

question_knowledge_points

ai_analysis_results

wrong_question_records

---

# 原始数据原则

永久保留：

* 原始PDF
* 原始图片
* 学生答题图片

---

# AI原则

AI结果允许重算。

AI结果不得覆盖原始数据。

原始数据优先级最高。

---

# V1 不设计

用户权限

收费系统

班级管理

学校管理

多租户

企业版功能

后续版本扩展。
