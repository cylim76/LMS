# Database Review V1

# LMS 数据库评审 V1

## 评审目标

在正式开发前检查数据库设计。

避免：

* 重复设计
* 难以扩展
* 数据冗余
* 后期大规模重构

---

# 核心原则

## 原始数据优先

必须永久保留：

* 原始PDF
* 原始图片
* 学生答题图片

任何AI结果都不得覆盖原始数据。

---

## AI结果属于衍生数据

允许：

重新分析

重新计算

更换模型

多模型并存

---

# students 评审

当前设计：

基本满足V1需求。

---

未来扩展：

family_id

avatar

school

class_name

parent_note

暂不增加。

---

# exam_papers 评审

当前设计：

满足V1需求。

---

建议增加：

paper_version

用于记录：

第一次上传

重新上传

修正版

---

# exam_files 评审

当前设计：

合理。

---

建议增加：

file_hash

避免重复上传。

---

建议增加：

file_source

来源：

学生上传

家长上传

老师上传

系统导入

---

# questions 评审

当前设计：

合理。

---

注意：

Question 不应保存：

知识点

解析

AI结果

---

Question 仅保存：

题目主体信息。

---

# question_images 评审

当前设计：

合理。

---

建议：

支持多个图片。

例如：

题目图

学生答案图

标准答案图

页面图

---

不得限制一题一图。

---

# question_references 评审

当前设计：

合理。

---

统一保存：

标准答案

标准解析

评分标准

参考范文

AI讲解

---

避免后续建立大量重复表。

---

# student_question_answers 评审

重点关注。

---

未来可能出现：

同一道题

多次练习

多次复习

多次提交

---

建议：

允许多条记录。

禁止：

question_id 唯一。

---

# knowledge_points 评审

当前版本：

使用树结构。

---

parent_id

实现：

知识点树。

---

优点：

简单。

容易实现。

---

V1 保持树结构。

---

未来再评估：

路径结构

图结构

知识图谱

---

# question_knowledge_points 评审

必须保留。

---

原因：

一道题可能关联：

多个知识点。

---

例如：

导数最值

↓

函数定义域

↓

分类讨论

---

禁止在 question 表直接保存 knowledge_point_id。

---

# ai_analysis_results 评审

重点表。

---

必须保留：

provider

model_name

prompt_version

confidence

---

原因：

未来允许：

重新分析

结果对比

模型升级

---

# wrong_question_records 评审

建议未来增加：

mastered_at

last_review_date

review_level

---

V1 可暂缓。

---

# study_reports 评审

保存：

历史报告快照。

---

不要动态生成覆盖旧报告。

---

原因：

需要保留成长轨迹。

---

# V1 不建立

多租户

班级

学校

收费

订单

支付

消息通知

---

# V1 最终结论

当前数据库结构满足：

学生管理

试卷管理

题目管理

知识点管理

错题管理

学习报告

AI分析

需求。

允许进入开发阶段。

后续通过迁移脚本逐步升级。
