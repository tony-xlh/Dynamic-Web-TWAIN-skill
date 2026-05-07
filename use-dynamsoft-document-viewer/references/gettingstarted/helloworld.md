---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Getting Started - Creating HelloWorld
keywords: Documentation, Dynamsoft Document Viewer, Getting Started, Creating HelloWorld
breadcrumbText: Creating HelloWorld
description: Dynamsoft Document Viewer Documentation Getting Started, Creating HelloWorld
permalink: /gettingstarted/helloworld.html
---

# Creating HelloWorld

In this section, we’ll break down and show all the steps needed to build the HelloWorld.

### Mobile View Mockup

![Hello World for Mobile](/assets/imgs/edit-viewer-mobile-3.0.jpg)

### Desktop View Mockup

![Hello World for Desktop](/assets/imgs/edit-viewer-3.0.jpg)

We’ll build on this skeleton page:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DDV - HelloWorld</title>
</head>
<body>
</body>
<script type="module">
// Write your code here
</script>
</html>
```

## Adding the dependency

Please refer to [Adding the dependency]({{ site.gettingstarted }}add_dependency.html).

## Define necessary HTML elements

For HelloWorld, we define below elements.

- Container to hold the viewer

```html
<div id="container"></div>
```

- Container's style

```html
<style>
    html,body {
        width: 100%;
        height: 100%;
        margin:0;
        padding:0;
        overscroll-behavior-y: none;
        overflow: hidden;
    }

    #container {
        width: 100%;
        height: 100%;
    }
</style>
```

## SDK initialization

```javascript
// Public trial license which is valid for 24 hours
// You can request a 30-day trial key from https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";
Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";
// Preload DDV Resource
Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

## Create an edit viewer

```javascript
// Create an edit viewer
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "container",
    uiConfig: Dynamsoft.DDV.getDefaultUiConfig("editViewer"),
});
```

## Review the complete code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DDV - HelloWorld</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.css">
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/ddv.js"></script>
</head>
<style>
    html,body {
        width: 100%;
        height: 100%;
        margin:0;
        padding:0;
        overscroll-behavior-y: none;
        overflow: hidden;
    }

    #container {
        width: 100%;
        height: 100%;
    }
</style>
<body>
    <div id="container"></div>
</body>
<script type="module">
    (async () => {
        // Public trial license which is valid for 24 hours
        // You can request a 30-day trial key from https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv
        Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";
        Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";
        // Preload DDV Resource
        Dynamsoft.DDV.Core.loadWasm();
        await Dynamsoft.DDV.Core.init();
        const editViewer = new Dynamsoft.DDV.EditViewer({
            container: "container",
            uiConfig: Dynamsoft.DDV.getDefaultUiConfig("editViewer"),
        });
    })();
</script>
</html>
```
