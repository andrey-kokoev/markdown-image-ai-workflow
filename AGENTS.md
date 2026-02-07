# AGENTS.md

Guidelines for AI agents working on the Markdown Image AI Workflow VSCode extension.

## Project Overview

**Markdown Image AI Workflow** is a VSCode extension that automates image hosting for Markdown files. When users paste images into Markdown documents, the extension automatically uploads them to configured cloud services (GitHub, COS, OSS, Qiniu, etc.) and replaces local paths with remote URLs.

## Quick Reference

- **Language**: TypeScript
- **Runtime**: VSCode Extension Host (Node.js)
- **Build Tool**: Webpack + TypeScript
- **Package Manager**: npm
- **Entry Point**: `src/extension.ts`
- **Distribution**: `dist/extension.js`

## Architecture

### Core Components

```
src/
├── extension.ts           # Main entry point, activates the extension
├── core/
│   ├── configReader.ts    # Reads VSCode and plugin configuration
│   ├── pathResolver.ts    # Resolves image paths from Markdown
│   └── fileWatcher.ts     # Watches for file changes/pastes
├── uploaders/
│   ├── uploader.interface.ts  # Factory and interfaces
│   ├── github.uploader.ts     # GitHub as image host
│   ├── cos.uploader.ts        # Tencent Cloud COS
│   ├── oss.uploader.ts        # Alibaba Cloud OSS
│   ├── qiniu.uploader.ts      # Qiniu Cloud
│   └── smms.uploader.ts       # SM.MS (deprecated)
├── utils/
│   ├── markdownReplacer.ts    # Replaces image URLs in Markdown
│   ├── imagePathParser.ts     # Parses image paths from Markdown
│   ├── cursorPosition.ts      # Handles cursor positioning
│   └── configGuide.ts         # Configuration helper UI
├── providers/
│   └── imageCodeActionProvider.ts  # Quick fixes and diagnostics
├── i18n/
│   └── locales/             # Translation files
│       ├── en.json
│       └── zh-cn.json
└── types/
    └── index.ts            # TypeScript type definitions
```

### Key Workflow

1. **Activation**: Extension activates when Markdown files are opened
2. **File Watching**: `ImageFileWatcher` monitors for new image files in configured paths
3. **Upload**: When images detected, `UploaderFactory` creates appropriate uploader
4. **Replace**: `MarkdownReplacer` updates Markdown content with remote URLs
5. **Status**: Status bar shows real-time upload progress and provider info

## Development Commands

```bash
# Install dependencies
npm install

# Compile TypeScript
npm run compile

# Watch for changes during development
npm run watch

# Build production bundle
npm run package

# Launch extension in debug mode (VSCode)
# Press F5 in VSCode with this project open
```

## Testing Strategy

- **Manual Testing**: Use VSCode's "Run Extension" (F5) to test in a development host
- **Test Cases**:
  - Paste images in Markdown and verify upload
  - Test each image hosting provider
  - Verify Markdown link replacement
  - Check status bar updates
  - Test configuration validation

## Code Style Guidelines

- Use **TypeScript strict mode** (configured in tsconfig.json)
- Follow **existing naming conventions**:
  - Classes: `PascalCase` (e.g., `ImageFileWatcher`)
  - Functions/Variables: `camelCase` (e.g., `uploadImage`)
  - Constants: `UPPER_SNAKE_CASE` for true constants
  - Interfaces: `PascalCase` with `I` prefix (e.g., `IUploader`)
- **Error Handling**: Always wrap external API calls in try-catch
- **Logging**: Use `console.log()` for development, remove before committing
- **Comments**: Write in English for code, Chinese OK for internal notes

## Adding New Image Hosting Providers

To add a new uploader (e.g., AWS S3):

1. Create `src/uploaders/s3.uploader.ts`
2. Implement the `IUploader` interface
3. Add provider to `UploaderFactory`
4. Add configuration schema to `package.json`
5. Add translations to i18n locales
6. Update README.md with setup instructions

### Interface Template

```typescript
export class S3Uploader implements ImageUploader {
  public readonly name = 's3';

  isConfigured(): boolean {
    // Check required configuration is available (env vars, settings, etc.)
    return true;
  }

  async upload(filePath: string): Promise<UploadResult> {
    // Implementation
    return {
      success: true,
      provider: this.name,
      // error: 'Error message if upload failed' // optional
    };
  }
}
```

## Configuration System

Configurations are defined in `package.json` under `contributes.configuration`:

- **Basic Settings**: Enable/disable, language, provider selection
- **Provider Configs**: Separate sections for each hosting service
- **Runtime**: Access via `vscode.workspace.getConfiguration()`

## Internationalization (i18n)

- **Languages Supported**: English (`en`), Simplified Chinese (`zh-cn`)
- **Files**: `src/i18n/locales/{lang}.json`
- **Usage**: Import `t()` function from `src/i18n`
- **Adding Language**: Create new locale file, add to `package.json` enum

## Common Tasks

### Adding a New Command

1. Define command in `package.json` under `contributes.commands`
2. Register command in `extension.ts` activate function
3. Implement command handler

### Updating Status Bar

Modify `updateStatusBar()` method in `MarkdownImageAIWorkflowExtension` class.

### Debugging Tips

- Open "Developer: Toggle Developer Tools" in VSCode to see console logs
- Check Output panel → "Log (Extension Host)" for errors
- Use breakpoints in `src/extension.ts` for main logic

## Security Considerations

- **Never commit** API keys, tokens, or secrets
- Use VSCode's `SecretStorage` for sensitive data (currently in plain config, should be improved)
- Validate all file paths to prevent directory traversal
- Sanitize image file names before upload

## Dependencies

Key production dependencies:
- `axios` - HTTP requests for uploads
- `ali-oss`, `cos-nodejs-sdk-v5`, `qiniu` - Cloud SDKs
- `minimatch` - Path pattern matching

## Build & Package

```bash
# Build production version
npm run package

# This creates dist/extension.js which is the bundled extension
# VSCode marketplace packaging happens via vsce (not in this repo)
```

## Documentation

- **README.md**: User-facing documentation (keep updated!)
- **CHANGELOG.md**: Track version changes
- **AGENTS.md**: This file - for AI agents

## Questions?

For architectural decisions, check:
- Why Webpack? For bundling and tree-shaking dependencies
- Why Factory pattern for uploaders? Easy to add new providers
- Why file watching vs. clipboard interception? VSCode security model

---

Last Updated: 2026-02-01
