# Jekyll GitHub Pages 设置指南

## 📋 已创建的文件结构

```
├── _config.yml              # Jekyll 配置文件
├── _data/                   # 数据文件目录
│   ├── profile.yml         # 个人信息配置
│   ├── awards.yml          # 奖项列表
│   ├── news.yml            # 新闻列表
│   ├── services.yml        # 专业服务
│   ├── books.yml           # 书籍列表
│   └── members.yml         # 成员信息
├── _layouts/               # 布局模板
│   ├── default.html        # 默认布局（包含导航栏）
│   └── home.html           # 首页布局
├── index.md                # 首页（使用 home 布局）
├── people.html             # 成员页面（已转换为 Jekyll）
├── publication.html       # 论文页面（已转换为 Jekyll）
├── .gitignore             # Git 忽略文件
├── Gemfile                 # Ruby 依赖管理
└── README.md               # 项目说明
```

## 🚀 快速开始

### 1. 本地测试（可选）

如果你想在本地预览网站：

```bash
# 安装 Ruby（如果还没有）
# Windows: 下载 RubyInstaller
# Mac: brew install ruby
# Linux: sudo apt-get install ruby-full

# 安装 Jekyll 和依赖
gem install bundler
bundle install

# 启动本地服务器
bundle exec jekyll serve

# 访问 http://localhost:4000
```

### 2. 直接推送到 GitHub

如果你不需要本地测试，可以直接：

```bash
git add .
git commit -m "Add Jekyll template structure"
git push
```

GitHub Pages 会自动构建网站。

## ✏️ 如何编辑内容

### 编辑个人信息

打开 `_data/profile.yml`，修改以下字段：

```yaml
name: "你的名字, Ph.D."
name_en: "Your Name"
name_cn: "你的中文名"
title: "Professor"
school: "你的学院"
school_url: "学院网址"
university: "你的大学"
university_url: "大学网址"
office: "办公室地址"
email: "你的邮箱"
email2: "备用邮箱"
bio: "你的简介"
```

### 添加奖项

编辑 `_data/awards.yml`，在列表开头添加：

```yaml
- year: 2025
  content: "你的奖项描述，可以使用 <a href='链接'>HTML</a>"
```

### 添加新闻

编辑 `_data/news.yml`，在列表开头添加：

```yaml
- year: 2025
  content: "新闻内容，可以使用 <a href='链接'>HTML 链接</a>"
```

### 添加/修改成员

编辑 `_data/members.yml`，在相应的分类下添加：

**添加教师：**
```yaml
teachers:
  - name: "姓名"
    image: "图片文件名.jpg"  # 图片需放在 img/ 目录
    link: "个人主页链接（可选）"
    title: "Professor"
    research:
      - "研究方向1"
      - "研究方向2"
```

**添加博士生：**
```yaml
phd_students:
  - name: "姓名"
    image: "图片文件名.jpg"
    link: ""  # 留空或填写链接
    highlight: false  # true 表示高亮显示
    tooltip: "提示信息（可选）"
    start_date: "Sept. 2023"
    end_date: ""  # 留空表示在读
```

**添加硕士生：**
```yaml
ms_students:
  - name: "姓名"
    image: "图片文件名.jpg"
    link: ""
    highlight: false
    tooltip: ""
    start_date: "Sept. 2023"
    end_date: ""
    research: "研究方向（可选）"
```

**添加校友：**
```yaml
alumni:
  - name: "姓名"
    image: "图片文件名.jpg"
    link: ""
    highlight: false  # 可选
    tooltip: ""  # 可选
    current: "当前工作单位"
```

### 修改导航菜单

编辑 `_config.yml`，修改 `navigation` 部分：

```yaml
navigation:
  - title: Home
    url: /
  - title: Publication
    url: /publication.html
  - title: Members
    url: /people.html
  # 添加更多菜单项
```

## 📝 重要提示

1. **保留原有的 HTML 文件**：`publication.html` 中的论文列表部分需要保留。你可以：
   - 将原有的论文列表 HTML 复制到新的 `publication.html` 的 `<div class="panel-body">` 中
   - 或者创建一个 `_includes/publications.html` 文件，然后在 `publication.html` 中使用 `{% include publications.html %}`

2. **图片路径**：所有图片路径会自动处理，使用 `{{ '/img/文件名' | relative_url }}` 格式

3. **YAML 格式**：编辑 YAML 文件时注意缩进和格式，错误的格式会导致网站构建失败

4. **测试**：每次修改后，建议先在本地测试（`bundle exec jekyll serve`），确认无误后再推送到 GitHub

## 🔧 故障排除

### 网站无法构建

1. 检查 YAML 文件格式是否正确
2. 查看 GitHub Actions 日志（如果有）
3. 在本地运行 `bundle exec jekyll build` 查看错误信息

### 图片不显示

1. 确认图片文件在 `img/` 目录中
2. 检查 `_data/members.yml` 中的图片文件名是否正确
3. 确认图片文件名大小写匹配

### 导航菜单不更新

1. 确认 `_config.yml` 中的 `navigation` 配置正确
2. 清除浏览器缓存
3. 检查页面 URL 是否匹配配置中的 URL

## 📚 更多资源

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)
- [Liquid 模板语言](https://shopify.github.io/liquid/)

## ✅ 下一步

1. 根据你的信息修改 `_data/profile.yml`
2. 更新 `_data/awards.yml` 和 `_data/news.yml`
3. 修改 `_data/members.yml` 添加你的团队成员
4. 将 `publication.html` 中的论文列表内容复制到新文件中
5. 推送到 GitHub 并查看效果

祝你使用愉快！🎉

