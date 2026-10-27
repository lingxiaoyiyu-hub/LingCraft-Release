# 零创（LingCraft）· 安全策略与防伪核验

用户的数据资产、创作成果与软件供应链完整性是零创的最高优先级。

---

## 官方防伪校验

官方构建产物提供双重核验：

### 1. SHA-256 哈希核对

每个版本的安装包都在 Release 说明与云端 `version.json` 中公开实测 SHA-256。

以当前版本为例，在 PowerShell 中执行：

```powershell
Get-FileHash -Algorithm SHA256 "LingCraft_Setup_v3.6.14.exe"
```

与官方公布值比对：

- `LingCraft_Setup_v3.6.14.exe`
- SHA-256：`d5f4fb41e8ce9fb84d3e010c8f97083f19bfab5fa6c966af16511c4fa7ea0cf0`

一致即代表文件自发布后未被修改。历史版本哈希见对应 Release 说明。

### 2. Ed25519 云端清单签名

客户端检查更新时会校验云端 `version.json` 的 `manifest_sig`（Ed25519 签名）。即使 DNS 被劫持或清单被篡改，验签失败也会立即拒绝自动下载与安装，只保留官方发布页的手工下载通道。

---

## 官方下载渠道

请只从以下渠道下载：

1. 魔搭 ModelScope 官方发布页：<https://www.modelscope.cn/models/lingxiaoyiyu/lingcraft-releases/files>
2. GitHub Releases：<https://github.com/lingxiaoyiyu-hub/LingCraft-Release/releases>

网盘转载、破解版与二次打包版本可能被植入木马或窃取账号，请勿使用。

---

## 安全反馈

发现安全缺陷、可疑异常或下载到异常文件，请通过：

- GitHub Issue：<https://github.com/lingxiaoyiyu-hub/LingCraft-Release/issues>
- 客服 QQ：574719738

我们会在收到反馈后尽快评估与处理。
