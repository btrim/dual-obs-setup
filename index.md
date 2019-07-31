# OBS Setup to Replace AmarecTV

## Summary

This is for users who are using Amarec primarily for recording gameplay in its own separate video, while simultaneously streaming with webcam, layout, timer, etc.

If you're using Amarec solely for its deinterlacing features (e.g. when using gv-usb2, dazzle, or ezcap) and don't care about your recording having more content than just gameplay, this isn't necessarily for you.  However, you should be able to use OBS Studio to deinterlace without any issues, as far as I know.

## Requirements
 - [OBS Studio Portable](https://obsproject.com/download) 
   - Choose "Download Zip"
 - Your favorite streaming program that supports NDI.  I'm using [OBS Studio](https://obsproject.com/download).  This can be the install you have already.
 - [OBS NDI Plugin](https://obsproject.com/forum/resources/obs-ndi-newtek-ndi%E2%84%A2-integration-into-obs-studio.528/updates)
 - A Video capture source that works in OBS. (This is usually a capture card but could also be window, monitor, game capture, etc).
 
## Portable OBS Install

 1. Extract the OBS-Studio-x.y.z-Full-x64.zip that you downloaded into a folder on your system.  For my examples, I'll be using ``G:\obs-recording``
 2. Browse to ``g:\obs-recording\bin\64bit`` in Explorer.
 3. Find obs64.exe in this folder in Explorer
 4. Right-click obs64.exe and select "Create Shortcut"
 5. (Optional) Rename the shortcut to "obs-recording"
 6. Right-click "obs-recording" shortcut and select properties.
 7. In the "Target" field, add ``--portable`` such that it contains ``G:\obs_recording\bin\64bit\obs64.exe --portable``
 * ![Shortcut Properties Screenshot](/obs-recording-shortcut-properties.png)
 
When you launch OBS via this shortcut, the scenes and settings will now be stored within the G:\obs_recording folder.

### Install OBS-NDI Plugin into OBS portable

  1. Download the NDI Runtime and Windows ZIP version of the OBS-NDI plugin from [here](https://github.com/Palakis/obs-ndi/releases)
  2. Extract the ZIP into your portable OBS folder, e.g. ``G:\obs-recording``.
  3. Install the NDI™ 3.5+ Runtime.  Instructions indicate a reboot will be required.
  
## Portable OBS Configuration

I'll leave most of the configuration to you, but remember this is what will be used to record your gameplay video and audio.

The one special thing you need to do is to add a new filter to your scene (or to your video capture source)
  1. Add your video capture device source to OBS and configure it as required.  Make sure to send audio to out to stream.
  2. On either the scene or the video capture source, right-click and add a filter.
  3. Under "Effect Filters", add "Dedicated NDI™ Output"
     * In the NDI Name field, choose something meaningful.  Mine is named "Video feed"
  4. Configure recording as needed.   There is no need to setup streaming
     * Due to potential issues with CPU usage, using nvenc, qsync, or vce might be necessary.  Use a high bitrate.
     * Lots of people use amarec with lagarith.  high quality or lossless h264 is the easiest replacement
     * Make sure to set up your video settings (e.g. resolution and framerate).  Keep in mind you can record in any aspect ratio (e.g. 4:3 960x720)
 
 
## Main Streaming Application Configuration 

### OBS Studio
  1. Install or update OBS Studio (Or, if you're using a portable version for your main OBS, follow the portable OBS install above using a different destination folder.  Then skip to step 4)
  2. Download the OBS-NDI windows installer from here [here](https://github.com/Palakis/obs-ndi/releases)
  3. Run the installer to install the OBS-NDI plugin on your main OBS instance.
  4. Launch OBS Studio
  5. Disable your old source, if applicable
  6. Add a new NDI™ Source 
  7. Choose the name you used in the previous section.  It will have your computer's hostname in front of it.
 
### Other
   ``¯\_(ツ)_/¯``
