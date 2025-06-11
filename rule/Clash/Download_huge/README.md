# 大文件下载域名列表 (Download_huge.yaml)

这个规则文件包含了各种大文件下载场景的域名，适用于需要特殊网络策略处理大文件下载的场景。

## 📋 包含的域名类别

### 🤖 AI/ML 模型下载

- **HuggingFace 生态系统**: 包括官方域名和镜像站点
  - `huggingface.co` - HuggingFace 官方网站
  - `hf-mirror.com` - 国内镜像站
  - `aifasthub.com` - AI快站镜像服务
  - `cdn-lfs.huggingface.co` - LFS 大文件存储

### 💻 软件开发与分发

- **GitHub**: 代码仓库和 Release 文件下载
- **Docker**: 容器镜像下载
- **开发工具**: JetBrains、Visual Studio、Eclipse 等 IDE
- **包管理器**: npm、PyPI、Maven 等

### 🎮 游戏平台

- **Steam**: 游戏下载和 Workshop 内容
- **Epic Games Store**: 游戏和 Unreal Engine
- **其他平台**: Battle.net、Origin、GOG、Uplay
- **游戏模组**: Nexus Mods、CurseForge、ModDB

### ☁️ 云服务与 CDN

- **主要 CDN**: Cloudflare、AWS CloudFront、Azure CDN
- **专业 CDN**: Fastly、KeyCDN、BunnyCDN、Akamai
- **云存储**: Google Drive、OneDrive、Dropbox、Mega

### 🖥️ 操作系统与固件

- **Microsoft**: Windows 更新和软件下载
- **Linux 发行版**: Ubuntu、Debian、CentOS、Fedora
- **Apple**: macOS 和 iOS 相关下载

### 📱 移动应用

- **Google Play Store**: Android 应用下载
- **Apple App Store**: iOS 应用下载
- **第三方**: APKPure、APKMirror

### 🎬 多媒体内容

- **视频平台**: YouTube、Twitch、Netflix
- **内容分发**: 各种 CDN 和流媒体服务

### 📚 学术与研究

- **论文数据库**: arXiv、IEEE、ACM、Nature
- **研究平台**: ResearchGate、ScienceDirect

## 🔧 使用方法

### Clash 配置

将此规则文件放置在 Clash 配置目录的 `rules` 文件夹中，然后在主配置文件中引用：

```yaml
rule-providers:
  download-huge:
    type: http
    behavior: domain
    url: "https://your-domain/Download_huge.yaml"
    path: ./rules/Download_huge.yaml
    interval: 86400

rules:
  - RULE-SET,download-huge,PROXY
```

### 策略建议

根据您的网络环境和需求，可以考虑以下策略：

1. **直连策略**: 如果本地网络对这些域名访问良好

   ```yaml
   - RULE-SET,download-huge,DIRECT
   ```
2. **代理策略**: 如果需要通过代理访问

   ```yaml
   - RULE-SET,download-huge,PROXY
   ```
3. **专用策略组**: 为大文件下载创建专门的策略组

   ```yaml
   proxy-groups:
     - name: "大文件下载"
       type: select
       proxies:
         - DIRECT
         - "高速节点1"
         - "高速节点2"

   rules:
     - RULE-SET,download-huge,大文件下载
   ```

## 🌟 特色功能

### HuggingFace 加速下载

针对 AI 开发者，特别优化了 HuggingFace 模型下载：

- **官方域名**: `huggingface.co`
- **镜像站点**: `hf-mirror.com`、`aifasthub.com`
- **CDN 节点**: `cdn-lfs.huggingface.co`

### 多种下载方式支持

- **网页下载**: 直接通过浏览器
- **命令行工具**: huggingface-cli、git、docker 等
- **API 下载**: 各种编程语言的 SDK
- **专用工具**: WorkshopDL、hfd 脚本等

## 📊 覆盖的下载场景

| 场景类型 | 典型文件大小  | 主要域名示例                       |
| -------- | ------------- | ---------------------------------- |
| AI 模型  | 1GB - 100GB+  | huggingface.co, hf-mirror.com      |
| 游戏下载 | 10GB - 150GB+ | steamcontent.com, epicgames.com    |
| 软件分发 | 100MB - 10GB  | github.com, sourceforge.net        |
| 容器镜像 | 100MB - 5GB   | docker.io, quay.io                 |
| 系统更新 | 1GB - 20GB    | download.microsoft.com, ubuntu.com |

## 🔄 更新频率

建议每周更新一次规则文件，以确保包含最新的域名和服务。

## ⚠️ 注意事项

1. **带宽消耗**: 大文件下载会消耗大量带宽，请根据网络套餐合理使用
2. **存储空间**: 确保有足够的本地存储空间
3. **网络稳定性**: 建议在网络稳定时进行大文件下载
4. **断点续传**: 优先使用支持断点续传的下载工具

## 🤝 贡献

如果您发现遗漏的重要域名或有改进建议，欢迎提交 Issue 或 Pull Request。

## 📄 许可证

本规则文件遵循项目的开源许可证。
