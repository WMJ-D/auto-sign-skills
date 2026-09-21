---
name: auto-sign-cloud
description: 读取本机 Trae、WorkBuddy 或 CodeBuddy、Qoder 登录凭证并执行三平台积分签到。用户要求获取签到凭证、执行自动签到或排查平台凭证时使用。
---

# 自动签到

使用当前项目中的 `get-credentials.js` 完成凭证读取和签到。

## 执行流程

1. 在项目根目录运行：
   ```powershell
   node "get-credentials.js"
   ```
2. 观察脚本输出的实际数据目录、凭证有效性和签到结果。
3. 对失败平台，根据错误信息判断是目录不存在、客户端未登录、凭证过期还是接口失败。
4. 不要输出或复制完整 Token 到聊天内容；仅展示脱敏凭证和必要错误信息。
5. 生成的 `签到凭证.txt` 包含敏感凭证，不要提交到 Git 或发送给他人。

## 路径兼容

脚本会根据必需文件自动探测本机目录：

- Trae：`TRAE SOLO CN`、`TraeCode`、`TraeWork`、相关 CN 目录
- WorkBuddy / CodeBuddy：`CodeBuddy CN`、`WorkBuddy CN` 等目录
- Qoder：`QoderCN`、`Qoder CN`、`Qoder` 等目录

不要把平台目录写死为单一名称；优先使用目录探测结果。

## 约束

- 只使用 Node.js 内置模块，不主动下载依赖。
- 修改代码后只做语法诊断和人工审查，不执行打包。
- 不提交代码，除非用户明确要求提交。
- 凭证失效时提示用户重新登录对应桌面端后再次运行脚本。
