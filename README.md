# AMC 使用统计

一个静态单页，有两个页签：

- **AMC 模型**：4 个数据来源的 294 个分析模型，包括 13 个模板的总排名、各来源内的排名、创建人统计和模型明细
- **用户受众**：AI 按受众名称归入 7 个受众模板的统计（按数量排序），用户受众的类型、站点、广告主、投放类型、更新频率、行为规则、失败原因和创建人统计，以及受众明细（4 个来源共 353 条：sparkxustopshoesusna 211 条、sparkxdreampairseueu 101 条、US 多店铺账户 33 条、sparkxmiraclemilesukeu 8 条）

页面就是 `index.html`，不依赖外部资源，也不需要构建。

## 文件

| 文件 | 作用 |
|---|---|
| `index.html` | 页面本身 |
| `.nojekyll` | 让 GitHub Pages 跳过 Jekyll 处理 |
| `.github/workflows/pages.yml` | 推送到 `main` 后自动部署到 GitHub Pages |

## 发布步骤

> **注意：** 页面里有模型名称、受众名称和创建人邮箱。免费账号只能把公开仓库发布到 Pages，任何人都能访问。付费账号（Pro / Team）的私有仓库也能发布 Pages，但页面仍是公开的。只有 GitHub Enterprise Cloud 支持限制为仅组织成员访问。

本目录已经执行过 `git init -b main`，所有文件也已暂存。

1. 如果从没配置过 git 身份，先配置一次：

   ```bash
   git config --global user.name "你的名字"
   git config --global user.email "你的邮箱"
   ```

2. 在 GitHub 上新建一个空仓库，例如 `amc-template-ranking`，不要勾选自动生成 README。
3. 在本目录提交并推送：

   ```bash
   git commit -m "Add template ranking page"
   git remote add origin https://github.com/<你的账号>/amc-template-ranking.git
   git push -u origin main
   ```

4. 在仓库的 **Settings → Pages → Build and deployment → Source** 中选择 **GitHub Actions**。
5. 打开 **Actions** 页签，等待 `Deploy to GitHub Pages` 运行完成。之后访问 `https://<你的账号>.github.io/amc-template-ranking/`。

## 更新数据

用新生成的页面覆盖 `index.html`，然后提交并推送：

```bash
git add index.html
git commit -m "Update data"
git push
```

推送后会自动重新部署。
