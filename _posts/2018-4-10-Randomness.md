---
layout: post
title: "Computer Generated Randomness"
categories: electronicrituals
---

I struggled to think of an idea for how to seed my random function. My first idea was to use MTA data on whether a train was late or not when [I read that trains are ontime only 58% of the time](https://www.nytimes.com/2018/03/19/nyregion/new-york-subways-on-time-performance-hits-new-low.html){:target="_blank"} which is almost like flipping a coin. However, I had trouble getting the data and I didn't want to spend the majority of the time figuring out MTA's api. I may use this for a future project. So I decided to implement psuedo-randomness using my local system time. I wanted to see how often and when it would feel like I'm cycling through the same values.

### Part 1 ###
<p data-height="265" data-theme-id="light" data-slug-hash="GxejYE" data-default-tab="js,result" data-user="jzhong" data-embed-version="2" data-pen-title="GxejYE" class="codepen">See the Pen <a href="https://codepen.io/jzhong/pen/GxejYE/">GxejYE</a> by Jillian (<a href="https://codepen.io/jzhong">@jzhong</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Above is a codepen with my function. The buttons let you get an example of what numbers would be generated depending on your needs. Below is the actual function that generates a number between 0 and 1.

```javascript
function randomNum(){
  var currentTime = new Date();
  var currentHours = currentTime.getHours();
  var currentMinutes = currentTime.getMinutes();
  var currentSeconds = currentTime.getSeconds();
  var currentMiliSeconds = currentTime.getMilliseconds();
  var timeVal = currentHours * currentMinutes * currentSeconds * currentMiliSeconds;
  
  var maxVal = 23 * 59 * 59 * 999;
  var stringNum = String(timeVal / maxVal);
  var editedNum = stringNum.slice(3,16);
  var finalNum = Number(editedNum) / 1e13;
 
  return finalNum;
}

```

### Part 2 ###
I decided to try using my custom random function to replace the javascript random() function in a bookmarklet I made for Hacking the Browser to see if I would perceive a difference in the behavior. 
Drag the link to your bookmarks bar and click it to start. Then click on any links on the browser page. After clicking a link, it should fly off in one of 8 directions that are randomly chosen.

<a href="javascript:!function(){function%20e(e){function%20t(){1==l%3Fo++:2==l%3F(o++,i++):3==l%3Fi++:4==l%3F(o--,i++):5==l%3Fo--:6==l%3F(o--,i--):7==l%3Fi--:(o++,i--),n.style.top=linkPos.top-window.scrollY+o+%22px%22,n.style.left=linkPos.left-window.scrollX+i+%22px%22}e.preventDefault();var%20n=this;n.style.position=%22fixed%22,linkPos=n.getBoundingClientRect();var%20o=0,i=0,l=(setInterval(t,5),Math.floor(8*Math.random())+1)}document.getElementsByTagName(%22body%22)[0].style.position=%22relative%22;for(var%20t=document.getElementsByTagName(%22a%22),n=0;n%3Ct.length;n++)t[n].addEventListener(%22click%22,e),t[n].addEventListener(%22click%22,function(){this.removeEventListener(%22click%22,e)})}();">Flying Links with Javascript random()</a>

<a href="javascript:!function(){function%20e(e){function%20n(){1==s%3Fo++:2==s%3F(o++,l++):3==s%3Fl++:4==s%3F(o--,l++):5==s%3Fo--:6==s%3F(o--,l--):7==s%3Fl--:(o++,l--),i.style.top=linkPos.top-window.scrollY+o+%22px%22,i.style.left=linkPos.left-window.scrollX+l+%22px%22}e.preventDefault();var%20i=this;i.style.position=%22fixed%22,linkPos=i.getBoundingClientRect();var%20o=0,l=0,s=(setInterval(n,5),Math.floor(8*t())+1)}function%20t(){var%20e=new%20Date,t=e.getHours(),n=e.getMinutes(),i=e.getSeconds(),o=e.getMilliseconds(),l=t*n*i*o,s=String(l/79982937),r=s.slice(3,16);return%20Number(r)/1e13}document.getElementsByTagName(%22body%22)[0].style.position=%22relative%22;for(var%20n=document.getElementsByTagName(%22a%22),i=0;i%3Cn.length;i++)n[i].addEventListener(%22click%22,e),n[i].addEventListener(%22click%22,function(){this.removeEventListener(%22click%22,e)})}();">Flying Links with custom random function</a>


