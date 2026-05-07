# jmrlzw

> Beta: Play MIDI Online

---

JMR 与 LZW 的专属静态页面。访问地址：<https://jiangmuran.com/jmrlzw/>

## 这是什么

一页复古收据风格的纪念页，记录：

- JMR 对 LZW 的喜欢时长（从 2024/08/07 开始计时）
- LZW 生日倒计时（09/26）
- 生日当天自动触发的彩纸 + 蛋糕特效
- 条形码彩蛋（点击后播放打字机动画的长信）
- 背景音乐控制（Sunny Day）

## 文件

| 文件 | 说明 |
|---|---|
| `index.html` | 页面本体，包含全部样式、结构和脚本 |
| `bulr.jpg` | 左侧宝丽来装饰照片（仅桌面端加载，手机端不请求） |
| `audio/sunny.mp3` | Track I · Sunny |
| `audio/distance.aac` | Track II · Distance |
| `audio/theone.mp3` | Track III · The One |

## 音乐播放

右下角浮动黑胶唱片：

- 点击黑胶：播放/暂停（当前曲目）
- 悬停（桌面）或点击黑胶（手机）：展开曲目条 `‹  ● ○ ○  ›`
- 点任一圆点：跳到对应曲目（含 550ms 交叉淡化）
- `Space`：播放/暂停；`←/→`：上一首/下一首
- 所有音频 `preload="none"`，只在用户点播放时才加载，节省流量

## 本地预览

从仓库根目录：

```bash
cd static_apps/jmrlzw && python3 -m http.server 8000
```

然后访问 <http://localhost:8000/>。

## 部署

该页面作为 `static_apps/` 下的静态资源，由 `scripts/copy-static.js` 复制到每个 locale 构建产物中，随主站一同部署到 `jiangmuran.com`。

不需要独立构建，修改 `index.html` 后跟随主站发布即可。

## 关键参数

如果关键日期发生变化，编辑 `index.html`：

- `startDate`（JS 里的起始时间戳）
- `bdayMonth` / `bdayDay`（生日月/日，用于倒计时）
- 页面可见文本里的日期（DATE / SINCE / 条形码 / 宝丽来 caption / 版权）

## SEO

meta 标签、Open Graph、Twitter Card、JSON-LD 均已针对 `jmrlzw / JMR LZW / crush timer` 等关键词做了配置。修改时请同步更新 `<title>` / `description` / `og:*` / `twitter:*` / `application/ld+json`。
