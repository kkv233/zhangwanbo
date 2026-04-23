# Zhang Wanbo Homepage

个人主页静态站点，可直接部署到 GitHub Pages。

当前仓库保存的是已经导出的站点产物，而不是完整的 Next.js 源码工程。页面真实内容以 `index.html` 为准，样式和交互逻辑主要打包在 `_next/static/` 中。

## 仓库结构

- `index.html`: 主页入口文件，包含当前页面主体内容和一小段内联 splash 动画脚本
- `images/`: 页面使用的本地图像资源，包括头像、论文配图、学校/项目 logo、二维码等
- `_next/static/`: 导出后的前端静态资源，包括 JS、CSS、字体等构建产物
- `Wanbo_Zhang_CV.pdf`: 页面引用的 CV 文件
- `favicon.ico`: 站点图标
- `.nojekyll`: GitHub Pages 配置文件，避免 `_next/` 目录被 Jekyll 特殊处理
- `STRUCTURE_NOTES.md`: 当前页面结构和维护说明

## 当前页面分区

- `#home`: 个人介绍、研究方向、教育信息、头像与联系入口
- `#publications`: 代表性论文卡片
- `#journey`: 时间线式经历与研究进展
- `#awards`: 奖项与 reviewer service
- `footer`: 页脚签名、兴趣标签与收尾文案

## 本地预览

```bash
python -m http.server 8000
```

打开 `http://localhost:8000` 即可预览。

## GitHub Pages 部署

1. 推送仓库到 GitHub。
2. 进入仓库 `Settings` -> `Pages`。
3. 在 `Build and deployment` 中选择：
   - `Source`: `Deploy from a branch`
   - `Branch`: `main`（或你的默认分支）
   - `Folder`: `/ (root)`
4. 保存并等待部署完成。

## 维护建议

- 修改个人信息、论文、经历、奖项、链接：直接编辑 `index.html`
- 替换图片或 PDF：更新 `images/` 或根目录中的对应文件，并保持路径不变
- 当前 `index.html` 是导出后的成品文件，可维护性一般；如果后续要频繁迭代，建议把源工程一并纳入仓库
