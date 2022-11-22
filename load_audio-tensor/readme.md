Use of torchAudio basci I/O API to load audio files into Pytorch tensor object.
Save tensor objects to audio files
Install the neccesary libs and modules and download the test data
Querying Audio metadata (data showing the constitution of the audio)
Take note of the Encoding formart, Samplerate and # of frames also channles & bit/sample (bit depth)
PCM_S -> Signed integer linear PCM (pulse code modulation) -> method of converting analog audio into digital
Load audio returns waveform tensors and sample rate int

PLot to monitor the waveform structure of the audio file

Define a Spectogram - spectrum of frequencies of a record audio over time

use numpy to listen to the audio

Slicing into overlapping frames:
Vanilla tensor slicing: num_frames and frame_offset