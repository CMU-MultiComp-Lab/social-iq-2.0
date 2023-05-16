---
layout: page
permalink: /challenge/
title: Social-IQ 2.0 Challenge @ ICCV 2023
description: At ICCV '23 in Paris, France
nav: false
nav_order: 5
social: true  # includes social icons at the bottom of the page
---

<!-- ![alt text paris](/assets/img/paris.jpg){: .banner-image} -->
<!-- ![alt text paris](/assets/img/paris2.jpg){: .banner-image} -->
![alt text paris](/social-iq-2.0/assets/img/paris2.jpg){: .banner-image}

The inaugural <b>Social-IQ Challenge</b> will be co-hosted with the [Artificial Social Intelligence Workshop](https://sites.google.com/view/asi-iccv-2023/home) at [ICCV '23](https://iccv2023.thecvf.com). This challenge welcomes paper submissions on the new Social-IQ 2.0 task, focused on multimodal VideoQA in socially-rich situations (1000+ videos, 6000+ questions, 24,0000+ answers). There are $1,200 in total prizes for challenge participants.

If you plan to participate, please fill out this [form](https://forms.gle/ZVTAvNunBQUa9ncJ6) with your email address so we can keep you up to date with any relevant updates about the challenge.

## Important Dates 📅
- [x] Challenge is released: <b>May 15</b>
- [ ] Challenge and paper submission sites open, test set released: <b> mid-June</b>
- [ ] Paper submissions and final challenge submissions due: <b>July 21</b>
- [ ] Acceptance decisions issued: <b>August 4</b>
- [ ] Camera ready paper due: <b>August 11</b>
- [ ] ICCV workshop: <b>October 2</b>

## Awards 🏆 and Prizes 💰
There will be over $1,200 in total prizes. We will give the following awards and may create additional awards as well.
- **Challenge Winner**: highest performing submission
- **Best Few-Shot Paper**: best paper in the Few-Shot Research Focus (described below)
- **Best Fusion and Reasoning Paper**: best paper in the Fusion and Reasoning Focus (described below)

## Research Focuses 🔍
In order to encourage diverse, innovative research into solving the Social-IQ 2.0 task, submissions will specify one of three research focuses.

### Few-Shot Focus 🎯
This focus is intended to encourage research into composing foundation models in a zero- or few-shot way, motivated by works such as [Socratic Models](https://socraticmodels.github.io/). As foundation models improve, we believe this is a very interesting area of research to explore in challenging domains such as artificial social intelligence. This focus is intended to be accessible to anyone with the ability to compose models zero-shot. It is ok to use API-accessed models such as ChatGPT and Bard.

We encourage you to compose models zero- or few-shot, and **expect that you will not perform any training** on Social-IQ 2.0 data.

### Fusion and Reasoning Focus 🧠
In this focus, we hope to foster approaches that make creative use of pretrained feature representations with relatively small amounts of training on top (e.g. a few hours on a single GPU).  The goal here is to encourage researchers to *combine* features that may not be immediately composable zero shot (e.g. latent vector representations instead of text). We encourage you to think about *which features you can extract* and *how you can fuse or reason over those features* cleverly, using relatively small amounts of training / fusion layers to combine feature representations.

For this focus, **we expect that the number of *learnable parameters* you train will be relatively low (<< 1e+9)**. An interesting paper to look at for inspiration on this focus is the [Neural State Machine](https://arxiv.org/pdf/1907.03950.pdf).

### Representation Learning Focus 🎛️
While research into few-shot and low-resource settings is important, we also want to encourage novel training procedures that scale to high resource settings. For this focus, you may use as much compute as you would like, provided (as with all challenge submissions) that you only use data in the Social-IQ 2.0 dataset release for your training. Please reach out to us if you intend to use specialized hardware such as TPU's, so we can ensure your code is reproducible. If you would like to use TPU's, we recommend applying for [this program from Google](https://sites.research.google/trc/about/); their generous support allowed us to run the MERLOT-Reserve baselines for this challenge. You may choose to research a purely self-supervised setting (e.g. continued pretraining + partially frozen finetuning, as in [this paper](https://arxiv.org/pdf/2208.01036.pdf)) or in a supervised setting such as MERLOT's finetuning results.

## Challenge Submissions 🏔️
You can use the validation data to evaluate your model's performance. Once you have found your best performing model, you will submit it to the online submission site to see your performance on the held-out test set. The submission site will be posted in mid-June. **You can only submit five times**, so use your submissions wisely!

You may use models pretrained on large corpora but **may not train on any additional data not included in the Social-IQ 2.0 dataset release**. Please do not do any additional training or adaptation on the test set.

## Paper Submissions 📤
For your submission to be considered for the challenge, **please submit a paper describing your approach in great detail, and share your github with the challenge organizers so they can ensure your results are reproducible.** Along with your paper and challenge submission, please let us know in the paper submission site which focus you would like your paper to be considered for using. We will release the paper submission site in June. Please format your papers according to [ICCV's submission guidelines](https://iccv2023.thecvf.com/submission.guidelines-361600-2-20-16.php). Papers can be up to 6 pages (with no cap on additional pages for references and appendices).

## Paper Decisions 🎉
Paper decisions will be based on four criteria:
1. The contribution / novelty of the approach
2. The reproducibility of the results
3. The clarity of the writing
4. The challenge performance (*with respect to the focus area* – i.e. performance of a zero-shot vs. high-resource training will be taken into consideration)

**Even if your approach does not have high performance, it can still be accepted if it is interesting, clearly described, and makes a valuable contribution to one of the three focus areas!** We are curious how you will compose models few-shot, what kinds of features you will extract and how you will reason and fuse over them, and how you will learn robust and generalizable representations.

In addition, we believe that negative results are important information for the community. In your submission, we would be interested in seeing as well what you tried that did not work, so future research can learn from your experiments. 

## The Social-IQ 2.0 Dataset
We provide scripts to download the videos and question / answer files that comprise the task. Videos are drawn from youtube videos in three categories: general youtube videos containing socially rich situations, youtube clips from movies, and clips containing socially rich situations in passenger vehicles.

The `siq2` folder looks like this:
```
siq2
├── audio
│   ├── mp3 # will contain mp3 files
│   └── wav # will contain wav files
├── download_all.py
├── frames
├── original_split.json # contains which video ids are in train/val/test splits for the different subsets: youtubeclips, movieclips, car clips
├── qa # contains question / answer labelled data; will contain unlabelled qa_test.json file when submission site is released
│   ├── qa_train.json
│   └── qa_val.json
├── requirements.txt
├── transcript # will contain .vtt transcript files
├── trims.json # contains start times for the videos; videos are 60 seconds long from that start second
└── video # will contain .mp4 video files
└── youtube_utils.py
```

To download the data, first install all required dependencies:
```
conda create -n siq2 python=3.8 -y && conda activate siq2
pip install -r requirements.txt
sudo apt update && sudo apt install ffmpeg # or however you need to install ffmpeg; varies per machine
```

Then, run the following to download the dataset
```
python siq2/download_all.py # this takes about 4 hours to download and 60GB to store the whole dataset. This goes down to 30GB if you run with flag --no_frames
```
This will update `siq2/current_split.json`, which will describe the videos in the train/val/test splits. There is also `siq2/original_split.json`, which contains all the video ID's we have questions and answers for, regardless of whether they're available at the moment on youtube or not.

**A finer point about the dataset**: Because you will download videos from youtube directly, the set of videos that constitute the dataset may change slightly between the release and conclusion of the challenge. **We will treat the "final" dataset as the set of videos downloaded from youtube one week before the challenge concludes**. If you download the dataset now and report your results later, that is ok – we will simply discard predictions made on test set videos that are no longer available when we determine final testing accuracies, and you will not be penalized for training or validating on videos that are no longer available by the end of the challenge.

## Questions
If you have any questions, please open a Github issue in our [repository](https://github.com/abwilf/Social-IQ-2.0-Challenge) or email awilf@cs.cmu.edu


## Team
The [Social-IQ 2.0 Challenge](https://cmu-multicomp-lab.github.io/social-iq-2.0/) was created by several members of the [MultiComp Lab](http://multicomp.cs.cmu.edu) at [CMU](https://www.cmu.edu). 

<table align="center">
  <tr>
     <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/alexwilf.jpg"/>
         <br/><a href="https://abwilf.github.io" style="text-align:center;">Alex Wilf</a>
     </td>
     <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/leena.jpg"/>
         <br/><a href="https://l-mathur.github.io" style="text-align:center;">Leena Mathur</a>
     </td>
     <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/youssouf.jpg"/>
         <br/><a href="https://gkebe.github.io" style="text-align:center;">Youssouf Kebe</a>
     </td>
    <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/paul.jpeg"/>
         <br/><a href="https://www.cs.cmu.edu/~pliang/" style="text-align:center;">Paul Liang</a>
     </td>

  </tr>
     <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/sheryl.jpg"/>
         <br/><a href="https://www.linkedin.com/in/sheryl-m-a26809188/" style="text-align:center;">Sheryl Mathew</a>
     </td>
     <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/claire.jpeg"/>
         <br/><a href="https://www.linkedin.com/in/claire-ko-053706190/" style="text-align:center;">Claire Ko</a>
     </td>
      <td>
        <img style="width: 150px" src="/social-iq-2.0/assets/img/lp.jpg"/>
         <br/><a href="https://www.cs.cmu.edu/~morency/" style="text-align:center;">Louis-Philippe Morency</a>
     </td>
</table>

<!-- Write your biography here. Tell the world about yourself. Link to your favorite [subreddit](http://reddit.com). You can put a picture in, too. The code is already in, just name your picture `prof_pic.jpg` and put it in the `img/` folder.

Put your address / P.O. box / other info right below your picture. You can also disable any of these elements by editing `profile` property of the YAML header of your `_pages/about.md`. Edit `_bibliography/papers.bib` and Jekyll will render your [publications page](/al-folio/publications/) automatically.

Link to your social media connections, too. This theme is set up to use [Font Awesome icons](http://fortawesome.github.io/Font-Awesome/) and [Academicons](https://jpswalsh.github.io/academicons/), like the ones below. Add your Facebook, Twitter, LinkedIn, Google Scholar, or just disable all of them. -->
