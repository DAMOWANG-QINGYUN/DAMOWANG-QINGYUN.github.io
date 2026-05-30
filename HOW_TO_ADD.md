# 作品集网站 —— 自己动手改的教程

## 工具准备

你只需要两样东西：
- **记事本**（或任何文本编辑器，推荐用 VS Code）
- **终端**（就是你现在用 Claude 的这个窗口，或者搜索"PowerShell"打开）

所有文件都在你桌面的 `portfolio` 文件夹里。


---


## 一、改文字

用记事本打开 `index.html`，你会看到类似这样的内容：

```
第 29 行   <h1 class="hero-name">蔡青芸</h1>
```

尖括号 `<>` 里的东西是代码标记，**不要动**。
你只需要改**两个尖括号中间的中文字**。

### 常见的改法举例

**改名字（第 29 行）：**
```
<h1 class="hero-name">蔡青芸</h1>
                       ^^^^^^^^ 改这里
```

**改一句话介绍（第 30 行）：**
```
<p class="hero-tagline">关注玩家情绪与沉浸体验 · 互动叙事与关系设计 · 游戏策划方向</p>
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ 改这里
```

**改关于我（第 44 行）：**
```
<p>数字媒体技术专业<br>独立游戏开发 / 叙事策划方向</p>
   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ 改这里
```
注意：`<br>` 表示换行，不要删。

**改技能标签（第 47-50 行）：**
```
<span class="skill-tag">心理叙事</span>
                         ^^^^^^^^ 改这里
```
想加一个新标签？复制一整行粘贴到下面，改中间的字就行。
想删一个？把整行 `<span ...>...</span>` 删掉。

**改作品卡片的标题和介绍（比如第 68-72 行）：**
```
<h3 class="card-title">「Been Seen」</h3>      ← 项目名
<p class="card-description">                    ← 项目介绍开始
    参加莉莉丝高校游戏提案赛的完整视觉小说作品...    ← 改这段话
</p>                                            ← 项目介绍结束
```

**改联系邮箱（第 140-142 行）：**
两个地方都要改：
```
<a href="mailto:caiqingyun18@gmail.com" ...>    ← 改 mailto: 后面的邮箱
    <span>caiqingyun18@gmail.com</span>         ← 改显示的邮箱文字
```


---


## 二、加一个新作品

分 3 步：

### 第 1 步：在首页加一张卡片

打开 `index.html`，找到第 128 行附近的 `</div>`（最后一张卡片结束的地方），
在它**前面**粘贴这段（整段复制）：

```html
                <div class="project-card fade-in">
                    <div class="card-image">
                        <div class="card-image-placeholder">项目名字</div>
                    </div>
                    <div class="card-content">
                        <h3 class="card-title">项目名字</h3>
                        <p class="card-description">
                            一两句话介绍你的项目。
                        </p>
                        <div class="card-tags">
                            <span class="tag">Unity</span>
                            <span class="tag">C#</span>
                        </div>
                        <div class="card-links">
                            <a href="新页面.html" class="card-link">查看详情 →</a>
                        </div>
                    </div>
                </div>
```

把"项目名字"、介绍、标签、"新页面.html"改成你自己的。

### 第 2 步：做一个详情页

最简单的方法：
1. 复制 `beenseen.html`，改名为你的项目名（比如 `unity-game.html`）
2. 用记事本打开，把里面的文字改成你的新项目内容
3. 把图片/GIF/PDF放到 `assets` 对应文件夹里，改 `src="..."` 路径

### 第 3 步：把图片等素材放进去

- 图片/GIF → 放到 `assets/images/` 里（可以建子文件夹）
- PDF 文件 → 放到 `assets/pdfs/` 里
- 游戏安装包（太大的文件）→ 去 GitHub Releases 上传（见最后一节）


---


## 三、改完之后怎么上线

每次改完文件，打开终端（PowerShell），输入这 3 行命令：

```
cd ~/Desktop/portfolio
git add -A
git commit -m "说明你改了什么"
git push
```

比如你加了一个新项目：
```
cd ~/Desktop/portfolio
git add -A
git commit -m "添加新作品：Unity小游戏"
git push
```

等 1-2 分钟，刷新 https://DAMOWANG-QINGYUN.github.io 就能看到更新了。


---


## 四、上传游戏包到 GitHub Releases

游戏包太大（几百MB）不能直接放在网站文件夹里。用这个方法：

1. 把游戏文件夹压缩成 `.zip`
2. 打开 https://github.com/DAMOWANG-QINGYUN/DAMOWANG-QINGYUN.github.io/releases/new
3. Tag version 填个版本号，比如 `v2.0`
4. Title 填游戏名字
5. 把 zip 拖到下面的上传区域
6. 点 Publish release
7. 发布后，右键点 zip 文件名 → 复制链接
8. 把链接粘贴到你网页里的 `href="..."` 里


---


## 文件在哪里？速查

```
桌面/portfolio/
├── index.html          ← 首页（改文字、加卡片在这里）
├── beenseen.html       ← Been Seen 详情页
├── analysis.html       ← 游戏分析详情页
├── pixelart.html       ← 像素美术详情页
├── css/style.css       ← 样式（颜色、字体，一般不用动）
├── js/main.js          ← 动画效果（一般不用动）
└── assets/
    ├── images/         ← 放图片和GIF
    └── pdfs/           ← 放PDF文档
```


## 记住一个原则

HTML 文件里，你只需要改 `>这里的文字<` 和 `="这里的链接"`，
其他带尖括号的代码标记不要动，就不会出问题。
