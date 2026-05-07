---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Getting Started - SDK Initialization
keywords: Documentation, Dynamsoft Document Viewer, Getting Started, SDK Initialization
breadcrumbText: SDK Initialization
description: Dynamsoft Document Viewer Documentation Getting Started, SDK Initialization
permalink: /gettingstarted/sdk_init.html
---

# SDK Initialization

## License

### Get a trial key

- A free public trial license is available for every new device for first use of Dynamsoft Document Viewer. The public trial license is the default key used in samples. You can also find the public trial license on the following parts of this page.
- If your free key is expired, please visit <a href="https://www.dynamsoft.com/customer/license/trialLicense?product=ddv&source=docs" target="_blank">Private Trial License Page</a> to get a 30-day trial extension.

### Get a full license

- [Contact us](https://www.dynamsoft.com/company/contact/)  to purchase a full license

## Initializiation

The following code snippets are using the public trial license to initialize the license. You can replace the public trial license with your own license key.

<div class="multi-panel-switching-prefix"></div>

- [Use a CDN](#-)
- [Host the SDK yourself](#--)

<div class="multi-panel-start"></div>

<div style="height: 20px;"></div>
 

```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"; // Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";// Lead to a folder containing the distributed WASM files
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

<div style="height: 20px;"></div>
  

```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"; // Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "./node_modules/dynamsoft-document-viewer/dist/engine";// Lead to a folder containing the distributed WASM files
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div>

### deviceFriendlyName

A human-readable name for the device which corresponds to its UUID is able to set during initialization. This name will appear in the device details table when you check the statistics of the according license.


<div class="multi-panel-switching-prefix"></div>

- [Use a CDN](#---)
- [Host the SDK yourself](#----)

<div class="multi-panel-start"></div>

<div style="height: 20px;"></div>

   

```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";// Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine"; // Lead to a folder containing the distributed WASM files
Dynamsoft.DDV.Core.deviceFriendlyName = "Dynamsoft-iPhone"; // A string representing the device which is easier to recognize than its UUID
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

<div style="height: 20px;"></div>
    

```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";// Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "./node_modules/dynamsoft-document-viewer/dist/engine"; // Lead to a folder containing the distributed WASM files
Dynamsoft.DDV.Core.deviceFriendlyName = "Dynamsoft-iPhone"; // A string representing the device which is easier to recognize than its UUID
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div>


{% comment %}


```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9"; // Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine";// Lead to a folder containing the distributed WASM files
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

### deviceFriendlyName

A human-readable name for the device which corresponds to its UUID is able to set during initialization. This name will appear in the device details table when you check the statistics of the according license.

```javascript
Dynamsoft.DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";// Public trial license which is valid for 24 hours
Dynamsoft.DDV.Core.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-document-viewer@latest/dist/engine"; // Lead to a folder containing the distributed WASM files
Dynamsoft.DDV.Core.deviceFriendlyName = "Dynamsoft-iPhone"; // A string representing the device which is easier to recognize than its UUID
await Dynamsoft.DDV.Core.loadWasm();
await Dynamsoft.DDV.Core.init(); 
```

{% endcomment %}
