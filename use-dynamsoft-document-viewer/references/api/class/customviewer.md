---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - CustomViewer Class
keywords: Documentation, Dynamsoft Document Viewer, API Reference, CustomViewer Class
breadcrumbText: CustomViewer Class
description: Dynamsoft Document Viewer Documentation API Reference CustomViewer Class Page
permalink: /api/class/customviewer.html
---

# CustomViewer Class

Custom Viewer does not have any built-in UI or functionality, it is used for creating your own viewer.

## API Index

**Create and Destroy Instances** 

| API Name       | Description                                   |
| ------------ | --------------------------------------------- |
| [`CustomViewer()`](#customviewer) | Default constructor of a `CustomViewer` instance. |
| [`destroy()`](#destroy)             | Destroy the `CustomViewer` instance.                             |

**Viewer Control**

| API Name              | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| [`bindContainer()`](#bindcontainer)     | Bind the viewer to the specified container.                  |
| [`unbindContainer()`](#unbindcontainer) | Unbind the viewer from the specified container.              |
| [`isBoundContainer`](#isboundcontainer) | Return whether the viewer is bound to a container. |
| [`getUiConfig()`](#getuiconfig)         | Get current `UiConfig` object.                               |
| [`updateUiConfig()`](#updateuiconfig)     | Update `UiConfig` object.                                    |
| [`show()`](#show)                | Show the viewer.                                             |
| [`hide()`](#hide)                | Hide the viewer.                                             |
| [`isVisible`](#isvisible)        | Return whether the viewer is shown or hidden.      |

**Events**

| API Name | Description                                        |
| -------- | -------------------------------------------------- |
| [`on()`](#on)     | Bind a listener to the specified event.            |
| [`off()`](#off)    | Unbind event listener(s) from the specified event. |

### CustomViewer()

Default constructor of a `CustomViewer` instance.

**Syntax**

```typescript
new Dynamsoft.DDV.CustomViewer(options?: CustomViewerConstructorOptions);
```

**Parameters**

`options`: The constructor options for a `CustomViewer` instance. Please refer to [`CustomViewerConstructorOptions`]({{ site.api }}interface/customviewerconstructoroptions.html).

**Code Snippet**

```typescript
const customViewer = new Dynamsoft.DDV.CustomViewer({
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

### destroy()

Destroy the `CustomViewer` instance.

**Syntax**

```typescript
destroy(): void;
```

**Code Snippet**

```typescript
customViewer.destroy();
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
customViewer.bindContainer("viewercontainer");
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
customViewer.unbindContainer();
```

### isBoundContainer

Return whether the viewer is bound to a container.

**Syntax**

```typescript
readonly isBoundContainer: boolean;
```

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
const viewerUi = customViewer.getUiConfig();
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
customViewer.show();
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
customViewer.hide();
```

### isVisible

Return whether the viewer is shown or hidden.

**Syntax**

```typescript
readonly isVisible: boolean;
```

**Remark**

- The viewer is shown automatically when it is created which means the default value of `isVisible` is `true`.

## Events

### on()

Bind a listener to the specified event. 

**Syntax**

```typescript
on(eventName: EventName, listener:(event:EventObject)=>void): void;
```

**Parameters**

`eventName`: Specify the event name. It can be a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener.

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

`eventName`: Specify the event name. It can be a custom event name configured through [`UiConfig`-`events`]({{ site.api }}interface/uiconfig.html#events).

`listener`: Specify the listener. If no listener is specified, unbind all event listeners from the specified event.

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  