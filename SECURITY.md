# 🛡️ LingCraft · 安全策略与防伪核验指引 (Security Policy)

用户的数据资产安全、创作成果隐私与软件供应链完整性是 LingCraft 的最高优先级。

---

## 🔒 官方防伪校验机制

为了防止恶意第三方在网络中劫持或向安装包投毒，官方构建产物提供 **双重密码学核验防线**：

### 1. SHA-256 哈希值核对
每一个官方发布的二进制可执行文件（`.exe` 与 `.zip`）都在发布的 Release 说明与 `version.json` 中公开其实测 SHA-256 哈希值。

**核验方法（以当前版本为例）：**
在 Windows 系统的 PowerShell 窗口中运行以下命令：
```powershell
Get-FileHash -Algorithm SHA256 "LingCraft_Setup_v3.5.17.exe"
```
对比计算结果是否与官方发布的哈希值一致：
- 安装向导版官方指纹：`a00e3aaf641472e70b6e19e5f1e23ed95a6eb685ecdb45d47b03fa5f5a8c31e8`
- 绿色免安装版官方指纹：`c5419457bac981d393458f3fecd72d21c066483c2de556e84eeadbd7f2c6e938`
若一致，代表该文件自官方出厂后未被修改过任何 1 个字节。

### 2. Ed25519 云端清单防篡改签名
客户端在自动检测升级时，必须校验云端版本清单的 `manifest_sig`（基于工业级高强度 **Ed25519 椭圆曲线数字签名**）。即使中间人劫持了 DNS 或修改了清单内容，客户端验签失败会立即拒绝自动下载并阻断安装，杜绝供应链中间人投毒风险。

---

## 🌐 官方唯一受信任的分发源

请用户仅从以下两个官方权威渠道下载 LingCraft，切勿轻信未经授权的网盘散装链接：

1. **阿里云魔搭社区 (ModelScope 官方发布页)**：
   <https://www.modelscope.cn/models/lingxiaoyiyu/lingcraft-releases/files>
2. **GitHub Releases 官方发行页面**：
   <https://github.com/lingxiaoyiyu-hub/LingCraft-Release/releases>

---

## 🛡️ 漏洞与安全反馈通道

如果您在使用过程中发现了任何安全缺陷、可疑异常或希望就技术安全进行交流，请通过以下方式联系：

- 提交 GitHub Issue：[Security Advisory / Report Issue](https://github.com/lingxiaoyiyu-hub/LingCraft-Release/issues)
- 官方联系邮箱：`dev@lingcraft.local`

我们将在收到反馈后 24 小时内进行评估、分析与收口加固。
