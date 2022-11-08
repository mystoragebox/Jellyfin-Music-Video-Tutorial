# Jellyfin-Music-Video-Tutorial
Before you begin this is a slow process. This does not use any Jellyfin plugins. I will show you the way for manual input and organisation of the files and setup of Jellyfin for your Music Video library. You will need some software on your computer to make this work. These include:
- Musicbee (or any other music sorting program that can edit MP4 meta)
- ffmpeg
- Powertoys (optional, it makes changing many filenames really easy)
## Jellyfin Library Settings
You will only need to do this step once. I will only mention the settings that need to change for this to work, all other settings are at your descretion. Open Jellyfin and add a new media library;
1. Change the content type to ***Music Videos***
2. Select ***Prefer embedded titles over filenames***
3. Unselect all ***Metadata downloaders (Music Videos)***
4. Select **Never** from ***Automatically refresh metadata from the internet***
5. Select ***Save artwork into media folders*** (If you want to have sidecar files)
Thats it for setting Jellyfin.
## File and Folder Preperation
I have tested two ways of storing the files. The first way is to make Artist folders and the second is to make Various Artists folders. I'll start with the Artists folders. When setup correctly songs in artist folders can connect to your music collection.
### Adding an Artist folder
Create a new folder with the artist name in your music videos (root) folder. At this time you can save artist images and backgrounds the artist folder. These images are the files I found work with music videos.
- root\Artist 1
- root\Artist 1\logo.png
- root\Artist 1\folder.jpg
- root\Artist 1\banner.jpg
- root\Artist 1\backdrop1.jpg
You can have multiple backdrops. Use this naming convention so Jellyfin automatically uses the images.
#### Format your videos
**Make sure your video files are mp4 only.** If the format is not mp4 convert them quickly by following my converting guide below. Rename all your mp4 videos to have song name only (this is where powertoys can be handy). If you have multiple versions of a song follow Jellyfin naming conventions.
- root\Artist 1\song 1.mp4
- root\Artist 1\song 1 - Live.mp4
- root\Artist 1\song 2.mp4
