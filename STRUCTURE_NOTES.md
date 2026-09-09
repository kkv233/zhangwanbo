# Structure Notes

当前仓库是 `Wanbo Zhang (Kc.)` 个人主页的静态导出版本。

这份文档记录的是仓库真实现状，方便后续维护时快速定位入口文件、页面结构和常见修改点。

## 1. 项目形态

- 站点类型：静态导出站点
- 当前入口：`index.html`
- 资源目录：`images/`、`_next/static/`
- 部署方式：直接用仓库根目录发布到 GitHub Pages
- 当前仓库不包含完整的 Next.js 源码、`package.json`、`styles.css`、`script.js`

结论：

- 页面内容的第一编辑入口是 `index.html`
- 样式和大部分交互已经被打包进 `_next/static/chunks/*.js` 和 `_next/static/chunks/*.css`
- 根文件末尾还包含一段内联 `style` 和 `script`，用于 splash opening 动画

## 2. 页面元信息

- Title: `Wanbo Zhang (Kc.) | Homepage`
- Meta description: `Personal homepage of Wanbo Zhang (Kc.). Research on Large Language Models in Finance, LLM evaluation, agent cognition, and applied AI. HKUST(GZ) Fintech PhD Incoming.`
- 语言：`en`

## 3. 关键文件

- `index.html`
  页面主体。导航、各 section、footer、内联 splash 动画都在这里。

- `images/`
  本地图片资源目录。当前页面引用了头像、论文图、学校 logo、兴趣图、二维码等。

- `_next/static/`
  构建输出目录。包含站点运行所需的 JS、CSS 和字体文件。

- `Wanbo_Zhang_CV.pdf`
  当前站点引用的 CV 文件。

- `.nojekyll`
  GitHub Pages 所需，避免 `_next/` 被 Jekyll 忽略。

## 4. 页面结构

页面主导航锚点如下：

- `#home`
- `#publications`
- `#journey`
- `#awards`

### 4.1 Navigation

顶部导航是固定定位的单页导航，包含：

- 首页入口 `#home`
- `Home`
- `Publications`
- `Experience`，链接到 `#journey`
- `Awards`
- 联系方式图标

### 4.2 Home

`#home` 是首屏区域，当前主要包含：

- `Wanbo Zhang` 的标题与自我介绍
- 研究方向概览
- 教育信息模块
- 头像与联系入口
- 外部链接与 CV 入口

当前首页对外链接包括：

- `mailto:23302010062@m.fudan.edu.cn`
- `https://github.com/kkv233`
- `https://orcid.org/0009-0008-2926-9624`
- `https://scholar.google.com/citations?user=Nlt4wAYAAAAJ&hl=zh-CN&authuser=1`
- `https://space.bilibili.com/3494360431725516?spm_id_from=333.1007.0.0`
- `https://cs.fudan.edu.cn/dky/`
- `Wanbo_Zhang_CV.pdf`

### 4.3 Publications

`#publications` 当前是代表性论文卡片区域，页面中可见的论文标题包括：

- `Towards Efficient LLMs Annealing with Principled Sample Selection`
- `UniG2U-Bench: Do Unified Models Advance Multimodal Understanding?`
- `Understanding the Limitations of Neural SDEs under Shifting Data-Generating Processes`

这一块通常需要同步修改：

- 论文标题
- 作者顺序
- venue / status / tag
- 缩略图路径
- 外链按钮

### 4.4 Journey

`#journey` 是时间线区域，当前包含：

- Fudan 本科阶段
- Data-centric LLM research 开始时间点
- IJCAI / ICML / ECCV 相关进展节点

这是最适合放教育、研究经历和阶段性 milestone 的区域。

### 4.5 Awards

`#awards` 当前包含：

- 奖项列表
- `Reviewer Service` 标题区

当前可见奖项数量不多，因此这个区域维护成本较低，通常是追加新条目或更新时间。

### 4.6 Footer

页脚包含：

- `Built with ... by zwb.` 签名
- 兴趣标签
- 版权信息
- 个性化收尾文案

## 5. Splash 动画

`index.html` 末尾包含一个独立的 splash overlay：

- 容器 ID：`zwb-splash`
- 作用：页面加载时展示几行终端风格文本和一段中文文案
- 实现方式：根文件末尾的内联 `style` + 立即执行脚本

如果要移除或修改开场效果，优先搜索：

- `#zwb-splash`
- `zwb-splash-quote`
- `showNext`

## 6. 当前资源引用特征

当前页面资源有两类：

- 本地静态资源
  例如 `images/my_picture.png`、`images/fudan.png`、`images/icml26.png`、`images/wechat.jpg`

- 构建产物资源
  例如 `_next/static/chunks/*.js`、`_next/static/chunks/*.css`、`_next/static/media/*.woff2`

维护时应注意：

- 不要随意删除 `_next/static/`，否则页面样式和交互会失效
- 替换图片时尽量沿用原路径，避免还要改动压缩后的 HTML

## 7. 当前维护策略

如果只是更新主页内容，推荐方式如下：

1. 改文字内容：直接改 `index.html`
2. 改头像、论文图、二维码：直接替换 `images/` 中对应文件，或改 HTML 中的资源路径
3. 改简历：替换 `Wanbo_Zhang_CV.pdf`
4. 改开场动画：编辑 `index.html` 末尾的内联 `style` 和 `script`

## 8. 风险提示

- `index.html` 是导出后的成品文件，内容被压缩，可读性一般
- 当前仓库没有原始组件源码，复杂改版会比较费力
- 如果后续要长期维护，建议把源工程一并保存，静态导出产物只用于部署

## 9. 推荐的后续整理方向

- 把 `index.html` 做一次可读化或恢复为源码结构
- 建立图片命名规范，减少临时命名
- 将论文、经历、奖项抽成单独数据源，降低手改 HTML 的成本
