# Wei Zhang Academic Homepage

这是 Wei Zhang 的个人学术主页，使用 [Jekyll](https://jekyllrb.com/) 和 Academic Pages（Minimal Mistakes）主题构建，并通过 GitHub Pages 发布。

## 以后要修改内容时，应该改哪里？

| 要修改的内容 | 对应文件或目录 | 说明 |
| --- | --- | --- |
| 主页个人简介 | `_pages/about.md` | 修改开头的个人介绍、研究方向、Scholar、DBLP 和邮箱 |
| 主页 News | `_pages/about.md` | 修改 `## News` 下方的列表；每条消息以 `- ` 开头 |
| 主页 Recent Publications | `_pages/about.md` | 修改 `## Recent Publications:` 下方的编号列表 |
| 主页 Services、Education 等 | `_pages/about.md` | 在对应的 Markdown 标题下修改 |
| 左侧头像 | `images/zhangwei.jpg` | 用新图片替换此文件；建议保持文件名不变 |
| 左侧姓名、职位、单位、邮箱和学术链接 | `_config.yml` | 修改 `author:` 下方的 `name`、`bio`、`location`、`employer`、`email`、`googlescholar` 等字段 |
| 网站标题、网址和仓库信息 | `_config.yml` | 修改文件顶部的 `title`、`name`、`description`、`url`、`baseurl` 和 `repository` |
| 顶部导航栏 | `_data/navigation.yml` | 修改菜单名称、顺序和链接；删除一项即可从导航栏隐藏 |
| Gallery 页面标题和说明 | `_pages/our-team.md` | 当前页面地址由文件顶部的 `permalink: /gallery/` 决定 |
| Gallery 照片 | `images/team/` | 直接添加或删除图片；支持 `.jpg`、`.jpeg`、`.png` 和 `.webp` |
| 可下载的 PDF、幻灯片等 | `files/` | 文件放入后，可使用 `/files/文件名.pdf` 形式链接 |
| 网站整体样式 | `assets/css/main.scss`、`_sass/` | 仅在需要调整颜色、字体、间距或布局时修改 |

> 不要直接修改 `_site/` 目录。它是 Jekyll 自动生成的网站结果，下次构建时其中的内容会被覆盖。

## 最常用的修改示例

### 修改主页

打开 `_pages/about.md`。这个文件对应网站首页 `/`，当前主要结构如下：

```text
个人简介
研究方向
Google Scholar / DBLP / EMAIL
News
Recent Publications
Services
Education
```

Markdown 常用写法：

```markdown
## 二级标题

- 无序列表第一项
- 无序列表第二项

1. 编号列表第一项
2. 编号列表第二项

[链接文字](https://example.com)
**粗体文字**
*斜体文字*
```

### 修改左侧个人信息

打开 `_config.yml`，找到：

```yaml
author:
  avatar: "zhangwei.jpg"
  name: "Wei Zhang"
  bio: "Professor at the School of Cyber Science and Technology, Shandong University"
  location: "Qingdao, China"
  employer: "Shandong University"
  email: "sduzhangwei@sdu.edu.cn"
```

修改 `_config.yml` 后，本地预览服务有时不会自动更新，建议停止服务后重新运行。

### 修改顶部导航

打开 `_data/navigation.yml`。每个菜单项包含显示名称和页面地址：

```yaml
main:
  - title: "Gallery"
    url: /gallery/
```

增加新页面时，需要同时：

1. 在 `_pages/` 中创建 Markdown 文件。
2. 在文件顶部设置 `permalink` 和 `title`。
3. 在 `_data/navigation.yml` 中添加入口。

例如：

```markdown
---
permalink: /new-page/
title: "New Page"
author_profile: true
---

这里填写页面内容。
```

### 修改 Gallery

- 页面内容和布局：修改 `_pages/our-team.md`。
- 添加照片：将照片放入 `images/team/`，页面会自动读取并显示。
- 删除照片：从 `images/team/` 删除对应文件。
- 更换照片时建议使用有意义的英文文件名，避免空格和中文符号。

## 本地预览

首次使用前，需要安装 Ruby 和 Bundler。

macOS：

```bash
brew install ruby
gem install bundler
```

进入项目目录后安装依赖：

```bash
bundle install
```

启动本地网站：

```bash
bundle exec jekyll serve -l -H localhost
```

然后访问：

```text
http://localhost:4000/zhangwei2/
```

如果只想检查 Markdown 和配置是否能够成功生成，可以运行：

```bash
bundle exec jekyll build
```

## 使用 Docker 预览

已安装 Docker 时，可以运行：

```bash
docker build -t zhangwei-homepage .
docker run --rm -p 4000:4000 -v "$(pwd):/usr/src/app" zhangwei-homepage
```

然后访问 `http://localhost:4000/zhangwei2/`。

## 发布更新

确认修改无误后，将变更提交并推送到 GitHub：

```bash
git status
git add _pages/about.md
git commit -m "Update homepage"
git push
```

如果修改了多个文件，可以按实际文件名逐个添加。推送后，在 GitHub 仓库的 **Settings → Pages** 或 **Actions** 中查看部署状态。

## 修改前后的检查清单

1. 链接是否可以打开，URL 是否以 `https://` 开头。
2. Markdown 标题前是否有 `#`，列表项前是否有 `- ` 或数字。
3. `_config.yml` 和 `_data/navigation.yml` 的缩进是否仍使用空格。
4. 图片文件名及扩展名是否与引用完全一致（注意大小写）。
5. 本地运行 `bundle exec jekyll build` 是否成功。
6. 使用 `git status` 确认只提交了需要修改的文件。

## 主要目录结构

```text
.
├── _config.yml             # 网站全局配置和左侧个人信息
├── _data/
│   └── navigation.yml      # 顶部导航栏
├── _pages/
│   ├── about.md            # 主页
│   └── our-team.md         # Gallery 页面
├── images/
│   ├── zhangwei.jpg        # 左侧头像
│   └── team/               # Gallery 照片
├── files/                  # PDF、幻灯片等下载文件
├── assets/css/main.scss    # 样式入口
└── _sass/                  # 主题样式文件
```

## 主题来源

本网站基于 [Academic Pages](https://academicpages.github.io/) 和 [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) 构建，许可证见 `LICENSE`。
