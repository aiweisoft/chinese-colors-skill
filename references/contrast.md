# 色块文字对比度算法

> 来源: chinese-colors 项目 `src/utils.js` 中的 `getCorrectTextColor()`，基于 W3C AERT 亮度公式。

## 何时使用

在深色/浅色色块上放置文字（按钮、色卡标签、横幅文案）时，需要自动选择**深色文字还是浅色文字**保证可读性。

## 算法

```
1. 输入: 背景色 RGB 或 HEX（HEX 需先转 RGB）
2. 计算亮度: cBrightness = (R*299 + G*587 + B*114) / 1000
3. 判断: 亮度 > 130 → 用深色文字 #50616d（墨色）
         亮度 ≤ 130 → 用浅色文字 #e9f1f6（霜色）
```

## 参考实现

```js
// 输入可为 [r,g,b] 数组或 '#rrggbb' 字符串
function getCorrectTextColor(rgb = [0, 0, 0]) {
  if ((typeof rgb === 'string') && rgb.indexOf('#') > -1) {
    rgb = convert.hex.rgb(rgb); // 需 color-convert，或自行解析
  }
  const threshold = 130;
  const [hRed, hGreen, hBlue] = rgb;
  const cBrightness = (hRed * 299 + hGreen * 587 + hBlue * 114) / 1000;
  return cBrightness > threshold ? '#50616d' : '#e9f1f6';
}
```

## 要点

- 阈值 130 约为 256 的一半，调低则更多场景偏向深色文字。
- 返回的两种文字色本身也是传统色（墨色 `#50616d`、霜色 `#e9f1f6`），保证整体风格统一。
- 若需纯黑/纯白文字（如高对比场景），将返回值替换为 `#000000` / `#ffffff` 即可，判断逻辑不变。
- 高精度场景可改用 WCAG 相对亮度公式，但本项目色库场景下该公式足够。
