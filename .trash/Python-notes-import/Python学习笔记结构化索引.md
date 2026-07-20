---
title: Python学习笔记结构化索引
created: 2026-07-07
tags: [Python, 学习路线, Obsidian整理]
---

# Python学习笔记结构化索引

这份索引用来整理从印象笔记导入的截图资料。完整原始笔记在：[[YinXiangBiJi-import]]。

## 1. Python基础语法与类型转换

对应图片范围：`yinxiangbiji-001.png` 到 `yinxiangbiji-009.png`

重点复习：

- 基本数据类型
- 类型转换
- 字符串、整数、浮点数
- `input()` 输入后的类型处理
- `int()`、`float()`、`str()` 的使用

当前要求：能看懂代码，并能独立写出简单输入、计算、输出程序。

## 2. 元组、列表、字典等容器

对应图片范围：`yinxiangbiji-010.png` 到 `yinxiangbiji-020.png`

重点复习：

- 单元素元组必须加逗号，例如 `(123,)`
- 元组索引从 0 开始
- 元组本身不可变，但元组内部如果包含列表，列表内容仍然可以修改
- 字典通过 `key` 取值
- 修改字典值：`dict[key] = new_value`
- 合并字典时，如果 key 相同，后面的值会覆盖前面的值

当前要求：看到“按名称查找、保存多个对象、统计数量”时，优先想到字典。

## 3. 函数与 lambda

对应图片范围：`yinxiangbiji-021.png` 到 `yinxiangbiji-023.png`

重点复习：

- 函数名、参数、函数体、返回值
- `return` 用来把函数内部结果交回外部
- `lambda` 适合写一行简单函数
- 排序时经常配合 `key=lambda item: item[1]`

当前要求：能把重复代码封装成函数，而不是所有逻辑都写在主循环里。

## 4. 模块与代码组织

对应图片范围：`yinxiangbiji-024.png` 到 `yinxiangbiji-057.png`

重点复习：

- 模块导入
- 常用模块
- `if __name__ == "__main__"`
- 只在需要时运行某段代码
- 把功能拆分到不同函数或文件中

当前要求：理解“写项目时不是所有代码都堆在一个地方”，要逐步学会分层。

## 5. API / 大模型调用 / AI应用开发

对应图片范围：`yinxiangbiji-058.png` 到 `yinxiangbiji-079.png`

重点复习：

- API 调用流程
- `system` 是系统提示词，用来给 AI 设置角色和规则
- `user` 是用户输入
- `assistant` 是模型回复
- 流式输出时，模型会一段一段返回内容
- 本地模型和云端 API 的区别

当前要求：能写出“用户输入 -> 调用大模型 -> 显示回复”的最小程序。

## 6. SQL / MySQL基础

对应图片范围：`yinxiangbiji-080.png` 到 `yinxiangbiji-097.png`

重点复习：

- SQL 是操作数据库的语言
- `show databases;` 查看数据库
- 建表：`create table`
- 字符串类型用 `varchar`，不是 Python 里的 `str`
- `char` 性能较好但可能浪费空间，`varchar` 更灵活
- `tinyint` 是小整数类型，适合保存状态、性别、年龄等小范围数字
- MySQL CLI 中语句必须以英文分号 `;` 结尾

当前要求：先掌握 SQL 最小基础，不要过早深挖数据库优化。

## 7. 当前学习主线

你现在不应该回头反复刷 Python 基础，而应该沿着这条线推进：

```text
Python 小项目
↓
FastAPI
↓
SQL / ORM / 数据库
↓
大模型 API
↓
AI 应用项目
↓
RAG / Agent
```

当前最重要任务：

```text
用 FastAPI + ORM + 数据库，重构成绩管理系统。
```

## 8. 后续处理建议

- 这次导入保留了原图，适合查漏补缺。
- 如果要让图片里的文字可以被 Obsidian 搜索，需要做 OCR。
- 后面新增笔记时，尽量直接写 Markdown 文字，不要只保存截图。
- 每学完一个主题，建议补一段“我自己的理解”和“一段可运行代码”。
