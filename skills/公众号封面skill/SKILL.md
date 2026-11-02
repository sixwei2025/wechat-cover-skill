---
name: 公众号封面skill
description: >-
  当需要为袁六伟/汇芯红公众号生成黑红金封面（左文右人、右侧真人抠像、2350×1000 母版导出 900×383 与 1:1 方图）时使用。HTML + headless Chrome 渲染；硬闸含真人 IP 露出与对外口径文案。
---

# 公众号封面 Skill（黑红金 · v2b）

> 作者：袁六伟 · 台州汇芯。风格规范见 `references/cover-style-spec.md`；数字上限见 `rules.yaml`。

## 你得到什么
1. **左文右人**黑红金封面：白/金两行大标题 + 红底斜切眉标 + 右侧真人抠像
2. **导出**：`cover_900x383.jpg`（列表）+ `cover_1x1.png`（方图）+ QA 缩略图
3. **默认风格**（六伟 2026-10-17 认可）：`templates/default-brief.json` 只放风格参数；每篇只换内容字段
4. **硬闸**：对外封面必须真人 IP；封面字全对外口径；主色只黑红金白

## 安装
```bash
npx skills add sixwei2025/wechat-cover-skill
```
或把 `skills/公众号封面skill/` 拷进 agent 的 skills 目录。

## 依赖
- Python 3 + Pillow、numpy、scipy、PyYAML
- Google Chrome / Chromium（或设 `CHROME_BIN`）
- 字体：思源黑体 Heavy / Noto Sans CJK SC Black  
  放到 `assets/fonts/NotoSansCJKsc-Black.otf`，或装到系统字体目录

## 流程（给 Agent）
1. 复制 `templates/example-brief-xiaowangzi.json` → 工作区 `cover_brief.json`
2. **只改内容字段**（缺一项脚本 exit 2）：
   - `kicker` ≤16 字
   - `title_lines` 固定 2 行；第1行白陈述/反差，第2行金结论/劝告；每行 ≤9 视觉字
   - `subtitle` ≤14 字（读者一秒懂）
   - `square_badge` ≤8 字
   - `background`：无真人的题材帧（游戏/产品主体），200px 仍能认出
   - `bg_subject_x`：主体在原帧横向 0–1（`layout=fullbleed` 时可省略）
3. 渲染：
```bash
python3 scripts/render_cover.py cover_brief.json --out ./build/cover
```
4. 看 `cover_sheet.png`：200px 上两行标题可读；方图含完整脸
5. 交片用 `cover_900x383.jpg` + `cover.meta.json` 里的 `pic_crop_1_1`

可选对照：`python3 scripts/compare_refs.py --refs <参考封面> --new build/cover/cover_900x383.jpg --out cmp.png`

## 硬闸
| 项 | 要求 |
|---|---|
| 真人 IP | 默认 `assets/owner_cutout_hd.png`；**禁止** `portrait: false` |
| 文案 | kicker/title/subtitle/badge 全对外口径；禁内部选题包装话术 |
| 人像 | 不重绘脸；只内侧弱轮廓光 `rim_strength`≈0.14 |
| 主色 | 黑 / 红 `#C8102E` 系 / 金 / 白；禁蓝紫霓虹、奶油底 |
| 标题 | 固定两行；不压脸；1:1 必须含脸 |

`layout=fullbleed`：整图背景铺满 + 压暗/虚化衬字，**右侧仍保留抠像**（不是去人像）。

## 换人像
```bash
python3 scripts/make_cutout_hd.py --src <原图> --box … --face …
```
放大 3 倍检查发顶、耳朵、下颌、肩膀边缘。

## 目录
```
skills/公众号封面skill/
  SKILL.md
  rules.yaml
  references/cover-style-spec.md
  assets/owner_cutout_hd.png (+ .json)
  templates/cover.html
  templates/default-brief.json
  templates/example-brief-xiaowangzi.json
  scripts/render_cover.py
  scripts/chrome_shot.py
  scripts/rules.py
  scripts/make_cutout_hd.py
  scripts/compare_refs.py
```
