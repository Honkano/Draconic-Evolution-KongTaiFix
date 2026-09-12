_______________________________________________________________
# Draconic Evolution - GTNH (KongTai Fix)

> 一个专注于兼容性的非官方修复分支。
>
> An unofficial compatibility fork.
_______________________________________________________________

中文

本分支由空太（KongTai）与 AI 助手共同开发与维护。未来可能会新增一些物品或功能，但所有新增内容都将继续遵循原项目的 LGPL 协议。原作者的版权与知识产权始终归 brandon3055 及 GTNH 团队所有。我永远不会声称自己是原作者，也永远尊重并感谢原作者的贡献。

English

This fork is developed and maintained by KongTai with the assistance of an AI assistant. New items or features may be added in the future, but all additions will continue to follow the original project's LGPL license. All original copyrights and intellectual property remain with brandon3055 and the GTNH team. I will never claim to be the original author, and I will always respect and appreciate the original authors' contributions.

---

## 关于本分支 / About This Fork

本仓库是 [GTNewHorizons/Draconic-Evolution](https://github.com/GTNewHorizons/Draconic-Evolution) 的一个**非官方修复分支**，由 **空太 (KongTai)** 维护。

This repository is an **unofficial compatibility fork** of [GTNewHorizons/Draconic-Evolution](https://github.com/GTNewHorizons/Draconic-Evolution), maintained by **KongTai**.

### 目的 / Purpose

中文：

- 本分支的核心目的，是解决 工业升级2.5.21 Mod (Industrial Upgrade 2) 与 最新版格雷版龙之研究 之间的兼容性崩溃问题。注意：本修复仅保证与工业升级2.5.21版本兼容，且游戏版本必须为 Minecraft 1.7.10。其他版本的工业升级2或非 1.7.10 的游戏版本，兼容性均不予保证。 它面向那些正在- 使用工业升级2.5.21，但又希望使用最新格雷版龙之研究的玩家。

English:

- The primary goal of this fork is to resolve a compatibility crash between Industrial Upgrade 2.5.21 Mod (Industrial Upgrade 2) and the latest GTNH version of Draconic Evolution. Note: This fix is only guaranteed to be compatible with Industrial
- Upgrade 2.5.21 and Minecraft 1.7.10. Compatibility with other versions of Industrial Upgrade 2 or non-1.7.10 game versions is not guaranteed. It is intended for players who use Industrial Upgrade 2.5.21 and want to run the latest GTNH version of
- Draconic Evolution at the same time.

### 当前状态 / Current Status

- 基于 `Draconic-Evolution-1.5.33-GTNH` 构建。
- **不保证**跟随上游 GTNH 版本进行持续更新。
- 本修复**不代表** GTNH 官方立场。

- Built against `Draconic-Evolution-1.5.33-GTNH`.
- **Continuous updates** to track upstream GTNH releases are **not guaranteed**.
- This fix **does not represent** the official stance of the GTNH team.

---

## 修改内容 / Changes

本分支包含 **两项** 核心兼容性修复：

This fork includes **two** core compatibility fixes:

### 1. 新增 `KeyBindings` 兼容类 / Added `KeyBindings` Compatibility Class

工业升级2在渲染工具提示时，会调用 `com.brandon3055.draconicevolution.client.keybinding.KeyBindings.toolConfig.getKeyCode()`。但**最新版格雷版龙之研究已经移除了这个类**，导致工业升级2在翻开物品栏时直接崩溃（`NoClassDefFoundError`）。

本修复重新创建了 `KeyBindings` 类，并在 `KeyInputHandler` 构造时把 `toolConfig` 实例赋值给它，恢复兼容。

Industrial Upgrade 2 calls `com.brandon3055.draconicevolution.client.keybinding.KeyBindings.toolConfig.getKeyCode()` when rendering item tooltips. However, the **latest GTNH version of Draconic Evolution removed this class**, causing Industrial Upgrade 2 to crash with a `NoClassDefFoundError` when opening the inventory.

This fix recreates the `KeyBindings` class and assigns the `toolConfig` instance to it inside the `KeyInputHandler` constructor, restoring compatibility.

### 2. 恢复旧包名/类名的兼容壳（`utills` → `utils`）/ Restored Legacy Package Name Compatibility Shell (`utills` → `utils`)

旧版龙之研究里，工具相关的包名拼写是 `utills`（**多了一个字母 `l`**）。工业升级2正是按这个错误拼写去引用这些类的。

但在**最新版格雷版龙之研究**里，作者已经把这个拼写错误修正为 `utils`（**去掉了多余的 `l`**）。于是工业升级2依然按旧名字找，结果找不到，再次崩溃。

本修复在旧的 `utills` 路径下新增了兼容壳，转发到新的 `utils` 路径，让工业升级2和新版龙之研究**双方都能正常工作，互不干扰**。

In older versions of Draconic Evolution, the package name for tool-related utilities was misspelled as `utills` (**with an extra letter `l`**). Industrial Upgrade 2 references these classes using that exact misspelled name.

In the **latest GTNH version of Draconic Evolution**, the author corrected this typo to `utils` (**removing the extra `l`**). As a result, Industrial Upgrade 2 could no longer find the classes and crashed.

This fix adds compatibility shims under the old `utills` package that forward to the new `utils` package, so both **Industrial Upgrade 2 and the latest Draconic Evolution can work correctly without interfering with each other**.

---

## 下载与构建 / Downloads & Builds

本仓库使用 **GitHub Actions** 自动构建。

- **发布页 (Releases)**：稳定版本会发布在这里，直接下载 `jar` 即可使用。
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/releases
- **构建页 (Actions)**：每次代码更新都会自动构建，可以在这里查看构建状态或下载最新的开发版构建产物。
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/actions

This repository uses **GitHub Actions** for automated builds.

- **Releases**: Stable builds are published here. Download the `jar` and drop it into your `mods` folder.
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/releases
- **Actions**: Every code update triggers an automatic build. You can check the build status or download the latest development build here.
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/actions

---

## 关于原作者 / About the Original Author

- **龙之研究 (Draconic Evolution)** 的**真正原作者**是 **brandon3055**。
- **格雷团队 (GTNH)** 维护的是针对 **Minecraft 1.7.10** 的分支版本。
- 我**不是**原作者，也**没有加入** GTNH 团队，未来也**不会**加入。
- 我仅以个人身份，为 1.7.10 社区做一点力所能及的贡献。

- The **original author** of **Draconic Evolution** is **brandon3055**.
- The **GTNH team** maintains the **Minecraft 1.7.10** fork.
- I am **not** the original author, I am **not** a member of the GTNH team, and I will **not** join the team in the future.
- I am doing this as an individual, hoping to contribute a little to the 1.7.10 community.

---

## 许可证 / License

本分支**沿用原项目的 LGPL 许可证**。完整的许可证文本请参见本仓库根目录下的 `LICENSE` 文件。所有原作者的版权声明均予以保留。

This fork **inherits the original project's LGPL license**. The full license text is available in the `LICENSE` file at the root of this repository. All original copyright notices are retained.

---

## 反馈与联系 / Feedback & Contact

如果你在使用中遇到任何问题，或者有任何建议，欢迎通过以下方式联系：

- **GitHub Issues**：请直接在本仓库的 Issues 页面提出。这是最推荐的方式。
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/issues
- **QQ**：`2897626982`（仅限中文交流）。
- **GitHub**：你也可以通过 GitHub 站内信联系我。

If you encounter any problems or have suggestions, please reach out via:

- **GitHub Issues**: Please open an issue on the Issues page. This is the preferred method.
  👉 https://github.com/Honkano/Draconic-Evolution-KongTaiFix/issues
- **QQ**: `2897626982` (Chinese only).
- **GitHub**: You can also message me directly on GitHub.

---

*我是空太 (KongTai)，一个想为 1.7.10 社区做点事的普通玩家。*

*I am KongTai, a regular player hoping to contribute something to the 1.7.10 community.*


