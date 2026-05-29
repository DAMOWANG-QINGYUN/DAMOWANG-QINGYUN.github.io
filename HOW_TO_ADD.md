# 如何添加新作品到作品集

## 第一步：首页加卡片

打开 `index.html`，找到 `projects-grid` 区域，在最后一个 `</div>` 前复制粘贴以下模板：

```html
<div class="project-card fade-in">
    <div class="card-image">
        <div class="card-image-placeholder">项目名</div>
    </div>
    <div class="card-content">
        <h3 class="card-title">你的新项目名</h3>
        <p class="card-description">一两句话介绍这个项目</p>
        <div class="card-tags">
            <span class="tag">Unity</span>
            <span class="tag">C#</span>
        </div>
        <div class="card-links">
            <a href="新页面文件名.html" class="card-link">查看详情 →</a>
        </div>
    </div>
</div>
```

如果有项目截图，把 `card-image-placeholder` 那行换成：
```html
<img src="assets/images/你的图片.png" alt="项目截图">
```

## 第二步：建详情页

复制一个现有的详情页当模板：
- 游戏类项目 → 复制 `beenseen.html`
- 分析文章类 → 复制 `analysis.html`
- 美术展示类 → 复制 `pixelart.html`

改里面的文字、图片路径、PDF链接即可。

## 第三步：放素材

- 图片放到 `assets/images/` 下（建议按项目建子文件夹）
- PDF 放到 `assets/pdfs/`
- 游戏包（太大的文件）→ 去 GitHub Releases 上传，见下方说明

## 第四步：推送上线

打开终端，运行：
```
cd Desktop\portfolio
git add -A
git commit -m "添加新作品：项目名"
git push
```

等 1-2 分钟后刷新 https://DAMOWANG-QINGYUN.github.io 就能看到。

## 上传游戏包到 GitHub Releases

游戏包太大不能放在网页仓库里，用 Release 托管：

1. 先把游戏文件夹压缩成 zip
2. 打开 https://github.com/DAMOWANG-QINGYUN/DAMOWANG-QINGYUN.github.io/releases/new
3. Tag 填版本号（如 v2.0）
4. Title 填游戏名
5. 把 zip 拖到 Attach binaries 区域上传
6. 点 Publish release
7. 上传完成后，右键复制 zip 的下载链接，填到详情页的按钮里

## 文件结构参考

```
portfolio/
├── index.html              ← 首页（改卡片在这）
├── beenseen.html           ← Been Seen 详情页
├── analysis.html           ← 游戏分析详情页
├── pixelart.html           ← 像素美术详情页
├── 你的新页面.html          ← 新项目详情页
├── css/style.css           ← 样式（一般不用改）
├── js/main.js              ← 动画（一般不用改）
└── assets/
    ├── images/             ← 图片
    │   ├── beenseen/
    │   ├── pixel/
    │   └── 新项目文件夹/
    └── pdfs/               ← PDF文档
```
