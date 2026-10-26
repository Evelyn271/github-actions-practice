# 使用指南

1. 编写 Markdown 文档。
2. 将修改提交并推送到 GitHub 的 main 分支。
3. GitHub Actions 自动构建并部署到 gh-pages 分支。
4. 等待 Pages 发布完成，打开公开网站确认更新。

## 本地测试

在项目根目录的虚拟环境中安装测试依赖，然后运行：

```powershell
python -m pip install -r requirements.txt
python -m pytest -v
```

正确实现应有 2 个测试通过，包含 4 条断言。
将 add 中的加法临时改为乘法时，应出现 1 个失败和 1 个通过。
观察失败信息后恢复加法，并重新验证。

## 本地预览文档

```powershell
python -m pip install -r requirements-docs.txt
python -m mkdocs build --strict
python -m mkdocs serve
```

打开终端显示的本地地址。预览完成后按 Ctrl+C 停止。

## 发布源

GitHub 仓库 Settings → Pages 的 Source 选择 Deploy from a branch，
分支选择 gh-pages，目录选择 /(root)。
