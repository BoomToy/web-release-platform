# 工具下载目录

此目录用于存放提供给用户下载的工具文件。

## 目录结构

```
downloads/
├── README.md           # 本说明文件
├── scripts/            # 脚本工具 (.sh, .py, .js, .bat 等)
│   ├── backup.sh
│   └── deploy.py
├── apps/               # 应用程序 (.zip, .exe, .dmg, .apk 等)
│   ├── tool-a.zip
│   └── tool-b.dmg
├── html/               # HTML 工具 (.html, .htm)
│   ├── calculator.html
│   └── timer.html
└── docs/               # 文档资料 (.pdf, .md, .txt 等)
    └── guide.pdf
```

## 使用方式

1. 将可下载的工具文件放入此目录的合适子文件夹中
2. 在 `index.html` 的 `toolsData` 中配置工具时，将 `url` 指向此目录下的文件路径

示例：

### 1. 脚本工具
```javascript
{
    id: 'backup-script',
    name: '自动备份脚本',
    description: '定时备份文件到云端...',
    url: 'downloads/scripts/backup.sh',
    category: 'utility',
    icon: '💾',
    platforms: ['script']
}
```

### 2. 应用程序
```javascript
{
    id: 'desktop-tool',
    name: '桌面小工具',
    description: 'Windows桌面辅助工具...',
    url: 'downloads/apps/tool.zip',
    category: 'utility',
    icon: '🖥️',
    platforms: ['desktop']
}
```

### 3. HTML 工具
```javascript
{
    id: 'html-calculator',
    name: '科学计算器',
    description: '功能完整的网页版计算器...',
    url: 'downloads/html/calculator.html',  // 可直接打开
    category: 'utility',
    icon: '🧮',
    platforms: ['desktop', 'mobile']  // HTML工具通常同时支持电脑和手机
}
```

**HTML 工具特点：**
- 用户点击后可直接在浏览器中打开使用
- 无需下载安装，即开即用
- 可同时适配电脑和手机浏览器

## 注意事项

- 建议按工具类型分子文件夹存放（如 `scripts/`、`apps/`、`html/`、`docs/`）
- 文件名建议使用英文，避免空格和特殊字符
- 大文件建议压缩后存放（zip、tar.gz 等）
- **HTML 文件**：可直接放入 `html/` 目录，用户可直接在浏览器中打开
- 更新工具版本时，可考虑保留旧版本或添加版本号到文件名

## 各类型文件存放建议

| 类型 | 存放目录 | 文件扩展名 | 使用方式 |
|------|---------|-----------|---------|
| 脚本工具 | `scripts/` | .sh, .py, .js, .bat, .ps1 | 下载后在本地运行 |
| 应用程序 | `apps/` | .zip, .exe, .dmg, .apk, .msi | 下载后安装运行 |
| HTML 工具 | `html/` | .html, .htm | 直接在浏览器中打开 |
| 文档资料 | `docs/` | .pdf, .md, .txt, .doc | 下载后查看 |

## Git 提交

此目录中的文件会被提交到 Git 仓库。如果文件较大（>10MB），建议：

1. 使用 Git LFS（Large File Storage）管理大文件
2. 或将大文件托管到外部存储（如云存储），此处只存放下载链接
