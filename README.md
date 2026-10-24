# github-actions-practice

依据《实验03-Github Action和GitHub Pages使用》准备的实验项目。

## 文件结构

```text
.github/workflows/ci.yml       Python 单元测试
.github/workflows/deploy.yml   MkDocs 构建并部署到 gh-pages
calculator.py                 add、multiply
test_calculator.py            2 个测试函数，4 条断言
requirements.txt              测试依赖
requirements-docs.txt         MkDocs 与 Material 主题
mkdocs.yml                    主题与四页导航
docs/index.md                 首页
docs/about.md                 关于
docs/guide.md                 使用指南
docs/api.md                   API 参考
```

## 本地验证

```powershell
py -3 -m venv .venv
& .\.venv\Scripts\python.exe -m pip install -r requirements.txt -r requirements-docs.txt
& .\.venv\Scripts\python.exe -m pytest -v
& .\.venv\Scripts\python.exe -m mkdocs build --strict
& .\.venv\Scripts\python.exe -m mkdocs serve
```

没有 py 命令时，使用可用 Python 的完整路径创建虚拟环境。
无需激活虚拟环境或调整 PowerShell 执行策略。

## 实验顺序

1. 首先只提交 Python 文件、测试依赖与 ci.yml，推送并确认 Actions 成功。
2. 将 add 的 return a + b 临时改成 return a * b，提交并观察失败。
3. 恢复正确加法，提交并确认最新运行成功。
4. 安装文档依赖，检查四个页面并预览。
5. 提交文档与 deploy.yml，触发构建并将网站推送到 gh-pages。
6. Pages Source 选择 Deploy from a branch → gh-pages → /(root)。

工作流已设置 contents: write 供文档部署使用。
文档工作流只在 main 的相关文件变化或手动触发时运行。
GitHub 托管任务使用 Python 3.11；本地可使用兼容的 Python 3.12。

网站预期地址：https://evelyn271.github.io/github-actions-practice/

是否发布成功，需要实际检查远程 Actions 和网站。
不将本地测试通过作为远程完成的证明。
