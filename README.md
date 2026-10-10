# 山东拜森机械有限公司官网 (Jinan Bison Machinery Co., Ltd. Website)

基于 [Storm Vehicle](https://www.stormvehicle.com/) 风格设计的现代化企业官网，响应式支持手机与电脑，纯静态 HTML/CSS/JS，全球可访问。

## 项目结构

```
bison-machinery/
├── index.html          # 首页
├── products.html       # 产品页
├── about.html          # 关于我们
├── contact.html        # 联系我们（表单）
├── news.html           # 新闻动态
├── css/
│   └── style.css       # 自定义样式
├── js/
│   └── main.js         # 交互脚本（菜单、动画、表单）
├── images/             # 预留本地图片目录（当前使用 Unsplash 外链）
└── README.md           # 本说明
```

## 主要特性

- **响应式设计**：手机 / 平板 / 桌面自适应（Tailwind CSS）
- **Logo 占位**：头部与页脚均有虚线框 “LOGO HERE”，替换即可
- **联系方式待定**：电话、邮箱、WhatsApp 均标注 TBD，后续修改
- **动画**：AOS 滚动动画
- **表单**：联系页表单前端演示（需接后端才真正发邮件）
- **图片**：使用 Unsplash 公开图（卡车、半挂、工厂），可自行替换为公司实拍或 Storm 站点图片链接

## 本地预览（自己运行看效果）

### 方法一：直接双击（最简单）
1. 解压或进入 `bison-machinery` 文件夹
2. 用浏览器打开 `index.html`（Chrome / Edge / Firefox 均可）
3. 注意：部分浏览器对本地 `file://` 协议限制外链字体/图片，推荐用下面方法二

### 方法二：本地静态服务器（推荐）

**Python 3（几乎都有）：**
```bash
cd bison-machinery
python3 -m http.server 8080
```
浏览器访问：http://localhost:8080

**Node.js：**
```bash
npx serve .
# 或
npx http-server -p 8080
```

**VS Code：**
安装插件 “Live Server”，右键 `index.html` → Open with Live Server

## 部署到全球可访问（详细教程）

静态网站部署非常简单，以下任选一种，**免费**且全球 CDN。

### 方案 A：Netlify（推荐，拖拽即用，最快）

1. 注册账号：https://www.netlify.com （可用 GitHub / 邮箱）
2. 登录后进入 Dashboard → **Add new site** → **Deploy manually**
3. 把整个 `bison-machinery` 文件夹拖进上传区域
4. 等待几秒，会得到类似 `https://随机名.netlify.app` 的网址
5. （可选）在 Site settings → Domain management 绑定自己的域名（如 `www.bisonmachinery.com`）

**后续更新：** 直接再拖一次新文件夹覆盖即可，或连接 GitHub 自动部署。

### 方案 B：Vercel

1. 注册：https://vercel.com
2. 安装 Vercel CLI 或直接用网页：
   - 网页：New Project → 上传文件夹 / 导入 Git
3. 部署后获得 `*.vercel.app` 地址，可绑自定义域名

### 方案 C：GitHub Pages（免费、长期稳定）

1. 注册 GitHub，新建一个仓库（例如 `bison-machinery`），设为 Public
2. 把项目文件上传到仓库根目录（或 `docs/` 文件夹）
3. 仓库 Settings → Pages → Source 选 `Deploy from a branch` → 选 `main` / `master`，文件夹 `/ (root)` 或 `/docs`
4. 保存后等待 1–2 分钟，访问 `https://你的用户名.github.io/仓库名/`

**命令行上传示例：**
```bash
cd bison-machinery
git init
git add .
git commit -m "Initial Bison Machinery website"
git branch -M main
git remote add origin https://github.com/你的用户名/bison-machinery.git
git push -u origin main
```

### 方案 D：自己服务器 / 阿里云 / 腾讯云 / 宝塔

1. 买一台轻量服务器（或使用已有）
2. 安装 Nginx：
   ```bash
   sudo apt update
   sudo apt install nginx
   ```
3. 把整个文件夹上传到 `/var/www/bison`（用 scp / FileZilla / 宝塔面板）
4. 配置 Nginx：
   ```nginx
   server {
       listen 80;
       server_name yourdomain.com www.yourdomain.com;
       root /var/www/bison;
       index index.html;
       location / {
           try_files $uri $uri/ /index.html;
       }
   }
   ```
5. 重启 Nginx：`sudo systemctl reload nginx`
6. 绑定域名 + 免费 SSL（Let’s Encrypt / 宝塔一键）

### 方案 E：Cloudflare Pages（全球加速最好）

1. 注册 Cloudflare，连接 GitHub 仓库
2. 创建 Pages 项目，选仓库，Build 命令留空，输出目录留空（纯静态）
3. 部署完成，自动全球 CDN

## 你需要自己做的修改清单

1. **替换 Logo**
   - 把公司 logo 图片放到 `images/logo.png`（建议透明 PNG，高度约 60–80px）
   - 在所有 HTML 里找到：
     ```html
     <div ...>LOGO<br>HERE</div>
     ```
     替换为：
     ```html
     <img src="images/logo.png" alt="山东拜森机械" class="h-12 lg:h-14 w-auto">
     ```
   - 页脚同理

2. **更新联系方式**
   - 搜索全文 `TBD` 或 `Phone: TBD` / `Email: TBD`
   - 替换为真实电话、邮箱、WhatsApp 链接（格式示例）：
     ```html
     <a href="tel:+86138xxxxxxxx">+86 138 xxxx xxxx</a>
     <a href="mailto:info@bison.com">info@bison.com</a>
     <a href="https://wa.me/86138xxxxxxxx">WhatsApp</a>
     ```

3. **公司地址、关于内容**
   - 编辑 `about.html` 和 `contact.html` 中的地址与介绍文字

4. **产品图片与描述**
   - 当前用 Unsplash 外链，可下载自己的实拍图放到 `images/`，然后改 `src`
   - 产品详情可继续扩展成单独页面

5. **表单真正发送邮件**
   - 当前只是前端演示
   - 推荐：Formspree（https://formspree.io）免费额度，或 Netlify Forms，或自建后端（PHP / Node）

6. **域名与备案（中国大陆访问）**
   - 如果主要服务海外，Netlify/Vercel/Cloudflare 即可
   - 如果需要中国大陆快速访问，建议国内服务器 + ICP 备案

## 技术栈

- HTML5 + Tailwind CSS（CDN）
- 自定义 CSS
- 原生 JavaScript
- AOS 动画库
- Google Fonts（Anton + Poppins）
- 图片：Unsplash（可替换）

## 后续可扩展

- 增加产品详情页
- 多语言（中/英切换）
- 真实后台 CMS（如 Strapi、WordPress 无头模式）
- Google Analytics / 百度统计
- WhatsApp 浮动按钮真实号码
- SEO meta、sitemap.xml、robots.txt

## 许可与使用

本网站模板为你公司定制，可自由修改、商用。图片来自 Unsplash（免费商用），请遵守其协议。设计参考了 Storm Vehicle 的布局与风格，但代码完全重新编写。

---

**生成日期：** 2026-10-10  
**联系方式待补充后即可正式上线。**

有任何修改需求（加页面、改颜色、加中文版等）直接告诉我即可。
