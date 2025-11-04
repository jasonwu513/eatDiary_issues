# Issue #002: Food Image Disappears When Changing Food Type

**GitHub Issue**: [#2](https://github.com/jasonwu513/eatDiary_issues/issues/2)

## Status: 🔴 OPEN

**Priority**: P2 - High
**Type**: Bug
**Component**: Food Management / UI
**Created**: 2025-11-04
**Labels**: `bug`, `ui`, `food-management`, `image-handling`

## 📋 Overview

When users change the food type (restaurant/recipes/manufacturer) on the food detail page, the food image disappears immediately. The image only reappears after reloading the page.

## 🐛 Problem Description

**Current Behavior:**
- User navigates to food detail page with an image displayed
- User changes the food type dropdown (e.g., from "Restaurant" to "Recipes")
- The food image immediately disappears from the UI
- The image remains missing until the user manually reloads the page

**Expected Behavior:**
- Food image should remain visible when changing the food type
- Image should persist across all food type selections
- No need to reload the page to restore the image

**User Impact:**
- Confusing user experience
- Users may think the image was deleted
- Extra step required (page reload) to see the image again
- Disrupts the workflow when editing food details

## 🔍 Technical Details

**Affected Components:**
- Food Detail Page
- Food Type Dropdown/Selector
- Image Display Component

**Root Cause (Hypothesis):**
- State management issue when updating food type
- Image widget may be re-rendering with null/empty image data
- Image URL or path not being preserved during food type change
- Possible key mismatch causing widget to rebuild incorrectly

**Affected Platforms:**
- [ ] iOS
- [ ] Android
- [ ] Both (needs verification)

## ✅ Acceptance Criteria

- [ ] Food image remains visible when changing food type from any type to any other type
- [ ] Image persists when switching between: Restaurant ↔ Recipes ↔ Manufacturer
- [ ] No page reload required to restore the image
- [ ] Image state is properly maintained during food type updates
- [ ] Verify fix works on both iOS and Android platforms

## 🛠️ Proposed Solution

1. **Investigate State Management**
   - Check how food type changes trigger state updates
   - Verify image data is included in state updates
   - Ensure image URL/path is not being cleared during type change

2. **Check Image Widget Implementation**
   - Verify the image widget key is stable across rebuilds
   - Ensure image source is properly bound to food model
   - Check if image caching is working correctly

3. **Potential Fixes**
   - Preserve image data when updating food type in state
   - Use stable widget keys for image components
   - Ensure food model update includes all fields (not just type)
   - Add image data validation before state update

4. **Testing**
   - Test all food type transitions (Restaurant → Recipes, Restaurant → Manufacturer, etc.)
   - Verify fix on both iOS and Android
   - Test with different image sources (local, network)
   - Verify no regressions in other food detail functionality

## 📱 Affected Screens

- Food Detail Page (all food types)

## 🔗 Related Issues

None currently

## 📸 Screenshots

_To be added: Screenshots showing image disappearing after food type change_

## 💡 Additional Context

This appears to be a state management or widget lifecycle issue. The food type change likely triggers a rebuild that doesn't properly maintain the image state. This is a high-priority bug as it affects core food management functionality and creates a poor user experience.

## 🧪 Steps to Reproduce

1. Open eatDiary app
2. Navigate to any food item with an image
3. Open the food detail page
4. Verify the image is displayed correctly
5. Change the food type using the dropdown (e.g., Restaurant → Recipes)
6. Observe that the image disappears immediately
7. Reload the page
8. Observe that the image reappears

## 🏷️ Tags

`bug`, `ui`, `food-management`, `image-handling`, `state-management`, `high-priority`
