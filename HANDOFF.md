# 珠海一日游网站：异机恢复说明

## 项目状态

这是一个纯静态网站。网页入口是 `dist/index.html`，图片也全部位于 `dist/`。

- 不需要 Node.js 依赖，也没有 `package.json` 或锁文件。
- 不需要构建步骤。
- 不需要 `.env`、API Key、数据库、Git LFS 或 Git 子模块。
- 页面正文、CSS 和 JavaScript 都在 `dist/index.html` 中。
- 景点图片均已存入仓库，不依赖当前电脑上的绝对路径。
- 弹窗中的地图瓦片在浏览时从 OpenStreetMap 联网加载；12306、高德地图和图片来源按钮也是外部链接。没有网络时，网站主体和本地图片仍可打开，但地图与外链不可用。

## 家里电脑从零恢复

先安装 Git，然后在终端运行：

```powershell
git clone https://github.com/LIULIY6/zhuhai-day-trip.git
cd zhuhai-day-trip
```

本项目没有依赖，因此**不用运行 `npm install`**。

### 启动方式 A：Python（推荐）

如果电脑已安装 Python：

```powershell
python -m http.server 4173 -d dist
```

浏览器打开：<http://localhost:4173>

### 启动方式 B：Node.js

如果只有 Node.js，可运行：

```powershell
npx --yes serve@latest dist -l 4173
```

浏览器打开：<http://localhost:4173>

## 恢复后检查清单

1. 首页能看到“珠海海岸线一日游”。
2. 顶部背景显示爱情邮局灯塔图片。
3. 四张景点卡片均有图片：爱情灯塔、城市阳台、珠海渔女、日月贝。
4. 每张卡片的“查看图片与位置”都能打开弹窗。
5. 联网时，弹窗地图能加载 OpenStreetMap 瓦片，高德地图和 12306 链接能打开。

## 继续开发与同步

开发前获取最新版本：

```powershell
git pull
```

修改后提交并推送：

```powershell
git add -A
git commit -m "描述本次修改"
git push
```

不要提交真实的密码、Token、API Key 或 `.env`。当前版本没有任何必须重新填写的环境变量。
