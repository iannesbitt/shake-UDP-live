# shake-UDP-live
A jupyter notebook designed to read and plot RaspberryShake UDP packets in real time

![Example Plot](img.gif)

## Disclaimer about script performance

This program is fairly processor-intensive, owing primarily to the large number of Fourier Transform calculations happening on each loop, and the fact that I'm not practiced at finding efficiencies in scripts. I haven't tested it on machines other than my own, but can envision people running into reduced performance problems in some cases. Even on my workstation the best I can do seems to be about 3.9 frames per second.

It may help to run this program without anything else open. (If you're on a Mac, this means actually quitting each open program in your dock, not just closing open windows.) You can speed up the program significantly by decreasing the number of seconds of data to display (i.e. 30 instead of 60). Inevitably you may end up with dropped packets simply because your processor can't keep up with the data rate.

If performance is an issue for you, please email me at ian dot nesbitt at gmail dot com and I will send you a less resource-hungry version (without the spectrogram). If you can find ways to make these calculations more efficient, please contribute to this project!

## Installing

The first couple of steps are different if you are trying to install on a desktop/laptop or a RaspberryPi. 

### Linux, Mac, and Windows desktop or laptop devices

1. The first step is to install [Anaconda](https://www.anaconda.com/download), which contains the Jupyter Notebook development environment. Depending on your level of comfort with the command line, this may or may not be a trivial task. There's a lot of stuff on Google about this, so I won't post anything here. Skip to step 2 below.

### Raspberry Pi with Raspbian OS

1. Great news! This script should be able to run on Raspberry Pi (tested and confirmed by TideMan). Follow the steps in [this instructable](https://www.instructables.com/id/Jupyter-Notebook-on-Raspberry-Pi/) to get Jupyter Notebook running on your RPi. Then skip down to step 2.

### Universal instructions (for all devices)

2. You will find the next step to being able to run this program in the [RaspberryShake documentation regarding UDP](https://manual.raspberryshake.org/udp.html#udp). Please refer there, then come back to this page. If you've already forwarded your UDP output to the machine you will run this script on, see step 3. If you've tried this and still need help, please feel free to post a question on the [community forum](https://groups.google.com/forum/#!forum/raspberryshake). I personally forwarded data from a remote RaspberryShake to port 18002 on my workstation, which is the way the `shake-UDP-live` script is set up to operate currently.

3. Once you've forwarded your UDP output, clone this repository. In a command prompt, type

```bash
git clone https://github.com/iannesbitt/shake-UDP-live
```
This command will cause Git to create a folder and download the contents of this repository into it.

4. Now go to a command prompt and type `jupyter-notebook`. A browser window will open. Using the Jupyter browser, navigate to the location on your computer where you cloned this repository and open the file named **shake_udp_live.ipynb**. Change the `port` variable to reflect the local port number to which your Shake is sending data. Then, click on the "Cell" menu and click on "Run All".

5. Enjoy beautiful live data!
