# 发布到公网（一个网址给别人打开）

本项目是纯静态网页，可**免费**托管。任选一种方式即可。

---

## 方式一：Netlify 拖拽（最简单，约 2 分钟）

1. 打开 https://app.netlify.com/drop  
2. 登录/注册（可用 GitHub 或邮箱）  
3. 把整个 **`song` 文件夹**拖进网页  
4. 会得到类似 `https://随机名.netlify.app` 的网址，点 **Site settings → Domain management** 可改成更好记的子域名  

无需改代码，拖完就能用。

---

## 方式二：GitHub Pages（稳定、可更新）

### 1. 在 GitHub 新建仓库

例如仓库名：`shaosong-battles`（公开 Public）

### 2. 在本机 `f:\song` 目录执行

```powershell
cd f:\song
git init
git add index.html yaoshan.html taiyuan.html huolu.html .nojekyll netlify.toml README.md DEPLOY.md
git commit -m "Publish Shao Song battle sandboxes"
git branch -M main
git remote add origin https://github.com/你的用户名/shaosong-battles.git
git push -u origin main
```

### 3. 开启 Pages

仓库 → **Settings** → **Pages** → Source 选 **Deploy from branch** → Branch 选 `main`，文件夹选 **`/ (root)`** → Save  

几分钟后访问：

`https://你的用户名.github.io/shaosong-battles/`

---

## 方式三：Vercel（与 Netlify 类似）

1. 打开 https://vercel.com/new  
2. 导入上面的 GitHub 仓库，或上传文件夹  
3. Framework 选 **Other**，Root 保持默认，Deploy  

---

## 线上需要哪些文件？

至少包含：

- `index.html`
- `yaoshan.html`
- `taiyuan.html`
- `huolu.html`

（均为单文件，**不需要** `shared` 文件夹。）

`tools/`、`yaoshan-data.js` 等仅本地构建用，可不传。

---

## 修改后如何更新？

改完本地 html 后：

- **Netlify**：再拖一次文件夹，或连接 Git 自动部署  
- **GitHub Pages**：`git add` → `git commit` → `git push`，等 1～2 分钟  

本地重新生成单文件页：

```powershell
python tools/build-standalone.py
```
