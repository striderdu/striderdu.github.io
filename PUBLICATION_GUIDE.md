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
- **venue_short**: 显示在列表左侧的简短标识（如 "[AAAI]", "[TKDE]"）
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

