# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **dedicated issue tracking repository** for eatDiary - a Flutter-based mobile application for tracking daily meals, nutrition, and eating habits. This repository does NOT contain the application source code; it serves solely as a centralized hub for:

- Bug reports
- Feature requests
- User feedback
- Issue documentation and tracking

The actual eatDiary application is developed separately.

## Repository Architecture

### Structure Overview

```
eatDiary_issues/
├── README.md              # English documentation
├── README_zh-TW.md        # Traditional Chinese documentation
└── issues/
    ├── README.md          # Issue tracking dashboard with statistics
    └── XXX-issue-name.md  # Individual issue documents
```

### Bilingual Support

This repository maintains **full bilingual support** for Traditional Chinese and English:
- All root-level README files exist in both languages
- Issue content is typically in English for consistency
- When updating README.md, also update README_zh-TW.md with corresponding Traditional Chinese content

## Issue Management System

### Issue File Naming Convention

Issue files follow the pattern: `NNN-brief-description.md` where:
- `NNN` is a zero-padded 3-digit sequential number (001, 002, etc.)
- `brief-description` is a kebab-case summary of the issue
- Example: `001-navigation-i18n-labels.md`

### Issue File Structure

Each issue file must contain:

```markdown
# Issue #NNN: [Title]

**GitHub Issue**: [#N](https://github.com/jasonwu513/eatDiary_issues/issues/N)

## Status: [🔴 OPEN | 🟡 IN PROGRESS | 🟢 RESOLVED | ⚫ CLOSED]

**Priority**: [P0-P4] - [Critical/Very High/High/Medium/Low]
**Type**: [Bug | Enhancement | Feature Request | Documentation]
**Component**: [Component Name]
**Created**: YYYY-MM-DD
**Labels**: `label1`, `label2`, ...

## 📋 Overview
[Clear description of the issue]

## 🐛 Problem Description / 💡 Feature Description
**Current Behavior:** / **Proposed Feature:**
**Expected Behavior:** / **Use Case:**

## 🔍 Technical Details
**Affected Components:**
**Root Cause:** (for bugs)

## ✅ Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## 🛠️ Proposed Solution
[Detailed implementation steps]

## 📱 Affected Screens
[List of screens]

## 🔗 Related Issues
[Links to related issues]

## 💡 Additional Context
[Any other relevant information]
```

### Priority Levels

- **P0 - Critical**: App-breaking bugs, data loss issues
- **P1 - Very High**: Major functionality broken, security issues
- **P2 - High**: Important features not working, significant UX issues
- **P3 - Medium**: Minor bugs, nice-to-have features
- **P4 - Low**: Cosmetic issues, future enhancements

### Issue Status Indicators

- 🔴 **OPEN**: Issue identified, not yet being worked on
- 🟡 **IN PROGRESS**: Actively being addressed
- 🟢 **RESOLVED**: Fixed but may need verification
- ⚫ **CLOSED**: Completed and verified

### GitHub Labels

Standard labels used across issues:
- `bug` - Something isn't working
- `enhancement` - New feature or request
- `iOS` - iOS specific issues
- `android` - Android specific issues
- `critical` - Critical bugs needing immediate attention
- `documentation` - Documentation improvements
- `question` - Further information requested
- `discussion` - General discussion topics
- `i18n` - Internationalization/localization
- `ui` - User interface
- `navigation` - Navigation components
- `core` - Core functionality
- `high-priority` - High priority issues

## Working with Issues

### Creating a New Issue

1. **Create local issue file** in `issues/` directory:
   - Use next sequential number (check `issues/README.md` for current count)
   - Follow naming convention: `NNN-brief-description.md`
   - Use the issue file structure template above

2. **Create GitHub issue** using `gh` CLI:
   ```bash
   gh issue create --title "Issue Title" --body "$(cat <<'EOF'
   [Issue content]
   EOF
   )"
   ```

3. **Add appropriate labels**:
   ```bash
   gh issue edit N --add-label "label1,label2,label3"
   ```

4. **Update tracking files**:
   - Add entry to `issues/README.md` issue table
   - Update statistics in `issues/README.md`
   - Update quick stats in both `README.md` and `README_zh-TW.md`
   - Add GitHub issue link to local issue file

### Updating Issue Status

When changing issue status:

1. Update the status emoji in the issue file header
2. Update the corresponding row in `issues/README.md` table
3. Update statistics in `issues/README.md`
4. Update quick stats in root README files (both languages)
5. Update GitHub issue status if applicable:
   ```bash
   gh issue close N    # Close issue
   gh issue reopen N   # Reopen issue
   ```

### Issue Table Format

The `issues/README.md` maintains a table with this structure:

```markdown
| ID | Title | Priority | Status | Type | Labels | GitHub |
|----|-------|----------|--------|------|--------|--------|
| [#NNN](NNN-file.md) | Title | P2 - High | 🔴 OPEN | Enhancement | `label1`, `label2` | [GH#N](https://github.com/jasonwu513/eatDiary_issues/issues/N) |
```

## GitHub CLI Commands

This repository uses the GitHub CLI (`gh`) for issue management:

```bash
# View issue
gh issue view N

# Create issue
gh issue create --title "Title" --body "Body"

# Edit issue
gh issue edit N --add-label "label1,label2"
gh issue edit N --title "New Title"

# Close/reopen issue
gh issue close N
gh issue reopen N

# List issues
gh issue list
gh issue list --label "bug"
gh issue list --state "open"

# Create repository labels
gh label create "label-name" --description "Description" --color "hex-color"
```

## Git Workflow

Standard git workflow for this repository:

```bash
# After creating/updating issues
git add .
git commit -m "Add issue #NNN: Brief description"
git push origin main
```

Remote repository: `git@github.com:jasonwu513/eatDiary_issues.git`

## Context About eatDiary Application

When creating or discussing issues, note that eatDiary is a **Flutter mobile application** with:

- **Platforms**: iOS and Android
- **Language Support**: Traditional Chinese (zh-TW) and English (en)
- **Key Features**: Meal tracking, nutrition tracking, eating habits analysis
- **Localization System**: Uses Flutter's `AppLocalizations` with `.arb` files

When writing issues related to the app:
- Specify platform if iOS/Android specific
- Consider both language contexts for UI/UX issues
- Reference Flutter/Dart conventions when discussing technical solutions
- Include device information requirements for bug reports

## Response Time Commitments

The repository maintains these response time goals:
- **Critical bugs** (P0-P1): 24 hours
- **Regular bugs** (P2-P3): 3-5 business days
- **Feature requests**: 1 week
- **General feedback**: 1 week

These should be considered when prioritizing and triaging issues.
