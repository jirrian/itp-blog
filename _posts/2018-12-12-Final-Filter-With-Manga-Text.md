---
layout: post
title: "Final: Filter with Manga Text"
categories: computationaltypo
---

![alt text](/images/computationtypo/final/withText.png)
I made a selfie filter that adjusts a photo with style transfer and poseNet. The filter is exaggerated and influenced by anime style, similar to filter apps like Meitu app.
This is a continuation of [my final for Machine Learning for the Web](http://blog.jzhong.today/mlforweb/Final-Anime-Filter/). I added options for users to add their own text overlays inspired by typesetting used in Shoujo manga.

#### Typesetting in Manga ####

I'm interested in the relationship between text and images in comics. For this project, I used conventions used in Shoujo manga (Japanese comics aimed for young girl audiences) because it is so nostalgic for me. Although originally, the text would be Japanese and thus the typesetting would be based on the Japanese language, there is now standards for manga translations to English. These are used by fan translation groups as well as official US print releases. I found [this reddit thread](https://www.reddit.com/r/manga/comments/60mi92/sl_typesetters_whats_your_font_template/) that has collected references to different fonts and typesetting conventions.
[A good manga translation typesetting guide](https://fallensyndicate.wordpress.com/typesetting-tutorial/)

#### Visual Inspiration ####

![alt text](/images/computationtypo/final/example.jpg)
I chose to focus on the white text bubbles and floating text that's used for sound effects and asides.

I used [Wild Words](http://fontsgeek.com/fonts/CC-Wild-Words-Roman) and [Augie](https://www.dafont.com/augie.font) fonts.

#### Demo ####

Users can type what they want to be in text bubbles or sound effects in comma separated strings. Users click on the canvas to add text bubbles. The sound effects are placed randomly based on points of eyes from PoseNet.
![alt text](/images/computationtypo/final/screenshot.png)

![alt text](/images/computationtypo/final/filtered.png)
![alt text](/images/computationtypo/final/withText.png)

![alt text](/images/computationtypo/final/withText2.png)

![alt text](/images/computationtypo/final/2peopleWithText.png)

#### To do ####
I want users to be able to upload their own photos and download the result.
I'm interested in if animating the text would add anything.
Also, the webpage needs to be cleaned up and made to look nicer.

[link to github repo](https://github.com/jirrian/anime_filter_with_text)

[try the demo here](http://jzhong.today/anime_filter_with_text/)
