# Jellyfin-Music-Video-Tutorial
Before you begin this is a slow process. This does not use any Jellyfin plugins. Hopefully in the future Jellyfin can manage this itself but for now I will show you the way for manual input, organisation of the files as well as setup of your Music Video library. When Jellyfin can update the library automatically you will be ready with the file structure. For now you will need this software to help you organise:
- Musicbee (or any other music sorting program that can edit MP4 meta)
- ffmpeg
- Powertoys (optional, it makes changing many filenames really easy)
## Jellyfin Library Settings
You will only need to do this step once. I will mention the settings that need to change for this to work, all other settings are at your discretion. Open Jellyfin and add a new media library;
1. Change the content type to ***Music Videos***
2. Select ***Prefer embedded titles over filenames***
3. Unselect all ***Metadata downloaders (Music Videos)***
4. Select **Never** from ***Automatically refresh metadata from the internet***
5. Unselect ***Metadata Savers*** (you wont need it)
6. Select ***Save artwork into media folders*** (If you want to have sidecar files)

Thats it for setting Jellyfin.
## File and Folder Preperation
I have tested two ways of storing the files. The first way is to make Artist folders and the second is to make Various Artists folders. I'll start with the Artists folders. When setup correctly songs in artist folders can connect to your music collection.
### Adding an Artist folder
Create a new folder with the artist name in your music videos (root) folder. At this time you can save artist images and backgrounds to the artist folder. These images are the files I found work with music videos.
- root\Artist 1
- root\Artist 1\logo.png
- root\Artist 1\folder.jpg
- root\Artist 1\banner.jpg
- root\Artist 1\backdrop1.jpg


#### Format your videos
**Make sure your video files are mp4 only.** If the format is not mp4 convert them quickly by following my converting guide below. Rename all your mp4 videos to have the song name only (this is where powertoys can be handy). If you have multiple versions of a song follow Jellyfin naming conventions.
- root\Artist 1\song 1.mp4
- root\Artist 1\song 1 - Live.mp4
- root\Artist 1\song 2.mp4

Then drag all of the mp4's into Musicbee and fix the song titles if required. Select all and edit the metadata. Most of the metadata fields do not show on Jellyfin, some wont even get saved to mp4. The following fields will work;
1. Artist
2. Album (copy the album name exactly from your music collection)
3. Year
4. Genre

Go back to Jellyfin and refresh the Music Videos library and your artist folders will show with correct images. You will see the song name with the album below, clicking into the songs page you can click onto the album, artist or genre, they are linked to your music.

### Adding a Various Artists Folder
Create a new folder with whatever name you like in your Music Videos (root) folder. At this time you can save folder images in the folder.
- root\J Music
- root\J Music\logo.png
- root\J Music\folder.jpg
- root\J Music\banner.jpg
- root\J Music\backdrop1.jpg

#### Format your videos
**Make sure your video files are mp4 only.** If the format is not mp4 convert them quickly by following my converting guide below. Remane all your mp4 videos to have Artist - Song naming. If you have multiple versions of a song follow Jellyfin naming conventions.
- root\J Music\Artist - Song 1.mp4
- root\J Music\Artist - Song 1 - Live.mp4
- root\J Music\Artist - Song 2.mp4

Drag all of the mp4's into Musicbee. Most of the metadata fields do not show on Jellyfin, some wont even get saved to mp4. The following fields will work;
1. Title
2. Artist
3. Album (Type the Artist here unless you have a corresponding CD in your collection)
4. Year
5. Genre

Go back to Jellyfin and refresh the Music Videos library and your artist folders will show with correct images. You will see the song name with the artist below, clicking into the songs page you can click onto the artist or genre, they are linked to your music.

## Converting Files
If you have video files that are not mp4's you will need to convert them. **You will need ffmpeg and command line for this next part.** I don't have a comprehensive list of files but I will show a few common types. Have all the files you need to convert in one folder. Click in the address bar and type cmd to bring up command prompt. I have some commands below I use most.

Convert MKV with no conversion of video or audio
> for /R %f IN (*.mkv) DO ffmpeg -i "%f" -c copy "%~nf.mp4"

Convert M4V with no conversion of video or audio
> for /R %f IN (*.m4v) DO ffmpeg -i "%f" -c copy "%~nf.mp4"

A common problem I encountered was the audio track could not be contained in mp4, use the following to convert to 320kb audio.
> for /R %f IN (*.mkv) DO ffmpeg -i "%f" -acodec mp2 -b:a 320k  -vcodec copy "%~nf.mp4"

