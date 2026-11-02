# 公众号封面 Skill（wechat-cover-skill）

> 🔴 **作者：袁六伟 · 台州汇芯**｜一人 AI 公司创业者，学员 7000+，客户 100+，得到/华为分享老师  
> 📮 更多 AI 工具实测与自动化实战，关注 **公众号 / 视频号：袁六伟**

黑红金公众号封面：左侧两行大字（白+金），右侧真人精修抠像。HTML 模板经 headless Chrome 渲染，2350×1000 母版导出 **900×383** 横封面和带脸的 **1:1** 方图。

## 效果展示

| | |
|:---:|:---:|
| ![gold](assets/showcase/01-gold-menping-kehu.jpg) | ![wb](assets/showcase/02-gold-workbuddy-laowai.jpg) |
| 金标准 · 门槛/客户 | 金标准 · WorkBuddy |
| ![trae](assets/showcase/03-sample-trae.jpg) | |
| 实产样张 · Trae | |

## 安装

```bash
npx skills add sixwei2025/wechat-cover-skill
```

也可把 `skills/公众号封面skill/` 整个文件夹拷进 agent 的 skills 目录（Claude Code / Codex / Cursor / WorkBuddy 等支持 `SKILL.md` 即可）。

## 依赖

- Python 3：`Pillow` `numpy` `scipy` `PyYAML`
- Chrome / Chromium（或环境变量 `CHROME_BIN`）
- 字体：Noto Sans CJK SC Black / 思源黑体 Heavy → 放到 skill 内 `assets/fonts/NotoSansCJKsc-Black.otf`

## 快速开始

对 agent 说：

> 用「公众号封面skill」，按默认黑红金风格出封面：眉标……，两行标题……，副标题……，角标……，背景用这张图。

或本地：

```bash
cp skills/公众号封面skill/templates/example-brief-xiaowangzi.json ./cover_brief.json
# 编辑内容字段后：
python3 skills/公众号封面skill/scripts/render_cover.py ./cover_brief.json --out ./build/cover
```

## 目录

```
README.md
LICENSE
assets/showcase/                 # 预览图
skills/公众号封面skill/
  SKILL.md
  rules.yaml                     # 封面数字上限
  references/cover-style-spec.md
  assets/                        # 抠像 + 示例背景帧
  templates/
  scripts/
```

## 硬规则摘要

- 对外封面**必须**右侧真人 IP 露出（禁止藏人像）
- 标题固定两行；主色只黑红金白
- 本仓库**不含**微信 AppSecret / 群发脚本；封面只做素材

## 许可

MIT。人像与品牌素材版权归袁六伟 / 台州汇芯；第三方商标归各自权利人。

---

## 关于作者

**袁六伟 · 台州汇芯**：一人 AI 公司创业者。公众号 / 视频号：**袁六伟**。

这个 Skill 免费开源。有用的话欢迎 ⭐ Star，再关注「袁六伟」看更多实战。
