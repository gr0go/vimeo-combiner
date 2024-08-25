# Combine Vimeo video and Vimeo audio using Python

Here’s the `_combine.py` script:

```python
import sys
from moviepy.editor import VideoFileClip, AudioFileClip

def combine_video_audio(video_path, audio_path, output_path):
    # Load the video file
    video_clip = VideoFileClip(video_path)
    # Load the audio file using AudioFileClip to avoid 'video_fps' error
    audio_clip = AudioFileClip(audio_path)

    # Set the audio to the video clip
    final_clip = video_clip.set_audio(audio_clip)

    # Export the final video
    final_clip.write_videofile(output_path, codec="libx264", audio_codec="aac")

if __name__ == "__main__":
    if len(sys.argv) != 4:
        print("Usage: python _combine.py <video_file> <audio_file> <output_file>")
    else:
        video_file = sys.argv[1]
        audio_file = sys.argv[2]
        output_file = sys.argv[3]
        combine_video_audio(video_file, audio_file, output_file)
```

### Steps to Run the Updated Script:

1. **Ensure `moviepy` is installed:**
   ```bash
   pip install moviepy
   ```

2. **Run the script for each video-audio pair:**

   ```bash
   python _combine.py video.mp4 audio.mp4 result.mp4
   ```
