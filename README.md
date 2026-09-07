# 幻光典藏 · 多卡全息站

在浏览器里拖、转、翻的交互式全息闪卡合集。一张站点、多张卡牌，顶栏即可切换。

**在线预览：** https://ds63.eu.org/holo-card-jingwang/

（`https://euds63.github.io/holo-card-jingwang/` 会跳到同一自定义域。）

---

## 致谢 · 技术来源

本站的分层出卡流水线与实时镭射/视差方案，基于 **[holo-card-studio](https://github.com/EverettFish/holo-card-studio)**（作者 [EverettFish](https://github.com/EverettFish)）这一 Codex Skill。

Skill 负责：四层素材约定、Blender 可编辑场景与材质图、导出几何，以及 Three.js 端按同一 UV 公式重建视差与箔光。本仓库是在该技术上做的**多卡合集站点与具体卡牌产物**（配置、分层图、`card.glb`、切换 UI），并非 Skill 本体本身。

若你也想从描述/参考图生成新卡，请直接使用上游 Skill：

https://github.com/EverettFish/holo-card-studio

浏览器渲染还依赖 [Three.js](https://threejs.org/)（本站通过 jsDelivr CDN 加载 `three@0.180.0`）。

---

## 当前卡牌

| 切换参数 | 标题 | 说明 |
|----------|------|------|
| `?card=fuyunjian` | 抚云间 | 星夜抚琴 · 仙侠风（默认） |
| `?card=peli` | 佩利 | 蓝白战术风 |
| `?card=aoki-hina` | 青木阳菜 | 粉银地雷系自拍抠像 |
| `?card=ditto` | 百变怪 | 粉紫软萌同人 |
| `?card=jingwang` | 静望 | 暖金映画肖像抠像 |

- 顶栏芯片可点选切换（会带上 `?card=` 刷新）。
- 也可直接打开对应链接，例如：  
  https://ds63.eu.org/holo-card-jingwang/?card=fuyunjian

> 部分卡牌为粉丝向同人素材，**不代表任何官方授权或联名**。

---

## 怎么玩

- **拖动 / 方向键**：旋转卡面  
- **滚轮**：缩放  
- **翻面 / `F`**：看背面  
- **复位 / `R`**：恢复默认视角  
- **滑杆**：镭射强度、主体缩放与深度、背景深度  
- **保存此刻**：导出当前画面 PNG  

---

## 本地预览

任意静态服务器即可（不要直接用 `file://`，否则模块与贴图可能加载失败）：

```bash
python3 -m http.server 8080
# 然后打开 http://127.0.0.1:8080/?card=fuyunjian
```

---

## 目录结构

```
.
├── index.html          # 页面壳 + Three importmap
├── app.js              # 多卡加载 / 切换 / 着色器合成
├── style.css
├── cards.json          # 卡牌目录（id / 标题 / config 路径）
├── .nojekyll           # 让 GitHub Pages 原样托管静态资源
└── cards/
    ├── fuyunjian/
    ├── peli/
    ├── aoki-hina/
    ├── ditto/
    └── jingwang/
        ├── card-config.json
        └── assets/
            ├── subject.png
            ├── background.png
            ├── lineart.png
            ├── text.png
            └── card.glb
```

每张卡的 `card-config.json` 里，资源路径相对于**该卡目录**（如 `./assets/subject.png`）。`app.js` 会按当前卡的 config 位置解析绝对路径。

新增一张卡时：放入 `cards/<id>/`，并在 `cards.json` 增加一项即可。

---

## 流水线简述

1. 准备同尺寸四层图：背景 / 主体（真 alpha）/ 线稿 / 文字  
2. 用 holo-card-studio 脚本校验素材、生成 Blender 场景并导出 `card.glb`  
3. 拷入本站 `cards/<id>/`，更新 `cards.json`  
4. 静态托管（本仓库使用 GitHub Pages：`main` + `/`）

---

## License 与素材

- 上游 Skill 的许可证见：https://github.com/EverettFish/holo-card-studio/blob/main/LICENSE  
- 本仓库中的卡牌图像与页面改动：除另有说明外，仅供个人展示与学习；涉及第三方角色/肖像的素材请自行确认使用权。
