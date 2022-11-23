feature extractions common in audio practices:
Transformation of raw data to numeriacal features.
It preserves the information on the original data set by identifying only the key features

R/ship btn common audio features vs pytorch's API to generate them

https://download.pytorch.org/torchaudio/tutorial-assets/torchaudio_feature_extractions.png

Spectrogram: Get the frequency as it varies with time.
Waveform is a Tensor
length of the windowed signal after padding with zeros.
power=2.0 -> power=2.0: wav -> power spectogram (real valued (refer to image))

Mel Scale:
 Log transformation of a signal's freq
 Mimics the human perception ability to distinguish lower freq sounds (100/200 Hz).
Therefore, on th eMEl Scale, sounds of equal dist are perceived to be of equal dist to the human ear.


The advantage of MFCC is that it is good in error reduction and able to produce a robust feature when the signal is affected by noise.


Look into Pitch and MFCC
https://www.mathworks.com/help/audio/ug/speaker-identification-using-pitch-and-mfcc.html

The motivating idea of MFCC is to compress information about the vocal tract (smoothed spectrum) into a small number of coefficients based on an understanding of the cochlea.


https://towardsdatascience.com/learning-from-audio-the-mel-scale-mel-spectrograms-and-mel-frequency-cepstral-coefficients-f5752b6324a8

https://haythamfayek.com/2016/04/21/speech-processing-for-machine-learning.html

# Features for Classification
- Pitch, MFCC
- Zero-crossing rate, short-time energy : Determine when the pitch feature is used

# Voiced Speech:
Air from lungs is modulated by vocal cords and results in a Quasi-periodic excitation.
- The sound is dominated by Low-frequency Oscillations (pitch)

Pitch is a characterstic of regions of voiced speech.
- Analyze short time energy to distinguish btn silence and speech.
If energy in a frame is above a given threshold ->  frame  = speech.
- Zero-crossing rate: Distinguishes btn voiced and unvoiced speech.
A large number of zero crossings -> no dominant low-freq oscillatoins
Therefore, below a given threshold -> voiced

Kaldi pitch feature is tuned for ASR applications. (pitch extraction alg)
