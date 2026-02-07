# VSCode Extension Publishing Guide

## 📋 Pre-Publish Checklist

### 🔧 Environment Setup
- [ ] Ensure latest version of `@vscode/vsce` is installed
- [ ] Have a valid Azure DevOps Personal Access Token
- [ ] Publisher account: `beifeng`

### 📝 Code Quality Checks
- [ ] Run `npm run compile` to ensure no compilation errors
- [ ] Test main functionality (test at least one image hosting service)
- [ ] Check README.md documentation completeness
- [ ] Verify package.json version number is correct

### 🎨 Resource Files Check
- [ ] Icon file `icons/icon.png` exists and is 128x128
- [ ] Icon displays correctly in different themes
- [ ] LICENSE file is complete

## 🚀 Publishing Process

### Method 1: Use One-Click Publish Script (Recommended)
```bash
./scripts/publish.sh
```

### Method 2: Manual Publishing Steps

#### 1. Login to Publisher Account
```bash
vsce login beifeng
```
> Note: Enter your Personal Access Token when prompted

#### 2. Version Update (Optional)
```bash
# Patch version (0.1.0 -> 0.1.1)
npm version patch

# Minor version (0.1.0 -> 0.2.0)  
npm version minor

# Major version (0.1.0 -> 1.0.0)
npm version major
```

#### 3. Local Package Testing
```bash
vsce package
```
Check if the generated .vsix file size and content are reasonable

#### 4. Publish to Marketplace
```bash
vsce publish
```

#### 5. Push Git Changes
```bash
git push origin main
git push origin --tags
```

## 📊 Post-Publish Verification

### Marketplace Verification
- [ ] Search for plugin name in VSCode marketplace
- [ ] Check plugin page information displays correctly
- [ ] Verify icon and description
- [ ] Test installing plugin from marketplace

### Functionality Verification
- [ ] Plugin activates normally after installation
- [ ] Configuration page is accessible
- [ ] Core functionality works properly

## ⚠️ Important Notes

### Security Requirements
- **Never hardcode Personal Access Token in code or scripts**
- Ensure sensitive configuration files are excluded in .gitignore
- Check for accidentally included test keys before publishing

### Version Management
- Follow Semantic Versioning
- Published versions cannot be undone, proceed with caution
- Major changes should increase major version number

### Publishing Frequency
- Bug fixes: Publish patch version promptly
- New features: Plan feature sets before publishing minor version
- Major refactoring: Carefully plan major version releases

## 🔗 Useful Links

- [VSCode Extension Marketplace](https://marketplace.visualstudio.com/)
- [Plugin Management Page](https://marketplace.visualstudio.com/manage/publishers/beifeng)
- [vsce Official Documentation](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)
- [Semantic Versioning Specification](https://semver.org/)

## 📞 Troubleshooting

### Common Publishing Errors
1. **Icon file not found**: Check if icons/icon.png exists
2. **Version compatibility error**: Ensure engines.vscode matches @types/vscode version
3. **Token validation failed**: Check Personal Access Token permissions and expiration
4. **File too large**: Check .vscodeignore configuration, exclude unnecessary files

### Emergency Rollback
If serious issues are found after publishing:
1. Immediately publish a fix version (increase patch number)
2. Do not attempt to delete published versions
3. Add known issues note on marketplace page

---

📝 **Last Updated**: 2026-02-01
🔧 **Maintainer**: beifeng

---

[中文](PUBLISH_GUIDE.zh.md) | English
