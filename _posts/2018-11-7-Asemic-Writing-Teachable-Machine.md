---
layout: post
title: "Asemic Writing Teachable Machine"
categories: computationaltypo
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/TMpmqJIXQF0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
I combined assignments from Computational Approaches to Typography and Machine Learning for the Web. For this project, I made an asemic writing generator that responds to user-set gestures.

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/computationtypo/week2/ceciltouchon.jpg)

I was inspired by this work by Cecil Touchon. I wanted to experiment with writing the 'text' in a pleasing graphic layout.
I broke down the asemic text generation into 4 elements:
- writing strokes
- long writing strokes
- spaces
- new line and carriage return

Each of these actions correspond to a gesture that can be set by the user.
The image classification code is based off of this [ml5 example of
KNN Classification on Webcam Images with mobileNet](https://github.com/yining1023/machine-learning-for-the-web/tree/master/week2-ImageClassifier-KNN-Posenet/KNNClassification_Video).

[my github repo with code](https://github.com/jirrian/asemicWritingTeachableMachine)

Some outputs:
![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/computationtypo/week2/output1.png)
![!alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/computationtypo/week2/output2.png)
![!alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/computationtypo/week2/output3.png)
![!alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/computationtypo/week2/output4.png)
