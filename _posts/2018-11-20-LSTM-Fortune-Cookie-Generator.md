---
layout: post
title: "Training LSTM: Fortune Cookie Fortune Generator"
categories: mlforweb
---

I wanted to see if I could generate new fortune cookie fortunes. I [trained a LSTM network](https://github.com/ml5js/training-lstm) on [this dataset of fortunes](https://github.com/bmc/fortunes). The dataset is rather small (around 2,800 quotes). I chose to try the LSTM network this week because I didn't get a chance to on the first week.

The final results are not that readable/understandable. I think to get more fortune cookie-like results, I should clean the dataset and get rid of unnecessary seperator characters (%) and remove the names of who is attributed to each quote.

[try it here](http://blog.jzhong.today/LSTMFortuneCookieGenerator/)
[link to github repo](https://github.com/jirrian/LSTMFortuneCookieGenerator)
