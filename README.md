# uDrop-Generation

# Overview
This program analyzes the rate and sizes of droplets produced from a microfluidic droplet generator from a high-speed video. The user inputs the general regions of droplet activity in the video and then gets the drop generation rate and average size of each droplet for droplet generation videos.

A video tutorial explaining uDROP can be found at https://www.youtube.com/watch?v=sHpFGO3Jh3E&list=PLqdo5Two_cXhm-twPwbpeV4aCSFE85_in&index=2

If you use uDROP for your research, we would be thankful if you referred to it by citing the following publication: https://pubs.rsc.org/en/content/articlelanding/2019/lc/c8lc01253a/unauth#!divAbstract

The BibTex is included here:
```
@article{lashkaripour2019performance,
  title={Performance tuning of microfluidic flow-focusing droplet generators},
  author={Lashkaripour, Ali and Rodriguez, Christopher and Ortiz, Luis and Densmore, Douglas},
  journal={Lab on a Chip},
  year={2019},
  publisher={Royal Society of Chemistry}
}
```

# Installation
## Linux
* Open up a terminal
* Update your repositories with ```sudo apt-get update```
* Install the folowing dependencies:
  * ```sudo apt-get install python3-pip```
  * ```sudo apt-get install python3-tk```
  * ```sudo apt-get install ffmpeg```
  * ```sudo apt-get install libsm6 libxext```
* Install pipenv with the following command:
  * ```sudo python3 -m pip install pipenv```
* Clone this repo into your local files
  *  ```git clone https://github.com/CIDARLAB/uDrop-Generation.git```
* Navigate to the directory
  * ```cd uDrop-Generation/```
* Now, install the dependencies into the virtual environment:
  * ```pipenv shell```
  * ```pipenv install```
 
## Mac
* Open up a terminal
* Install the following dependencies:
  * ```sudo easy_install pip```
  * ```sudo brew install ffmpeg```
* Install pipenv with the following command:
  * ```sudo python3 -m pip install pipenv```
* Clone this repo into your local files
  *  ```git clone https://github.com/CIDARLAB/uDrop-Generation.git```
* Navigate to the directory
  * ```cd uDrop-Generation/```
* Now, install the dependencies into the virtual environment:
  * ```pipenv shell```
  * ```pipenv install```
 
# Quick-start
* cd to the locally cloned repository
* Type in ```pipenv shell``` to activate your local virtual environment (if you are not already in a shell
* Type in ```python3 uDROP_Generation.py /path/to/video.mpg```
* The GUI will appear
* Make a bounding box over one of the droplets
  * Click once to enter in where you want the upper left bounding box
  * Click again to enter in where you want the bottom right bounding box
* Enter in a known distance on the video
  * For instance, if you know the channel has a width of 200 micrometers, then you can click once on the top left of the channel, click again on the top right, then click once more on the bottom center to draw the length.
  * The distance is drawn like a triangle. You first click twice to draw the base and then click again to draw the height. We did this because it is more accurate than just clicking by hand
* Enter in the blue line distance
  * 200 if we are going off the previous exeample
* Enter in how many frames per second your video is
  * This is not the same thing as the video playback speed.
  * If you had 1000 frames that covered 2 seconds in real time, then the video is 500 frames per second (even if it was slowed down to play at 60 FPS normally).
* Wait for uDROP to finish processing
* Look at the final video and see if it is good
  * Read the wiki if you have problems
  * The sine wave should be relatively smooth, with the wave peaks corresponding to droplets whose full diameter can be seen.
* Exit out of the program
  * Your results should be in files in the folder in addition to appearing on the command line and on the GUI
  * Read the wiki for more information on these outputs.

# Advanced Options
Sometimes, especially with videos that contain droplets which are clear or tightly packed together, the applications may have a hard time identifying the droplets. In order to mitigate this issue, optional filters may be applied using the following command.
```python3 uDROP_Generation.py {/path/to/video.mpg} filter {filter_type}```
This will apply a filter to the video which will highlight the droplet edges before uDROP begins processing it.
Valid filter options are:
* truncate
* binary
* tozero

Example. ```python3 uDROP_Generation.py videos/clear.mpg filter {binary}```
will apply the binary filter to the video named 'clear.mpg'.
If {filter_type} is omitted, the application will default to the 'truncate' filter.

## Wiki
* [Inputs/Usage](https://github.com/CIDARLAB/droplet-image-processing/wiki/Generation-Inputs-and-Usage)
* [Outputs](https://github.com/CIDARLAB/droplet-image-processing/wiki/Generation-Outputs)
* [Run Analysis](https://github.com/CIDARLAB/droplet-image-processing/wiki/Generation-Run-Analysis)
* [How it Works](https://github.com/CIDARLAB/droplet-image-processing/wiki/Generation-Code-Explanation)

