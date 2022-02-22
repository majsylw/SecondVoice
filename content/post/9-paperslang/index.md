---
title: Mysterious abbreviations in the literature on Sign Language 
subtitle: Little glossary for sign language researchers
summary: Get to know the phrases commonly used in SL papers and the meaning behind them


date: "2022-02-22T00:00:00Z"
lastmod: "2022-02-22T00:00:00Z"

featured: false
draft: false

image:

  caption: ''

  focal_point: "Center"
  placement: 2
  preview_only: false

authors:
- Alicja Kzremińska

tags:
- vocabulary
- papers
- slang
- sign language


---


Nowadays, Artificial Intelligence algorithms are present in daily life. Your friends' faces are recognized on the photo published on Facebook, you can experience a new world in the VR game and you can write an article in any language you want with the use of a Google translator. Why don't researchers use all these algorithms and create a solution to make life easier in more important cases? That's what they are already trying to do. Our team is one of such research groups. Our goal is to help Deaf people with daily online communication. We are aware that many researchers before us have already worked on this issue, so we started our investigations with a wide literature review.

Scientists, who are working on Sign Language, have a specific vocabulary and a lot of “well-known” keywords and shortcuts. It’s much easier to read papers knowing the meaning of these mysterious words so let’s explain them. Below we present the list of the most common technical phrases.

**Gloss** - spoken language word that matches the meaning of signs and, linguistically, manifests as a minimal lexical item.

**SLT - Sign Language Translation** - full translation of signs to a spoken language.

**(C)SLR - (Continuous) Sign Language Recognition** - sign language recognition and understanding (continuous - using not only single words but whole phrases), getting knowledge about the meaning of signs, essential for SLT.

**NLT - Neural Machine Translation** - an approach to translation with the use of a neural network to predict a sequence of words.

**CTC - Connectionist Temporal Classification** - sequence-to-sequence learning loss function; designed for tasks where we need alignment between sequences, but where that alignment is difficult.

**SLRT - Sign Language Recognition Transformer** - an encoder transformer model trained to predict sign gloss sequences; it takes spatial embeddings and learns spatio-temporal representations.

**SLTT - Sign Language Translation Transformer -** an autoregressive transformer decoder model, trained on output from SLRT to predict one word at a time to generate the corresponding spoken language sentence.

![Source: https://media.giphy.com/media/26FKSD8CaY4RB0uk0/giphy.gif](https://media.giphy.com/media/26FKSD8CaY4RB0uk0/giphy.gif) 



**WER - Word Error Rate -** metric to measure performance used in NLP solutions, e.g. in automatic speech recognition (ASR).

**BLEU - Bilingual Evaluation Understudy -** score of the effectiveness of translating one language into another one.

**HamNoSys** - **Hamburg Sign Language Notation System** - a system that describes sign language symbols; more details are available [here](https://www.hearai.pl/post/4-hamnosys/) and [here](https://www.hearai.pl/post/5-hamnosys2/) - these are very useful and descriptive tutorials about HamNoSys prepared by one of our team members. More posts about HamNoSys are still on our backlog list so stay tuned!

**Sign2Text** - full translation from the sign language into the spoken one, grammar and syntax are included.

**Sign2Gloss** - one to one translation from the single sign to the single gloss.

**Gloss2Text** - transforming raw glosses into meaningful sentences.

**Sign2(Gloss+Text)** - two-steps process, requires joint learning of sign language recognition and translation.

**Sign Segmentation** - extraction of the single sign from the series of continuous signs.

This, of course, is not a complete list of mysterious shortcuts that you may come across while browsing the specialist literature. It's just a fraction of our everyday language that we use in technical meetings. Soon we will reveal more details of our solution.

_Sources:_

_[1] Necati Cihan Camgoz, Oscar Koller, Simon Hadfield, Richard Bowden [“Sign Language Transformers: Joint End-to-end Sign Language Recognition and Translation”](https://openaccess.thecvf.com/content_CVPR_2020/papers/Camgoz_Sign_Language_Transformers_Joint_End-to-End_Sign_Language_Recognition_and_Translation_CVPR_2020_paper.pdf), CVPR 2020_

_[2] Alex Graves, Santiago Fernandez, Faustino Gomez, Jurgen Schmidhuber “[Connectionist Temporal Classification: Labelling Unsegmented Sequence Data with Recurrent Neural Networks](https://www.cs.toronto.edu/~graves/icml_2006.pdf)”, ICML 2006_

_Source of the gif: https://media.giphy.com/media/26FKSD8CaY4RB0uk0/giphy.gif_
