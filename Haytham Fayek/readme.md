https://haythamfayek.com/2016/04/21/speech-processing-for-machine-learning.html

Feature Extraction:
Features:
Mel-freq Cesptral co-efficients MFCC  vs Filter banks

These are features to be computed.

Signal steps:
   - Pre-empahsis filter
   - Slice into overlapping frames
   - Apply window function on each frame
   - Do a Fourier Transform on each frame: Short Time Fourier Transfrom
   - calc. the power spectrum
   - Compute Filter banks **
    
   Apply a Discrete Cosine Transform (DCT) to filter banks to obtain MFCC
    ** Some co-efficients are retained while others are discarded
    
   - Normalize

    Speech reference link:
    http://www.voiptroubleshooter.com/open_speech/american.html

# 1. Pre-emphasis Filter:
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
Windows are neccessary for:
- Counteract the assumtion made by fft that data is infinite.
- Reduce spectral leakage




can also be expressed as:

-    frames = frames * (0.54 - 0.46*numpy.cos((2*numpy.pi*n)/(frame_length - 1)))

- frame_length = Window size , N

# 4. Fourier Transform FFT & Power Spectrum

Short-time fourier transfrom STFT aka Frequency spectrum.
We do an N-point fft on each frame to calculate stft
- N is typically 256/512

# 5. Filter Banks
Goal is to extract frquency bands
- Apply trinagular filters (40 filters) on a mel scale to the power spectrum

    Modelling the Mel Freq:
    http://practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/

- The mel filterbank linearly spaces the first 10 triangular filters and logarithmically spaces the remaining filters

- freq bins: 
 https://www.mathworks.com/matlabcentral/answers/322142-what-are-frequency-bins


# MFCCs

High correlation of filter banks in pose some challenges in some machine learning algorith

Therefore: Decorrelation of the co-eff to yield a compressed represenation of the filter bank is done using ~ DCT
for ASR, resulting cepsral coeff btn 2-13 are retained while the rest are discarded:
- Why discard ? They represent fast changing nature in the, and such fine details don't contribute to ASR

- decorrelate filter bank coefficients, a process also referred to as whitening

# sinusoidal liftering
- apply sin liftering to the MFCC to de-emphasize higher MFCC which improves speech recognition in a noisy environment.

# 6. Mean Normalization

Involves subtracting the mean of each co-efficients from all frames
- Goal: Balance spectrum and improve Signal to Noise Ratio SNR


- note that all steps needed to compute filter banks were motivated by the nature of the speech signal and the human perception of such signals.

- the extra steps needed to compute MFCCs were motivated by the limitation of some machine learning algorithms