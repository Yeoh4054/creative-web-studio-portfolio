# Creative Web Studio — QA 与部署审计

日期：2026-11-09。

## 部署及内容

| 项目 | 状态 | 证据 / 范围 |
| --- | --- | --- |
| 新 Vercel 静态项目 | Pass | creative-web-studio-portfolio；Production READY |
| 公共 HTTPS | Pass | https://creative-web-studio-portfolio.vercel.app/ 匿名请求 HTTP 200；HTTP 308 跳转 HTTPS；HSTS |
| 实际部署源码一致性 | Pass | 两页、robots、sitemap、四个资产全部 HTTP 200，下载字节与本地源码逐一一致 |
| 原品牌、八个 section | Pass | Hero、Problem、Solution、Services、Process、Portfolio、FAQ、Final CTA，加 Footer；没有新造内容 |
| 价格、评论、客户及成果 | Pass | 无虚构商业成果或价格；LUNA 明示自主制作的虚构品牌演示 |
| 独立模板库/套餐区 | 不适用 | 原稿没有独立模板库或已确认价格，此次未新增 |
| 示范邮箱 | User verification required | 保留用户要求的 .example 邮箱，明确不接收邮件；不提供虚假发信功能 |
| WhatsApp | Pass / User verification required | 号码 60194884054 与 URL 编码消息检查通过；用户设备上的打开、接收及发送需本人确认，未发送消息 |
| LUNA 外链 | Pass | HTTPS 返回 200；保留直接打开原演示的链接；未改动 LUNA |
| 表单、数据库、付款 | 不适用 | 未添加，询问走 WhatsApp；无假成功提示 |

## 最终版本浏览器响应式测试

使用真实 Chrome 渲染，测试夹具中的同源 iframe 设置为以下 viewport；夹具位于独立 Preview Deployment，未放进 Production。iframe 具有真实独立布局 viewport，滚动条会占用约 15px 内容宽度。最终测试源码与 Production 页面相同，包含对比度修复。

| Viewport | 英文 | 中文 | 横向溢出 | Hero CTA 在首屏 |
| --- | --- | --- | --- | --- |
| 375 × 812 | Pass | Pass | 无 | 是 |
| 390 × 844 | Pass | Pass | 无 | 是 |
| 430 × 932 | Pass | Pass | 无 | 是 |
| 768 × 1024 | Pass | Pass | 无 | 是 |
| 1024 × 1366 | Pass | Pass | 无 | 是 |
| 1280 × 800 | Pass | Pass | 无 | 是 |
| 1440 × 900 | Pass | Pass | 无 | 是 |

另在同一 iframe 上连续调整 320–1600px 并往返经过 900/901、1100/1101 等布局断点；无横向溢出，语言和服务展开状态保留。不是实体手机或平板测试，也不是拖动浏览器外壳窗口。最终版再次覆盖上述七个固定尺寸、中英文共 14 组。

| 交互 / 可访问性 | 状态 | 实际检查 |
| --- | --- | --- |
| 语言切换 | Pass | 中英文真实静态 URL、即时切换、标题、html lang、canonical；最终公开生产页复核 |
| 移动菜单 | Pass | 打开、aria-expanded、锚点跳转后关闭；最终版本复测 |
| FAQ | Pass | 展开目标项，其他项关闭；最终版本复测 |
| 服务详情 | Pass | 原生 details 展开，服务内容及询问链接可用 |
| 法律弹窗 | Pass | 隐私弹窗打开，焦点移入，Escape 关闭 |
| 键盘 | Pass（已查路径） | Tab 可到 FAQ summary，3px 可见焦点；非完整屏幕阅读器审计 |
| 音乐 | Pass / User verification required | 浏览器收到可播放音频（readyState 4、无媒体错误），点击后播放，开关可暂停；不声称已验证用户扬声器。默认尝试播放仍受浏览器自动播放政策限制 |
| 文字动画对比度 | Fixed | 首次桌面 Lighthouse 为 96；部分进入视口的文字透明度太低。保留位移/视差，透明度最低 0.96，复测 Accessibility 100 |
| 动画及鼠标粒子 | Pass（源代码和既有浏览器交互路径） | 保留轻量效果、无重库；未测所有硬件上的帧率或 GPU 开销 |
| Reduced motion | Pass（源代码与 DOM 模拟） | CSS/JS 规则及 reduced-motion=true 模拟通过；浏览器操作系统偏好切换 Not tested |
| 站点 console 错误 | Pass（已测会话） | 未发现站点来源错误；浏览器扩展自身的 metadata 通讯报错单独排除 |
| 图片 | Pass | 无破图，资产字节未变；原图 1333×683。极大屏放大不等于重新生成更高分辨率截图 |
| Safari / Firefox / 实体设备 / 屏幕阅读器 | Not tested | 当前只运行 Chrome 浏览器 |

## Lighthouse / PageSpeed Insights 实测

正式 HTTPS 英文主页，Google PageSpeed Insights，Lighthouse 13.6.0。测量日期 2026-11-09。最初直接 API 调用遇到配额 429，随后通过公开 PageSpeed 网页成功完成测试；以下是网页报告实测值，并非估计分数。

| 最终版本 | Performance | Accessibility | Best Practices | SEO | FCP | LCP | TBT | CLS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Mobile | 100 | 100 | 100 | 100 | 0.9s | 1.2s | 0ms | 0.003 |
| Desktop | 100 | 100 | 100 | 100 | 0.3s | 0.3s | 0ms | 0 |

- Mobile：模拟 Moto G Power，Slow 4G；Desktop：模拟桌面、custom throttling。
- 最终报告：https://pagespeed.web.dev/analysis/https-creative-web-studio-portfolio-vercel-app/c0ap8iqgl9?form_factor=mobile
- Desktop：https://pagespeed.web.dev/analysis/https-creative-web-studio-portfolio-vercel-app/c0ap8iqgl9?form_factor=desktop
- 报告文字已保存到 evidence；自动检查只覆盖部分可访问性问题。
- 初次 Desktop：100 / 96 / 100 / 100；修复透明度后最终四项均 100。
- 中文页面已做布局、交互、metadata 和 HTTP 检查；没有另跑中文 Lighthouse 分数。
- 这是单次实验室加载测试，结果会波动，不能证明滚动和鼠标交互始终达到特定帧率。
- PageSpeed 真实用户数据：No Data。尚无 CrUX/INP 等真实用户 Core Web Vitals 结论。

## SEO 与交付

| 项目 | 状态 |
| --- | --- |
| 两语言静态正文、title、description、canonical、互相 hreflang | Pass |
| 单 H1、标题层级、图片描述、无重复 ID、内部锚点 | Pass（源码） |
| OG / Twitter 分享 metadata 及真实资源 URL | Pass（源码和 HTTP） |
| 实际 WhatsApp/社交应用分享卡呈现 | User verification required；应用缓存可能延迟刷新 |
| JSON-LD | Pass（JSON/字段源码检查）；只包含 WebSite / WebPage，未运行完整外部 Schema validator |
| robots / sitemap | Pass（公开 HTTP 200、XML 可解析、实际生产域名） |
| 一年 immutable 资源缓存、安全头 | Pass（HTTP 响应） |
| GitHub 仓库 | 已建立 https://github.com/Yeoh4054/creative-web-studio-portfolio，源码提交至 main；上传后复核 Git tree |
| GitHub → Vercel 自动部署 | User verification required；待将现有 Vercel 项目连接至源码仓库并验证部署 |
| Google Search Console | User verification required；未登录验证，未提交 sitemap，未请求索引 |
| Google 收录 / 排名 / 流量 | Not tested / 未验证，不作保证 |
| 原生静态源码与离线 HTML | Pass（源码检查）；HTML 以 DOCTYPE 开始、以 html 结束，无构建依赖 |
| 离线 file:// 浏览器打开 | Not tested；当前浏览器不支持访问本地文件。嵌入图片/音频及无外部库已经源码验证 |

详细 Search Console 操作及未来更新方法见 README。

## 剩余阻碍

1. 将现有 Vercel 项目连接至已建立的 GitHub 源码仓库，并验证自动部署；不影响已上线站点。
2. Google 账号登录、Search Console property 验证文件/标签、验证、提交及检查索引。
3. 用户设备验证 WhatsApp 号码接收及消息发送；如需真实邮件联系须提供邮箱。
4. Hobby 只按用户声明的非商业学习演示使用；未来实际商业用途需重新核对计划。无付费升级。

未发现阻止当前演示上线的代码问题。上面未测试或需账号/设备的项目没有标为已完成。
