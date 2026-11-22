# Windows → macOS 迁移

- 当前在 Windows 上开发和验证。目标环境为 Mac Studio 上的桌面 Chrome 或 Chromium。
- 两个平台都可以在 `chrome://extensions/` 开启开发者模式并加载 `extension/`。也可以解压安装包并加载含 `manifest.json` 的目录。
- 页面响应旁听在 `extension/network.js`，允许读取的响应在 `extension/data.js`，页面渲染在 `extension/content.js`，可选趋势记录在 `extension/background.js`。
- 扩展、打包脚本和安装包无需 Windows 专属路径、脚本或依赖。打包使用 Python 3。Windows 运行 `python scripts/package.py`，macOS 运行 `python3 scripts/package.py`。
- Node 测试使用 `node --test tests/*.test.cjs`。浏览器测试使用 Python Playwright 与 Chromium，可用 `CHROMIUM_EXECUTABLE` 指定浏览器。若需验证 X Pro 版面，可用 `XFC_TEST_ORIGIN=https://pro.x.com` 运行 `tests/browser_test.py`。
- 更换浏览器配置或更换扩展 ID 后，本机趋势不会自动迁移。若要迁移，先确认老扩展的存储与新环境，再验证记录。
- 2026-11-22 加入 X Pro 支持并默认关闭趋势记录。搬到 macOS 时无需改代码，重新加载同一套文件即可。
- 2026-11-22 将原安装包连同 MIT 许可发布为 GitHub Release。两端共用同一个下载附件和加载步骤。
