---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Upgrade Guide Dynamsoft Document Viewer Documentation 
keywords: Documentation, Dynamsoft Document Viewer, Upgrade
breadcrumbText: Upgrade Guide
description: Upgrade guide for Dynamsoft Document Viewer
---

# Upgrade Guide

Upgrading Dynamsoft Document Viewer from an old version to the latest version (v3.x as of now) is straightforward. You need to pay attention to the following changes:

* Changes of APIs
* Changes of [`UIConfig`](/api/interface/uiconfig.md)


There are some code snippets that are frequently used and we will talk about the changes you have to make.

## Initialization of Edit Viewer

In v2.x, you can use an additional options parameter to enable the annotation icon in the default UI.

```js
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "container",
    uiConfig: Dynamsoft.DDV.getDefaultUiConfig("editViewer", {includeAnnotationSet: true}),
});
```

In v3.x, the option is removed and the annotation icon is included in the default UI. So you can just initialize it with the following code:

```js
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "container"
});
```

## Default UI Config

The default UI elements may be different across different versions. Check out [this post](/ui/default_ui.md) to learn about the default configs.

You can try to unify the UI across versions by specifying the [`UIConfig`](/api/interface/uiconfig.md). But pay attention to supported [elements](/ui/default_elements.md) of different versions.

## Getting the Page Data

Before v3.x, [`getPageData()`](/api/interface/idocument/index.md#getpagedata) returns a promise object, which was time consuming as it required getting all the image blobs. In v3.x, it directly returns an [`IPageData`](/api/interface/ipagedata.md) object and you can retrieve image blobs with its functions.
