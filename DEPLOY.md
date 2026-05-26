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

仓库名：**`shaosong`**（公开 Public）

### 2. 在 GitHub 网页新建空仓库

打开 https://github.com/new  

- Repository name：`shaosong`  
- Public  
- **不要**勾选 “Add a README”（本地已有代码）

### 3. 在本机 `f:\song` 执行（仓库已 init 并 commit 后可只执行 push 部分）

```powershell
cd f:\song
git branch -M main
git remote add origin https://github.com/你的GitHub用户名/shaosong.git
git push -u origin main
```

若远程已有内容，改用：

```powershell
git push -u origin main --force
```

（仅在你确认远程仓库是新建空仓库时使用 `--force`。）

### 4. 开启 GitHub Pages（重要：二选一，不要混用）

仓库 **shaosong** → **Settings** → **Pages** → **Build and deployment** → **Source**

**推荐：GitHub Actions（与仓库内 `.github/workflows/pages.yml` 配套）**

1. Source 选 **GitHub Actions**（不要选 Deploy from a branch）
2. 推送 `main` 后打开 **Actions** 标签，等绿色 ✓
3. 再回到 **Settings → Pages**，应出现绿色链接

若 Source 选了「从分支」而仓库里又有 Actions 工作流，Actions 会报错、网站也会一直 404。

**备选：从分支发布**（需删除 `.github/workflows/pages.yml`）  
- Source：**Deploy from a branch** → `main` → **/ (root)** → Save  

保存后等 1～3 分钟，访问：

`https://你的GitHub用户名.github.io/shaosong/`

首页：`.../shaosong/index.html`  
尧山：`.../shaosong/yaoshan.html`

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
