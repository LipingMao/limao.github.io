---
title: WebRTC -- Sample 6
---

获取Audio设备和Tracks:

```
'use strict';

// Put variables in global scope to make them available to the browser console.
const audio = document.querySelector('audio');

const constraints = window.constraints = {
  audio: true,
  video: false
};

function handleSuccess(stream) {
  const audioTracks = stream.getAudioTracks();
  console.log('Got stream with constraints:', constraints);
  console.log('Using audio device: ' + audioTracks[0].label);
  stream.oninactive = function() {
    console.log('Stream ended');
  };
  window.stream = stream; // make variable available to browser console
  audio.srcObject = stream;
}

function handleError(error) {
  const errorMessage = 'navigator.MediaDevices.getUserMedia error: ' + error.message + ' ' + error.name;
  document.getElementById('errorMsg').innerText = errorMessage;
  console.log(errorMessage);
}

navigator.mediaDevices.getUserMedia(constraints).then(handleSuccess).catch(handleError);

```

see : https://webrtc.github.io/samples/src/content/getusermedia/audio/
