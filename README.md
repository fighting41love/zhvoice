# 中文语音语料

**zhvoice**: Chinese voice corpus

tips: 中文或汉语的语言简称缩写是**zh**。

## 语料简介

zhvoice语料由8个开源数据集，经过降噪和去除静音处理而成，音频约900小时，文本约113万条，共有约1300万字。

zhvoice语料比较原始数据而言，更加清晰和自然，减少了噪声的干扰，减少了因说话人说话不连贯造成的不自然。

zhvoice语料包含文本、语音和说话人3个方面的信息，可适用于多种语音相关的任务。

zhvoice语料由[智浪淘沙](https://github.com/zhilangtaosha)清洗和处理。

## 处理方法
- 用python的工具模块[**aukit**](https://github.com/KuangDD/aukit)处理音频，降噪和去除静音。

```
pip install -U aukit

from aukit import remove_noise, remove_silence
```

- 用python的工具模块[**phkit**](https://github.com/KuangDD/phkit)处理文本，文本正则化和汉字转拼音。

```
pip install -U phkit

from phkit import text_to_sequence, pinyin
```

## 应用场景

- 用于语音克隆模型，可直接用于githup的语音克隆项目[**zhrtvc**](https://github.com/KuangDD/zhrtvc)。

- 用于语音合成模型，用标贝开源的中文标准女声音频**zhbznsyp**数据集，或者筛选音质较好，和目标声音相似的说话人语音及其文本。

- 用于声码器模型，即由语音特征转为语音信号的模型。用语音数据，可结合[**aukit**](https://github.com/KuangDD/aukit)的音频转频谱。

```
from aukit import linear_spectrogram, mel_spectrogram, world_spectrogram
```

- 用于语音编码器模型，即把语音编码到预定维度的向量空间。
- 用于声纹识别模型，用语音和对应的说话人标签。
- 用于语音识别模型，用语音和文本，可以适当加噪声。


## 下载路径

百度网盘：

链接: https://pan.baidu.com/s/1uHXE2WIt0kdm_dPSej-TtA 

提取码: i5b3


## 文件介绍

- info：各个数据集的源数据信息，包含源数据出处、简介等。
- text：语音语料对应的文本，包含文本、相对路径、说话人、参考拼音等信息。
- sample：样本语音，每个说话人一个音频。
- metadata：语料元数据，一行对应一个音频文件，每行的格式`音频相对路径\t汉字文本\n`。
- zh*：zh开头的是语料文件，目录结构：根目录下包含metadata.csv和语音文件目录。一个说话人对应一个子目录，音频是mp3格式。metadata.csv的数据结构和metadata的一样，记录当前数据集的信息。

## 统计信息

- character_W: 字符个数，单位：万字。包括汉字、英文字母和标点符号。
- duration_H: 语音时长，单位：小时。
- n_audio_per_speaker：每个说话人的音频数量。
- n_minute_per_speaker：平均每个说话人的音频总时长，单位：分钟。
- n_speaker：说话人个数。
- sentence_W：文本数目，单位：万条。
- size_MB：音频占用存储空间，单位：MB。

注意：**total**是全部数据集合集的结果。

```
{
    "total": {
        "character_W": 1287.0836999999997,
        "duration_H": 889.7492555555556,
        "n_audio_per_speaker": 348.30255463219453,
        "n_character_per_sentence": 11.37366465335554,
        "n_minute_per_speaker": 16.431195855134913,
        "n_second_per_audio": 2.8305039345725436,
        "n_speaker": 3249,
        "sentence_W": 113.1635,
        "size_MB": 9164.134941101074
    },
    "zhaidatatang": {
        "character_W": 233.5123,
        "duration_H": 145.47232,
        "n_audio_per_speaker": 395.4416666666667,
        "n_character_per_sentence": 9.841835078920194,
        "n_minute_per_speaker": 14.547232000000001,
        "n_second_per_audio": 2.2072381177164773,
        "n_speaker": 600,
        "sentence_W": 23.7265,
        "size_MB": 1498.3187255859375
    },
    "zhaishell": {
        "character_W": 204.0219,
        "duration_H": 142.5542,
        "n_audio_per_speaker": 354.0,
        "n_character_per_sentence": 14.40832627118644,
        "n_minute_per_speaker": 21.38313,
        "n_second_per_audio": 3.6242593220338986,
        "n_speaker": 400,
        "sentence_W": 14.16,
        "size_MB": 1468.2630157470703
    },
    "zhbznsyp": {
        "character_W": 18.3708,
        "duration_H": 10.544652222222222,
        "n_audio_per_speaker": 10000.0,
        "n_character_per_sentence": 18.3708,
        "n_minute_per_speaker": 632.6791333333333,
        "n_second_per_audio": 3.7960748,
        "n_speaker": 1,
        "sentence_W": 1.0,
        "size_MB": 108.60657119750977
    },
    "zhmagicdata": {
        "character_W": 567.2561,
        "duration_H": 406.01905,
        "n_audio_per_speaker": 563.8938053097345,
        "n_character_per_sentence": 9.891471367789634,
        "n_minute_per_speaker": 23.953926253687317,
        "n_second_per_audio": 2.548769930947897,
        "n_speaker": 1017,
        "sentence_W": 57.348,
        "size_MB": 4181.867351531982
    },
    "zhprimewords": {
        "character_W": 105.2203,
        "duration_H": 81.30301,
        "n_audio_per_speaker": 171.96621621621622,
        "n_character_per_sentence": 20.67115241051432,
        "n_minute_per_speaker": 16.480339864864863,
        "n_second_per_audio": 5.750085183293388,
        "n_speaker": 296,
        "sentence_W": 5.0902,
        "size_MB": 837.3951988220215
    },
    "zhspeechocean": {
        "character_W": 3.1078,
        "duration_H": 1.8908433333333334,
        "n_audio_per_speaker": 120.0,
        "n_character_per_sentence": 12.949166666666668,
        "n_minute_per_speaker": 5.67253,
        "n_second_per_audio": 2.836265,
        "n_speaker": 20,
        "sentence_W": 0.24,
        "size_MB": 19.475086212158203
    },
    "zhstcmds": {
        "character_W": 111.9317,
        "duration_H": 74.53628,
        "n_audio_per_speaker": 120.0,
        "n_character_per_sentence": 10.909522417153998,
        "n_minute_per_speaker": 5.230616140350877,
        "n_second_per_audio": 2.6153080701754385,
        "n_speaker": 855,
        "sentence_W": 10.26,
        "size_MB": 767.7000274658203
    },
    "zhthchs30": {
        "character_W": 43.6628,
        "duration_H": 27.4289,
        "n_audio_per_speaker": 223.13333333333333,
        "n_character_per_sentence": 32.61338512100388,
        "n_minute_per_speaker": 27.4289,
        "n_second_per_audio": 7.375563190917239,
        "n_speaker": 60,
        "sentence_W": 1.3388,
        "size_MB": 282.5089645385742
    }
}
```
