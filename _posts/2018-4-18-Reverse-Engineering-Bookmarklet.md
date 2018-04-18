---
layout: post
title: "Reverse Engineering a Bookmarklet"
categories: hackingthebrowser
---
I tried to reverse engineer this [Page Zipper bookmarklet](http://www.printwhatyoulike.com/pagezipper). This is the original code I got from copy pasting the bookmarklet:
```
javascript:(function()%7Bif(window%5B%27pgzp%27%5D)%7B_pgzpToggleBookmarklet()%3B%7Delse%7Bwindow._page_zipper_is_bookmarklet%3Dtrue%3Bwindow._page_zipper%3Ddocument.createElement(%27script%27)%3Bwindow._page_zipper.type%3D%27text/javascript%27%3Bwindow._page_zipper.src%3D%27//www.printwhatyoulike.com/static/pagezipper/pagezipper_10.js%27%3Bdocument.getElementsByTagName(%27head%27)%5B0%5D.appendChild(window._page_zipper)%3B%7D%7D)()%3B
```

### Decode with the decoder ###
Using [this decoder](https://meyerweb.com/eric/tools/dencoder/):
```
javascript:(function(){if(window['pgzp']){_pgzpToggleBookmarklet();}else{window._page_zipper_is_bookmarklet=true;window._page_zipper=document.createElement('script');window._page_zipper.type='text/javascript';window._page_zipper.src='//www.printwhatyoulike.com/static/pagezipper/pagezipper_10.js';document.getElementsByTagName('head')[0].appendChild(window._page_zipper);}})();
```

### De-obfuscate with JS Nice ###
Using [JS Nice](http://jsnice.org/):
``` javascript
'use strict';
javascript: {
  (function() {
    if (window["pgzp"]) {
      _pgzpToggleBookmarklet();
    } else {
      /** @type {boolean} */
      window._page_zipper_is_bookmarklet = true;
      /** @type {!Element} */
      window._page_zipper = document.createElement("script");
      /** @type {string} */
      window._page_zipper.type = "text/javascript";
      /** @type {string} */
      window._page_zipper.src = "//www.printwhatyoulike.com/static/pagezipper/pagezipper_10.js";
      document.getElementsByTagName("head")[0].appendChild(window._page_zipper);
    }
  })();
}
;
```

### Analysis ###
When the bookmarlet is executed, the bookmarklet creates a script element that references the main PageZipper functionalities script and adds it to the head of the page. The script with the main functionalities is `www.printwhatyoulike.com/static/pagezipper/pagezipper_10.js`, [viewable here](http://www.printwhatyoulike.com/static/pagezipper/pagezipper_10.js). 
The check for `if (window["pgzp"])` is so that the bookmarklet doesn't execute again if it's already been executed on the page. If you click it while it's already running, it stops running (`_pgzpToggleBookmarklet()`).
This bookmarklet uses jQuery.

