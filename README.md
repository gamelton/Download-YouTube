# Download YouTube video

This instructions will help you download video or audio from YouTube using the yt-dlp tool.

## Requirements 
1. Operating system: Windows (the instruction is adapted for it, but yt-dlp works on Linux/macOS as well).  
2. Programs: yt-dlp and FFmpeg installed (instructions below)  
3. Internet access to download utilities and videos.  
4. Administrator rights (requires installation in system folders).  
5. Disk: enough free space for files (high resolution videos can be large).

## Instructions
- Download yt-dlp.exe from the latest release https://github.com/yt-dlp/yt-dlp/releases/latest  
[Mirror on GitHub](https://github.com/gamelton/Download-YouTube/releases/download/v1.0.0/yt-dlp.exe)
- Copy to I:\VK\youtube-dl folder (or other folder).  
- Download ffmpeg-{version}-full_build.zip from the latest release https://github.com/GyanD/codexffmpeg/releases/latest  
[Mirror on GitHub](https://github.com/gamelton/Download-YouTube/releases/download/v1.0.0/ffmpeg-7.1.1-full_build.zip)
- Extract to C:\Program Files\ffmpeg folder  
- Open a command prompt (`Win + R` → `cmd`) and navigate to the folder with yt-dlp.exe.  
    ```
    cd /d I:VK\youtube-dl
    ```
- Use one of the following commands depending on the task. Replace the link to the video. See https://github.com/yt-dlp/yt-dlp/blob/master/README.md for a complete list of options  
    - Download the video at a maximum resolution no higher than 1080 and encode in x264:
        ```
        yt-dlp -f "bestvideo[height<=1080]+bestaudio/best[height<=1080]" --use-postprocessor FFmpegCopyStream --ppa CopyStream:"-c:v libx264 -c:a aac -f mp4" --ffmpeg-location "C:\Program Files\ffmpeg\bin\ffmpeg.exe" --downloader-args "ffmpeg_i1:-reconnect 1" --downloader-args "ffmpeg_i2:-reconnect 1" https://www.youtube.com/watch?v=dQw4w9WgXcQ
        ```
    - Download a snippet from the video:
        ```
        yt-dlp.exe -f "bestvideo[height<=720]+bestaudio/best[height<=720]" --download-sections "*00:01:01-00:02:02" --force-keyframes-at-cuts --ffmpeg-location "C:\Program Files\ffmpeg\bin\ffmpeg.exe" --use-postprocessor FFmpegCopyStream --ppa CopyStream:"-c:v libx264 -c:a aac -f mp4" --downloader-args "ffmpeg_i1:-reconnect 1" --downloader-args "ffmpeg_i2:-reconnect 1" https://www.youtube.com/watch?v=dQw4w9WgXcQ
        ```
    - Download audio:
        ```
        yt-dlp --extract-audio --audio-format mp3 --audio-quality 0 --use-postprocessor FFmpegCopyStream --ffmpeg-location "C:\Program Files\ffmpeg\bin\ffmpeg.exe" --downloader-args "ffmpeg_i1:-reconnect 1" --downloader-args "ffmpeg_i2:-reconnect 1" https://www.youtube.com/watch?v=dQw4w9WgXcQ
        ```
    - You can use the `proxy` parameter to use a proxy server:
        ```
        --proxy https://login:password@proxy.server.com:4443 
        ```
