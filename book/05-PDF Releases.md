修改yaml文件

name: 印成PDF

on: [push]

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-24.04
    steps:
      - name: 把稿子取过来
        uses: actions/checkout@v5

      - name: 装印书工具和中文书法字体
        run: |
          sudo apt-get update
          sudo apt-get install -y pandoc weasyprint fonts-noto-cjk

      - name: 合成一本 PDF
        run: |
          mkdir -p dist
          printf 'body{font-family:"Noto Sans CJK SC",sans-serif;line-height:1.8}h1{page-break-before:always}\n' > style.css
          pandoc book/*.md -s --toc --pdf-engine=weasyprint --css=style.css -o dist/book.pdf

      - name: 发布到 Releases
        uses: softprops/action-gh-release@v2
        with:
          tag_name: v1.0.${{ github.run_number }}
          name: 我的书 第${{ github.run_number }}版
          files: dist/book.pdf
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

№.05) ：第 5 步：别人能下载到我的书​，PDF 自动发到 Releases。

提交后去哪看：仓库首页右侧边栏 → Releases​ → 点进去就能下载 book.pdf。

<img width="1920" height="978" alt="image" src="https://github.com/user-attachments/assets/2a2b3683-53f5-4222-ac3e-062e24723cf3" />


以后每改一次稿子，自动多一版：第 1 版、第 2 版、第 3 版…… 再也不用去 Actions 页面翻 Artifacts 了，而且 Releases 里的文件永久保存（Artifacts 90 天后会过期删掉）。
