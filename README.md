# readthedocs 导入包（`advanced-engines-corp.com`）

## 这份东西是什么

`readthedocs` 建项目**必须**先有一个 Git 仓库（GitHub / GitLab / Bitbucket 三者之一），
平台不接受手工上传文件。本目录就是**可以直接推上去的仓库内容**，推完在 readthedocs
点一次导入即可。

## 现状

- 账号**已建好并验证过邮箱**（用户名 `advanced-engines-archive`），登录仪表盘实测可用。
- 卡点只有一个：**缺一个 Git 仓库**。
- 已实测：GitLab 注册有 Arkose 人机验证、Codeberg 有 Anubis 反爬，都无法脚本完成
  → 这一步需要人。

## 人工操作（约 5 分钟）

1. 在 GitHub 新建一个**公开**仓库，名字建议 `heavy-fuel-diesel-engine-emissions-compliance-reference`。
2. 把本目录（`repo/` 里的全部内容，含隐藏文件 `.readthedocs.yaml`）推到该仓库默认分支。
3. 登录 readthedocs（用户名 `advanced-engines-archive`）→ **Add project** → 选中该仓库 → 导入。
4. 项目建好后到 **Admin → Settings**，把 **Privacy level 改成 Public**（默认是 Private，
   私有的话页面不公开、外链等于没有）。
5. 首次构建完成后，回来跑一遍验收：
   `python ops/w113_verify.py <存下来的页面.html> advanced-engines-corp.com`
   两条判据都要过：页面没有 `noindex`、正文里指向 `advanced-engines-corp.com` 的链接 `rel` 不含 `nofollow`。

## 为什么值得做

readthedocs 的文档页是**可收录 + 正文链接不带 nofollow** 的形态，和已经打通的
GitBook 同一类。文档正文里已经放了指向 `https://advanced-engines-corp.com` 的链接，页面一上线就是一条真外链。

## 别做的事

- **不要**在仓库里加 `canonical_url` 之类的字段。
- 正文里的链接**原样保留**，不要改写锚文本。
- 同一域 30 天内不要在别的平台重复投。
