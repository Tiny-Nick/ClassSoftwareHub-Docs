# ClassSoftwareHub 文档库

桌面版 ClassSoftwareHub 的教程文章仓库。客户端从 `文档库/` 读取，按篇缓存到本机。

单独开一个仓库，是为了让文档的投稿、审阅与自动化（Issue 表单 → 自动整理成草稿 PR → 校验）都集中在内容这一侧，不必和客户端代码仓库互相牵制。

## 目录

```
文档库/            文章本体，一篇一个文件夹（客户端读这里）
scripts/           校验与投稿整理脚本（Actions 调用，也可本地跑）
.github/           Issue 表单与两个工作流
```

## 投稿

- **不想碰 git**：开一个 [文档投稿](https://github.com/Tiny-Nick/ClassSoftwareHub-Docs/issues/new?template=doc-submission.yml) Issue，填标题、文章 id、署名、简介与正文。工作流会自动整理成 `文档库/<id>/`、跑一遍校验，然后开一个草稿 PR。
- **愿意直接改**：fork 后新建 `文档库/<id>/`，放 `meta.json` 与正文，提交 PR 即可。

两种方式都要过 [校验文档库](https://github.com/Tiny-Nick/ClassSoftwareHub-Docs/actions/workflows/validate-docs.yml)：目录名、`meta.json` 字段、正文扩展名、图片引用按客户端读取口径核对，不通过不会被合入。

文章格式、`meta.json` 字段、正文里可用的链接协议，见 [`文档库/README.md`](文档库/README.md)。

## 本地校验

```bash
node scripts/validate-docs.mjs
```

纯只读检查，不上传、不改文件。
