---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Capture Viewer
keywords: Documentation, Dynamsoft Document Viewer, Features, Capture Viewer
breadcrumbText: Capture Viewer
description: Dynamsoft Document Viewer Documentation Features, Capture Viewer
permalink: /features/viewers/captureviewer.html
---

# Capture Viewer

Capture Viewer is used to control camera, play video stream, and capture the images from camera.

- [Default user interface]({{ site.ui }}default_ui.html#capture-viewer)
- [Default viewer configuration]({{ site.viewer }}viewerconfig.html#capture-viewer)

```typescript
const captureViewer = new Dynamsoft.DDV.CaptureViewer({
    container: document.getElementById("viewer"),
});

```

## Control camera

### Select camera

DDV's built-in Camera Viewer will select the best camera device in the camera list as the default camera. The method [`selectCamera()`]({{ site.api }}class/captureviewer.html#selectcamera) can help to select the camera you would like to use.

- Select the first camera in the camera list
    ```typescript
    const cameras = await captureViewer.getAllCameras();
    if (cameras.length) {
        await captureViewer.selectCamera(cameras[0]);
    }
    ```

- Select the camera whose label is "Dynamsoft camera".

    ```typescript
    const cameras = await captureViewer.getAllCameras();
    for (var i=0;i<cameras.length;i++)
    { 
        if(cameras[i].label == "Dynamsoft camera"){
            captureViewer.selectCamera(cameras[i]);
            break;
        }
    }
    ```

### Play/stop video stream

After selecting the specified camera, you need to call [`play()`]({{ site.api }}class/captureviewer.html#play) to play the video stream.

```typescript
await captureViewer.play();
```

If you want to stop the video stream, please call [`stop()`]({{ site.api }}class/captureviewer.html#stop) method.

```typescript
captureViewer.stop();
```

### Set resolution

The resolution of camera can be set when playing the video stream.

```typescript
// Set to 1080P
await captureViewer.play({
    resolution: [1920,1080], 
});
```

### Turn on flashlight

After playing the video stream, the flashlight can be opened by using [`turnOnTorch()`]({{ site.api }}class/captureviewer.html#turnontorch).

```typescript
// Turn on flashlight
await captureViewer.turnOnTorch();

// Turn off flashlight
await captureViewer.turnOffTorch();
```

> Note that it only works with Chromium-based browsers such as Edge and Chrome on Windows or Android. Other browsers such as Firefox or Safari are not supported. 

> Note that all browsers on iOS (including Chrome) use WebKit as the rendering engine and are not supported.

## Capture

### Real-time boundaries detection

After configuring [Document Detection]({{ site.features }}advanced/documentdetect.html), if you set [`enableAutoDetect`]({{ site.api }}class/captureviewer.html#enableautodetect) to `true`, real-time border detection in video stream will be enabled.

```typescript
captureViewer.enableAutoDetect = true;
```

### Auto capture

When [`enableAutoCapture`]({{ site.api }}class/captureviewer.html#enableautocapture) is set to `true`, the capture viewer will capture frame automatically.

```typescript
captureViewer.enableAutoCapture = true;
```

> If the auto detect is disabled, it will automatically capture a frame every 1 second by default. It can be set by [autoCaptureDelay]({{ site.api }}interface/captureviewerconfig.html#autocapturedelay).

> If the auto detect is enabled, automatic capturing will only be performed when the detection result meets expectations. 

## FAQ

### What cameras are supported?

Capture Viewer uses the [getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) API to access the camera. Normally, the device's built-in cameras and UVC cameras are supported.

### Why can't I use my camera?

This feature is available only in secure contexts (HTTPS or localhost). In addition, if the user denies permission, or the matching media is not available, it will reject your request with `NotAllowedError` or `NotFoundError` DOMException respectively.
