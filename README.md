# CodexRelay 使用说明

CodexRelay 是一个 macOS 菜单栏工具，用来管理多个 Codex 账号配置，并在需要时切换当前使用的账号。

## 安装 App

1. 从 GitHub 下载 `CodexRelay-macos.dmg` 和 `CodexRelay-macos.dmg.sha256`。
2. 双击打开 `CodexRelay-macos.dmg`。
3. 在打开的窗口里，把 `CodexRelay.app` 拖到 `Applications`。
4. 第一次打开时，建议右键点击 `CodexRelay.app`，选择“打开”。
5. 如果 macOS 提示“无法验证开发者”，选择“打开”继续。
6. 如果仍然被拦截，打开“系统设置 -> 隐私与安全性”，在提示区域点击“仍要打开”。

![打开 DMG 后把 CodexRelay.app 拖到 Applications](assets/docs/install-dmg.png)

不需要运行 `sudo`，也不要修改系统安全设置。

## 可选校验

如果你想确认收到的 DMG 没有被改过，把 `.dmg` 和 `.dmg.sha256` 放在同一个目录，然后运行：

```bash
shasum -a 256 -c CodexRelay-macos.dmg.sha256
```

看到 `OK` 就表示文件和打包时一致。

## 使用菜单栏 App

打开 App 后，屏幕顶部菜单栏会出现 `CodexRelay`。点击它可以看到账号配置列表、当前账号、用量和操作按钮。

![CodexRelay 菜单栏面板总览](assets/docs/menu-overview.png)

常用操作：

- `刷新`：重新读取当前状态。
- `同步全部`：刷新所有账号配置的用量信息。
- `同步`：只刷新某一个账号配置。
- `切换`：切到另一个账号配置。
- `删除`：移除一个不用的账号配置。不会删除你的 Codex 或 ChatGPT 账号。
- `打开 Codex`：启动 Codex App。
- `诊断`：查看当前环境是否能正常工作。

## 第一次使用

如果你已经在 Codex 中登录过账号，第一次打开 CodexRelay 时可以创建第一个 profile。建议用容易识别的名字，例如：

```text
work
personal
plus
pro
```

profile 只是本机里的账号配置名称，方便你区分不同账号。

## 添加新账号

添加账号前，先确认浏览器里登录的是你要添加的 ChatGPT 账号。

如果当前浏览器已经登录了另一个账号，有两种做法：

1. 先在浏览器里切换到要添加的 ChatGPT 账号。
2. 开始添加后，把 App 里显示的登录地址复制到一个新的浏览器窗口打开。

添加流程：

1. 点击菜单栏面板右上角的 `+`。
2. 输入 profile 名称。
3. 确认后，App 会显示一个登录地址。
4. 复制这个地址，在新的浏览器窗口中打开。
5. 在浏览器里完成登录授权。
6. 回到 CodexRelay，等待它自动完成保存和刷新。

![添加 profile 时复制登录地址到新的浏览器窗口](assets/docs/add-profile-login.png)

如果你暂时不想继续，可以点击“取消新增”。等待浏览器登录期间，菜单栏不会卡住，你可以继续关闭面板、刷新或使用其他功能。

## 切换账号

在账号列表里点击目标 profile 的 `切换`。

如果 Codex 正在运行，CodexRelay 会先提示你确认。确认后，它会关闭 Codex、切换账号，再重新打开 Codex。

![切换和删除 profile 的确认界面](assets/docs/switch-delete.png)

如果切换失败，先点 `诊断` 看提示；常见原因是 Codex 还没有完全退出，或目标账号配置不可用。


## 常见问题

### 打不开 App

右键点击 App，选择“打开”。如果仍然被拦截，到“系统设置 -> 隐私与安全性”里点击“仍要打开”。

### 添加账号时一直没有完成

通常是浏览器里没有登录正确的 ChatGPT 账号。复制 App 里显示的登录地址，用新的浏览器窗口打开，再完成登录。

### 切换后 Codex 里还是旧账号

先退出 Codex，再回到 CodexRelay 切换一次。切换完成后再打开 Codex。

### 不想保留某个 profile

在列表里点击删除按钮。删除前会要求确认，不会删除你的 Codex 或 ChatGPT 账号。
