
# AI改变音色

## 准备音色模型

- 【UVR5】 第一步，分离bgm和人声
    - Demucs
        - Vocals
        - v3|UVR_Model_1
        - GPU conversion
- 【UVR5】 第二步，去除合声，保留干声
    - VR Architecture
        - 320
        - 10
        - 5_HP-Karaoke-UVR
        - GPU conversion & Vocals Only
- 【FFMPEG】用ffmpeg来把大段的空白声音去掉
    - ffmpeg -i xxx.wav -af silenceremove=stop_periods=-1:stop_duration=2:stop_threshold=-23dB xxx_cut.wav
- 【Audio Slicer】声音切片
    - 选好输入输出就行
    - 片段太长无法训练

## 模型训练

- `so-vits-svc-4.0/dataset_raw` 目录下创建一个文件夹，
`xxx_processed`，上一步处理好的数据放入
- 数据预处理.bat
- 训练.bat
    - 显卡够好可以提高`bach_size`，这里数字填18就会占用18个G的GPU显存
    - 生成的模型在`./logs/44k/G_xxx.pth`，这里的`xxx`超过10000基本就可以用了
    - 模型训练可以中断，支持断点继续训练
- 推理预测.bat
    - `app.py` 文件里面的模型地址改成上一步训练的地址
    - 如果唱歌的话记得放进来的音频也要是干声，和***准备音色模型***前两步一样的操作
