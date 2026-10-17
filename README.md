
# 实验04 CSS布局实战——网站首页

> 湖南文理学院芙蓉学院 · Web应用开发技术实验
> 学生：肖素琴 ｜ 学号：24310120 ｜ 班级：软工2401

## 一、实验内容

基于实验提供的"网站首页"HTML结构（含 header、banner、recommend、course、学科课程、rights 等模块），为其编写完整的 CSS 样式，实现一个具有现代布局和交互效果的企业官网首页。实验要求**不允许修改 HTML 结构，只能通过 CSS 完成任务**，并配合 Git 提交与 README 说明。

| 文件 | 说明 |
| --- | --- |
| `index.html` | 网站首页 HTML 结构（header 导航、banner 横幅、recommend 推荐、course 精品课程、学科课程、rights 版权区域） |
| `base.css/index.css` | 完整 CSS 样式，实现页面骨架、卡片网格、固定导航、悬停动效 |
| `images/` | 页面引用的图标等静态资源 |
| `uploads/` | banner 横幅背景图等素材 |
| `README.md` | 本说明文件 |

## 二、实现思路与关键技术

### 1. Flex 布局——页面整体骨架
用 `display: flex` 完成单轴排列模块：
- 顶部导航栏（`.header .wrapper`、`.nav ul`、`.search`）
- 横幅区（`.banner .wrapper`）
- 精品推荐（`.recommend`）
- 课程标题行（`.hd`）
- 页脚（`.rights .wrapper`）

```css
.header .wrapper { display: flex; padding-top: 29px; }
.nav ul { display: flex; }
.search { display: flex; width: 430px; border-radius: 20px; }
```

### 2. Grid 布局——课程卡片网格
卡片区域用 Grid 实现二维网格排列：
```css
.bd ul {
    display: grid;
    grid-template-columns: repeat(5, 1fr); /* 精品课程 5 列 */
    gap: 15px;
}
.bottom ul { grid-template-columns: repeat(4, 1fr); } /* 学科课程 4 列 */
```

### 3. transition/transform 动效——卡片悬停上浮
```css
.bd li { transition: all 0.3s ease; }          /* 过渡：让变化平滑 */
.bd li:hover {
    transform: translateY(-5px);               /* 位移：上浮 */
    box-shadow: 0 10px 20px rgba(0,0,0,0.15);  /* 阴影：浮起感 */
}
```

## 三、关键技术点一览

| 技术点 | 说明 | 应用位置 |
| --- | --- | --- |
| Flex | 单轴排列与对齐 | 导航、横幅、推荐、标题行、页脚 |
| Grid | 二维网格卡片 | `.bd ul`、`.bottom ul` 课程卡片 |
| position: fixed | 固定导航栏 / 全屏遮罩 | `.header`、`.modal` |
| transition | 平滑过渡动画 | `.bd li` |
| transform | 位移变形（上浮） | `.bd li:hover` |
| box-shadow | 阴影浮起效果 | 卡片悬停 |

## 四、遇到的问题与解决

**课程卡片想用 Flex 排多行列很繁琐**——改用 Grid 的 `grid-template-columns: repeat(n, 1fr)` + `gap`，一次声明行列与间距，代码更简洁。

## 五、运行方法

1. 用 VS Code 打开本项目，安装 **Live Server** 插件；
2. 右键 `index.html` → `Open with Live Server`；
3. 或直接用 Chrome 打开 `index.html` 预览（注意 CSS 引用 `css/index.css` 及 `images/`、`uploads/` 相对路径，需保持目录结构完整）。

## 六、实验总结

本次实验综合运用了 Flex、Grid、position 定位、transition/transform 动效，仅用 CSS 便完成了企业官网首页的现代布局与交互效果，加深了对二维 Grid 布局和纯 CSS 弹窗实现的理解。


