# 🏠 个人主页 — GitHub Pages 部署指南

> 一份米白色简约风格的秋招个人主页，单文件结构，零依赖，改完即部署。

---

## 📁 文件结构

```
your-username.github.io/
├── index.html      ← 主页（唯一需要编辑的文件）
├── resume.pdf      ← 你的简历（放这里即可被下载）
└── README.md       ← 本说明文件
```

就这三个文件，没有构建工具、没有框架、没有 node_modules。

---

## 🚀 首次部署（5 分钟搞定）

### 第一步：创建 GitHub 仓库

1. 登录 GitHub → 右上角 **+** → **New repository**
2. 仓库名必须是：`你的用户名.github.io`（比如用户名是 `zhangsan`，就填 `zhangsan.github.io`）
3. 设为 **Public**
4. 不要勾选 Initialize with README
5. 点 **Create repository**

### 第二步：本地初始化并推送

打开终端，依次执行：

```bash
# 1. 新建文件夹并进入
mkdir your-username.github.io
cd your-username.github.io

# 2. 把下载的 index.html 和你的 resume.pdf 放进来

# 3. 初始化 Git 并推送
git init
git add .
git commit -m "init: 个人主页上线"
git branch -M main
git remote add origin https://github.com/your-username/your-username.github.io.git
git push -u origin main
```

### 第三步：开启 GitHub Pages

1. 进入仓库页面 → **Settings** → 左侧 **Pages**
2. Source 选择 **Deploy from a branch**
3. Branch 选择 **main** → 文件夹选 **/ (root)** → **Save**
4. 等待 1-2 分钟，访问 `https://your-username.github.io` 即可

---

## ✏️ 日常修改工作流

每次想更新内容，只需三步：

```bash
# 1. 用任何编辑器打开 index.html，修改内容
#    推荐：VS Code（右键 → Open with Live Server 可实时预览）

# 2. 本地预览没问题后，提交修改
git add .
git commit -m "update: 更新了项目经历"

# 3. 推送上线
git push
```

大约 1 分钟后刷新页面即可看到更新。

---

## 🔍 index.html 修改地图

文件中用醒目的注释框标注了 **5 个修改区域**，用编辑器搜索 `✏️` 即可快速定位：

| 区域 | 搜索关键词 | 要改什么 |
|------|-----------|---------|
| 修改区域 1 | `修改区域 1` | 姓名、邮箱、电话、GitHub、标签行、简介 |
| 修改区域 2 | `修改区域 2` | 教育背景（学校、专业、GPA、时间） |
| 修改区域 3 | `修改区域 3` | 技术栈标签（复制/删除 `skill-pill` 即可增删） |
| 修改区域 4 | `修改区域 4` | 项目经历（复制/删除整个 `project` 块即可增删） |
| 修改区域 5 | `修改区域 5` | 实习经历（复制/删除整个 `exp-item` 块即可增删） |

### 常见修改示例

**添加一个新项目：** 复制下面这段，粘贴到 `修改区域 4` 里的最后一个 `</div>` 前：

```html
<div class="project">
  <div class="project-head">
    <span class="project-name">项目名称</span>
    <a class="project-link" href="https://github.com/xxx" target="_blank">source →</a>
  </div>
  <p class="project-desc">
    项目描述，一两句话说清楚做了什么、用了什么、效果如何。
  </p>
  <div class="skills-row">
    <span class="skill-pill">技术1</span>
    <span class="skill-pill">技术2</span>
  </div>
</div>
```

**添加一段新经历：** 复制下面这段：

```html
<div class="exp-item">
  <div class="exp-date">2024.xx — xx</div>
  <div>
    <div class="exp-role">岗位名称</div>
    <div class="exp-company">公司名 · 部门名</div>
    <div class="exp-desc">一句话描述你做了什么、成果如何。</div>
  </div>
</div>
```

**添加一个技能标签：** 在对应分类的 `skills-row` 里加一行：

```html
<span class="skill-pill">新技能</span>
```

---

## 🛠 本地预览方法

**方法 A — VS Code Live Server（推荐）：**
1. 安装 VS Code 插件 `Live Server`
2. 右键 index.html → `Open with Live Server`
3. 浏览器自动打开，修改后自动刷新

**方法 B — Python 一行命令：**
```bash
python3 -m http.server 8000
# 然后打开 http://localhost:8000
```

**方法 C — 直接双击：**
直接双击 index.html 用浏览器打开也能预览（简历下载链接可能不生效）。

---

## 💡 小贴士

- **简历更新**：直接用新的 `resume.pdf` 覆盖旧文件，push 即可
- **改颜色**：修改 `index.html` 顶部 `:root` 里的 CSS 变量
- **改字体**：修改 `:root` 里的 `--font-display` 和 `--font-body`
- **自定义域名**：Settings → Pages → Custom domain，填入你的域名，并在域名 DNS 添加 CNAME 记录指向 `your-username.github.io`
