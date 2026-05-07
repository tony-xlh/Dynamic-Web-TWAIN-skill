---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - CaptureViewer Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, CaptureViewer Class
breadcrumbText: CaptureViewer Class
description: Dynamsoft Document Viewer Documentation API Reference CaptureViewer Class Page
permalink: /api/class/captureviewer.html
---

# CaptureViewer Class

Capture Viewer is used to control camera, play video stream, and capture the images from camera.

## API Index

**Create and Destroy Instances** 

| API Name       | Description                                   |
| ------------ | --------------------------------------------- |
| [`CaptureViewer()`](#captureviewer) | Default constructor of a `CaptureViewer` instance. |
| [`destroy()`](#destroy)             | Destroy the `CaptureViewer` instance.                             |

**Viewer Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`bindContainer()`](#bindcontainer)     | Bind the viewer to the specified container.                  |
| [`unbindContainer()`](#unbindcontainer) | Unbind the viewer from the specified container.              |
| [`isBoundContainer`](#isboundcontainer) | Return whether the viewer is bound to a container. |
| [`getStyle()`](#getstyle)            | Get the style object of `CaptureViewer`.                        |
| [`updateStyle()`](#updatestyle)        | Update the style object of `CaptureViewer`.                     |
| [`getUiConfig()`](#getuiconfig)         | Get current `UiConfig` object.                               |
| [`updateUiConfig()`](#updateuiconfig)     | Update `UiConfig` object.                                    |
| [`show()`](#show)                | Show the viewer.                                             |
| [`hide()`](#hide)                | Hide the viewer.                                             |
| [`isVisible`](#isvisible)        | Return whether the viewer is shown or hidden.      |

**Document Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`openDocument()`](#opendocument)        | Open the specified document by document uid.                 |
| [`closeDocument()`](#closedocument)       | Close current document.                                      |
| [`currentDocument`](#currentdocument)   | Return the object of the current document.         |

**Camera Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`play()`](#play)                 | Play the camera video stream.                                |
| [`stop()`](#stop)                 | Stop the camera video stream.                                |
| [`capture()`](#capture)              | Capture a frame from video stream.                           |
| [`getAllCameras()`](#getallcameras)        | Return information of all available cameras on the device.   |
| [`selectCamera()`](#selectcamera)         | Select a camera as the video source.                         |
| [`getCurrentCamera()`](#getcurrentcamera)     | Return information about the current camera.                 |
| [`getCurrentResolution()`](#getcurrentresolution) | Return the resolution of the current video input.            |
| [`turnOnTorch()`](#turnontorch)          | Turn on the torch/flashlight if the current camera supports it. |
| [`turnOffTorch()`](#turnofftorch)         | Turn off the torch/flashlight.                               |
| [`enableAutoCapture`](#enableautocapture)           | Specify or return whether to enable automatic capture.       |
| [`enableAutoDetect`](#enableautodetect)            | Specify or return whether to enable automatic border detection in video stream. |
| [`acceptedPolygonConfidence`](#acceptedpolygonconfidence)   | Specify or return the confidence when detecting the border.  |
| [`maxFrameNumber`](#maxframenumber)              | Specify or return the maximum number of frames detected per second. |


**Events**

| API Name | Description                                        |
| -------- | -------------------------------------------------- |
| [`on()`](#on)     | Bind a listener to the specified event.            |
| [`off()`](#off)    | Unbind event listener(s) from the specified event. |

***Integrated Events***

| Event Name    |
| ------------- |
| [`resized`](#resized)       |
| [`played`](#played)         |
| [`stopped`](#stopped)       |
| [`captured`](#captured)     |
| [`cameraChanged`](#camerachanged) |
| [`click`](#click)           |
| [`dblclick`](#dblclick)     |
| [`rightclick`](#rightclick) |
| [`visibilityChanged`](#visibilitychanged) |
| [`paginationChanged`](#paginationchanged)                   |

## Create and Destroy Instances

### CaptureViewer()

Default constructor of a `CaptureViewer` instance.

**Syntax**

```typescript
new Dynamsoft.DDV.CaptureViewer(options?: CaptureViewerConstructorOptions);
```

**Parameters**

`options`: The constructor options for a `CaptureViewer` instance. Please refer to [`CaptureViewerConstructorOptions`]({{ site.api }}interface/captureviewerconstructoroptions.html).

**Code Snippet**

```typescript
const captureViewer = new Dynamsoft.DDV.CaptureViewer({
    container: document.getElementById("viewer"),
});
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                                     
 -80001 | License string is invalid.                              
 -80002 | *XXX(LicenseModuleName)* module license has expired.                                                           
 -80003 | *XXX(LicenseModuleName)* module license is missing.                         
 -80004 | *XXX(LicenseModuleName)* module license version does not match.                                 
 -80005 | Domain does not match the domain bound to the *XXX(LicenseModuleName)* module license.  
 -80050 | DDV.Core.init() has not been set up yet.   
 -80051 | DDV.Core.init() has not been completed.   

**Warning**

 Error Code | Error Message                                                 
 ---------- | ------------------------------------------------------------ 
 -80315     | DocumentDetect needs to be configured by Dynamsoft.DDV.setProcessingHandler to enable the document detection feature. 

### destroy()

Destroy the `CaptureViewer` instance.

**Syntax**

```typescript
destroy(): void;
```

**Code Snippet**

```typescript
captureViewer.destroy();
```

## Viewer Control

### bindContainer()

Bind the viewer to the specified container.

**Syntax**

```typescript
bindContainer(container: string | HTMLElement): void;
```

**Parameters**

`container`: The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

**Code Snippet**

```typescript
// Assume there is a container with id "viewercontainer" on the page.
captureViewer.bindContainer("viewercontainer");
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80301 | The specified container does not exist. 

**Remark**

- A viewer can only be bound to one container at once. If you bind the viewer to another container when it has been bound to a container, the viewer will be bound to the new container and unbound from the old container automatically. 

### unbindContainer()

Unbind the viewer from the specified container.

**Syntax**

```typescript
unbindContainer(): void;
```

**Code Snippet**

```typescript
captureViewer.unbindContainer();
```

### isBoundContainer

Return whether the viewer is bound to a container.

**Syntax**

```typescript
readonly isBoundContainer: boolean;
```

### getStyle()

Get the style object of `CaptureViewer`.

**Syntax**

```typescript
getStyle(captureViewerStyleName: CaptureViewerStyleName): CaptureViewerStyle | null;
```

**Parameters**

`captureViewerStyleName`: A `CaptureViewerStyleName` can be one of two types.

```typescript
type CaptureViewerStyleName = "canvasStyle" | "quadSelectionStyle";
```

**Return values**

The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Code Snippet**

```typescript
// Get canvasStyle object;
const canvasStyle = captureViewer.getStyle("canvasStyle");
```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `null`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `null`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `null`

### updateStyle()

Update the style object of `CaptureViewer`.

**Syntax**

```typescript
updateStyle(captureViewerStyleName: CaptureViewerStyleName, captureViewerStyle: CaptureViewerStyle): boolean;
```

**Parameters**

`captureViewerStyleName`: A `CaptureViewerStyleName` can be one of two types.

```typescript
type CaptureViewerStyleName = "canvasStyle" | "quadSelectionStyle";
```

`captureViewerStyle`: The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html)..

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

- First method

    ```typescript
    // Get style object;
    const canvasStyle = captureViewer.getStyle("canvasStyle");

    // Modify the style object.
    canvasStyle.background = "red";
    canvasStyle.border = "1px solid green";

    // Update canvas style;
    captureViewer.updateStyle("canvasStyle", canvasStyle);
    ```

- Second method

    ```typescript
    // Update the style object directly
    captureViewer.updateStyle("canvasStyle", {
        background: "red",
        border: "1px solid green",
    });
    ```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `false`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `false`


**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### getUiConfig()

Get current `UiConfig` object.

**Syntax**

```typescript
getUiConfig(): UiConfig;
```

**Return Value**

The [`UiConfig`]({{ site.api }}interface/uiconfig.html) object.

**Code Snippet**

```typescript
const viewerUi = captureViewer.getUiConfig();
```

### updateUiConfig()

Update `UiConfig` object.

**Syntax**

```typescript
updateUiConfig(uiConfig: UiConfig): boolean;
```

**Parameters**

`uiConfig`: The [`UiConfig`]({{ site.api }}interface/uiconfig.html) to update.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
const viewerUi = Dynamsoft.DDV.getDefaultUiConfig("captureViewer");
const header = viewerUi.children[0];
header.children.splice(0,1); //Remove Resolution element
captureViewer.updateUiConfig(viewerUi);
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`
 -80313 | The element *XXX(ElementName)* is not supported in *XXX(ClassName)* class.      | `false`

**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### show()

Show the viewer.

**Syntax**

```typescript
show(): void;
```

**Code Snippet**

```typescript
captureViewer.show();
```

**Remark**

- The viewer is shown automatically when it is created.

### hide()

Hide the viewer.

**Syntax**

```typescript
hide(): void;
```

**Code Snippet**

```typescript
captureViewer.hide();
```

### isVisible

Return whether the viewer is shown or hidden.

**Syntax**

```typescript
readonly isVisible: boolean;
```

**Remark**

- The viewer is shown automatically when it is created which means the default value of `isVisible` is `true`.

## Document Control

### openDocument()

Open the specified document.

**Syntax**

```typescript
openDocument(docUid: string | doc: IDocument): void;
```

**Parameters**

`docUid`: The uid of the specified document. 

`doc`: The object of the document to open. Please refer to [IDocument]({{ site.api }}interface/idocument/index.html).

**Code Snippet**

```typescript
// Assume there is a document whose id is "lnn0ll9o124".
captureViewer.openDocument("lnn0ll9o124");

// OR
// Assume there is a document object firstDoc.
const docUid = firstDoc.uid;
captureViewer.openDocument(docUid);
captureViewer.openDocument(firstDoc);
```

**Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: docUid or doc is invalid.   
 -80102 | *XXX(API)*: docUid or doc is missing.   
 -80104 | *XXX(API)*: The specified document(s) do not exist.  

**Remark**

- If another ducument is opened when there is a document already opened, the opened document will be closed automatically.
- If there are already pages in the opened document, the number of existing pages and the preview image of the last page will appear in the elements `Dynamsoft.DDV.Elements.ImagePreview`.

### closeDocument()

Close current document.

**Syntax**

```typescript
closeDocument(): boolean; 
```

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

```typescript
captureViewer.closeDocument();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `false`

### currentDocument

Return the object of the current document.

**Syntax**

```typescript
readonly currentDocument: IDocument | null;
```

**Code Snippet**

```typescript
const currentDoc = captureViewer.currentDocument;
```

**See Also**

[IDocument]({{ site.api }}interface/idocument/index.html)

## Camera Control

### play()

Play the camera video stream.

**Syntax**

```typescript
play(videoConfig?: VideoConfig): Promise<void>;
```

**Parameter**

`videoConfig`: The object [`VideoConfig`]({{ site.api }}interface/videoconfig.html) which can be used to set resolution, etc.

**Code Snippet**

```typescript
const captureViewer = new Dynamsoft.DDV.CaptureViewer({
    container: document.getElementById("viewer"),
});
await captureViewer.play({
     resolution: [1080, 720], 
     fill: true, 
});
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80401 | The specified camera is occupied.   
 -80403 | Not HTTPS, failed to play the video stream. 
 -80405 | No camera available.
 -80406 | The selected camera is denied by browser.

**Remark**

- The value of `videoConfig` will be remembered and automatically applied the next time `play()` is called, unless another `videoConfig` is specified.

### stop()

Stop the camera video stream.

**Syntax**

```typescript
stop(): void;
```

**Code Snippet**

```typescript
captureViewer.stop();
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80402 | No video stream is played.

### capture()

Capture a frame from video stream.

**Syntax**

```typescript
capture(): Promise<Blob>;
```

**Return value**

The Blob of the captured image.

**Code Snippet**

```typescript
const captureViewer = new Dynamsoft.DDV.CaptureViewer({
    container: document.getElementById("viewer"),
});
await captureViewer.play( {
     resolution: [1080, 720], 
     fill: true, 
});

const capturedPage = await captureViewer.capture();
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80402 | No video stream is played.
 -80407 | No bound container.

**Remark**

- If there is no document opened while capturing, a new document will be created and opened automatically.

### getAllCameras()

Return information of all available cameras on the device.

**Syntax**

```typescript
getAllCameras(): Promise<VideoDeviceInfo[]>;
```

**Return value**

A promise resolving to an array of [`VideoDeviceInfo`]({{ site.api }}interface/videodeviceinfo.html) objects.

**Code Snippet**

```typescript
const cameras = await captureViewer.getAllCameras();
```

### selectCamera()

Select a camera as the video source.

**Syntax**

```typescript
selectCamera(cameraObjectOrDeviceID: VideoDeviceInfo | string): Promise<PlayCallbackInfo>;
```

**Parameters**

`cameraObjectOrDeviceID`: Specify the camera by an object [`VideoDeviceInfo`]({{ site.api }}interface/videodeviceinfo.html) or the device id string.

**Return value**

A promise resolving to a [`PlayCallbackInfo`]({{ site.api }}interface/playcallbackinfo.html) object.

**Code Snippet**

```typescript
const cameras = await captureViewer.getAllCameras();
if (cameras.length) {
    await captureViewer.selectCamera(cameras[0]);
}
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.   
 -80400 | The specified camera does not exist.         
 -80401 | The specified camera is occupied.            

**Remark**

- If called before [`play()`](#play), the selected camera will be used. Otherwise, the system will decide which one to use.

### getCurrentCamera()

Return information about the current camera.

**Syntax**

```typescript
getCurrentCamera(): VideoDeviceInfo;
```

**Parameters**

None.

**Return value**

A [`VideoDeviceInfo`]({{ site.api }}interface/videodeviceinfo.html) object with details about the current camera.

**Code Snippet**

```typescript
const currentCamera = captureViewer.getCurrentCamera();
console.log("Current camera is "currentCamera.label);
```

### getCurrentResolution()

Return the resolution of the current video input.

**Syntax**

```typescript
getCurrentResolution(): [number, number]; //current resolution
```

**Parameters**

None.

**Return value**

An array of two numbers representing the resolution in the sequence of `[width, height]`.

**Code Snippet**

```typescript
const currentRes = captureViewer.getCurrentResolution();
console.log("Current resolution is " + currentRes[0] + " x " + currentRes[1]);
```

### turnOnTorch()

Turn on the torch/flashlight if the current camera supports it.

**Syntax**

```typescript
turnOnTorch(): Promise<void>; 
```

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```typescript
await captureViewer.turnOnTorch();
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80402  | No video stream is played.                  
 -80404 | The camera does not support a flashlight.

**Remark**

- This method should be called when the camera is played. 
- Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. 
- Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

### turnOffTorch()

Turn off the torch/flashlight.

**Syntax**

```typescript
turnOffTorch(): Promise<void>;
```

**Return value**

A promise that resolves when the operation succeeds.

**Code Snippet**

```typescript
await captureViewer.turnOffTorch();
```

**Promise Exception**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80402  | No video stream is played.                  
 -80404 | The camera does not support a flashlight.

**Remark**

- This method should be called when the camera is played. 
- Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. 
- Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

### enableAutoCapture

Specify or return whether to enable automatic capture. 

**Syntax**

```typescript
enableAutoCapture: boolean; 
```

**Code Snippet**

```typescript
captureViewer.enableAutoCapture = true;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   

**Remark** 

- If it is not specified in [`viewerConfig`]({{ site.api }}interface/captureviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, the default value is `false`.
- If the auto detect is disabled, it will automatically capture a frame every 1 second by default. It can be set by [autoCaptureDelay]({{ site.api }}interface/captureviewerconfig.html#autocapturedelay).
- If the auto detect is enabled, automatic capturing will only be performed when the detection result meets expectations. See also [`enableAutoDetect`](#enableautodetect).

### enableAutoDetect

Specify or return whether to enable automatic border detection in video stream.

**Syntax**

```typescript
enableAutoDetect: boolean; 
```

**Code Snippet**

```typescript
captureViewer.enableAutoDetect = true;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80315      | DocumentDetect needs to be configured to enable the document detection feature.

**Remark**

- If it is not specified in [`viewerConfig`]({{ site.api }}interface/captureviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, the default value is `false`. 
- This API only takes effect when [`DocumentDetect`]({{ site.api }}class/advanced/documentdetect.html) is set by [`setProcessingHandler()`]({{ site.api }}namespace/ddv.html#static-setprocessinghandler).

### acceptedPolygonConfidence

Specify or return the threshold confidence level when detecting boundaries.

**Syntax**

```typescript
acceptedPolygonConfidence: number; 
```

**Code Snippet**

```typescript
captureViewer.acceptedPolygonConfidence = 60;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   

**Remark**

- If it is not specified in [`viewerConfig`]({{ site.api }}interface/captureviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, the default value is 80. 
- The range of available values is [0,100] on a percentage scale.
- The higher the setting, the more accurate the automatic border detection.

### maxFrameNumber

Specify or return the maximum number of frames detected per second.

**Syntax**

```typescript
maxFrameNumber: number; 
```

**Code Snippet**

```typescript
captureViewer.maxFrameNumber = 3;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   

**Remark**

- If it is not specified in [`viewerConfig`]({{ site.api }}interface/captureviewerconstructoroptions.html#viewerconfig) while creating the viewer additionally, the default value is 10. 
- The value range is (0,60].

## Events

### on()

Bind a listener to the specified event. 

**Syntax**

```typescript
on(eventName: EventName, listener:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It can be [an integrated event name](#integrated-events) or a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener.

**Code Snippet**

```typescript
// Bind a listener to the integrated event resized.
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.oldWidth);
    console.log(e.newWidth);
};

captureViewer.on("resized", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  


### off()

Unbind event listener(s) from the specified event. 

**Syntax**

```typescript
off(eventName: EventName, listener?:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It can be [an integrated event name](#integrated-events) or a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener. If no listener is specified, unbind all event listeners from the specified event.

**Code Snippet**

```typescript
const eventFunc = (e)=>{
    console.log(e);
    console.log(e.oldWidth);
    console.log(e.newWidth);
};

captureViewer.on("resized", eventFunc);

// Unbind the specified event listener.
captureViewer.off("resized", eventFunc);
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  

### Integrated Events

#### resized

Triggered when the viewer is resized.

**Callback**

`ResizedEvent`: An EventObject.

**Attributes**

`oldWidth`: The old width of the viewer.

`oldHeight`: The old height of the viewer.

`newWidth`: The new width of the viewer.

`newHeight`: The new height of the viewer.

#### played

Triggered when the camera video stream is played.

**Callback**

`PlayedEvent`: An EventObject.

**Attributes**

`deviceId`: The camera device id.

`resolution`: The resolution used.

#### stopped

Triggered when the camera video stream is stopped.

**Callback**

`StoppedEvent`: An EventObject.

**Attributes**

`deviceId`: The camera device id.

#### captured

Triggered when a frame is captured.

**Callback**

`CapturedEvent`: An EventObject.

**Attributes**

`pageUid`: The pageUid of the captured image.

#### cameraChanged

Triggered when the used camera is changed.

**Callback**

`CameraChangedEvent`: An EventObject.

**Attributes**

`oldDeviceId`: The old camera device id.

`newDeviceId`: The new camera device id.

#### paginationChanged

Triggered when the viewer's current page number or the page count is changed. It will return an [`IPaginationChangedEvent`](/api/interface/ipaginationchangedevent.md) object.

#### visibilityChanged

Triggered when the viewer's visibility is changed. It will return an `isVisible` boolean value.


#### Mouse Events

##### click

Triggered when click in the viewer's viewing area. On mobile device, triggered when tap in the viewer's viewing area.

##### dblclick

Triggered when double click in the viewer's viewing area.

##### rightclick

Triggered when right click in the viewer's viewing area. On mobile device, triggered when long-tap in the viewer's viewing area.


**Callback for mouse events**

 `IPointerEvent`: An EventObject.

**Attributes**

`index`: The page index.

`pageUid`: The page uid.

`imageX`: The relative x-coordinate of the click pointer on the image.

`imageY`: The relative y-coordinate of the click pointer on the image.

`canvasX`: The relative x-coordinate of the click pointer on the canvas.

`canvasY`: The relative x-coordinate of the click pointer on the canvas.

`nativeEvent`: [`PointerEvent`](https://developer.mozilla.org/en-US/docs/Web/API/PointerEvent)