# Final Project


Qiyuan Wu, qiw103@ucsd.edu

Jiaye Wang, jiw609@ucsd.edu

(Your teammates' contact info, if appropriate)

## Abstract Proposal
For this project, we plan to convert a black and white classic clip from Modern Times by Charlie Chaplin into a colored video using the Deep Coloring neural network. We will also convert the background music and effects into a one with modern tune using MIDI analysis. We will revisit the neural network as well as style transfer knowledge we learned during latter part of the class. The inspiration of re-newing Chaplin's masterpiece is that its essence is still so relatable and relevant even after 83 years! The mundane, repeated and redundant work in pipeline resembles exactly the routine of most office and service workers of the current societies. Like the preface of the movie says, this is a story of industry, of individual enterprise - humanity crusading in the pursuit of happiness. This universal and eternal theme is what makes this movie an everlasting classic. The creative goal is to rejuvenate the classic by colorizing the clip intelligently and also innovating the background theme music to give it a more modern perception. We will present the work next Wednesday by going over the background of the movie, and then show the audience the original clip as well as the colorized clip. We will also walk through the procedures and rationale of the neural network model we have used.
 

## Project Report

Upload your project report (4 pages) as a pdf with your repository, following this template: [google docs](https://drive.google.com/open?id=1mgIxwX1VseLyeM9uPSv5GJQgRWNFqtBZ0GKE9d4Qxww).

## Model/Data

Briefly describe the files that are included with your repository:
- trained models

Gansynth: audio timbre transformer.

- training data (or link to training data)

## Code

Your code for generating your project:
- Python: generative_code.py

GANSynth: https://magenta.tensorflow.org/gansynth
• colab: https://colab.research.google.com/notebooks/magenta/gansynth/gansynth_demo.ipynb

mp3 to midi transformer:

https://www.bearaudiotool.com/mp3-to-midi

- Jupyter notebooks: generative_code.ipynb

## Results

Documentation of your results in an appropriate format, both links to files and a brief description of their contents:
- What you include here will very much depend on the format of your final project
  - image files (`.jpg`, `.png` or whatever else is appropriate)
  - 3d models
  - movie files (uploaded to youtube or vimeo due to github file size limits)
  - audio files
  - ... some other form

## Technical Notes

Any implementation details or notes we need to repeat your work. 
- Does this code require other pip packages, software, etc?
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

References to any papers, techniques, repositories you used:
- Papers
- Repositories
GANSynth: https://magenta.tensorflow.org/gansynth
• colab: https://colab.research.google.com/notebooks/magenta/gansynth/gansynth_demo.ipynb

- Blog posts
