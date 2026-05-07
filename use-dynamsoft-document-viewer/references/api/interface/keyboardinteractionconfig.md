---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface KeyboardInteractionConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface KeyboardInteractionConfig
breadcrumbText: Interface KeyboardInteractionConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface KeyboardInteractionConfig Page
permalink: /api/interface/keyboardinteractionconfig.html
---

# KeyboardInteractionConfig

```typescript
interface KeyBoardInteractionConfig {
    enableZoom?: boolean; // Ctrl + =/-
    enableUndoRedo?: boolean; // Ctrl + z/y
    enableAnnotationClipboard?: boolean; // Ctrl + c/x/v
    enableMultipleAnnotationsSelection?: boolean; // Ctrl + click
    enableMultiplePagesSelection?: boolean; // Ctrl/Shift + click 
    enableMoveAnnotation?: boolean; // Arrow
    enableDeleteAnnotation?: boolean; // Backspace/Delete
    enablePageNavigation?: boolean; // Home End ArrowLeft ArrowRight ArrowDown ArrowUp PageUP PageDown
}
```

## Attributes

Aside from the shortcuts controlled by `KeyboardInteractionConfig`, the uncontrolled shortcuts are always available for use.
- Esc: Deselects annotations or exits annotation editing mode.
- Delete/Backspace: Deletes text content in text-based annotations while in editing mode.
- Arrow keys: Moves the cursor within text-based annotations while in editing mode.
- Ctrl+A: Selects all text in text-based annotations while in editing mode, or selects all pages in the document in browsing and editing modes.
- Ctrl+C/X/V: Copies, cuts, or pastes text in text-based annotations while in editing mode.

### enableZoom

Enables using the `Ctrl(Cmd) + =/-` keyboard shortcuts to increase and decrease zoom level on the document, respectively. This is compatible with the Edit Viewers.

### enableUndoRedo

Enables using the `Ctrl(Cmd) + Z/Y` keyboard shortcuts to undo and redo changes to the document, respectively. This is compatible with the Edit Viewer.

### enableAnnotationClipboard

Enables using the `Ctrl(Cmd) + C/X/V` keyboard shortcuts to copy, cut, and paste the system clipboard to and from the document, respectively. This is compatible with the Edit Viewer.

### enableMultipleAnnotationsSelection

Enables using the `Ctrl(Cmd) + Left Click` keyboard shortcuts to select multiple annotations on the document. This is compatible with the Edit Viewer.

### enableMultiplePagesSelection

Enables using the `Ctrl(Cmd) + Left Click` or `Shift + Left Click` keyboard shortcuts to select multiple pages in the document. This is compatible with both Browse and Edit Viewers.

### enableMoveAnnotation

Enables using arrow keys to move selected annotations on the document. This is compatible with the Edit Viewers.

### enableDeleteAnnotation

Enables using the `Backspace/Delete` keys to delete annotations on the document. This is compatible with the Edit Viewer.

### enablePageNavigation

Enables document navigation with the following keys (compatible with the Browse and Edit Viewers):
- `ArrowLeft`
- `ArrowRight`
- `ArrowUp`
- `ArrowDown`
- `PageUp`
- `PageDown`
- `Home`
- `End`