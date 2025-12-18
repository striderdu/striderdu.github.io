# GitHub Pages Jekyll 模板

这是一个基于 Jekyll 的 GitHub Pages 网站模板，用于学术研究实验室网站。

## 目录结构

```
.
├── _config.yml          # Jekyll 配置文件
├── _data/               # 数据文件目录
│   ├── profile.yml      # 个人信息
│   ├── awards.yml       # 奖项列表
│   ├── news.yml         # 新闻列表
│   ├── services.yml     # 专业服务
│   ├── books.yml        # 书籍列表
│   └── members.yml      # 成员信息
├── _layouts/            # 布局模板
│   ├── default.html     # 默认布局
│   └── home.html        # 首页布局
├── index.md             # 首页
├── people.html          # 成员页面
├── publication.html     # 论文页面
├── css/                 # CSS 样式文件
├── js/                  # JavaScript 文件
├── img/                 # 图片文件
└── Gemfile              # Ruby 依赖文件
```

## 使用方法

### 1. 本地开发

首先安装 Jekyll（需要 Ruby）：

```bash
# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve

# 访问 http://localhost:4000
```

### 2. 编辑内容

#### 编辑个人信息
编辑 `_data/profile.yml` 文件

#### 添加奖项
编辑 `_data/awards.yml` 文件，添加新的奖项条目：
```yaml
- year: 2025
  content: "你的奖项内容"
```

#### 添加新闻
编辑 `_data/news.yml` 文件，添加新的新闻条目：
```yaml
- year: 2025
  content: "你的新闻内容，可以使用 <a href='链接'>HTML</a>"
```

#### 添加成员
编辑 `_data/members.yml` 文件，在相应的分类下添加成员信息：
```yaml
phd_students:
  - name: "姓名"
    image: "图片文件名.jpg"
    link: "个人主页链接（可选）"
    highlight: false  # 是否高亮显示
    tooltip: "提示信息（可选）"
    start_date: "Sept. 2023"
    end_date: ""
```

#### 修改导航菜单
编辑 `_config.yml` 文件中的 `navigation` 部分

### 3. 部署到 GitHub Pages

1. 将代码推送到 GitHub 仓库
2. 在仓库设置中启用 GitHub Pages
3. 选择主分支作为源
4. GitHub 会自动构建和部署网站

## 优势

- ✅ **内容与样式分离**：只需编辑 YAML 数据文件即可更新内容
- ✅ **统一导航**：修改 `_config.yml` 即可更新所有页面的导航
- ✅ **模板复用**：修改布局文件即可更新所有页面样式
- ✅ **易于维护**：结构清晰，便于扩展

## 注意事项

1. `publication.html` 文件中的论文列表需要手动维护，或者可以创建数据文件来管理
2. 图片路径使用 `{{ '/img/文件名' | relative_url }}` 格式
3. 确保所有数据文件的 YAML 格式正确

## 许可证

根据原项目许可证
