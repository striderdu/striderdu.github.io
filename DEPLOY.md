# GitHub Pages 部署指南

## 准备工作

1. **创建 GitHub 仓库**
   - 如果仓库名是 `username.github.io`，网站会自动部署到根域名
   - 如果仓库名是其他名称，需要在 `_config.yml` 中设置 `baseurl`

2. **检查配置文件**
   - 确认 `_config.yml` 中的 `url` 和 `baseurl` 设置正确
   - 当前配置：`url: "https://striderdu.github.io"`

## 推送步骤

1. **初始化 Git 仓库**（如果还没有）
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **添加远程仓库**
   ```bash
   git remote add origin https://github.com/striderdu/striderdu.github.io.git
   # 或者你的仓库地址
   ```

3. **推送到 GitHub**
   ```bash
   git branch -M main
   git push -u origin main
   ```

4. **启用 GitHub Pages**
   - 进入仓库的 Settings → Pages
   - Source 选择 "Deploy from a branch"
   - Branch 选择 "main" 或 "master"
   - Folder 选择 "/ (root)"
   - 点击 Save

5. **等待部署**
   - GitHub Pages 会自动构建和部署
   - 通常需要几分钟时间
   - 部署完成后可以通过 `https://striderdu.github.io` 访问

## 文件说明

### 需要提交的文件
- ✅ `_config.yml` - Jekyll 配置
- ✅ `_data/` - 数据文件
- ✅ `_layouts/` - 布局模板
- ✅ `_includes/` - 包含文件
- ✅ `css/`, `js/`, `img/`, `figures/` - 静态资源
- ✅ `index.md`, `publication.html`, `experience.html` - 页面文件
- ✅ `Gemfile` - Ruby 依赖（GitHub Pages 会自动安装）

### 不需要提交的文件（已在 .gitignore 中）
- ❌ `_site/` - Jekyll 生成的站点文件
- ❌ `.sass-cache/`, `.jekyll-cache/` - 缓存文件
- ❌ `node_modules/`, `vendor/` - 依赖目录
- ❌ `.DS_Store`, `Thumbs.db` - 系统文件

## 更新网站

每次修改后，只需：
```bash
git add .
git commit -m "Update content"
git push
```

GitHub Pages 会自动重新构建和部署。

## 注意事项

1. **不要提交 `_site/` 目录** - GitHub Pages 会自动生成
2. **确保 `Gemfile` 存在** - GitHub Pages 需要它来安装依赖
3. **检查 `_config.yml` 中的插件** - 确保只使用 GitHub Pages 支持的插件
4. **图片和文件路径** - 使用相对路径，确保在 GitHub Pages 上正常工作

## 故障排除

如果网站没有正常显示：
1. 检查仓库的 Settings → Pages 是否已启用
2. 查看 Actions 标签页中的构建日志
3. 确认 `_config.yml` 配置正确
4. 检查文件路径是否正确

