# iOS 11+ CoreML in Titanium
Use the native iOS 11+ "CoreML" framework in Axway Titanium.

## Requirements
- [x] Titanium SDK 6.2.0 and later
- [x] iOS 11 and later
- [x] Compiled CoreML models (`xcrun coremlcompiler compile path/to/model.mlmodel /path/to/output`)

## API's

### `createRealtimeRecognitionView(args)`
- `model` (String - _Required_)

#### Methods
- `startRecognition()`
- `stopRecognition()`
- `isRecognizing()` (Boolean)

#### Events
- `classification` (`Event.classifications`)

### `isSupported()` (Boolean)

## Example
```js
var CoreML = require('ti.coreml');

var recognitionView = CoreML.createRealtimeRecognitionView({
    top: 40,
    height: 300,
    model: 'Inceptionv3.mlmodelc'
});

recognitionView.addEventListener('classification', function(e) {
    Ti.API.info(e);
});

var win = Ti.UI.createWindow({
    backgroundColor: '#fff'
});

win.add(recognitionView);

var triggerButton = Ti.UI.createButton({
    bottom: 40,
    title: 'Start Real-Time Recognition'
});

triggerButton.addEventListener('click', function() {
    recognitionView.startRecognition();
});

win.add(triggerButton);
win.open();
```

## Build
```js
cd iphone
appc ti build -p ios --build-only
```

## Legal

This module is Copyright (c) 2017-Present by Axway Appcelerator, Inc. All Rights Reserved. 
Usage of this module is subject to the Terms of Service agreement with Appcelerator, Inc.  
