# audio_process
 audio wave visualization, detect & cut silence

ai voice refer to: https://www.bilibili.com/read/cv22375562

slience remove refer to: https://onkar-patil.medium.com/how-to-remove-silence-from-an-audio-using-python-50fd2c00557d


- mp4剥离音频
ffmpeg -i mc03.mp4 -vn -ar 44100 -ac 2 -b:a 192k mc03.wav

- mp3 截取时长
ffmpeg -ss 0 -i butterfly.mp3 -t 85 output3.wav

- 合并音视频
ffmpeg -i videoplayback.webm -i videoplayback_AUDIO.m4a -vcodec copy -acodec copy test_zelda.mp4

- 去掉空白段落
ffmpeg -i xxx.wav -af silenceremove=stop_periods=-1:stop_duration=2:stop_threshold=-23dB xxx_cut.wav
