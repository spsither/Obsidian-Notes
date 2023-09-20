
[Connectionist Temporal Classification (CTC)](https://distill.pub/2017/ctc/)

[ASR](https://towardsdatascience.com/audio-deep-learning-made-simple-automatic-speech-recognition-asr-how-it-works-716cfce4c706)

Convert to uniform dimensions: sample rate, channels, and duration

Apply a noise-removal algorithm to eliminate background noise

Data augmentation: Time Shift our audio left or right randomly by a small percentage, or change the Pitch or the Speed of the audio by a small amount.

Convert to Mel Spectrograms

Mel Spectrogram into MFCC (Mel Frequency Cepstral Coefficients)
MFCCs produce a compressed representation of the Mel Spectrogram by extracting only the most essential frequency coefficients, which correspond to the frequency ranges at which humans speak.

Data Augmentation of Spectrograms
Using SpecAugment technique. This involves Frequency and Time Masking that randomly masks out either vertical (ie. Time Mask) or horizontal (ie. Frequency Mask) bands of information from the Spectrogram.

One should always keep in mind that pre-processing is a very important step before training your model. E.g., we don't want our model to differentiate between `a` and `A` just because we forgot to normalize the data. The difference between `a` and `A` does not depend on the "sound" of the letter at all

### Audio Pre-processing

Audio pre-processing is a crucial, yet often overlooked component of ASR inference mechanics. It comprises several steps including transcoding the audio into a required format (e.g., 16-bit PCM), resampling it at a specified rate, splitting it into chunks of a specified size, deriving acoustic features (e.g., log-mel spectrograms) over the chunks, and then grouping chunks together to form batches for inference.

Despite its importance, audio-preprocessing is usually not well described in open-source model documentation and may require delving deeply into underlying source code to understand a particular model's audio pre-processing requirements. Open-source models and their associated toolkits offer varying levels of audio pre-processing support. In many cases, you may have to roll your own pipeline.

[Compare Wav2vec2 vs Whisper](https://blog.deepgram.com/benchmarking-top-open-source-speech-models/)

[how to use wav2vec2](https://medium.com/att-israel/use-a-very-good-speech-recognition-model-with-pytorch-89ecc126ef7b)

[data augmentation with SpecAugment ](https://arxiv.org/pdf/1904.08779.pdf)


[LSTM](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)
# Questions ?
Should the model output characters, syllables or words.
char: 59
syll: 87436
words: ?

word-based language model vs character-based language model