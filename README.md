# Chinese Colors Skill

> opencode Skill：中国传统色查询与中国风配色方案

基于 [zerosoul/chinese-colors](https://github.com/zerosoul/chinese-colors) 项目提炼的 opencode skill，内置 **9 大色系、161 种中国传统色** 的权威色值（HEX/RGB）与文化注解，让 AI 在设计任务中自动使用正宗的中国传统色。

## 功能

- **查色**：按色名查询具体色值和文化含义（如「竹青」→ `#789262`「竹子的绿色」）
- **色系浏览**：红色系、黄色系、蓝色系等 9 大色系
- **中国风配色**：国潮、新中式、水墨、宫廷、江南等风格自动配色，输出带文化注脚的方案
- **对比色计算**：根据背景色亮度自动选择深/浅文字色（墨色 `#50616d` / 霜色 `#e9f1f6`）

## 安装

```bash
# 方法一：克隆到全局 skill 目录
git clone https://github.com/aiweisoft/chinese-colors-skill.git
# Windows: 放到 ~\.config\opencode\skills\chinese-colors\
# macOS/Linux: 放到 ~/.config/opencode/skills/chinese-colors/
```

或手动将 `SKILL.md`、`colors.json`、`references/` 复制到 `~/.config/opencode/skills/chinese-colors/` 下，然后 **重启 opencode** 生效。

## 触发场景

| 触发词 | 示例 |
|---|---|
| 中国传统色 / 传统色 | 「中国传统色有哪些好看的蓝」 |
| 中国风 / 国潮 / 国风配色 | 「给我一个国潮落地页配色」 |
| 新中式 / 水墨 / 古风设计 | 「水墨风格的 PPT 配色」 |
| 具体色名（黛蓝/朱砂/月白等） | 「胭脂是什么颜色」 |
| Chinese traditional colors | 「Oriental palette for a poster」 |

## 数据结构

`colors.json` 结构：

```jsonc
{
  "name": "红色系",              // 色系名
  "hex": "#ffb3a7",             // 色系代表色
  "RGB": [255, 179, 167],       // 代表色 RGB
  "id": 0,
  "colors": [
    {
      "id": "0-0",
      "hex": "#ffb3a7",          // 具体颜色 HEX
      "name": "粉红",             // 颜色名
      "intro": "即浅红色。别称：妃色、杨妃色、湘妃色、妃红色"  // 文化注解
    }
  ]
}
```

## 目录结构

```
chinese-colors/
├── SKILL.md              # 技能定义（触发词 + 查询工作流 + 输出规范）
├── colors.json           # 161 种传统色数据
└── references/
    └── contrast.md       # 色块文字对比度算法
```

## 许可

数据与算法源自 [chinese-colors](https://github.com/zerosoul/chinese-colors)（ISC License），Skill 封装亦以 ISC 协议开源。

## License

[MIT](LICENSE)
