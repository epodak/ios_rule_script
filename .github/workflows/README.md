# 🔄 工作流程说明

## 📋 分支策略

### 🌿 分支说明
- **`master`** - 主分支，完全追踪上游 `blackmatrix7/ios_rule_script`
- **`dev`** - 开发分支，包含个人配置和workflow文件

### ⚡ 同步策略
1. **强制同步**: master分支会被强制重置到上游最新版本
2. **个人文件**: 从dev分支复制个人配置文件到master
3. **workflow位置**: 所有workflow文件都在dev分支，避免被上游覆盖

## 🔧 工作流文件

### `sync-master-from-dev.yml` - 主同步工作流
**触发条件**:
- ⏰ 每天北京时间早上8点自动执行
- 📝 dev分支有推送时触发
- 🎯 支持手动触发

**执行流程**:
1. 🚀 检出dev分支
2. 📥 获取上游和origin的最新更新
3. 🌿 切换到master分支
4. ⚡ 强制将master重置到上游最新版本
5. 🔧 从dev分支复制个人配置文件
6. 💾 提交并推送master分支更改

### 📁 个人文件列表
当前工作流会从dev分支复制以下文件到master:
```
rule/Clash/Cursor/Cursor.yaml
rule/Clash/DIY_Mac/DIY_Mac.yaml
rule/Clash/DIY_Win/DIY_Win.yaml
rule/Clash/Download_huge/Download_huge.yaml
rule/Clash/Download_huge/README.md
rule/Clash/porn_list/porn_list.yaml
rule/Clash/porn_video/porn_video.yaml
```

## 🎯 使用方法

### 手动触发同步
1. 进入GitHub仓库的Actions页面
2. 选择 "🔄 从dev分支同步master" 工作流
3. 点击 "Run workflow" 按钮

### 添加新的个人文件
1. 将文件添加到dev分支
2. 编辑 `sync-master-from-dev.yml` 中的 `PERSONAL_FILES` 数组
3. 提交到dev分支，会自动触发同步

### 修改个人配置
1. 在dev分支修改个人配置文件
2. 推送到dev分支
3. 工作流会自动将更改同步到master分支

## ⚠️ 重要说明

1. **不要在master分支直接修改**: master分支会被强制重置，所有直接修改都会丢失
2. **所有自定义内容都在dev分支**: 包括workflow、个人配置等
3. **备份机制**: 每次强制重置前会自动创建备份标签
4. **冲突处理**: 使用强制重置，避免任何合并冲突

## 🔗 相关链接
- [上游仓库](https://github.com/blackmatrix7/ios_rule_script)
- [GitHub Actions文档](https://docs.github.com/en/actions) 