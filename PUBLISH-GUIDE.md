# Tableau Public 发布指引

发布后可以得到一个**可交互的在线预览链接**，既写进 README 和简历，也能从发布页导出截图放进仓库。

---

## 一、准备工作

### 1. 注册 Tableau Public 账号（免费）

打开 https://public.tableau.com ，用邮箱注册即可。注册后建议顺手把**显示名**设成
`SRTURK` 或你习惯的技术 ID（发布页会显示这个名字，**不要填真实姓名**，
与你在 GitHub 上不暴露个人信息的做法保持一致）。

### 2. 确认数据源可用

用 Tableau Desktop 打开 `workbook/takeout-operations-dashboard.twbx`（数据已打包），
确认 10 个工作表和仪表板都能正常显示。

> ⚠️ **两个容易踩的坑**
>
> **坑一：CSV 编码。** 三个 CSV 是 **GBK 编码**。如果你在数据源里改过连接、
> 或重新指向了 `data/` 下的原始文件，一定要把文本文件编码设为 **GBK**，
> 否则中文列名和门店名会全部变成乱码。发布前请先目视确认一下门店名称显示正常。
>
> **坑二：federated 连接。** 工作簿用的是 federated（多表关联）数据源，
> 发布时 Tableau Public 会要求提取为数据提取（.hyper）。按提示点「提取」即可，
> 4,419 条订单 + 2,385 条门店数据体量很小，提取会很快。

---

## 二、发布步骤

1. Tableau Desktop 中打开工作簿
2. 菜单 **服务器 → Tableau Public → 保存到 Tableau Public**
3. 若未登录，会提示登录（首次需要授权）
4. 填写工作簿信息：
   - **名称**：`外卖平台门店经营分析仪表盘` 或 `Takeout Platform Operations Dashboard`
   - **说明**：可填一句"Based on 11 chain restaurant stores across Meituan and Eleme platforms, covering traffic funnel, ad ROI, order and delivery distribution."
5. 点击 **保存**，等待上传完成（约 10–30 秒）
6. 完成后浏览器会自动打开发布页，**复制地址栏链接**发给我

链接形如：
```
https://public.tableau.com/app/profile/<你的ID>/viz/<工作簿名>/<工作表名>
```

---

## 三、发布后要做的三件事

### 1. 把链接发我

我会：
- 把链接写进仓库 README 的醒目位置
- 尝试抓取发布页的预览图存入 `screenshots/`
- 把链接加进简历的项目描述

### 2. 自己导出截图（推荐，双保险）

Tableau Public 发布页的预览图分辨率可能偏低。建议自己导出高清截图：

- **方法一（最优）**：Tableau Desktop 中打开仪表板 → 菜单
  **仪表板 → 导出图像** → 选择 PNG，分辨率拉满 → 保存
- **方法二**：浏览器打开发布页，把**仪表板**和**2–3 个关键工作表**（推荐
  `经营情况总览`、`每日流量数据`、`投放情况`）分别截图

命名建议：

```
screenshots/
├── 01-dashboard-overview.png      仪表板整图
├── 02-traffic-funnel.png          每日流量数据（流量漏斗）
├── 03-ad-placement.png            投放情况（散点图）
└── 04-store-contribution.png      门店占比（饼图）
```

保存到任意位置后告诉我路径，我会重命名、放进仓库并提交。

### 3. 确认发布页的隐私设置

Tableau Public 上的一切都是**公开可见**的。发布前请确认：

- [ ] 工作簿中**没有**包含真实姓名、学号、邮箱等个人信息
      （当前工作簿的 10 个工作表标题均为业务名称，应无个人信息，
       但请你在 Tableau 里扫一眼标题、筛选器名称、数据源名称）
- [ ] 数据是课程提供的示例数据，不涉及真实商业机密或客户隐私
      （该数据集为教学用脱敏数据，可安全发布）

---

## 四、如果发布遇到问题

| 问题 | 解决办法 |
| :--- | :--- |
| 提示需要数据提取 | 按提示点「提取」，或先把数据源改为提取（数据 → 提取数据） |
| 中文显示乱码 | 数据源编码改为 GBK；若已发布，删掉重新发布 |
| 地图不显示 | Tableau Public 地图服务偶有限流，等几分钟或改用符号地图 |
| 上传失败 | 检查网络；或先保存为 .twbx 本地文件再上传 |
| 不想公开数据 | Tableau Public 无法设为私有。若必须保密，改用**截图方案**（见下方说明） |

> 💡 **若你临时改变主意不想公开数据**：告诉我，我把 README 改成"仅含截图"版本，
> 用你本地导出的 PNG 展示效果，GitHub 仓库里只留 workbook 与 data，
> 不涉及任何在线发布。
