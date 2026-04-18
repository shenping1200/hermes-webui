# Hermes Agent + WebUI 部署指南

本仓库提供 Hermes Agent 及其可视化 WebUI 的完整部署方案，支持本地运行 Gemma 4 模型并对接微信。

## 🚀 快速部署流程

### 一、安装 WSL2 (Windows 用户)
在 PowerShell（管理员）执行：
```powershell
wsl --install
```
安装完成后重启电脑，然后安装 Ubuntu：
```powershell
wsl --install -d Ubuntu
```
检查版本确保输出为 `WSL2`：
```powershell
wsl --version
```

### 二、部署 Hermes Agent + UI

#### 1. 安装 Hermes Agent
进入 Ubuntu 后执行：
```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```
安装后运行 `hermes doctor` 检查环境。

#### 2. 安装 Hermes WebUI
```bash
git clone https://github.com/nesquena/hermes-webui.git hermes-webui
cd hermes-webui
./start.sh
```
启动后访问：`http://127.0.0.1:8787` 🎉

#### 3. Mac 系统一键部署
```zsh
git clone https://github.com/nesquena/hermes-webui.git hermes-webui
cd hermes-webui
python3 bootstrap.py
```



### 四、对接微信 (重点)
1. 执行 `hermes setup`
2. 在 `messaging platforms` 中选择 `weixin / wechat`
3. 扫码登录即可完成绑定。

## 🎯 最终效果
- ✅ **可视化管理**: 通过 WebUI 轻松配置。
- ✅ **微信对话**: 拥有一个可执行自动化任务的微信 AI 助手。

## 🛠️ 常见问题排查
- **上下文不足**: 换更大模型或手动设置 `context_length`。
- **Ollama 无法访问**: 检查是否使用了局域网 IP 而非 `127.0.0.1`。
- **WebUI 打不开**: 尝试重新运行 `./start.sh` 或检查端口占用。
- **微信掉线**: 保持 Hermes 常驻运行，避免频繁重启。
