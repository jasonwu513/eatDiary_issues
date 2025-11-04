# Issue #001: Navigation Bar i18n - Hardcoded English Labels

**GitHub Issue**: [#1](https://github.com/jasonwu513/eatDiary_issues/issues/1)

## Status: 🟢 RESOLVED

**Priority**: P2 - High
**Type**: Enhancement
**Component**: Core / Navigation
**Created**: 2025-11-04
**Resolved**: 2025-11-04
**Labels**: `i18n`, `ui`, `navigation`, `core`

## 📋 Overview

The bottom navigation bar and navigation rail currently display hardcoded English route names instead of localized labels. This creates a poor user experience for non-English users and breaks the app's dual-language support (Traditional Chinese / English).

## 🐛 Problem Description

**Current Behavior:**
- Navigation items show raw route names (e.g., "home", "calendar", "statistics")
- No localization applied to navigation labels
- Inconsistent with the rest of the app's i18n implementation

**Expected Behavior:**
- Navigation labels should display localized text based on user's language preference
- Traditional Chinese users should see: "首頁", "日曆", "統計" etc.
- English users should see: "Home", "Calendar", "Statistics" etc.

## 🔍 Technical Details

**Affected Components:**
- Bottom Navigation Bar (mobile view)
- Navigation Rail (tablet/desktop view)

**Root Cause:**
- Navigation labels are likely using route names directly instead of calling localization keys
- Missing integration with Flutter's localization system (AppLocalizations)

## ✅ Acceptance Criteria

- [x] Bottom navigation bar displays localized labels
- [x] Navigation rail displays localized labels
- [x] Labels update when user changes language preference
- [x] All navigation items are properly translated (Traditional Chinese & English)
- [x] No hardcoded strings in navigation components

## 🛠️ Proposed Solution

1. **Update Navigation Item Configuration**
   - Replace hardcoded route names with localization keys
   - Use `AppLocalizations.of(context)` to fetch localized strings

2. **Add Translation Keys**
   - Add navigation label keys to `app_en.arb` and `app_zh.arb`
   - Follow existing naming conventions (e.g., `navigation_home`, `navigation_calendar`)

3. **Test Language Switching**
   - Verify labels update when language changes
   - Test on both mobile and tablet layouts

## 📱 Affected Screens

- Main navigation (all screens with bottom nav or rail)

## 🔗 Related Issues

None currently

## 📸 Screenshots

_To be added if available_

## 💡 Additional Context

This issue is part of the broader i18n improvement initiative to ensure full dual-language support throughout the application.

## 🏷️ Tags

`i18n`, `localization`, `navigation`, `ui`, `enhancement`, `high-priority`
