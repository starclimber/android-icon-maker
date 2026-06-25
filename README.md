# Android Icon Maker / 安卓图标生成器

将任意图片（JPG/PNG）转换为 Android 应用图标，自动裁剪为圆形并生成全套 mipmap 分辨率。

---

## 功能 | Features

- 🖼️ **支持格式**：JPG / PNG 输入
- ⭕ **圆形裁剪**：自动居中裁剪为圆形，边缘平滑
- 📱 **全套分辨率**：自动生成 mdpi / hdpi / xhdpi / xxhdpi / xxxhdpi 五个密度版本
- 🛠️ **Python + Pillow**：纯 Python 实现，无需 Node.js 或额外依赖

---

## 输出规格 | Output Specs

| 密度 | 倍率 | 尺寸 |
|------|------|------|
| mdpi | 1× | 48×48 |
| hdpi | 1.5× | 72×72 |
| xhdpi | 2× | 96×96 |
| xxhdpi | 3× | 144×144 |
| xxxhdpi | 4× | 192×192 |

---

## 安装依赖 | Install Dependencies

```bash
pip install pillow
# Linux 如果报错，加：
pip install pillow --break-system-packages
```

---

## 使用方法 | Usage

```bash
python3 scripts/make_round_icon.py <图片路径> <输出目录> [基准尺寸]
```

**示例 | Examples**：

```bash
# 使用默认输出目录（android_icons/）
python3 scripts/make_round_icon.py photo.jpg

# 指定输出目录
python3 scripts/make_round_icon.py photo.jpg ./my_app_icons

# 指定基准尺寸（dp）
python3 scripts/make_round_icon.py photo.jpg ./icons 48
```

**输出文件 | Output**：
```
output_dir/
├── icon_mdpi.png    (48×48)
├── icon_hdpi.png    (72×72)
├── icon_xhdpi.png   (96×96)
├── icon_xxhdpi.png  (144×144)
└── icon_xxxhd.png   (192×192)
```

---

## OpenClaw Skill 触发方式 | OpenClaw Skill Triggers

在 OpenClaw AI 助手中发送图片并说：

**中文**：做成 App 图标 / 生成安卓图标 / 做个图标吧 / 图片转图标 / 安卓图标生成器

**English**：make this an app icon / generate android icon / convert to android icon / android icon maker

---

## 复制到 Android 项目 | Copy to Your Android Project

生成后，将对应密度的图标文件复制到 Android 项目的 `app/src/main/res/mipmap-*/` 目录：

```
your-android-project/
└── app/
    └── src/
        └── main/
            └── res/
                ├── mipmap-mdpi/    ic_launcher.png    (48×48)
                ├── mipmap-hdpi/    ic_launcher.png    (72×72)
                ├── mipmap-xhdpi/   ic_launcher.png    (96×96)
                ├── mipmap-xxhdpi/  ic_launcher.png   (144×144)
                └── mipmap-xxxhdpi/ ic_launcher.png   (192×192)
```

---

## 技术细节 | Technical Details

- **裁剪算法**：居中正方形裁剪 + LANCZOS 缩放，质量优先
- **透明通道**：保留 RGBA 透明通道，圆形区域外为透明
- **圆形蒙版**：ImageDraw 绘制圆形蒙版，边缘平滑
- **无需 Java/Gradle**：纯 Python 脚本，直接调用 Pillow

---

## License

MIT-0 — Free to use, modify, and redistribute. No attribution required.

## Links

- 🏪 ClawHub: https://clawhub.ai/starclimber/skills/android-icon-maker
- 💻 GitHub: https://github.com/starclimber/android-icon-maker
