```js
let audioCtx = new window.AudioContext();

async function createReverb() {
  let convolver = audioCtx.createConvolver();

  // load impulse response from file
  let response = await fetch("path/to/impulse-response.wav");
  let arraybuffer = await response.arrayBuffer();
  convolver.buffer = await audioCtx.decodeAudioData(arraybuffer);

  return convolver;
}

// …

let reverb = await createReverb();

// someOtherAudioNode -> reverb -> destination
someOtherAudioNode.connect(reverb);
reverb.connect(audioCtx.destination);
```
- [acoustic_sandbox/acoustic_sandbox.py at main · Burhanuddin98/acoustic_sandbox](https://github.com/burhanuddin98/acoustic_sandbox/blob/main/acoustic_sandbox.py)
- IR
  - Soldano SLO 100
  - Vox AC30s
