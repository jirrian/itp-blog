---
layout: post
title: "Meditation #3: Social Media Birth Chart"
categories: electronicrituals
---

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/electronicrituals/socialmediabirthchart/screenshot.png)
[Social Media Birth Chart](http://blog.jzhong.today/papermemorypapermeaning/){:target="_blank"}

#### Concept ####
I wanted to generate birth charts based on social media activity. I thought, maybe I could predict the personality of a person based on their social media. And I would do this by generating a birth chart for their account based on the location, time, and date the account was created. However, I could not get information on when an account is created from the instagram API. Instead, I opted to create a birth chart for each post based on when it was posted and the location tag. This is roughly answering the question: Where were the planets in relation to my last post on instagram when it was created?

#### How it works ####
I could generate a birth chart for each post a user has; however, to demonstrate the concept, I only generate one for the most recent.
The user has to log in to their instagram account. Since my instagram developer account is in Sandbox mode, only instagram accounts registered by me have permission to log in. If you log in with a non-registered account, you will get an error on login.

You can test with the public itp instagram account which I have registered.
username: public_itp
password: Public

I then feed the results from the API call to the [Astolabe website](https://alabe.com/){:target="_blank"} used in [Allison's random birth chart example](http://alpha.editor.p5js.org/full/rkn4XL_2x){:target="_blank"} after parsing the information to find month, day, hour, minute, latitude, and longitude.
If the post has no location tag, I enter the default as the latitude and longitude of New York. I set the timezone to UTC since the timestamp returned from instagram is a Unix timestamp.

#### Example ####
I signed into my instagram account and generated a birth chart for this post:
<blockquote class="instagram-media" data-instgrm-captioned data-instgrm-permalink="https://www.instagram.com/p/Bf1zr2oA4CY/" data-instgrm-version="8" style=" background:#FFF; border:0; border-radius:3px; box-shadow:0 0 1px 0 rgba(0,0,0,0.5),0 1px 10px 0 rgba(0,0,0,0.15); margin: 1px; max-width:658px; padding:0; width:99.375%; width:-webkit-calc(100% - 2px); width:calc(100% - 2px);"><div style="padding:8px;"> <div style=" background:#F8F8F8; line-height:0; margin-top:40px; padding:50.0% 0; text-align:center; width:100%;"> <div style=" background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACwAAAAsCAMAAAApWqozAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAMUExURczMzPf399fX1+bm5mzY9AMAAADiSURBVDjLvZXbEsMgCES5/P8/t9FuRVCRmU73JWlzosgSIIZURCjo/ad+EQJJB4Hv8BFt+IDpQoCx1wjOSBFhh2XssxEIYn3ulI/6MNReE07UIWJEv8UEOWDS88LY97kqyTliJKKtuYBbruAyVh5wOHiXmpi5we58Ek028czwyuQdLKPG1Bkb4NnM+VeAnfHqn1k4+GPT6uGQcvu2h2OVuIf/gWUFyy8OWEpdyZSa3aVCqpVoVvzZZ2VTnn2wU8qzVjDDetO90GSy9mVLqtgYSy231MxrY6I2gGqjrTY0L8fxCxfCBbhWrsYYAAAAAElFTkSuQmCC); display:block; height:44px; margin:0 auto -44px; position:relative; top:-22px; width:44px;"></div></div> <p style=" margin:8px 0 0 0; padding:0 4px;"> <a href="https://www.instagram.com/p/Bf1zr2oA4CY/" style=" color:#000; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px; text-decoration:none; word-wrap:break-word;" target="_blank">hi from the dystopian future</a></p> <p style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; line-height:17px; margin-bottom:0; margin-top:8px; overflow:hidden; padding:8px 0 7px; text-align:center; text-overflow:ellipsis; white-space:nowrap;">A post shared by <a href="https://www.instagram.com/queefape/" style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px;" target="_blank"> Jillian 🔔</a> (@queefape) on <time style=" font-family:Arial,sans-serif; font-size:14px; line-height:17px;" datetime="2018-03-03T00:20:51+00:00">Mar 2, 2018 at 4:20pm PST</time></p></div></blockquote> <script async defer src="//www.instagram.com/embed.js"></script>

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/electronicrituals/socialmediabirthchart/examplebirthchart.gif)
[Link to birth chart on astrolabe.com](https://alabe.com/cgi-bin/chart/astrobot.cgi?INPUT1=queefape&MONTH=3&DAY=3&YEAR=2018&HOUR=12&MINUTE=20&AMPM=AM&INPUT6=40.73061&INPUT7=-73.935242&INPUT8=UTC){:target="_blank"}

Main placements for my post:
Sun - Pisces
Moon - Virgo
Rising - Sagittarius

#### API ####
[instagram API](https://www.instagram.com/developer/){:target="_blank"}

