# Final Project


Qiyuan Wu, qiw103@ucsd.edu

Jiaye Wang, jiw609@ucsd.edu

Yifan Hou, yihou@ucsd.edu

(Your teammates' contact info, if appropriate)
![wink](https://img3.doubanio.com/view/photo/l/public/p2362920220.jpg)
## Abstract Proposal
For this project, we plan to convert a black and white classic clip from Modern Times by Charlie Chaplin into a colored video using the Deep Coloring neural network. We will also convert the background music and effects into a one with modern tune using MIDI analysis. We will revisit the neural network as well as style transfer knowledge we learned during latter part of the class. The inspiration of re-newing Chaplin's masterpiece is that its essence is still so relatable and relevant even after 83 years! The mundane, repeated and redundant work in pipeline resembles exactly the routine of most office and service workers of the current societies. Like the preface of the movie says, this is a story of industry, of individual enterprise - humanity crusading in the pursuit of happiness. This universal and eternal theme is what makes this movie an everlasting classic. The creative goal is to rejuvenate the classic by colorizing the clip intelligently and also innovating the background theme music to give it a more modern perception. We will present the work next Wednesday by going over the background of the movie, and then show the audience the original clip as well as the colorized clip. We will also walk through the procedures and rationale of the neural network model we have used.
 

## Project Report

Upload your project report (4 pages) as a pdf with your repository, following this template: [google docs](https://drive.google.com/open?id=1mgIxwX1VseLyeM9uPSv5GJQgRWNFqtBZ0GKE9d4Qxww).

## Model/Data
We used NoGAN to automatically color the videos. This is a new type of GAN training that has been developed to solve some key issues in the previous DeOldify model. It provides the benefits of GAN training while spending minimal time processing direct GAN training. Instead, most of the training time is spent pretraining the generator and critic separately with more straight-forward, fast and reliable conventional methods. A key inspiration here is that those more "conventional" methods generally get us most of the results we need, and that GANs can be used to close the gap on reality. During the very short amount of actual GAN training the generator not only gets the full realistic colorization capabilities that used to take days of progressively resized GAN training, but it also doesn't accrue nearly as much of the artifacts and other ugly baggage of GANs. In fact, we can pretty much eliminate glitches and artifacts almost entirely depending on our approach. This is a new and incredibly effective technique.

The video is supposed to be stable because NoGAN training is crucial to getting the kind of stable and colorful images seen in this iteration of DeOldify. NoGAN training combines the benefits of GAN training (wonderful colorization) while eliminating the nasty side effects (like flickering objects in video). In fact, videos are rendered using isolated image generation without any sort of temporal modeling tacked on. The process performs 30-60 minutes of the GAN portion of "NoGAN" training, using 1% to 3% of imagenet data once. Then, as with still image colorization, we "DeOldify" individual frames before rebuilding the video.

In addition to improved video stability, there is an interesting thing going on here worth mentioning. It turns out the models we run, even different ones and with different training structures, keep arriving at more or less the same solution. That's even the case for the colorization of things you may think would be arbitrary and unknowable, like the color of clothing, cars, and even special effects (as seen in "Metropolis").

Gansynth: audio timbre transformer.

- training data (or link to training data)
https://www.youtube.com/watch?v=nLlMbHatRwo
https://www.youtube.com/watch?v=6n9ESFJTnHs
https://www.youtube.com/watch?v=BZk-nIy9RY8

## Code

Your code for generating your project:
video colorize:
https://colab.research.google.com/drive/1W4c3nWjt0gskJLdA_OsI6fs80YhpjJH-#scrollTo=6Fz5ggA2Ukv4

GANSynth: https://magenta.tensorflow.org/gansynth
• colab: https://colab.research.google.com/notebooks/magenta/gansynth/gansynth_demo.ipynb

mp3 to midi transformer:

https://www.bearaudiotool.com/mp3-to-midi



## Results

We have uploaded the re-generated audio files here in the GitHub. We have uploaded the colorized videos at the Google drive: https://drive.google.com/drive/u/0/folders/0AM7acZ7fifDSUk9PVA

## Technical Notes
The colorization model steps are as follows: First train the generator in a conventional way by itself with just the feature loss. Next, generate images from that, and train the critic on distinguishing between those outputs and real images as a basic binary classifier. Finally, train the generator and critic together in a GAN setting (starting right at the target size of 192px in this case). Now for the weird part: All the useful GAN training here only takes place within a very small window of time. There's an inflection point where it appears the critic has transferred everything it can that is useful to the generator. Past this point, image quality oscillates between the best that you can get at the inflection point, or bad in a predictable way (orangish skin, overly red lips, etc). There appears to be no productive training after the inflection point. And this point lies within training on just 1% to 3% of the Imagenet Data! That amounts to about 30-60 minutes of training at 192px.

I(Jiaye Wang) extracted the background music of the movie, and pass the mp3 file music in to the mp3 to midi file transformer. 
It took me a long time to pass a wave audio file into the Gansynth, but then I realize I can just transfer the mp3 to midi.
The reason of me passing the mp3 to mid file transformer is because the Gansynth only accept the midi file as input.
I am slo attaching the link of the transformer below. In the Gansynth there are two ways to generate new audio.
They both switch the timbre of the original audio file to another timbre. 
I download both wave file for my teamates to choose. (generated_clip (1).wav;generated_clip (2).wav)
Here is a graph of the input midi file.
![Image of score](https://github.com/ucsd-ml-arts/ml-art-final-qiyuan_yifan_jiaye/blob/master/1.PNG)


![Image of score](https://github.com/ucsd-ml-arts/ml-art-final-qiyuan_yifan_jiaye/blob/master/2.PNG)

Here is the graph for the generated audio.

![Image of score](https://github.com/ucsd-ml-arts/ml-art-final-qiyuan_yifan_jiaye/blob/master/3.PNG)
- Does it run on some other (non-datahub) platform? (CoLab, etc.)

## Reference


GANSynth: https://magenta.tensorflow.org/gansynth
• colab: https://colab.research.google.com/notebooks/magenta/gansynth/gansynth_demo.ipynb


