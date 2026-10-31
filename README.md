# md2PDF
写好一份md稿子，再让一个"机器人"帮你把它印成 PDF。流程是：写 .md 稿子 → 存到 GitHub → 机器人印成 PDF → 下载。

<img width="1920" height="970" alt="image" src="https://github.com/user-attachments/assets/f6b22f79-df10-4d88-88c1-c7cf18284694" />

关键：文件名 01-第一章.md、02-第二章.md 前面加数字，机器人就会按 01、02、03 的顺序排版，不会乱。

<img width="1920" height="978" alt="image" src="https://github.com/user-attachments/assets/8737926c-53cb-4236-bc76-5ab499b4731b" />


别人能下载到我的书​，PDF 自动发到 Releases。

提交后去哪看：仓库首页右侧边栏 → Releases​ → 点进去就能下载 book.pdf。

<img width="1920" height="978" alt="image" src="https://github.com/user-attachments/assets/b7191dfd-1bde-4b35-b721-a3e1854f099e" />

以后每改一次稿子，自动多一版：第 1 版、第 2 版、第 3 版…… 再也不用去 Actions 页面翻 Artifacts 了，而且 Releases 里的文件永久保存（Artifacts 90 天后会过期删掉）。
