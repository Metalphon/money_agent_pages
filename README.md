# OKX 钱包资产余额可视化

本项目通过GitHub Pages展示从OKX API获取的钱包总资产估值（以USDT计价）随时间变化的折线图。

**数据由一个独立的、私有的GitHub Actions流程自动获取、处理并定期同步到本仓库的 `balance_data.json` 文件中。本仓库仅包含前端展示代码和公开的JSON数据。**

## 页面访问

您可以通过以下链接访问实时更新的图表：

[https://<你的GitHub用户名>.github.io/<本公开仓库名>/](https://<你的GitHub用户名>.github.io/<本公开仓库名>/)

例如：[https://metalphon.github.io/okx-balance-pages/](https://metalphon.github.io/okx-balance-pages/)  (请替换为你的实际链接)

## 功能

*   以折线图形式可视化展示OKX账户总资产（以USDT计价）的历史趋势。
*   显示当前的最新总资产估值。
*   显示最近一次数据更新的时间 (UTC)。
*   计算并显示24小时内的资产变化百分比和绝对值。
*   数据通常每隔数小时自动更新一次。

## 技术实现

*   **前端：** 使用纯HTML, CSS, 和 JavaScript。
*   **图表库：** [Chart.js](https://www.chartjs.org/) 用于绘制折线图。
*   **日期/时间处理：** 使用 [Luxon](https://moment.github.io/luxon/) (或 [Moment.js](https://momentjs.com/)，根据实际使用) 配合Chart.js的日期适配器处理时间轴。
*   **数据源：** 前端页面通过 `fetch` API 读取本仓库根目录下的 `balance_data.json` 文件。
*   **数据更新：** `balance_data.json` 文件由一个位于作者私有仓库中的GitHub Actions工作流程自动生成并定期推送到本仓库。该自动化流程负责安全地与OKX API交互。
*   **托管：** 本页面通过 [GitHub Pages](https://pages.github.com/) 托管。

## 文件结构

*   `index.html`: 主要的前端页面，包含图表渲染逻辑。
*   `balance_data.json`: (由GitHub Actions自动更新) 存储用于图表绘制的时间序列数据。
*   (可选) `luxon.min.js`, `chartjs-adapter-luxon.min.js` (或对应的Moment.js文件): 如果选择本地托管这些JS库而不是使用CDN。

## 关于数据

*   本页面展示的数据来源于用户通过OKX API自行配置的监控脚本。
*   数据的准确性和更新频率取决于API的可用性和后台脚本的运行情况。
*   所有资产估值均以USDT近似计算。

## 注意

本仓库不包含任何敏感的API密钥或私密信息。所有与OKX API的交互都在一个独立的私有自动化流程中进行。

---
