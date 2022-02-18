[English Version](# English Version) 

[中文版](# 中文版)

###### English Version

GitHub Address:https://github.com/tensorflow/models/tree/master/research/audioset/vggish

Colab Address: https://colab.research.google.com/drive/1E3CaPAqCai9P9QhJ3WYPNCVmrJU4lAhF#scrollTo=PPUqQtVHKggi

# Introduction

The advantage of VGGish is that it was trained by Google for a long time on a huge dataset called Audioset.

VGGish supports the extraction of 128-dimensional embedding feature vectors with semantics from audio waveforms.

The VGGish model converts audio input features into semantic and meaningful 128-dimensional high-level feature vectors, which can be used as input to downstream models.

# The process of  feature extraction

The **input data** is a wav audio file, and the feature extraction process of the audio file is as follows:

1. Resample the audio to 16kHz mono audio;
2. Use a 25 ms Hann time window and a 10 ms frame shift to perform a short-time Fourier transform on the audio to obtain a spectrogram;
3. Calculate the mel spectrum by mapping the spectrogram to the 64th order mel filter bank;
4. Calculate log(mel-spectrum + 0.01) to get a stable mel spectrum. The added bias of 0.01 is to avoid taking the logarithm of 0;
5. The features are then framed with a duration of 0.96s, and there is no overlap of frames, each frame contains 64 mel bands with a duration of 10ms (i.e. a total of 96 frames).

The **output data** format of the VGGish model is [nums_frames, 128], where nums_frames is the frame length, and nums_frames=audio duration/0.96.

# Model files



**The VGGish model contains 8 python script files:**

- vggish_slim.py: Model definition in TensorFlow Slim.
- vggish_params.py: Hyperparameters.
- vggish_input.py: Convert the audio waveform to the desired input data format.
- mel_features.py: Audio feature extraction.
- vggish_postprocess.py: post-processing embedding.
- vggish_inference_demo.py: shows how to generate VGGish embeddings from arbitrary audio.
- vggish_train_demo.py: shows how to add a model on top of VGGish and train the whole model
- vggish_smoke_test.py: VGGish installation successful test

# Example of  Data process

1. Resampling the audio to 16kHz mono (vggish_input.py), as shown in Figure 1, the output data format is [num_samples, 96, 64], where num_samples is related to the duration of the audio.

![image-20220218215324797](VGGish.assets/image-20220218215324797.png)

2. Use the frame length of 25ms, the frame shift of 10ms, and the periodic Hann window to frame the speech, perform short-time Fourier transform on each frame, and then use the signal amplitude to calculate the spectrogram, as shown in Figure 2 .

![image-20220218215402351](VGGish.assets/image-20220218215402351.png)

3. The mel spectrum is computed by mapping the spectrum into a 64-order mel filter bank, as shown in Figure 3.![image-20220218215438861](VGGish.assets/image-20220218215438861.png)

4. Calculate log(mel-spectrum + 0.01), resulting in a stable mel spectrum (Figure 4), with a bias of 0.01 added to avoid taking the logarithm of 0

![image-20220218215521190](VGGish.assets/image-20220218215521190.png)

The features are then framed with a duration of 0.96s, with no overlap of frames, each frame contains 64 mel bands with a duration of 10ms (i.e. a total of 96 frames). The framed feature data format is [nums_frames, 128] feature vector, which will be input to the downstream model for further training.



中文版

GitHub 地址:https://github.com/tensorflow/models/tree/master/research/audioset/vggish

Colab 地址: https://colab.research.google.com/drive/1E3CaPAqCai9P9QhJ3WYPNCVmrJU4lAhF#scrollTo=PPUqQtVHKggi

# 介绍

VGGish的优势在于，这是Google在一个名为Audioset的庞大数据集上进行长时间训练出来的。

VGGish支持从音频波形中提取具有语义的128维embedding特征向量。

VGGish模型将音频输入特征转化为具有语义和有意义的128 维high-level的特征向量，而128维high-level特征向量可以作为下游模型的输入。

###### 

# VGGish提取特征过程

**输入数据为wav音频文件，音频文件的特征提取过程如下：**

1. 将音频重采样为16kHz单声道音频；
2. 使用25 ms的Hann时窗，10 ms的帧移对音频进行短时傅里叶变换得到频谱图；
3. 通过将频谱图映射到64阶mel滤波器组中计算mel声谱；
4. 计算 log(mel-spectrum + 0.01)，得到稳定的 mel 声谱，所加的 0.01 的偏置是为了避免对 0 取对数；
5. 然后这些特征被以 0.96s的时长被组帧，并且没有帧的重叠，每一帧都包含 64 个mel 频带，时长 10ms（即总共 96 帧）。

VGGish模型输出数据格式为[nums_frames， 128]，其中nums_frames为帧长，nums_frames=音频时长/0.96。





# VGGish模型文件

**VGGish模型包含8个python脚本文件：**

- vggish_slim.py: TensorFlow Slim中模型定义。
- vggish_params.py：超参数。
- vggish_input.py：音频波形转换为所需的输入数据格式。
- mel_features.py：音频特征提取。
- vggish_postprocess.py：后处理embedding。
- vggish_inference_demo.py：显示了如何从任意音频中生成VGGish embedding。
- vggish_train_demo.py：显示了如何在VGGish之上添加模型并训练整个模型
- vggish_smoke_test.py：VGGish安装成功测试

# 数据处理示例

1. 将音频重采样为 16kHz 单声道（vggish_input.py）,如图1所示，此时输出数据格式为[num_samples, 96, 64]， 其中num_samples与音频的时长有关。

![image-20220218215324797](VGGish.assets/image-20220218215324797.png)

2. 使用 25ms 的帧长、10ms 的帧移，以及周期性的 Hann 窗口对语音进行分帧，对每一帧做短时傅里叶变换，然后利用信号幅值计算声谱图，如图2所示。

![image-20220218215402351](VGGish.assets/image-20220218215402351.png)

3. 通过将声谱映射到 64 阶 mel 滤波器组中计算 mel 声谱， 如图3所示。![image-20220218215438861](VGGish.assets/image-20220218215438861.png)

4. 计算 log(mel-spectrum + 0.01)，得到稳定的 mel 声谱（图4），所加的 0.01 的偏置是为了避免对 0 取对数

![image-20220218215521190](VGGish.assets/image-20220218215521190.png)

然后这些特征被以 0.96s的时长被组帧，并且没有帧的重叠，每一帧都包含 64 个 mel 频带，时长 10ms（即总共 96 帧）。这些组帧后的特征数据格式为[nums_frames, 128]特征向量，将输入给下游模型进行进一步训练。

