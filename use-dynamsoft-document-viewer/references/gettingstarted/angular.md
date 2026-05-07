---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Angular Document Viewer - Dynamsoft Document Viewer Documentation
keywords: Documentation, Dynamsoft Document Viewer, PDF, Getting Started, Angular
breadcrumbText: Angular
description: Learn how to integrate Dynamsoft Document Viewer into your Angular project with this step-by-step guide.
---

# How to Integrate Document Viewer into an Angular Project

This guide will show you how to integrate Dynamsoft Document Viewer into an Angular project.

You can can download the sample on GitHub:

![Download](/assets/imgs/download.png)[Angular Helloworld](https://github.com/Dynamsoft/document-viewer-samples/blob/main/hello-world/angular)

## Preparation

Make sure you have node and Angular CLI (v17 in this guide) installed.

## New Project

Create a new Angular project.

```bash
ng new ddv-angular
```

## Add Dependencies

1. Install Dynamsoft Document Viewer.

   ```bash
   npm install dynamsoft-document-viewer
   ```
   
2. Modify `angular.json` to copy the resources of Dynamsoft Document Viewer and import its CSS.


   ```json
   {
     "assets": [
       "src/favicon.ico",
       "src/assets",
       {
         "glob": "**/*",
         "input": "node_modules/dynamsoft-document-viewer/dist",
         "output": "/dynamsoft-document-viewer/dist"
       }
     ],
     "styles": [
       "src/styles.css",
       "node_modules/dynamsoft-document-viewer/dist/ddv.css"
     ]
   }
   ```

## Create a Document Viewer Component

1. Generate a viewer component.

   ```bash
   ng generate component viewer
   ```
   
2. Add the following HTML code to `viewer.component.html`.

   ```html
   <div id="container"></div>
   ```

3. Add the following CSS code to `viewer.component.css`.

   ```css
   :host, #container {
       width: 100%;
       height: 100%;
   }
   ```

4. Add the following JavaScript code to `viewer.component.ts`. It will bind Edit Viewer to a container. A license is set here. You can apply for a 30-day trial on [this page](https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv).

   ```ts
   import { Component } from '@angular/core';
   import { DDV } from 'dynamsoft-document-viewer';

   @Component({
     selector: 'app-viewer',
     standalone: true,
     imports: [],
     templateUrl: './viewer.component.html',
     styleUrl: './viewer.component.css'
   })

   export class ViewerComponent {
     async ngOnInit() {
       DDV.on('error', (e) => {
         alert(e.message)
       })
       
       // Public trial license which is valid for 24 hours
       DDV.Core.license = 'DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9';
       DDV.Core.engineResourcePath = '/dynamsoft-document-viewer/dist/engine';
       DDV.Core.loadWasm();
       await DDV.Core.init();

       const viewer = new DDV.EditViewer({
         container: 'container'
       });
     }
   }
   ```

## Use the Document Viewer Component


1. Open `app.component.html` and add the viewer component.

   ```html
   <style></style>
   <h1>Hello World for Angular</h1>
   <app-viewer
   ></app-viewer>
   <router-outlet></router-outlet>
   ```

2. Import the viewer component in `app.component.ts`.

   ```js
   import { ViewerComponent } from './components/viewer/viewer.component';
   
   @Component({
       selector: 'app-root',
       standalone: true,
       templateUrl: './app.component.html',
       styleUrl: './app.component.css',
       imports: [
         CommonModule,
         RouterOutlet,
         ViewerComponent,
       ],
   })
   ```
   
3. Add CSS in `app.component.css`.

   ```css
   :host {
       width: 100%;
       height: 100%;
       display: flex;
       flex-direction: column;
   }
   ```

Run the app with the following command and you should see the viewer mounted in your application!

```bash
ng serve
```

## Other Samples

You can find other samples on [this GitHub repo](https://github.com/Dynamsoft/document-viewer-samples/).



