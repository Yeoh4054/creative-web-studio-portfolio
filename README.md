# Creative Web Studio — 交付及更新说明

交付日期：2026-11-09。个人、非商业学习作品集演示。

## 已上线

- 英文：https://creative-web-studio-portfolio.vercel.app/
- 简体中文：https://creative-web-studio-portfolio.vercel.app/zh/
- Sitemap：https://creative-web-studio-portfolio.vercel.app/sitemap.xml
- Robots：https://creative-web-studio-portfolio.vercel.app/robots.txt
- 新建 Vercel 项目：creative-web-studio-portfolio。部署已 READY，公开 HTTPS 可访问。
- 未修改 LUNA 或其他现有项目，未购买域名或启用付费订阅。

## 文件与使用

这是原生静态网站，无框架、npm、数据库或构建步骤。

- `index.html`：可索引的英文页面。
- `zh/index.html`：可索引的简体中文页面。
- `assets/`：原有截图、原有音乐、CW favicon，以及品牌社交分享图。
- `vercel.json`：静态路由、安全响应头及资源缓存配置。
- `robots.txt`、`sitemap.xml`：搜索引擎入口。
- `QA-REPORT.md`：实际测试记录、限制及下一步。
- `evidence/`：源代码检查、HTTP 检查及实测结果文本。

网站托管版的图片及音乐引用 `/assets/`；请保留目录结构并通过 HTTP/HTTPS 访问，不要仅复制根 HTML。另附独立的离线展示版 `index.html`，图片及音乐均嵌入该文件，下载后可直接在浏览器打开；WhatsApp、LUNA 演示及版权来源链接仍需互联网。离线展示版不代替线上双语目录、robots 或 sitemap。

## 保留与优化

保留既有品牌配色、字体、布局、八个主要 section、服务展开、LUNA 直接预览链接、FAQ、移动菜单、语言切换、页脚法律说明、音乐与鼠标粒子。没有加入原稿不存在的模板库、价格套餐、假评论或案例成果。

原文件中的同一张 1333×683 WebP 截图和同一段音乐以原始字节提取为共享文件，未改变质量；HTML 由约 1.60 MB 降为英文约 91 KB、中文约 90 KB。这是 HTML 大小变化，不是整个网站的总下载量减少 94%。音乐仍约 1.08 MB，延后到初始页面加载后尝试播放。浏览器可要求首次点击才允许有声播放，页面会如实提示。

滚动脚本先集中读取布局，再更新样式，减少交错读写。文字保留滚动位移，但渐显透明度限制在 0.96–1，避免屏幕边缘文字对比度不足。保留视差、轻量交互与 reduced-motion 规则。

## SEO

- EN、ZH 各自具有静态内容、独立标题、描述、canonical。
- 语言切换保留即时体验，并使用真实 `/` 与 `/zh/` 链接；关闭 JS 也能切换。
- 两页互相声明 `en-MY`、`zh-Hans-MY` 与 `x-default` hreflang。
- Open Graph、Twitter/X metadata 与 1200×630 分享图。
- 每页单一 H1，语义标题、图片描述、可用内部锚点。
- 只使用真实的 WebSite / WebPage JSON-LD；没有评分、评论、虚构地址或客户 schema。
- robots 允许抓取，sitemap 列出两种语言 URL。
- 内容哈希资源缓存一年；HTML、robots、sitemap 可重新验证。

这些配置改善抓取与理解，不保证收录、排名或客户询问。Lighthouse SEO 100 不是 Google 排名分数。

## 联系方式与内容维护

确认 WhatsApp：`60194884054`。保留每个服务的 URL 编码询问消息；不要替换成示例号码。

`hello@creativewebstudio.example` 是用户先前要求的展示邮箱，已明确标注不接收邮件，故没有假装可发信的按钮。未来提供真实邮箱后才能作为联系渠道。

LUNA 是自主制作的虚构品牌演示，不是付费客户案例。AIGC 与 AI 广告图保持“计划推出”。没有发布未确认价格或保证。

## 以后更新网站

1. 备份本次 ZIP。英文和中文 HTML 中的可翻译文字带 `data-en` / `data-zh`；修改时同步更新两个文件的静态文字、对应属性与必要的标题/描述。
2. 修改 CSS / JS 时，同步两份 HTML。保持 WhatsApp 与演示链接正确。不要把离线版覆盖线上英文页，否则会丢失托管版的语言 URL 行为。
3. 新图片压成合适尺寸的 WebP；替换资源时使用新文件名并更新两页引用，避免一年缓存继续显示旧图。保留字体为系统字体。
4. 先在新 Preview Deployment 测试手机、平板、桌面、双语、菜单、FAQ、动画及音乐，再发布到本项目 Production。
5. GitHub 连接完成后，提交到连接的生产分支可触发 Vercel 自动部署。当前源码仓库已建立，Vercel Git 连接仍待完成；当前公开站点由直接静态文件部署。
6. 需要手动部署时，只选择本项目 `creative-web-studio-portfolio`，Framework 选 Other，关闭 build/install，发布根目录；不要选择 LUNA。当前页面不需要环境变量。
7. 新增页面或改域名时，同时更新 canonical、hreflang、OG URL、JSON-LD、robots 和 sitemap。

## GitHub 源码与待完成连接

源码仓库：https://github.com/Yeoh4054/creative-web-studio-portfolio

生产分支：`main`。已创建仓库并将经过 QA 的静态网站源码提交至该分支。原始初始提交保留在历史中；未触碰 LUNA 仓库。

Vercel 自动部署连接尚未完成。请打开 Vercel 现有项目 `creative-web-studio-portfolio` → Settings → Git → Connect Git Repository，选择 GitHub 账号 Yeoh4054 下的同名仓库。不要另建/导入第二个 Vercel 项目，也不要选择 LUNA。保持根目录为仓库根目录、Framework 为 Other、无需 build/install。连接后需检查 `main` 为 Production Branch，并验证一次来自 GitHub 的部署成功，才可确认自动部署已完成。

不要在聊天中发送密码、OTP 或 token。

## Search Console：需要 Google 账号操作

当前尚未建立/验证 property、提交 sitemap 或请求索引，Google 收录状态未验证。

1. 打开 https://search.google.com/search-console/ 并登录要管理网站的 Google 账号。
2. 添加 **URL prefix（网址前缀）** property，准确填写 `https://creative-web-studio-portfolio.vercel.app/`；不要添加整个 `vercel.app` Domain property。
3. 选择 **HTML 文件** 验证，下载 Google 提供的实际 `google….html` 文件。将原文件提供给开发者，加入部署根目录并部署；保持文件名及验证文字不变。不要自造验证文件。
4. 确认 Google 显示的验证文件 URL 可公开访问，回到 Search Console 点 Verify。验证文件应保留在后续部署中。
5. 在 Sitemaps 中提交 `sitemap.xml`，查看是否成功读取。当前 sitemap 本身已经线上 HTTP 200。
6. 在 URL Inspection 分别输入英文主页与 `/zh/`，运行 Test live URL；如允许，点 Request indexing。这不保证立即收录。
7. 在 Pages 查看已索引/未索引及具体原因；在 Performance 查看 Impressions（展示次数）、Clicks（点击）、Average CTR（点击/展示）、Average Position（平均位置）及 Queries（搜索词）。新站可能暂时没有数据。

官方说明：

- https://support.google.com/webmasters/answer/34592
- https://support.google.com/webmasters/answer/9008080
- https://developers.google.com/search/docs/specialty/international/localized-versions

## 音乐版权与计划边界

保留原有 Scott Buckley 的 “Reverie”，CC BY 4.0，90 秒剪辑、淡入淡出及音频压缩；网站页脚保留作品、作者、许可及改编说明。不要移除署名。

当前项目按用户声明作为个人、非商业学习演示使用 Vercel Hobby。Hobby 的非商业用途限制仍适用；如果以后改成实际商业获客/销售站，应重新核对 Vercel 计划规则。此次没有升级或产生付费订阅。

规则来源：https://vercel.com/docs/plans/hobby
