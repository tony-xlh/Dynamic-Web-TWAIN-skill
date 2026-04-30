---
name: use-dynamic-web-twain
description: Integrate Dynamic Web TWAIN document scanning into web apps. Scan, upload, and process images from scanners/cameras in vanilla JS or React.
version: 1.0.0
license: MIT
---

## What is Dynamic Web TWAIN?

Dynamic Web TWAIN (DWT) is a cross-platform document scanning SDK that runs in the browser. It connects to scanners (TWAIN/SANE/ICA/WIA/eSCL), cameras, and other image capture devices, then lets you process, edit, and upload the scanned images — all from client-side JavaScript.

> **Official documentation:** [Dynamic Web TWAIN Docs](https://www.dynamsoft.com/web-twain/docs/)

## When to Use Dynamic Web TWAIN

Use DWT when you need:

- **Document scanning** — Capture documents from physical scanners or device cameras
- **Image processing** — Convert to binary/bw, rotate, flip, crop, or deskew
- **Batch scanning** — Scan multiple pages into a buffer, reorder, then save as PDF/TIFF/PNG
- **PDF processing** — View PDFs in the browser, modify its pages and scan documents into PDF
- **Browser-based scanner control** — Select scanner source, set resolution, color mode, paper size
- **File upload from scanners** — Stream scanned images directly to a server via HTTP/FTP
- **Barcode/OCR** — DWT add-ons can read barcodes and perform OCR on scanned documents

## Setup Approaches

Choose based on your project constraints:

| Approach | Best for | Network required |
| --- | --- | --- |
| CDN | Quick prototypes, demos | Yes |
| Local Resources | Intranet, offline, production | No (self-hosted) |
| npm Package | React, Vue, Angular, bundled apps | No (self-hosted) |

---

### 1. CDN (Quick Start)

Include the DWT script from CDN, configure, and load:

```html
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/dwt/dist/dynamsoft.webtwain.min.js"></script>
  </head>

  <body>
    <button onclick="AcquireImage();">Scan</button>
    <button onclick="upload();">Upload</button>
    <button onclick="binarizeImage();">Convert to BW</button>
    <button onclick="rotateCW();">Rotate Clockwise</button>
    <button onclick="rotateCCW();">Rotate Counter-Clockwise</button>
    <div id="dwtcontrolContainer"></div>

    <script>
      Dynamsoft.DWT.AutoLoad = false;
      Dynamsoft.DWT.IfCheckCssFiles = false;
      Dynamsoft.DWT.Containers = [
        { ContainerId: "dwtcontrolContainer", Width: "380px", Height: "400px" },
      ];
      Dynamsoft.DWT.ProductKey = "YOUR-PRODUCT-KEY";
      Dynamsoft.DWT.ResourcesPath =
        "https://cdn.jsdelivr.net/npm/dwt/dist";
      Dynamsoft.DWT.ServiceInstallerLocation =
        "https://unpkg.com/dwt/dist/dist/";
      Dynamsoft.DWT.Load();

      var DWTObject;

      Dynamsoft.DWT.RegisterEvent("OnWebTwainReady", function () {
        DWTObject = Dynamsoft.DWT.GetWebTwain("dwtcontrolContainer");
      });

      function AcquireImage() {
        if (DWTObject) {
          DWTObject.SelectSourceAsync()
            .then(function () {
              return DWTObject.AcquireImageAsync({
                IfCloseSourceAfterAcquire: true,
                IfShowUI: false,
                PixelType: Dynamsoft.DWT.EnumDWT_PixelType.TWPT_GRAY,
                Resolution: 150,
              });
            })
            .catch(function (exp) {
              alert(exp.message);
            });
        }
      }

      function upload() {
        if (DWTObject && DWTObject.HowManyImagesInBuffer > 0) {
          var strUrl = "https://demo.dynamsoft.com/sample-uploads/";
          var imgAry = [DWTObject.CurrentImageIndexInBuffer];
          DWTObject.HTTPUpload(
            strUrl,
            imgAry,
            Dynamsoft.DWT.EnumDWT_ImageType.IT_PNG,
            Dynamsoft.DWT.EnumDWT_UploadDataFormat.Binary,
            "WebTWAINImage.png",
            function () {
              alert("Upload successful");
            },
            function (errorCode, errorString, sHttpResponse) {
              alert(sHttpResponse.length > 0 ? sHttpResponse : errorString);
            }
          );
        } else {
          alert("There is no image in buffer.");
        }
      }

      function binarizeImage() {
        DWTObject.ConvertToBW(DWTObject.CurrentImageIndexInBuffer);
      }

      function rotateCW() {
        DWTObject.RotateRight(DWTObject.CurrentImageIndexInBuffer);
      }

      function rotateCCW() {
        DWTObject.RotateLeft(DWTObject.CurrentImageIndexInBuffer);
      }
    </script>
  </body>
</html>
```

> **Note:** When using CDN, `ResourcesPath` must point to a proper CDN location (it can be where the main script is hosted), otherwise DWT's internal resource loader will fail.

---

### 2. Local Resources (Offline / Intranet)

Download the DWT resource package and host it alongside your app. This is the recommended approach for production deployments where you don't want CDN dependencies.

**Step 1:** Copy the `Resources/` directory from the DWT installation into your project.

**Step 2:** Reference the local scripts and set `ResourcesPath` to the local directory:

```html
<html>
  <head>
    <script src="Resources/dynamsoft.webtwain.initiate.js"></script>
    <script src="Resources/dynamsoft.webtwain.config.js"></script>
  </head>

  <body>
    <button onclick="AcquireImage();">Scan</button>
    <button onclick="upload();">Upload</button>
    <button onclick="binarizeImage();">Convert to BW</button>
    <button onclick="rotateCW();">Rotate Clockwise</button>
    <button onclick="rotateCCW();">Rotate Counter-Clockwise</button>
    <div id="dwtcontrolContainer"></div>

    <script>
      var DWTObject;

      if (!window.Dynamsoft) {
        alert(
          "Dynamic Web TWAIN is not loaded. Check that resources are in place."
        );
      }

      Dynamsoft.DWT.RegisterEvent("OnWebTwainReady", function () {
        DWTObject = Dynamsoft.DWT.GetWebTwain("dwtcontrolContainer");
      });

      function AcquireImage() {
        if (DWTObject) {
          DWTObject.SelectSourceAsync()
            .then(function () {
              return DWTObject.AcquireImageAsync({
                IfCloseSourceAfterAcquire: true,
                IfShowUI: false,
                PixelType: Dynamsoft.DWT.EnumDWT_PixelType.TWPT_GRAY,
                Resolution: 150,
              });
            })
            .catch(function (exp) {
              alert(exp.message);
            });
        }
      }

      // upload(), binarizeImage(), rotateCW(), rotateCCW() — identical to CDN example above
    </script>
  </body>
</html>
```

> When using local resources, the configuration (`ProductKey`, `ResourcesPath`, `Containers`) is set inside `dynamsoft.webtwain.config.js`. You don't set them again in your page script.

---

### 3. React (npm Package)

Install the npm package and use DWT inside a React component:

```bash
npm install dwt ncp
```

Add a script to copy DWT static resources from `node_modules` to your public folder:

```json
{
  "scripts": {
    "copy-resources": "ncp node_modules/dwt/dist public/dwt-resources",
    "dev": "npm run copy-resources && vite",
    "build": "npm run copy-resources && vite build"
  }
}
```

```tsx
// src/DWT.tsx
import React, { useEffect, useRef } from "react";
import Dynamsoft from "dwt";

function DWT() {
  const containerId = "dwtcontrolContainer";
  const dwtObject = useRef<any>(null);

  useEffect(() => {
    Dynamsoft.DWT.RegisterEvent("OnWebTwainReady", () => {
      dwtObject.current = Dynamsoft.DWT.GetWebTwain(containerId);
    });

    Dynamsoft.DWT.ProductKey = "YOUR-PRODUCT-KEY";
    Dynamsoft.DWT.ResourcesPath = "/dwt-resources";
    Dynamsoft.DWT.Containers = [
      {
        WebTwainId: "dwtObject",
        ContainerId: containerId,
        Width: "300px",
        Height: "400px",
      },
    ];

    Dynamsoft.DWT.Load();

    return () => {
      if (dwtObject.current) {
        dwtObject.current.Unload();
      }
    };
  }, []);

  const acquireImage = () => {
    if (dwtObject.current) {
      dwtObject.current
        .SelectSourceAsync()
        .then(() =>
          dwtObject.current.AcquireImageAsync({
            IfCloseSourceAfterAcquire: true,
          })
        )
        .catch((error: any) => {
          console.error(error.message);
        });
    }
  };

  return (
    <>
      <button onClick={acquireImage}>Scan</button>
      <div id={containerId}></div>
    </>
  );
}

export default DWT;
```

```tsx
// App.tsx
import DWT from "./DWT";

function App() {
  return <DWT />;
}

export default App;
```

> **Note:** When using the npm package, clear any default styles in `src/App.css` and `src/index.css` to avoid layout conflicts with the DWT viewer.

## DWT Configuration Reference

These properties must be set **before** calling `Dynamsoft.DWT.Load()`:

| Property | Required | Description |
| --- | --- | --- |
| `ProductKey` | Yes | Trial or full license key from Dynamsoft |
| `ResourcesPath` | Yes | Path to DWT static resources (.js, .css, .wasm files) |
| `Containers` | Yes | Array of container configs: `{ WebTwainId?, ContainerId, Width, Height }` |
| `AutoLoad` | No | Set to `false` for manual loading (recommended in frameworks) |
| `ServiceInstallerLocation` | No | URL for the Dynamsoft Service installer download |
| `IfCheckCssFiles` | No | Set to `false` when resources are bundled locally to skip CSS verification |

### Container Configuration

```js
Dynamsoft.DWT.Containers = [
  {
    WebTwainId: "dwtObject",    // Optional — id to reference this instance
    ContainerId: "dwtContainer", // Required — id of the div element
    Width: "100%",               // Required
    Height: "500px",             // Required
  },
];
```

- `ContainerId` must match the `id` of the `<div>` that will host the viewer
- `WebTwainId` is optional but useful when you have multiple DWT instances
- Width/Height define the viewer dimensions

## Common Operations

### Image Acquisition

DWT provides two modes: silent (custom settings) and interactive (scanner's native UI):

```js
// Mode 1: Silent scan with full control
async function acquireImage() {
  if (!DWTObject) return;
  try {
    await DWTObject.SelectSourceAsync();
    await DWTObject.AcquireImageAsync({
      IfCloseSourceAfterAcquire: true,
      IfShowUI: false,
      PixelType: Dynamsoft.DWT.EnumDWT_PixelType.TWPT_GRAY, // BW: 0, Gray: 1, RGB: 2
      Resolution: 200,
      IfDuplexEnabled: true,
      IfFeederEnabled: true,
    });
  } catch (exp) {
    alert(exp.message);
  }
}

// Mode 2: Let scanner's native dialog handle settings
async function acquireImageWithUI() {
  if (!DWTObject) return;
  try {
    await DWTObject.SelectSourceAsync();
    await DWTObject.AcquireImageAsync({
      IfCloseSourceAfterAcquire: true,
      IfShowUI: true,
    });
  } catch (exp) {
    alert(exp.message);
  }
}
```

Key `AcquireImageAsync` options:

| Option | Type | Description |
| --- | --- | --- |
| `IfShowUI` | bool | Show the scanner's native settings dialog |
| `IfCloseSourceAfterAcquire` | bool | Close scanner connection after scan completes |
| `PixelType` | enum | Color mode: BW (0), Gray (1), RGB (2) |
| `Resolution` | number | DPI (typical: 150–300) |
| `IfDuplexEnabled` | bool | Scan both sides of the page |
| `IfFeederEnabled` | bool | Use document feeder if available |

### Image Processing

```js
function binarizeImage() {
  DWTObject.ConvertToBW(DWTObject.CurrentImageIndexInBuffer);
}

function rotateClockwise() {
  DWTObject.RotateRight(DWTObject.CurrentImageIndexInBuffer);
}

function rotateCounterClockwise() {
  DWTObject.RotateLeft(DWTObject.CurrentImageIndexInBuffer);
}

function mirrorImage() {
  DWTObject.Mirror(DWTObject.CurrentImageIndexInBuffer);
}

function flipImage() {
  DWTObject.Flip(DWTObject.CurrentImageIndexInBuffer);
}

function cropImage(left, top, right, bottom) {
  DWTObject.Crop(DWTObject.CurrentImageIndexInBuffer, left, top, right, bottom);
}

function deskew(index) {
  DWTObject.GetSkewAngle(
    index,
    function(angle) {
      console.log("skew angle: " + angle);
      DWTObject.Rotate(index, angle, true,
        function() {
          console.log("Successfully deskewed an image!");
        },
        function(errorCode, errorString) {
          console.log(errorString);
        }
      );
    },
    function(errorCode, errorString) {
      console.log(errorString);
    }
  );
}
```

### TWAIN Capabilities

You can also use TWAIN capabilities directly for more advanced control. For example, enable barcode detection during scanning and read the results in the `OnPostTransferAsync` event with the following code:

```js
var DWTObject;
Dynamsoft.DWT.RegisterEvent("OnWebTwainReady", function () {
  DWTObject = Dynamsoft.DWT.GetWebTwain('dwtcontrolContainer'); // Get the Dynamic Web TWAIN object that is embeded in the div with id 'dwtcontrolContainer'
  DWTObject.RegisterEvent("OnPostTransferAsync", function (outputInfo) {
    console.log(outputInfo);
    var dwtBarcode = document.getElementById("DWTBarcode");
    if (outputInfo && outputInfo.extendedImageInfo && outputInfo.extendedImageInfo.barcode && outputInfo.extendedImageInfo.barcode.length > 0) {
      console.log(outputInfo.extendedImageInfo.barcode[0]);
    }
  });
});

function AcquireImage() {
  if (DWTObject) {
    DWTObject.SelectSourceAsync().then(function () {
      DWTObject.setCapabilities({
        exception: "fail", capabilities: [{
          capability: Dynamsoft.DWT.EnumDWT_Cap.ICAP_BARCODEDETECTIONENABLED,
          curValue: true
        }]
      }, function (c) {
        return DWTObject.AcquireImageAsync({
          IfShowUI: false,
          IfCloseSourceAfterAcquire: true, // Scanner source will be closed automatically after the scan.
          IfGetExtImageInfo: true,
          extendedImageInfoQueryLevel: 0
        });
      }, function (errorData) {
        if (errorData.capabilities && errorData.capabilities.length > 0)
          if (errorData.capabilities[0].errorString)
            alert(errorData.capabilities[0].errorString);
        DWTObject.CloseSourceAsync();
      });
    }).catch(function (exp) {
      alert(exp.message);
      DWTObject.CloseSourceAsync();
    });
  }
}
```

### Upload

```js
// Upload current image as PNG
function uploadCurrentAsPNG() {
  if (!DWTObject || DWTObject.HowManyImagesInBuffer === 0) return;

  DWTObject.HTTPUpload(
    "https://your-api.com/upload",
    [DWTObject.CurrentImageIndexInBuffer],
    Dynamsoft.DWT.EnumDWT_ImageType.IT_PNG, // JPG: 1, PNG: 2, TIF: 3, PDF: 4
    Dynamsoft.DWT.EnumDWT_UploadDataFormat.Binary, // Binary: 1, Base64: 2
    "ScannedDocument.png",
    function () {
      alert("Upload successful");
    },
    function (errorCode, errorString, sHttpResponse) {
      alert(sHttpResponse.length > 0 ? sHttpResponse : errorString);
    }
  );
}

// Upload all images as PDF
function uploadAllAsPDF() {
  if (!DWTObject || DWTObject.HowManyImagesInBuffer === 0) return;

  var indices = [];
  for (var i = 0; i < DWTObject.HowManyImagesInBuffer; i++) {
    indices.push(i);
  }

  DWTObject.HTTPUpload(
    "https://your-api.com/upload",
    indices,
    Dynamsoft.DWT.EnumDWT_ImageType.IT_PDF,
    Dynamsoft.DWT.EnumDWT_UploadDataFormat.Binary,
    "document.pdf",
    function () {
      alert("Upload successful");
    },
    function (errorCode, errorString, sHttpResponse) {
      alert(sHttpResponse.length > 0 ? sHttpResponse : errorString);
    }
  );
}

// Get image as base64 (for custom upload logic)
function getImageAsBase64(indices) {
  DWTObject.ConvertToBase64(
    indices,
    Dynamsoft.DWT.EnumDWT_ImageType.IT_PDF,
    function (result, indices, type) {
      console.log(result.getData(0, result.getLength()));
    },
    function (errorCode, errorString) {
      console.log(errorString);
    },
  );
}
```

### Input

```js
// Load image from file
function loadImageFromDisk() {
  DWTObject.IfShowFileDialog = true; //"Open File" dialog will be opened.
  DWTObject.LoadImageEx(
    "", //file name can be empty if "Open File" dialog is called.
    Dynamsoft.DWT.EnumDWT_ImageType.IT_JPG,
    function () {
      console.log("success");
    },
    function (errorCode, errorString) {
      console.log(errorString);
    },
  );
}

// Load image from binary (Blob | ArrayBuffer)
function loadImageFromBinary(imageData){
  DWTObject.LoadImageFromBinary(
    imageData,
    function () {
      console.log("success");
    },
    function (errorCode, errorString) {
      console.log(errorString);
    },
  );
}
```

### Buffer Management

```js
// Navigate through scanned images
DWTObject.CurrentImageIndexInBuffer = 2; // Switch to 3rd image (0-based)

// Remove current image
DWTObject.RemoveImage(DWTObject.CurrentImageIndexInBuffer);

// Remove selected images
DWTObject.RemoveImages([0, 2, 4]);

// Clear all images
DWTObject.RemoveAllImages();

// Get total pages in buffer
var count = DWTObject.HowManyImagesInBuffer;

// Reorder images
DWTObject.SwitchImage(0, 3); // Swap image at index 0 with index 3
```

### Saving Locally

```js
// Save current image as file
function saveCurrentImage() {
  DWTObject.SaveAsPNG(DWTObject.CurrentImageIndexInBuffer, "scanned.png");
}

function saveAllAsPDF() {
  DWTObject.SaveAsPDF("all-pages.pdf");
}

function saveAllAsTIFF() {
  DWTObject.SaveAllAsMultiPageTIFF("all-pages.tiff");
}
```

## DWT Events

Register events to react to scanner state changes:

```js
// Fires once when DWT is fully initialized
Dynamsoft.DWT.RegisterEvent("OnWebTwainReady", function () {
  DWTObject = Dynamsoft.DWT.GetWebTwain("dwtcontrolContainer");
});

// Fires when images in the buffer change
// Operation type:
// 1: new image(s) added at the tail
// 2: image(s) inserted before the current index
// 3: image(s) deleted
// 4: image(s) modified
Dynamsoft.DWT.RegisterEvent("OnBitmapChanged", function (updatedIndices, operationType, currentIndex) {
    console.log(updatedIndices);
});

// Fires after each page is scanned and transferred to the buffer
Dynamsoft.DWT.RegisterEvent("OnPostTransferAsync", function (outputInfo) {
  console.log("Page scanned, index:", outputInfo);
});
```

## Enum Reference

When using the CDN approach, you have access to the full `Dynamsoft.DWT.EnumDWT_*` namespace. When using the npm package or a bundler, these may not be available — use numeric values directly or define your own constants:

### PixelType

| Constant | Value | Description |
| --- | --- | --- |
| `EnumDWT_PixelType.TWPT_BW` | 0 | Black and white |
| `EnumDWT_PixelType.TWPT_GRAY` | 1 | Grayscale |
| `EnumDWT_PixelType.TWPT_RGB` | 2 | Full color |

### ImageType (output format)

| Constant | Value | Extension |
| --- | --- | --- |
| `EnumDWT_ImageType.IT_JPG` | 1 | .jpg |
| `EnumDWT_ImageType.IT_PNG` | 2 | .png |
| `EnumDWT_ImageType.IT_TIF` | 3 | .tif |
| `EnumDWT_ImageType.IT_PDF` | 4 | .pdf |

### UploadDataFormat

| Constant | Value | Description |
| --- | --- | --- |
| `EnumDWT_UploadDataFormat.Binary` | 1 | Raw binary data |
| `EnumDWT_UploadDataFormat.Base64` | 2 | Base64-encoded string |


## Dynamic Web TWAIN Service

DWT requires the **Dynamic Web TWAIN Service** (previously Dynamsoft Service) to be installed on the client machine for desktop scanning. The service:

- Communicates between the browser and scanner drivers (TWAIN/ICA/SANE/WIA/eSCL)
- Is bundled as a lightweight installer (Windows `.msi`, macOS `.pkg`, Linux `.deb`/`.rpm`)
- Must be running for scanner access to work

If the service is not installed, DWT will prompt the user to download it. Set `ServiceInstallerLocation` to control where the installer is fetched from:

```js
Dynamsoft.DWT.ServiceInstallerLocation =
  "https://unpkg.com/dwt/dist/dist/";
```

Without this URL, users will be directed to according to `ResourcesPath`.

## Platform Support

| OS | Browser | Scanner Protocols |
| --- | --- | --- |
| Windows | Chrome, Edge, Firefox | TWAIN, WIA, eSCL |
| macOS | Chrome, Safari, Firefox | ICA, TWAIN, eSCL |
| Linux | Chrome, Firefox | SANE |

