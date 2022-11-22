https://haythamfayek.com/2016/04/21/speech-processing-for-machine-learning.html

Feature Extraction:
Features:
Mel-freq Cesptral co-efficients MFCC  vs Filter banks

These are features to be computed.

Signal steps:
   - Pre-empahsis filter
   - Slice into overlapping frames
   - Apply window function on each frame
   - Do a Fourier Transform on each frame: Shrt Time Fourier Transfrom
   - calc. the power spectrum
   - Compute Filter banks **
    -------------
   - Apply a Discrete Cosine Transform (DCT) to filter banks to obtain MFCC
    ** Some co-efficients are retained while others are discarded
    -------------
   - Normalize

    Speech reference link:
    http://www.voiptroubleshooter.com/open_speech/american.html

# 1. Pre-ephasis Filter:
Amplifies the high freqs
By balancing freq spectrum. High freq have smaller magnitudes compared to lower freqs.
Prevent numerical problems during fourier transform ops
Improves signal to noise ratio. SNR

pre-emphasis filter can be achieved using mean normalization **

# 2. Framing:
Split the signal into short-time frames.
Since freq change over time, its not safe to do a fourier transorm across the entire signal -> we may lose freq contours of the signal over time.

Typical frame size: 20-40 ms w/50%(+/- 10%) overlap btn consecutive frames

- the seconds are always converted to samples -> sec*s_r

    no. of frames = (signal_length - frame_length)/frame_step

- Padding ensures all frames have equal number of samples w/out truncating any samples from the original signal

# 3. Window fxn to Frames:
