---
title: Machine Learning Basics and the Philosophers of Old
author: Andrew Hetherington
date: '2020-06-06'
slug: ml-philosophers-of-old
categories:
  - Data Science
  - Machine Learning
tags:
description: 'They probably wouldn’t get it either'
---

![](/page/ml-philosophers-of-old_files/statue.jpeg)

**Socrates glances up from his Jupyter notebook** and gives you that look — you’ve gotten used to it by now. You’ve spent enough time hanging around the great philosophers of antiquity to know that you’re about to get schooled. *Again.*

“What do you mean you don’t understand machine learning?” he says, with a wry smile. “That’s exactly the point. I’ve told you before, it’s better to know that you know nothing\*.”

You lean back in your chair and sigh. You give the waitress a weak smile as she whisks away your coffee cup. “But Socrates,” you start. “All the online resources that I find are either chock-full of jargon or are way too simplistic for me to be able to see the point of any of it.”

Socrates takes a sip of his third pumpkin spice latte\*\* and pauses in thought for a moment. Eventually he returns his gaze to his laptop and starts tapping away again. “If only someone would write a blog about it.”

## The Basics

Machine learning is a complex field, but if you can tuck a few of the fundamentals away in your memory bank then you’ll have a much easier time understanding some of the higher-level resources and conversations that are out there. Today we’re going to address a handful of these unavoidable concepts.
What is Machine Learning again?

Machine learning is “the science (and art) of programming computers so they can learn from data” (A. Géron in his [2019 book](https://www.amazon.co.uk/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1492032646/ref=pd_lpo_14_t_0/257-3076774-3184456?_encoding=UTF8&pd_rd_i=1492032646&pd_rd_r=dfb4d6ef-830b-45b4-a51e-655f75eb07c5&pd_rd_w=2JphL&pd_rd_wg=NXcYK&pf_rd_p=7b8e3b03-1439-4489-abd4-4a138cf4eca6&pf_rd_r=WR7PA4BFNEHM2DCHCMYC&psc=1&refRID=WR7PA4BFNEHM2DCHCMYC)). This is a useful thing to teach computers. While human brains are incredibly sophisticated, there are a lot of tasks that computers are better at than us. One such task is the recognition of patterns across very large collections of data. If you can give a computer enough examples of what you want it to do, it can learn how to make its own decisions when you feed it new examples.

## That’s good, right?

Yes, very good! The computer can be orders of magnitude faster that humans at certain tasks — and often far more accurate, too. The task could be image recognition — labelling or classifying images based on the objects in them, or detecting abnormalities in medical scans. It could be transcribing or translating speech. It could be predicting the likelihood of a certain even occurring in the future, which might ordinarily require years of study and expert knowledge of a phenomenon. Machine learning saves time, money, and can generate new possibilities for businesses and society more widely with its superhuman performance.

## Supervised learning

Supervised learning is where the data you train a machine learning model on comes with labels of the outcome you want to computer to predict. For example, if you wanted to predict if a bank customer was going to default on a new loan, you could feed the machine learning model data on previous customers, *including whether they actually ended up defaulting or not*, in hope of it learning how to recognise risky customers. In this way, the learning process is “supervised” since the computer gets told which answer the data corresponds to.

## Unsupervised learning

In unsupervised learning, the training data for the model does not come with any labels. The computer is then asked to do one of several things — this could be to separate the data into groups of similar instances, to identify outliers (data points that are radically different from the rest — like a grey-bearded man in a toga in an otherwise normal Starbucks), or to highlight potential relations between input variables. Unsupervised learning might be used to flag up uncharacteristic and fraudulent-looking financial transactions. Or it might be used to investigate what kind of products people tend to buy together when shopping at an online store.

![](/page/ml-philosophers-of-old_files/KyIu6zI_Eq29kTeV1IPmXQ.jpeg)


## Reinforcement learning

Reinforcement learning is defined by an “agent” that can choose from several actions or outputs. This agent is given feedback as it makes choices and is rewarded for making “good” choices (by some definition that we specify in advance). The agent is initially catastrophically bad at its job, but will quickly get better as it collects more and more feedback on its actions. Reinforcement learning can be used to train manufacturing robots — for example, a mechanical arm on a production line. The robot arm is rewarded for performing the desired action — whether it’s moving a component from one place to another, or building a certain car part — and punished for irrelevant or negative actions (eg dropping things, making a mess, or becoming self-aware and attempting to destroy all humans. Bad robot).

## What’s all this I hear about Deep Learning?

Deep learning is a subfield of machine learning that concerns itself with models made up of so-called “artificial neural networks”. These are made up of layered algorithms that can progressively pick up on more and more sophisticated features within input data. For example, a low-level and unsophisticated feature of an image of a human face would be where the edges of the face are. A more sophisticated feature could be whether the person looks happy or sad — which isn’t as straightforward. These algorithms are made up of layers of “neurons” that are loosely analogous to those of the human brain, because given a certain input, some neurons in the model will activate and others won’t. The neurons then work together to come up with a collective decision about what the model should output.

Deep learning systems can be extremely complex, but they can also be extremely powerful. These architectures underpin Facebook’s automatic photo tagging feature, Google Translate, and even algorithms that can beat world-class players at games like Go — which only a few years ago was a feat thought to be out of the reach of our current technology.

## And what on Earth is NLP???

Natural language processing, abbreviated to NLP, is another subfield of machine learning that aims to design computer models capable of understanding human language and the intent behind it. NLP models may be designed and trained to simplify or summarise documents, to analyse the tone or sentiment of written text, to recognise and translate speech, or to predict the next word you want to type out on your phone keyboard. NLP is the collective name for the range of machine learning problems such as these, which may be supervised or unsupervised in nature.

## Conclusion

This has been a very quick introduction to some high-level machine learning concepts. It may still feel like an incomprehensibly vast field of study — and that’s because it is! Like many other disciplines, people dedicate their lives to extremely narrow areas of research within it and have only found more and more depth to explore.

But hopefully, the next time you open up an article about a recent development in machine learning, you will be able to recognise some of the key themes this time. And then maybe you can pick one or two more topics or terms that you don’t quite understand and do some research to try and get a grip on them. You may end up with more questions than answers — but that’s not necessarily a bad thing. If you can do that, then at least you will know what you don’t know.

Socrates would be proud.

\*Of course, there’s no record that Socrates himself actually said this.

\*\*Or that he liked pumpkin spice lattes, for that matter.

## More info and credits

**Andrew Hetherington** is an actuary-in-training and data enthusiast based in London, UK.

* Connect with me on [LinkedIn](https://www.linkedin.com/in/andrewmhetherington/).
* See what I’m tinkering with on [GitHub](https://github.com/andrewhetherington/python-projects).

Photos by [Zac Farmer](https://unsplash.com/@zacfarmerart?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) and [Rod Long](https://unsplash.com/@rodlong?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText).