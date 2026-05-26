# 绍宋 · 战役沙盘（手机离线版）

## 最重要：怎么在手机上打开

每场战役都是 **一个独立的 .html 文件**，里面已经写好了全部代码，**不依赖 shared 文件夹、不需要联网**。

解压 zip 后，在文件夹里**直接点开**：

| 文件 | 内容 |
|------|------|
| `index.html` | 目录（可选） |
| `yaoshan.html` | 尧山之战 |
| `taiyuan.html` | 太原破城 |
| `huolu.html` | 获鹿决战 |

若从 `index.html` 点链接打不开，**不要管首页**，直接去文件管理器里点 `taiyuan.html` 或 `huolu.html`。

- 用 **系统浏览器**（Safari / Chrome）
- **不要**只在微信里「预览」单个文件
- 可以只发某一个 html 给朋友（例如只发 `taiyuan.html` 也能用）

`yaoshan/index.html` 与根目录的 `yaoshan.html` 内容相同，任选其一即可。

## 动画怎么用

- **🎬 动画播放**：从当前阶段自动播到结尾（兵力移动 + 旁白切换）
- **▶ 分步播放**：每阶段停一会儿，适合细读
- **← / →**：瞬间切阶段（无动画）
- 可关闭「阶段过渡动画」恢复瞬间切换

## 电脑

双击任意 html 即可。

## 重新打包

修改内容后可在电脑上运行：

```bash
python tools/build-standalone.py
```

会重新生成单文件的 `taiyuan.html`、`huolu.html`。
