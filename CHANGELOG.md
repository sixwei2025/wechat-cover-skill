# 更新日志

## v1.1.0 · 2026-11-13

- **新增 6 套差异化构图版式（Layout）**：升级 `render_cover_themes.py` 为「6 套视觉体系 × 6 种构图版式」（`editorial` 经典杂志双栏 / `masthead` 大刊报头破框 / `archive-card` 档案相框卡片 / `swiss-grid` 瑞士细线网格 / `duotone-split` 硬切双色对撞 / `cinema` 电影宽银幕），支持 `--layout` 自由混搭。
- **强化真人 IP 与品牌露出**：全版式强制保留真人形象照且不切头，新增「袁六伟 · 台州汇芯」品牌印章/铭牌与身份短签视觉锚点。
- **新增 Headless Chrome 原生渲染兜底**：无 Python `playwright` 包时自动回退至 Chrome `--headless=new` 渲染与 DOM 量测，零依赖稳定出图；100% 向后兼容原有参数。

## v1.0.0 · 2026-11-13

- 建立可追踪的版本记录，README、Skill 文件和 Git 标签保持一致。
- 后续功能变化、修复和兼容性调整会持续记录在本文件。

