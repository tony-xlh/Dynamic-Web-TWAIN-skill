---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer User Interface - Customize UI Dynamically
keywords: Documentation, Dynamsoft Document Viewer, User Interface, Customize Dynamically
breadcrumbText: Update UI Dynamically
description: Dynamsoft Document Viewer Documentation User Interface How to Customize UI dynamically 
permalink: /ui/customize/dynamically.html
---


# Update UI dynamically after creating the viewer

Sometimes, dynamically changing the layout is required, such as hiding specified elements or modifying the available status of elements under certain conditions. `getUiConfig()` and `updateUiConfig()` can help to achieve these requirements.

## Use case

Hide the header dynamically.

- Step one: Get current `UiConfig` by using method `getUiConfig()`.
    ```typescript
    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
    });
    const uiConfig = editViewer.getUiConfig();
    ```
- Step two: Remove the header from current `UiConfig`.
    ```typescript
    uiConfig.children.splice(0,1);
    ```
- Step three: Update the revised UiConfig by using method `updateUiConfig()`.
    ```typescript
    editViewer.updateUiConfig(uiConfig);
    ``` 

![Update UI dynamically](/assets/imgs/uidynamically.png)

## Related API

- [`getDefaultUiConfig()`]({{ site.api }}namespace/ddv.html#static-getdefaultuiconfig)
- `getUiConfig()` in 
    - [EditViewer Class]({{ site.api }}class/editviewer.html#getuiconfig)
    - [CaptureViewer Class]({{ site.api }}class/captureviewer.html#getuiconfig)
    - [PerspectiveViewer Class]({{ site.api }}class/perspectiveviewer.html#getuiconfig)
    - [BrowseViewer Class]({{ site.api }}class/browseviewer.html#getuiconfig)
    - [CustomViewer Class]({{ site.api }}class/customviewer.html#getuiconfig)
- `updateUiConfig()` in
    - [EditViewer Class]({{ site.api }}class/editviewer.html#updateuiconfig)
    - [CaptureViewer Class]({{ site.api }}class/captureviewer.html#updateuiconfig)
    - [PerspectiveViewer Class]({{ site.api }}class/perspectiveviewer.html#updateuiconfig)
    - [BrowseViewer Class]({{ site.api }}class/browseviewer.html#updateuiconfig)
    - [CustomViewer Class]({{ site.api }}class/customviewer.html#updateuiconfig)