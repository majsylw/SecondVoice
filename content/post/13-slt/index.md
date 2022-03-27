---
title: Sign Language Transformer
subtitle: Usage of tranformers for Sign Language processing
summary: Read about Transormers, and our usage of the architecture for SL processing



date: "2022-03-26T00:00:00Z"
lastmod: "2022-03-26T00:00:00Z"

featured: false
draft: false

image:

  caption: ''

  focal_point: "Center"
  placement: 2
  preview_only: false

authors:
- Wiktor Filipiuk

tags:
- transformer
- slt
- hugging face
- sign language


---










## Transformer and its use-cases.

Transformer - type of neural network’s architecture that consists of encoder-decoder substructure implementing attention mechanism. Mainly used in solving NLP (Natural Language Processing) tasks.

Exemplary architecture (based on [“Attention Is All You Need”](https://arxiv.org/abs/1706.03762))




![](image5.png)
 

This architecture might be utilized in problems that require grasping the meaning of natural language in the form of single words as well as full sentences, such as:

- **Sequence Classification**, i.e. Sentiment Analysis:



![](image2.png)


- **Extractive Question Answering** - finding answers based on previously delivered information:



![](image9.png)


- **Language Modeling**

  - Masked Language Modeling - filling gaps in the text:



![](image1.png)


   - Causal Language Modeling - adding single word at the end of sentence:



![](image10.png)


- **Text Generation** - generating new text based on provided base-text:


![](image6.png)


- **Named Entity Recognition** - assigning an entity to each word in a sentence, based on previously defined set of entities:



![](image4.png)


- **Summarization** - describing long piece of text in a simpler form:



![](image3.png)


- **Translation** - translating one language into another:



![](image7.png)


## HuggingFace Repository

Currently one of the most popular libraries that provides both pretrained Transformers & multitude of NLP processing functions is [HuggingFace](https://huggingface.co/models).

	

In the piece of code shown below we can see how simple and intuitive is its interface:


```python:
from transformers import pipeline

# 1. Translate text from polish into english.
model_checkpoint = "Helsinki-NLP/opus-mt-pl-en"
translator = pipeline("translation", model=model_checkpoint)
translated_text = translator("Wszyscy lubią dinozaury, ponieważ")
print(translated_text)
# Console output:
#  [{'translation_text': 'Everyone likes dinosaurs because'}]


# 2. Generate additional text complementing base-text.
text_generator = pipeline("text-generation", model='gpt2')
generated_text = text_generator(translated_text[0]['translation_text'], max_length=8, do_sample=False)
print(generated_text)
# Console output:
#  [{'generated_text': "Everyone likes dinosaurs because they're so big"}]


# 3. Perform Sentiment Analysis on generated sentence.
sentiment_analyzer = pipeline("sentiment-analysis", model='distilbert-base-uncased-finetuned-sst-2-english')
sentiment = sentiment_analyzer(generated_text[0]['generated_text'])
print(sentiment)
# Console output:
#  [{'label': 'POSITIVE', 'score': 0.9986183643341064}]
```


## Sign Language Transformer.

Due to widespread use of Transformer architecture in various language tasks, HearAI team decided to make use of it in the project of Sign Language words recognition.

It must be noted that input data in this type of problem is slightly different as compared to usual NLP tasks. Namely, it consists of video frames which present people singing words with their hands & body.

Therefore sentence’s context must be detected from information provided by consecutive RGB frames. Tokenization step is omitted in such a pipeline.

However datapoint’s character makes it possible to use different input modalities, such as information on joint location in the space of signing person. Thus placement of the arms, hands, fingers in all 3 axis XYZ are being fed into Transformer.

As in the first step of the project we would like to detect words (aka glosses), we used only Encoder part of the architecture developed in the paper: ["Sign Language Transformers: Joint End-to-end Sign Language Recognition and Translation", 2020, N.C. Camgoz, O. Koller, et al.](https://arxiv.org/pdf/2003.13830.pdf)

Below we can see the entire architecture proposed by the authors.



![](image8.png)


## Summary

Due to its extensive and universal structure Transformer is being successfully applied in many different tasks requiring understanding of human language. As it was presented earlier, it might be also applied to different input modalities, leveraging it’s context-detection powers to understand sign language from video datapoints, as long as images are being fed in the proper order (image at time t+1 follows image from time t)

Additionally, ease of use of Transformers, due to existing repositories with pretrained models, encourages using them in well known NLP problems as well as extending their applicability to new areas where attention mechanism encapsulated within encoder-decoder structure might be utilized! :D

## Sources

**Publications:**

 - "Attention is All You Need." 2017, Vaswani A., Shazeer N. et al.

 - "Sign Language Transformers: Joint End-to-end Sign Language Recognition and Translation", 2020, N.C. Camgoz, O. Koller, et al.

**Details on Transformers’ architecture:**

	- https://machinelearningmastery.com/the-transformer-model/

	- http://jalammar.github.io/illustrated-transformer/

**Transformers repository:**

	- https://huggingface.co/
