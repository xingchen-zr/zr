---
title: YinXiangBiJi notes import
source: C:/Users/lenovo/Desktop/YinXiangBiJi.notes.html
created: 2026-07-07
tags: [Python, notes, import]
---

# 印象笔记导入整理

> 说明：这份笔记由桌面导出的 YinXiangBiJi.notes.html 转成 Obsidian Markdown。原文件主要由截图组成，因此这里保留原始图片顺序，并提取 HTML 中已有的文字备注。

## 内容索引

- Python 基础语法与类型转换
- 元组、列表、字典等容器
- 函数、lambda、模块
- API / 大模型调用相关记录
- SQL / MySQL 基础记录

## 原始顺序整理

![[attachments/yinxiangbiji-001.png]]

![[attachments/yinxiangbiji-002.png]]

![[attachments/yinxiangbiji-003.png]]

### 基本数据的类型转换

![[attachments/yinxiangbiji-004.png]]

![[attachments/yinxiangbiji-005.png]]

![[attachments/yinxiangbiji-006.png]]

![[attachments/yinxiangbiji-007.png]]

![[attachments/yinxiangbiji-008.png]]

![[attachments/yinxiangbiji-009.png]]

![[attachments/yinxiangbiji-010.png]]

> 元组中只包含一个元素时，需要在元素后面添加逗号，如果不加逗号，创建出来的就不是元组（tuple），而是指 123 这个整数了

![[attachments/yinxiangbiji-011.png]]

> 元组下标索引也是从 0 开始，元组（tuple）可以使用下标索引来访问元组中的值，跟列表完全一样。

![[attachments/yinxiangbiji-012.png]]

### tuple内包含了可修改的list，修改列表进而间接修改了tuple

![[attachments/yinxiangbiji-013.png]]

![[attachments/yinxiangbiji-014.png]]

### 注意是中括号里为key后面接=

![[attachments/yinxiangbiji-015.png]]

![[attachments/yinxiangbiji-016.png]]

### 注意顺序从左到右，如果遇到相同的key，则与右边的字典相同

![[attachments/yinxiangbiji-017.png]]

![[attachments/yinxiangbiji-018.png]]

![[attachments/yinxiangbiji-019.png]]

![[attachments/yinxiangbiji-020.png]]

![[attachments/yinxiangbiji-021.png]]

> 函数名为add，add里有（num1）（num2）两个未知数，函数add表达式为num1+num2

![[attachments/yinxiangbiji-022.png]]

![[attachments/yinxiangbiji-023.png]]

### lambda只适合写一行简单的函数

![[attachments/yinxiangbiji-024.png]]

![[attachments/yinxiangbiji-025.png]]

![[attachments/yinxiangbiji-026.png]]

![[attachments/yinxiangbiji-027.png]]

![[attachments/yinxiangbiji-028.png]]

![[attachments/yinxiangbiji-029.png]]

![[attachments/yinxiangbiji-030.png]]

![[attachments/yinxiangbiji-031.png]]

![[attachments/yinxiangbiji-032.png]]

![[attachments/yinxiangbiji-033.png]]

![[attachments/yinxiangbiji-034.png]]

![[attachments/yinxiangbiji-035.png]]

![[attachments/yinxiangbiji-036.png]]

![[attachments/yinxiangbiji-037.png]]

![[attachments/yinxiangbiji-038.png]]

![[attachments/yinxiangbiji-039.png]]

![[attachments/yinxiangbiji-040.png]]

![[attachments/yinxiangbiji-041.png]]

![[attachments/yinxiangbiji-042.png]]

![[attachments/yinxiangbiji-043.png]]

![[attachments/yinxiangbiji-044.png]]

![[attachments/yinxiangbiji-045.png]]

![[attachments/yinxiangbiji-046.png]]

![[attachments/yinxiangbiji-047.png]]

![[attachments/yinxiangbiji-048.png]]

![[attachments/yinxiangbiji-049.png]]

![[attachments/yinxiangbiji-050.png]]

![[attachments/yinxiangbiji-051.png]]

![[attachments/yinxiangbiji-052.png]]

![[attachments/yinxiangbiji-053.png]]

![[attachments/yinxiangbiji-054.png]]

![[attachments/yinxiangbiji-055.png]]

### 加一个if的限制条件，需要的时候再用该模块

![[attachments/yinxiangbiji-056.png]]

![[attachments/yinxiangbiji-057.png]]

### 常用的模块

![[attachments/yinxiangbiji-058.png]]

![[attachments/yinxiangbiji-059.png]]

![[attachments/yinxiangbiji-060.png]]

![[attachments/yinxiangbiji-061.png]]

![[attachments/yinxiangbiji-062.png]]

![[attachments/yinxiangbiji-063.png]]

![[attachments/yinxiangbiji-064.png]]

![[attachments/yinxiangbiji-065.png]]

![[attachments/yinxiangbiji-066.png]]

![[attachments/yinxiangbiji-067.png]]

![[attachments/yinxiangbiji-068.png]]

![[attachments/yinxiangbiji-069.png]]

![[attachments/yinxiangbiji-070.png]]

![[attachments/yinxiangbiji-071.png]]

![[attachments/yinxiangbiji-072.png]]

### system:系统提示词，开发者给ai设置的角色

![[attachments/yinxiangbiji-073.png]]

![[attachments/yinxiangbiji-074.png]]

![[attachments/yinxiangbiji-075.png]]

![[attachments/yinxiangbiji-076.png]]

![[attachments/yinxiangbiji-077.png]]

![[attachments/yinxiangbiji-078.png]]

![[attachments/yinxiangbiji-079.png]]

![[attachments/yinxiangbiji-080.png]]

![[attachments/yinxiangbiji-081.png]]

![[attachments/yinxiangbiji-082.png]]

![[attachments/yinxiangbiji-083.png]]

![[attachments/yinxiangbiji-084.png]]

![[attachments/yinxiangbiji-085.png]]

![[attachments/yinxiangbiji-086.png]]

![[attachments/yinxiangbiji-087.png]]

### char的性能比varchar性能好，但是char浪费空间

![[attachments/yinxiangbiji-088.png]]

![[attachments/yinxiangbiji-089.png]]

![[attachments/yinxiangbiji-090.png]]

![[attachments/yinxiangbiji-091.png]]

![[attachments/yinxiangbiji-092.png]]

![[attachments/yinxiangbiji-093.png]]

![[attachments/yinxiangbiji-094.png]]

![[attachments/yinxiangbiji-095.png]]

![[attachments/yinxiangbiji-096.png]]

![[attachments/yinxiangbiji-097.png]]

## 后续整理建议

- 当前版本已经把原图完整导入 Obsidian，可以直接在 Obsidian 中查看。
- 如果需要让图片里的文字可搜索，需要再做 OCR，把截图内容识别成文本。
- 后续建议按主题拆分成：Python 基础、函数与模块、API 调用、FastAPI、SQL/MySQL。

## 导入统计

- 图片数量：97
- HTML 文字备注数量：12
- 缺失图片数量：0
- 附件目录：`{asset_dir}`
