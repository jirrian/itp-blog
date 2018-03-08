---
layout: post
title: "Meditation #3: Social Media Birth Chart"
categories: electronicrituals
---

![alt text](https://raw.githubusercontent.com/jirrian/jirrian.github.io/master/images/electronicrituals/papermemorypapermeaningss.png)
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

#### API ####
[instagram API](https://www.instagram.com/developer/){:target="_blank"}

