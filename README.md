# Markdown Image AI Workflow

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](https://github.com/beiffeng/markdown-image-ai-workflow)
[![VSCode](https://img.shields.io/badge/VSCode-1.79+-green.svg)](https://code.visualstudio.com/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> **AI-Powered Markdown Image Workflow Management Expert**
> A modern solution for AI-driven image workflow management designed for Markdown writing, integrating intelligent upload, automatic sync, and multi-platform adaptation

## ✨ Core Features

### 🤖 **AI Intelligence**
- **AI-Driven Processing** - Smart image recognition, automatic path generation, intelligent renaming
- **Workflow Automation** - Full automation from paste → process → upload → replace
- **Smart Adaptation** - Automatically selects optimal processing strategies based on project type

### 🔄 **Workflow Management**
- **Complete Workflow** - End-to-end processing from image acquisition to final publication
- **Status Monitoring** - Real-time monitoring of processing status at each step
- **Error Recovery** - Intelligent fault detection and automatic retry mechanisms

### 🚀 **Multi-Platform Ecosystem**
- **GitHub** - Private repository support, full control (recommended)
- **Tencent Cloud COS** - Preferred for China users, fast and stable
- **Alibaba Cloud OSS** - High-performance object storage, suitable for China users
- **Qiniu Cloud Storage** - CDN optimized, free quota, suitable for individual users
- **SM.MS** - Traditional image hosting support (registration closed)
- **Cloudinary** - Professional CDN service (planned)

### 🔮 **AI-Enhanced Features**
- **Smart Tagging** - AI automatically generates image alt text and descriptions
- **Content Recognition** - Smart classification and tagging based on image content
- **Workflow Optimization** - AI learns user habits to optimize processing workflows

## 🚀 Quick Start

### 1️⃣ Install the Extension

Search for **"Markdown Image AI Workflow"** in the VSCode Extension Marketplace and install it.

### 2️⃣ Configure Image Workflow (Recommended)

Use the Command Palette (`Ctrl+Shift+P`) to run:
```
Markdown Image AI Workflow: Set Recommended Configuration
```

Or manually configure VSCode settings:
```json
{
  "markdown.copyFiles.destination": {
    "**/*.md": "assets/${documentBaseName}/"
  },
  "markdown.editor.drop.copyIntoWorkspace": "mediaFiles",
  "markdown.editor.filePaste.copyIntoWorkspace": "mediaFiles"
}
```

### 3️⃣ Select Image Hosting Platform

> ⚠️ **Important Notice**: SM.MS is not recommended as the service has closed new user registration ("We have disabled the registration feature"), and existing users face many limitations. We recommend using GitHub as the image hosting solution.

#### 🔒 GitHub (Recommended)
```json
{
  "markdownImageAIWorkflow.provider": "github",
  "markdownImageAIWorkflow.github.repo": "username/your-repo",
  "markdownImageAIWorkflow.github.token": "ghp_your-token-here",
  "markdownImageAIWorkflow.github.branch": "main"
}
```

#### ☁️ Alibaba Cloud OSS (High Performance)
```json
{
  "markdownImageAIWorkflow.provider": "oss",
  "markdownImageAIWorkflow.oss.accessKeyId": "LTAI5t...",
  "markdownImageAIWorkflow.oss.accessKeySecret": "your-access-key-secret",
  "markdownImageAIWorkflow.oss.bucket": "your-bucket-name",
  "markdownImageAIWorkflow.oss.region": "oss-cn-hangzhou"
}
```

#### ☁️ Tencent Cloud COS (Stable & Reliable)
```json
{
  "markdownImageAIWorkflow.provider": "cos",
  "markdownImageAIWorkflow.cos.secretId": "AKxxxxxxxxxxx...",
  "markdownImageAIWorkflow.cos.secretKey": "your-secret-key",
  "markdownImageAIWorkflow.cos.bucket": "your-bucket-1234567890",
  "markdownImageAIWorkflow.cos.region": "ap-guangzhou"
}
```

#### ☁️ Qiniu Cloud Storage (Free Quota)
```json
{
  "markdownImageAIWorkflow.provider": "qiniu",
  "markdownImageAIWorkflow.qiniu.accessKey": "your-access-key",
  "markdownImageAIWorkflow.qiniu.secretKey": "your-secret-key",
  "markdownImageAIWorkflow.qiniu.bucket": "your-bucket",
  "markdownImageAIWorkflow.qiniu.domain": "example.com",
  "markdownImageAIWorkflow.qiniu.zone": "z0"
}
```

#### ❌ SM.MS (Not Recommended, Existing Users Only)
```json
{
  "markdownImageAIWorkflow.provider": "smms",
  "markdownImageAIWorkflow.smms.token": "your-api-token-here"
}
```

**Note**: SM.MS has stopped new user registration and anonymous upload services. Unless you already have an account and API Token, please use the GitHub solution.

### 4️⃣ Start Writing Fluently

1. 📝 Write in Markdown files
2. 📷 Paste images (`Ctrl+V`)
3. ⚡ Automatic upload processing
4. 🔗 Links automatically replaced
5. ✨ Continue focusing on writing

## 🎮 Command Palette

| Command | Function | Shortcut |
|---------|----------|----------|
| `Markdown Image AI Workflow: Check Configuration` | Diagnose configuration issues | - |
| `Markdown Image AI Workflow: Set Recommended Configuration` | One-click optimization | - |
| `Markdown Image AI Workflow: Upload Current Image` | Manual image upload | - |

## ⚙️ Complete Configuration Options

### 🎛️ Core Configuration
```json
{
  // Enable status
  "markdownImageAIWorkflow.enabled": true,
  
  // Image hosting selection
  "markdownImageAIWorkflow.provider": "smms", // "smms" | "github" | "cos" | "oss" | "qiniu" | "cloudinary"
  
  // Processing strategy
  "markdownImageAIWorkflow.respectVSCodeConfig": true,
  "markdownImageAIWorkflow.fallbackBehavior": "sameDirectory", // "sameDirectory" | "disable" | "prompt"
  
  // Cleanup options
  "markdownImageAIWorkflow.deleteLocalAfterUpload": false
}
```

### 🌐 Image Hosting Platform Configuration
```json
{
  // SM.MS Configuration
  "markdownImageAIWorkflow.smms.token": "",
  
  // GitHub Configuration
  "markdownImageAIWorkflow.github.repo": "username/repo",
  "markdownImageAIWorkflow.github.token": "ghp_xxxxxxxxxxxx",
  "markdownImageAIWorkflow.github.branch": "main",
  
  // Tencent Cloud COS Configuration
  "markdownImageAIWorkflow.cos.secretId": "AKxxxxxxxxxxx",
  "markdownImageAIWorkflow.cos.secretKey": "xxxxxxxxxxxxxxxx",
  "markdownImageAIWorkflow.cos.bucket": "bucket-name-1234567890",
  "markdownImageAIWorkflow.cos.region": "ap-guangzhou",
  
  // Alibaba Cloud OSS Configuration
  "markdownImageAIWorkflow.oss.accessKeyId": "LTAI5t...",
  "markdownImageAIWorkflow.oss.accessKeySecret": "xxxxxxxxxxxxxxxx",
  "markdownImageAIWorkflow.oss.bucket": "bucket-name",
  "markdownImageAIWorkflow.oss.region": "oss-cn-hangzhou",
  
  // Qiniu Cloud Storage Configuration
  "markdownImageAIWorkflow.qiniu.accessKey": "xxxxxxxxxxxxxxxx",
  "markdownImageAIWorkflow.qiniu.secretKey": "xxxxxxxxxxxxxxxx",
  "markdownImageAIWorkflow.qiniu.bucket": "bucket-name",
  "markdownImageAIWorkflow.qiniu.domain": "example.com",
  "markdownImageAIWorkflow.qiniu.zone": "z0"
}
```

## 🎨 Advanced Path Configuration

Supports all VSCode path variables for complex file organization:

```json
{
  "markdown.copyFiles.destination": {
    // 📁 Organize by document
    "**/*.md": "assets/${documentBaseName}/",
    
    // 📅 Organize by project
    "/blog/**/*.md": "static/images/${documentBaseName}/",
    "/docs/**/*.md": "public/assets/",
    
    // 🏷️ Organize by type
    "/tutorials/**/*.md": "media/tutorials/${documentDirName}/",
    
    // 📊 Unified management
    "/wiki/**/*.md": "images/"
  }
}
```

### 📖 Supported Variables
- `${documentBaseName}` - Document name (without extension)
- `${documentFileName}` - Full document name
- `${documentDirName}` - Document directory name
- `${documentWorkspaceFolder}` - Workspace root path
- `${fileName}` - Image file name

## 🚦 Status Monitoring

Real-time status display in the status bar:

| Status | Meaning |
|--------|---------|
| `🌊 SM.MS` | Normal operation, using SM.MS |
| `🌊 GitHub` | Normal operation, using GitHub |
| `🌊 Tencent Cloud COS` | Normal operation, using Tencent Cloud COS |
| `🌊 Alibaba Cloud OSS` | Normal operation, using Alibaba Cloud OSS |
| `🌊 Qiniu Cloud Storage` | Normal operation, using Qiniu Cloud Storage |
| `⚙️ Needs Configuration` | Incomplete configuration |
| `⏸️ Disabled` | Extension disabled |
| `✅ Upload Successful` | Just completed upload |

![alt text](assets/README/image.png)

## 🔧 Troubleshooting

![alt text](assets/README/image-1.png)

### ❓ Common Issues

<details>
<summary><strong>Extension not responding?</strong></summary>

1. Check VSCode version (requires 1.79+)
2. Run "Check Configuration" command to diagnose
3. View the status shown in the status bar
4. Check Developer Tools console (`Help → Toggle Developer Tools`)
</details>

<details>
<summary><strong>Images not uploading automatically?</strong></summary>

1. Confirm you're working in a `.md` file
2. Check image format (supports .png, .jpg, .gif, .webp, .svg)
3. Verify `markdown.copyFiles.destination` configuration
4. Confirm image hosting service configuration is correct
</details>

<details>
<summary><strong>Link replacement not accurate?</strong></summary>

1. Check if Markdown syntax is standard `![alt](path)`
2. Confirm file name matching
3. Try manual upload command
4. View console error information
</details>

## 🗺️ Development Roadmap

### 🚀 Coming Soon
- [ ] **Cloudinary Integration** - Professional CDN support (Priority: High)
- [ ] **More Hosting Support** - Stable alternatives to SM.MS
- [ ] **AI Smart Tagging** - Automatic image description generation
- [ ] **Batch Processing** - One-click processing for multiple images
- [ ] **History Records** - Upload history management

### 🌟 Long-term Planning
- [ ] **Content Recognition** - AI-based image classification
- [ ] **Multi-language Descriptions** - AI generates multi-language alt text
- [ ] **Performance Optimization** - Automatic image compression
- [ ] **Team Collaboration** - Shared hosting configuration

## 🤝 Contributing

We welcome contributions of any kind!

- 🐛 **Report Issues** - [GitHub Issues](https://github.com/beiffeng/markdown-image-ai-workflow/issues)
- 💡 **Feature Suggestions** - [GitHub Discussions](https://github.com/beiffeng/markdown-image-ai-workflow/discussions)
- 🔧 **Code Contributions** - [Pull Requests](https://github.com/beiffeng/markdown-image-ai-workflow/pulls)

## 📄 License

This project is licensed under the [MIT License](LICENSE).

## 🙏 Special Thanks

- **VSCode Team** - For providing the powerful editor platform
- **Open Source Community** - For providing excellent dependency libraries
- **User Feedback** - For helping us continuously improve

---

<div align="center">

**AI-Powered Markdown Image Workflow Expert** ✨

[⭐ Star](https://github.com/beiffeng/markdown-image-ai-workflow) | [🐛 Report Issue](https://github.com/beiffeng/markdown-image-ai-workflow/issues) | [💬 Discuss](https://github.com/beiffeng/markdown-image-ai-workflow/discussions)

</div>

---

[中文](README.zh.md) | English
