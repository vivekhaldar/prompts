# How to Create a Video Montage from a Folder of Images

This document outlines the steps to create a video montage from a folder of images.

## 0. Convert HEIC to JPEG (if necessary)

Before you begin, make sure all your images are in JPEG format. `ffmpeg` does not handle HEIC files well. If you have HEIC images, you can convert them to JPEG using the following command on macOS:

```bash
for file in *.HEIC; do sips -s format jpeg "$file" --out "${file%.*}.jpg"; done
```

This command will convert all HEIC files in the current directory to JPEG files. You should then use these new JPEG files for the rest of the process.

## 1. Describe the Images

First, you need to have a description for each image. Use a multimodal model, such as Gemini 2.5 Pro, to examine each image and then generate descriptions for them. The descriptions should be saved in a JSON file named `image_descriptions.json` in the following format:

```json
[
  {
    "file_name": "image1.jpg",
    "description": "A description of image1."
  },
  {
    "file_name": "image2.jpg",
    "description": "A description of image2."
  }
]
```

## 2. Create Shortened Captions

Create shortened, vlog-style captions for each image. Here are the captions that were used in the video:

1.  "Exploring the Japanese Tea Garden"
2.  "Pizza with a view of the Golden Gate"
3.  "Checking out the cool lighthouse lens!"
4.  "Beach day selfie!"
5.  "Homeward bound!"

## 3. Download Background Music

Download a royalty-free background music track and save it as `background_music.mp3` in the same folder as your images. You can use the following `curl` command to download the music that was used in the video:

```bash
curl -L -o background_music.mp3 "https://cdn.pixabay.com/download/audio/2022/08/04/audio_29b2a72a87.mp3"
```

## 4. Create the Video Montage

Use the following `ffmpeg` command to create the video montage. This command will:

*   Take your images as input.
*   Apply a Ken Burns (zoom and pan) effect to each image.
*   Overlay the shortened captions onto each corresponding image segment of the video.
*   Add the downloaded music as the background audio track.
*   Scale the images to fit the video's dimensions while preserving their original aspect ratio and adding black bars to fill the empty space.

**Note:** You will need to replace the image file names and the text for the captions in the command below with your own.

```bash
ffmpeg -y \
-i IMG_20250625_095548.jpg \
-i IMG_20250625_131322.jpg \
-i IMG_20250625_144319.jpg \
-i IMG_2712.jpg \
-i IMG_2761.jpg \
-i background_music.mp3 \
-filter_complex "[0:v]scale=1280:720:force_original_aspect_ratio=decrease,pad=1280:720:(ow-iw)/2:(oh-ih)/2,setsar=1,zoompan=z='min(zoom+0.0015,1.5)':d=125,fade=t=in:st=0:d=1,fade=t=out:st=4:d=1,drawtext=text='Exploring the Japanese Tea Garden':fontcolor=white:fontsize=50:x=(w-text_w)/2:y=(h-text_h)/2:box=1:boxcolor=black@0.5:boxborderw=5[v0]; \
[1:v]scale=1280:720:force_original_aspect_ratio=decrease,pad=1280:720:(ow-iw)/2:(oh-ih)/2,setsar=1,zoompan=z='min(zoom+0.0015,1.5)':d=125,fade=t=in:st=0:d=1,fade=t=out:st=4:d=1,drawtext=text='Pizza with a view of the Golden Gate':fontcolor=white:fontsize=50:x=(w-text_w)/2:y=(h-text_h)/2:box=1:boxcolor=black@0.5:boxborderw=5[v1]; \
[2:v]scale=1280:720:force_original_aspect_ratio=decrease,pad=1280:720:(ow-iw)/2:(oh-ih)/2,setsar=1,zoompan=z='min(zoom+0.0015,1.5)':d=125,fade=t=in:st=0:d=1,fade=t=out:st=4:d=1,drawtext=text='Checking out the cool lighthouse lens!':fontcolor=white:fontsize=50:x=(w-text_w)/2:y=(h-text_h)/2:box=1:boxcolor=black@0.5:boxborderw=5[v2]; \
[3:v]scale=1280:720:force_original_aspect_ratio=decrease,pad=1280:720:(ow-iw)/2:(oh-ih)/2,setsar=1,zoompan=z='min(zoom+0.0015,1.5)':d=125,fade=t=in:st=0:d=1,fade=t=out:st=4:d=1,drawtext=text='Beach day selfie!':fontcolor=white:fontsize=50:x=(w-text_w)/2:y=(h-text_h)/2:box=1:boxcolor=black@0.5:boxborderw=5[v3]; \
[4:v]scale=1280:720:force_original_aspect_ratio=decrease,pad=1280:720:(ow-iw)/2:(oh-ih)/2,setsar=1,zoompan=z='min(zoom+0.0015,1.5)':d=125,fade=t=in:st=0:d=1,fade=t=out:st=4:d=1,drawtext=text='Homeward bound!':fontcolor=white:fontsize=50:x=(w-text_w)/2:y=(h-text_h)/2:box=1:boxcolor=black@0.5:boxborderw=5[v4]; \
[v0][v1][v2][v3][v4]concat=n=5:v=1:a=0,format=yuv420p[v]" \
-map "[v]" -map 5:a -c:v libx264 -c:a aac -shortest montage.mp4
```
