---
name: web-twain
description: Dynamic Web TWAIN SDK documentation and API reference.
---

# Dynamic Web TWAIN Documentation

## When to Use

Use this skill when generating or modifying code that uses Dynamic Web TWAIN, including:

- scanning documents
- loading PDFs
- saving PDFs
- using Web TWAIN APIs
- working with scanners in browsers
- asking questions about Dynamic Web TWAIN

## Instructions

Use the documentation in `llms-full.txt` as the authoritative reference for the Dynamic Web TWAIN SDK APIs and usage patterns. The file lies in the references folder of the skill.

Prefer the APIs and code patterns described in the documentation. Avoid using deprecated or legacy APIs when modern alternatives are available.

Preferred Scanning APIs (modern APIs that should be used for new code and more scanner protocols support):

* GetDevicesAsync
* SelectDeviceAsync
* AcquireImageAsync

Example scanning workflow:

```js
DWTObject.GetDevicesAsync().then((deviceList)=>{
  return DWTObject.SelectDeviceAsync(deviceList[0])  //Select the first device
}).then(()=>{
    return DWTObject.AcquireImageAsync({
      IfCloseSourceAfterAcquire: true,
    }) 
}).catch((e)=>{
    console.error(e)
})
```

Disfavored Scanning APIs:

* OpenSource
* OpenSourceAsync
* GetSourceNames
* GetSourceNamesAsync
* SelectSource
* SelectSourceAsync
* SelectSourceByIndex
* SelectSourceByIndexAsync

