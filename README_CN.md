# 晋控电力山西新能源 NFC 领导展示卡

## 项目定位
面向晋控电力山西新能源公司领导的手机端 NFC 展示页，重点展示：
- 晋能控股品牌标识（使用用户提供的 PNG 文件）
- 晋控电力山西新能源企业介绍与公开业务布局
- 阳曲光伏电站日报展示区（日/月/年统计切换）
- 光伏主业、风电协同和基层场站展示
- 企业官网入口

本项目为静态 HTML/CSS/JavaScript，无框架、无构建步骤，适合 GitHub Pages。

## 目录结构
```text
index.html
report-data.js
assets/
  jineng-logo.png
README_CN.md
NFC_WRITE_URL.txt
```

## 特别重要：日报数据的公开范围
GitHub Pages 是公开网站。即使源代码仓库设置为 Private，发布出来的网站仍可能公开访问；GitHub 官方明确提示 Pages 网站公开可访问。请在上传真实日报数据前，先确认公司对外发布授权和数据范围。

- `GitHub公开样稿包` 中 `report-data.js` 为空，适合先部署和验证页面。
- `完整日报审阅包` 中 `report-data.js` 包含用户提供的 2026-11-16 阳曲光伏日报数值，仅用于内部审阅或已获得授权后的发布。
- 不要把未获批的真实发电量、上网电量、负荷、故障损失、设备可利用率等运行数据放到公开 GitHub Pages。
- 页面已注明“非实时”，它只显示静态日报快照，不连接生产控制系统，也不会自动刷新。

## 更新日报数据
获得授权后，编辑 `report-data.js`：
1. 更新 `date`、`dateCN`、`weather`、`weeklyGeneration`。
2. 更新 `radiation` 的 `day/month/year`。
3. 更新 `metrics` 中各项指标的 `day/month/year`。
4. 保存并提交到 GitHub，Pages 会按仓库设置重新部署。
5. 页面 URL 不变，因此 NFC 芯片不需要重新写入。

数值按原报表的口径和单位录入，保留原有小数位。网页只做展示，不对原始数据进行推算。

## 添加阳曲实景照片
目前阳曲区域使用矢量示意图，并预留三个照片位。后续可以在 `assets/` 中添加经批准可公开使用的场站全景、设备运维和一线巡检照片，再按 README 的说明替换相应占位区。
请勿上传包含控制室屏幕、设备编号、内部流程、人员隐私或未经批准的生产信息的照片。

## GitHub Pages 部署
1. GitHub 新建仓库，例如 `yangqu-nfc-showcase`。
2. 将本项目文件上传到仓库根目录，确保 `index.html` 位于根目录。
3. 进入仓库 `Settings` → `Pages`。
4. `Build and deployment` 中选择 `Deploy from a branch`。
5. Branch 选择 `main`，目录选择 `/(root)`，点击 Save。
6. 等待部署完成，在 Pages 页面查看网址。

项目站点地址一般为：
`https://你的GitHub用户名.github.io/仓库名/`

如仓库名为 `你的用户名.github.io`，则是：
`https://你的GitHub用户名.github.io/`

GitHub 官方说明：
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 写入 NTAG213
1. 先在手机浏览器确认 Pages 网址可访问。
2. Android 安装 NXP TagWriter（或可靠的 NDEF 写入工具）。
3. Create and write → New dataset → Link / URL。
4. 输入完整 HTTPS Pages 地址，写入 NTAG213。
5. 用另一台手机测试读取、跳转、页面适配。
6. 测试通过前不要锁定标签为只读。

NTAG213 只需存储网址，不需要存网页源码。以后更新 `report-data.js`、页面和照片，只要网址不变，卡片无需重新写入。

## 官方网站
https://jksxpower.jnkgjtnews.com/

## 数据来源说明
- 企业介绍和产业布局参考晋控电力官网公开页面。
- 阳曲日报数值来自用户提供的 2026-11-16 日报照片，仅按截图显示录入。
- “日历天数”一行未放入网页，因为截图中的列位置不够清晰，避免误读。
