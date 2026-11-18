# Publication 页面编辑指南

## 📝 如何添加新论文

### 1. 编辑 `_data/publications.yml` 文件

在文件开头添加新的论文条目（按年份从新到旧排序）：

```yaml
- year: 2025
  type: journal  # 或 conference 或 patent
  venue: TKDE    # 会议/期刊简称（用于分类）
  venue_short: "[TKDE]"
  venue_full: "IEEE Transactions on Knowledge and Data Engineering"
  title: "Your Paper Title Here."
  authors: "Author1, <u>Hao Peng</u>, Author2, Author3"
  pdf: "paper2025.pdf"  # PDF文件名（需放在 papers/ 目录）
  image: "paper2025.png"  # 图片文件名（需放在 figures/ 目录，可选）
  tags:
    - "2025"        # 年份（必须）
    - "journal"     # 类型（必须）
    - "TKDE"        # 会议/期刊简称（必须）
```

### 2. 字段说明

- **year**: 发表年份（数字）
- **type**: 论文类型
  - `journal` - 期刊论文
  - `conference` - 会议论文
  - `patent` - 专利
- **venue**: 会议/期刊的简称（用于分类筛选，如 AAAI, SIGIR, TKDE）
- **ccf_rank**: CCF 等级，填写 `A`、`B` 或 `C`，对 `type: conference` 和 `type: journal` 生效；未收录会议、未收录期刊及专利省略此字段。Findings、Workshop、Short paper 等不纳入 CCF 会议分类。国际会议和期刊依据 [CCF 第七版目录](https://www.ccf.org.cn/Academic_Evaluation/By_category/2026-03-31/870181.shtml)。本站不将《中国科学：信息科学》计入 CCF 分级筛选，该条目省略 `ccf_rank`。
- **venue_short**: 显示在列表左侧的简短标识（如 "[AAAI]", "[TKDE]"）
- **indexing**: 按期刊或论文集的收录范围分类，使用数组 `indexing: [SCI, EI]`；仅 SCI 填 `[SCI]`，仅 EI 填 `[EI]`。未列入两类填 `[]`；尚未核对则省略，页面显示待分类数量。此统计含本站所有列出论文（包括录用论文），不表示逐篇已取得检索记录。SCI 口径包含 SCIE。CCF 分级不代表 SCI/EI 收录。
- **venue_full**: 会议/期刊的完整名称（显示在论文信息中）
- **title**: 论文标题（注意末尾的点号）
- **authors**: 作者列表
  - 用 `<u>Hao Peng</u>` 标记自己（会显示为下划线）
  - 其他作者用逗号分隔
- **pdf**: PDF文件名（相对于 `papers/` 目录）
- **image**: 图片文件名（相对于 `figures/` 目录，可选）
- **tags**: 分类标签数组
  - 必须包含年份（如 "2025"）
  - 必须包含类型（"journal", "conference", 或 "patent"）
  - 必须包含会议/期刊简称（如 "AAAI", "TKDE"）

### 3. 示例

#### 期刊论文示例：
```yaml
- year: 2025
  type: journal
  venue: TKDE
  venue_short: "[TKDE]"
  venue_full: "IEEE Transactions on Knowledge and Data Engineering"
  title: "Deep Learning for Graph Analysis."
  authors: "Xianghua Zeng, <u>Hao Peng</u>, Angsheng Li, Philip S. Yu"
  pdf: "TKDE2025.pdf"
  image: "TKDE2025.png"
  tags:
    - "2025"
    - "journal"
    - "TKDE"
```

#### 会议论文示例：
```yaml
- year: 2025
  type: conference
  venue: AAAI
  ccf_rank: A
  venue_short: "[AAAI]"
  venue_full: "AAAI '25: Association for the Advancement of Artificial Intelligence"
  title: "Graph Neural Networks for Social Event Detection."
  authors: "Jingyun Zhang, <u>Hao Peng</u>, Xianghua Zeng"
  pdf: "AAAI2025.pdf"
  image: "AAAI2025.png"
  tags:
    - "2025"
    - "conference"
    - "AAAI"
```

#### 专利示例：
```yaml
- year: 2024
  type: patent
  venue: Patent
  venue_short: "[Patent]"
  venue_full: "Chinese Patent"
  title: "A Method for Social Event Detection."
  authors: "<u>Hao Peng</u>, Author2"
  pdf: "patent2024.pdf"
  image: ""  # 专利可能没有图片
  tags:
    - "2024"
    - "patent"
    - "Patent"
```

## 🔍 筛选功能

论文会自动根据以下条件进行分类：

1. **按年份筛选**: 使用 `year` 字段
2. **按类型筛选**: 使用 `type` 字段（journal/conference/patent）
3. **按会议筛选**: 使用 `venue` 字段（如 AAAI, SIGIR）
4. **按期刊筛选**: 使用 `venue` 字段（如 TKDE, IS）
5. **按 CCF 等级筛选**: 使用会议和期刊论文的 `ccf_rank` 字段（A/B/C），菜单自动合计各类会议和期刊论文数量；点击 All 恢复全部论文。筛选后没有匹配论文的年份会自动隐藏。新增论文时需填写等级，当前没有自动查询会议或期刊等级的数据库。
6. **SCI / EI 数量和筛选**: 读取每篇论文的 `indexing` 数组分别计数；同一篇属于两类时，两类各计一次，不可直接将两类数量相加作为去重总数。没有任何已分类数据时显示 `—`，而不是将未知情况显示为 0。补充收录范围数据后自动更新数量并启用筛选。

SCI/EI 分类来源（2026-11-18 核对）：

- Neural Networks、Neurocomputing：SCI（SCIE）期刊，来源为 [Clarivate 期刊目录](https://mjl.clarivate.com/)（ISSN 分别为 0893-6080、0925-2312）。
- EI 使用 [Elsevier Compendex 官方来源目录](https://www.elsevier.com/products/engineering-village/databases/compendex)中的 [2026-08-07 来源表](https://assets.ctfassets.net/o78em1y1w4i4/1vOKA5ELqWIoXeukEI0KPk/25a74b602fc5149a096bd87bf7d9c5e1/COMPENDEX_Source-list-082026.xlsx)。SERIALS 收录 Neural Networks、Neurocomputing、CIKM、AAAI、KDD、NeurIPS 及 LNCS；PAKDD、DASFAA、ICSI 按 LNCS 论文集系列范围分类。NON-SERIALS 明确列有 Findings of the Association for Computational Linguistics: EMNLP 2022。
- 《中国科学：信息科学》中文版（ISSN 1674-7267）未在本次官方 EI 来源表中匹配到，本站不计入 SCI/EI；勿与英文版 Science China Information Sciences 混淆。

现有期刊分级：Neural Networks（NN）为 B 类，Neurocomputing 为 C 类，来源为 [CCF 人工智能领域目录](https://www.ccf.org.cn/Academic_Evaluation/AI/)。《中国科学：信息科学》保留在全部列表和期刊筛选中，不计入 CCF 分级及数量。

筛选菜单会自动显示所有可用的选项。

## 📁 文件结构

确保以下文件/目录存在：

```
papers/          # PDF 文件目录
  ├── paper2025.pdf
  └── ...

figures/         # 论文图片目录
  ├── paper2025.png
  └── ...

_data/
  └── publications.yml  # 论文数据文件
```

## ✅ 添加论文后的步骤

1. 编辑 `_data/publications.yml`，添加新论文
2. 将 PDF 文件放入 `papers/` 目录
3. 将图片文件放入 `figures/` 目录（可选）
4. 保存文件
5. 本地测试：运行 `bundle exec jekyll serve` 查看效果
6. 推送到 GitHub：`git add . && git commit -m "Add new paper" && git push`

## 💡 提示

- 论文按年份从新到旧自动排序
- 同一年的论文按添加顺序显示（后添加的在前）
- 如果不需要图片，可以设置 `image: ""` 或省略该字段
- 作者列表中的 `<u>` 标签用于标记自己，会显示为下划线
- 确保 PDF 和图片文件名与 YAML 中的名称一致

## 🐛 常见问题

**Q: 论文不显示？**
A: 检查 YAML 格式是否正确，缩进是否正确（使用2个空格）

**Q: 筛选不工作？**
A: 确保 `tags` 数组中包含了正确的标签（年份、类型、会议/期刊名）

**Q: 图片不显示？**
A: 检查图片路径是否正确，文件名是否匹配，图片是否在 `figures/` 目录中

**Q: PDF 链接不工作？**
A: 检查 PDF 文件名是否正确，文件是否在 `papers/` 目录中

