# Notes from HuggingFace Learn Audio Course
## Unit 1: Working with Audio Data
### Sampling and Sampling Rate
- Sampling is measuring the value of a continuous signal.  This creates a discretized version of the signal.
- Sampling rate is the frequency at which measurements are taken.  Usually measured in Hz.  Examples:
    - 44,100 Hz -- CD audio
    - 192,000 Hz -- High res audio
    - 16,000 Hz -- training data for speech models
- Nyquist Limit: The sampling rate determines the highest frequency discernable in a recording.  Nyquist limit is exactly half the sampling rate.
- Models don't generalize to different sampling rates well which makes resampling an important pre-processing step
### Amplitude and Bit Depth
- Amplitude is how loud a sound is, and corresponds to the intensity of air pressure from the sound wave
    - Measured in deicbels (db), logarithmic scale
    - Real world audio db scale starts at 0db
    - Digital audio tops out at 0db and everything else is negative.
    - Rules of thumb in Digital Audio: -6db will halve the loudness.  -60db is too soft to be heard.
- Bit depth describes how closely the amplitude information can be captured.  A higher bit depth will be truer to the source signal
    - 16-bit and 24-bit are the most common bit depths
    - Respectively they have 65,536 and 16,777,216 steps, meaning there are that many values the amplitude information can be quantized to.
    - The quantization involved in quantization introduces some noise.  In practice, the noise in 16-bit audio is inaudible, so higher bit depth doesn't necessarily yield greater returns.
    - 32-bit audio also exists and uses floating point values which has values betwen [-1, 1].  ML models naturally expect this range of inputs, so conversion to floating point is also a preprocesing step.
### Audio as a Waveform
- Displaying audio as a waveform is also known as the time domain representation of sound.  Quick way to gague loudness and timing of particular events.
- This visualization is important just as with any other form of data.  Easy to learn to spot distortion and other irregularities in a sound signal.
### Frequency Spectrum
- Freq. Spectrum is computed using the Discrete Fourier Transform (DFT).  This yields the various frequencies present in the signal and the relative amplitudes of each.
- A DFT outputs an array of complex numbers.  The imaginary parts provide phase information which is generally not used for ML applications
- Power spectrum is the same thing, just with amplitude squared because $E ~ A^2$
### Spectrogram
- A frequency spectrum carries the limitation of only being for a single point in time.  A spectrogram is a bunch of Frequency Spectra on small time slices stacked up on top of one another.  It is able to show how the frequency information of the signal changes overtime.
- Calculated by the Short Time Fourier Transform (STFT)
- Griffin-Lim algorithm is a method for reconstructing phase information that might be lost.  Neural Networks called vocoders can also do this.

### Mel Spectrogram
- A spectrogram that uses the Mel-scale which accounts for the non-linear response to frequencies of the human ear.
- Because conversion to a Mel spectrum involves filtering the frequencies, it's lossy, and reconstructing a waveform from a Mel spectrogram requires something more sophisticated like a HiFiGAN vocoder
- Becasue the Mel spectrogram focuses on aspects of a signal more meaningful to humans, it is very useful for applications in speech recognition, speaker ID, and music genre classification
- 
