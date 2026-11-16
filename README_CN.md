# 晋控电力山西新能源 NFC 领导展示卡（无 assets 依赖版）

## 本版本解决的问题
晋能控股 Logo 已直接嵌入 `index.html`（Base64 图片数据），因此网页不再引用 `assets/` 文件夹，也不需要单独上传 logo 图片。只要将 `index.html` 与 `report-data.js` 放在 GitHub 仓库根目录，页面即可正确显示 Logo。

## 仓库根目录文件
```text
index.html       # 网页、样式、脚本及内嵌晋能控股 Logo
report-data.js   # 阳曲日报数据（公开样稿版为空；完整日报版含截图录入数据）
README_CN.md     # 本说明，可上传也可不上传
```

不要把 ZIP 文件本身当成网站文件直接放在仓库根目录；请先解压，再上传里面的文件。GitHub 网页端可通过 Add file → Upload files，一次选择多个文件上传，无需上传文件夹。

## 发布数据安全提醒
GitHub Pages 网站通常是公开可访问的。完整日报版含有用户提供的阳曲光伏 2026-11-16 日报运行数据。未取得公司批准前，请勿将完整日报版发布到公开 GitHub Pages。建议先部署公开样稿版；经审核授权后，再替换 `report-data.js`。

## 更新日报
经授权后，编辑 `report-data.js` 中对应日期、天气、辐照量及各指标的日/月/年数据，提交到 GitHub。网站地址不变时，NTAG213 无需重新写入。

## GitHub Pages 部署
1. 在 GitHub 创建仓库。
2. 解压 ZIP，将 `index.html`、`report-data.js`（以及可选的 README）上传至仓库根目录。
3. 进入 Settings → Pages。
4. Source 选择 Deploy from a branch；Branch 选择 `main`，目录选择 `/(root)`，保存。
5. 部署成功后，用手机浏览器测试网页，再把 HTTPS 地址写入 NTAG213。

## NFC 写入
NFC 芯片只保存网页 HTTPS 地址，不保存网页源码。使用 Android NFC 写入工具，创建 NDEF URI/URL 记录，写入 GitHub Pages 地址即可。测试完成前不要将标签锁定为只读。

## 页面说明
本页面为 NFC 创意展示页，不是企业官方业务系统；日报为静态数据快照，不代表实时生产监控。企业 Logo、宣传图片、场站实景及运行数据正式公开前，应按公司规定确认使用授权。

企业官网：https://jksxpower.jnkgjtnews.com/
