---
title: Project summary
subtitle: What we have done and learned 
summary: Read about what we have accomplished over couple of months


date: "2022-05-27T00:00:00Z"
lastmod: "2022-05-27T00:00:00Z"

featured: false
draft: false

image:

  caption: ''

  focal_point: "Center"
  placement: 2
  preview_only: false

authors:
- Marta Plantykow
- Alicja Kwaśniewska

tags:
- stats
- hamnosys
- project
- sign language
- end


---


On April 5th 2022, after 5 months of hard work the HearAI project officially ended. 

During this period our team focused on 3 main goals, each of which was successfully fulfilled.

First of all, we have made an attempt to **tackle the problem of automatic sign language translation using the HamNoSys notation**. This activity was not only about creating a Machine Learning (ML) based pipeline but also required a lot of work on data! Both [the model](https://github.com/hearai/hearai) and [a comprehensive list of available datasets](https://github.com/hearai/sign-language-review) were published by the team on GitHub to share the knowledge and further accelerate research in this area.

By doing this, we have **contributed to the existing knowledge database** in two areas.

First of all, the conducted research has put some light on the idea of translating sign language from video to text using the HamNoSys notation. This field, at the time of starting the project, was not explored from a ML point of view. On our way to solve this difficult, multilabel problem, we have faced many challenges, such as lack of data and the problem domain previously unexplored by the team. We had to quickly learn and understand the completely new language to be able to prepare data, design models and analyze results.  Whole research will be summarized soon in an official article that at the time of writing this post is still in progress, but you can already see that we did quite well[ in a short clip](https://www.linkedin.com/posts/women-in-ai-poland_hai-haimovie-hai-activity-6931663561865736193-YDKN?utm_source=linkedin_share&utm_medium=member_desktop_web) done by the team using sign language.

The other significant contribution refers to the HamNoSys notation itself. As previously mentioned, at the time of the project, the HamNoSys usage in Machine Learning based solutions was not explored well. As verified by our experiments, the notation itself is complex and cannot be directly used for ML in its base form. During the project execution another open-source [GitHub ](https://github.com/hearai/parse-hamnosys)code repository, namely parser, was created. The main goal of the parser is to translate a label representing an SL gloss written in the HamNoSys format into a format that can be used for a DL-based classification. We used a decision tree to decompose the notation into numerical labels for the defined classes. The parser analyzes a series of symbols and matches each symbol with the class that describes it (while assigning to it an appropriate number). We believe that the tool developed by us during this project will help to accelerate many other studies in this area by simplifying the process of handling HamNoSys representations.

In addition, we also verified a possibility of applying various neural network architectures to the automatic sign language translation problem. The ML research is progressing at a warp speed, with dozens of new solutions proposed every month. Selection of the best architecture is quite challenging. However, as proved by our studies, similar results can be achieved regardless of the used neural network topology, as both 3DCNNs and Transformers led to similar performance. It turned out that data selection, preparation and cleaning has more effect on the result than the used topology, so more focus should be placed on data quality.

Besides the technical aspect of a whole project, we also aimed to spread the knowledge about the reality of a Deafs life. Our blog (along with social media) and the micro conference organized by us successfully **increased the public awareness about challenges encountered by the Deafs' community every day**.


![]()


What’s more, the project was a great **opportunity for networking**. The whole team met not only our great mentors, but also multiple partners, many conference attendants, and lecturers.  It has been proven again that **alone we can do so little, but together we can do so much.** We are sure that collaborations and friendships started during this project will last much longer! 



![]()




