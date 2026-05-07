---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Other Viewers
keywords: Documentation, Dynamsoft Document Viewer, Features, Other Viewers
breadcrumbText: Other Viewers
description: Dynamsoft Document Viewer Documentation Features, Other Viewers
permalink: /features/viewers/others.html
---

# Other Viewers

## Browse Viewer

Browse Viewer is used to display pages in multiple-mode, pages can be multiple selected in this viewer. 

- [Default user interface]({{ site.ui }}default_ui.html#browse-viewer)
- [Default viewer configuration]({{ site.viewer }}viewerconfig.html#browse-viewer)

```typescript
const browseViewer = new Dynamsoft.DDV.BrowseViewer({
    container: document.getElementById("viewer"),
});

browseViewer.openDocument("docUid"); // Open a document which has pages
```

### Select page(s) via programming

- Select the second and third pages by using [`selectPages()`]({{ site.api }}class/browseviewer.html#selectpages).

    ```typescript
    browseViewer.selectPages([1,2]);
    ```

- Select all pages by using [`selectAllPages()`]({{ site.api }}class/browseviewer.html#selectallpages).

    ```typescript
    browseViewer.selectAllPages();
    ```

### Multiple select via UI

To enable multiple select mode, you need to set [`multiselectMode`]({{ site.api }}class/browseviewer.html#multiselectmode) to `true`. 

In this case, you can select multiple pages by clicking on them in the viewer without the need to additionally press the Ctrl key.

```typescript
browseViewer.multiselectMode = true;
```

## Custom Viewer

Custom Viewer does not have any built-in UI or functionality, it is used for creating your own viewer.

```typescript
const customViewer = new Dynamsoft.DDV.CustomViewer({
    container: document.getElementById("viewer"),
});
```