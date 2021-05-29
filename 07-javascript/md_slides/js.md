class: center, middle

## #1
# JavaScript and Dynamic Pages

---

# More Than HTML

- We've seen (the basics of) how you can define a page layout using HTML and CSS

  - Divs, headings, paragraphs, images

  - Styling to change the shape and appearance of those items

- But we haven't seen any *dynamic* elements. How would you build an interactive web page that changes based on a user's actions?

---

# More than HTML

- Let's take a highly-interactive site like Google Maps.

- What happens when we pull back its HTML to parse it?

---

# More than HTML

```python
import requests
from bs4 import BeautifulSoup

response = requests.get('https://maps.google.com')
response.status_code
```
```
200
```

---

# More than HTML

```python
bs = BeautifulSoup(response.content)
list(bs.html.body.children)
```
```
[' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">tick('b0');</script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">if (window.devicePixelRatio > 1){document.body.className += ' highres';}
 </script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">(function(){if(window.tactilecsi){window.tactilecsi.g={};window.tactilecsi.h=1;window.tactilecsi.setTimerName=function(d,a){d.name=a};var n=function(d,a,g){var b="";window.tactilecsi.srt&&(b+="&srt="+window.tactilecsi.srt,delete window.tactilecsi.srt);window.tactilecsi.pt&&(b+="&tbsrt="+window.tactilecsi.pt,delete window.tactilecsi.pt);try{window.external&&window.external.tran?b+="&tran="+window.external.tran:window.gtbExternal&&window.gtbExternal.tran?b+="&tran="+window.gtbExternal.tran():window.chrome&&window.chrome.csi&&
 (b+="&tran="+window.chrome.csi().tran)}catch(q){}var c=window.chrome;if(c&&(c=c.loadTimes)){c().wasFetchedViaSpdy&&(b+="&p=s");if(c().wasNpnNegotiated){b+="&npn=1";var e=c().npnNegotiatedProtocol;e&&(b+="&npnv="+(encodeURIComponent||escape)(e))}c().wasAlternateProtocolAvailable&&(b+="&apa=1")}if("undefined"!=typeof navigator&&navigator&&navigator.connection){c=navigator.connection;e=c.type;for(var f in c)if("type"!=f&&c[f]==e){b+="&conn="+f;break}}c=d.t;e=c.start;f=[];for(var h in c)if("start"!=h&&
 e){var k=d.t[h];var l=d.t.start;k&&l?(k-=l,k=Math.round(k)):k=void 0;f.push(h+"."+k)}delete c.start;if(a)for(var m in a)b+="&"+m+"="+a[m];(a=g)||(a="https:"==document.location.protocol?"https://csi.gstatic.com/csi":"http://csi.gstatic.com/csi");return d=[a,"?v=3","&s="+(window.tactilecsi.sn||"tactile")+"&action=",d.name,"",b,"&rt=",f.join(",")].join("")};window.tactilecsi.getReportUri=n;var p=function(d,a,g){d=n(d,a,g);if(!d)return"";a=new Image;var b=window.tactilecsi.h++;window.tactilecsi.g[b]=
 a;a.onload=a.onerror=function(){window.tactilecsi&&delete window.tactilecsi.g[b]};a.src=d;a=null;return d};window.tactilecsi.report=function(d,a,g){var b=document.visibilityState,c="visibilitychange";b||(b=document.webkitVisibilityState,c="webkitvisibilitychange");if("prerender"==b){var e=!1,f=function(){if(!e){a?a.prerender="1":a={prerender:"1"};if("prerender"==(document.visibilityState||document.webkitVisibilityState))var h=!1;else p(d,a,g),h=!0;h&&(e=!0,document.removeEventListener(c,f,!1))}};document.addEventListener(c,f,!1);return""}return p(d,a,g)}};}).call(this);</script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">tick('ms0');</script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==" src="/maps/_/js/k=maps.m.en.MKnG7pk9j0I.es5.O/m=sc2,per,mo,lp,ti,ds,stx,bom,b/am=N4A/rt=j/d=1/rs=ACT90oFMnFDbYGN5W0fKEmSJcQFZN0yQgQ"></script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">tick('ms1');</script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">tick('b1');</script>,
 ' ',
 <script nonce="J6BZe3qWhSTef2/hnZ2uVg==">tick('p1');</script>,
 ' ',
 <noscript> <div id="no-script"> <div class="no-script-message"> <div> When you have eliminated the <strong>JavaScript</strong>, whatever remains must be an empty page. </div> <a class="no-script-help-link" href="https://support.google.com/maps/?hl=en&amp;authuser=0&amp;p=no_javascript" target="_blank"> Enable JavaScript to see Google Maps. </a> </div> </div> </noscript>,
 ' ']
```

---

# More than HTML

- There are ... no elements except script tags

- Well, there is this last one, which at first feels almost like taunting:

```html
<noscript>
 <div id="no-script">
  <div class="no-script-message">
   <div>
    When you have eliminated the
    <strong>
     JavaScript
    </strong>
    , whatever remains must be an empty page.
   </div>
   <a class="no-script-help-link" href="https://support.google.com/maps/?hl=en&amp;authuser=0&amp;p=no_javascript" target="_blank">
    Enable JavaScript to see Google Maps.
   </a>
  </div>
 </div>
</noscript>
```

---

# More than HTML

- What's a `<noscript>` tag?

- w3schools.com: "The `<noscript>` tag defines an alternate content to be displayed to users that have disabled scripts in their browser or have a browser that doesn't support script."

- Google is telling us that we can't use the page without JavaScript.

```html
<noscript>
 <div id="no-script">
  <div class="no-script-message">
   <div>
    When you have eliminated the
    <strong>
     JavaScript
    </strong>
    , whatever remains must be an empty page.
   </div>
   <a class="no-script-help-link" href="https://support.google.com/maps/?hl=en&amp;authuser=0&amp;p=no_javascript" target="_blank">
*   Enable JavaScript to see Google Maps.
   </a>
  </div>
 </div>
</noscript>
```

---

# JavaScript

- JavaScript is a whole language designed specifically to be executed by browsers
  
  - Although it's evolved to be used in other places too

- Just like Python, JavaScript describes *actions*

  - In contrast to HTML, which just describes objects and layout

- JavaScript is often used to update the HTML of a page dynamically, based on some user action

- Sometimes it's also responsible for creating the HTML in the first place, as in Google Maps (there's no HTML at all until the JavaScript executes)

---

# JavaScript

- JavaScript is sent back within the HTML of a page, in `<script>` tags

- Here's one of the scripts from our Google Maps page:

```html
<script nonce="J6BZe3qWhSTef2/hnZ2uVg==">
  if (window.devicePixelRatio > 1){
    document.body.className += ' highres';
  }
</script>
```

- `document.body.className += ' highres';` changes the class of the `<body>` tag in the HTML code of the page -- conditionally! Pretty amazing.

---

# JavaScript

- Pretty much every site has at least *some* JavaScript in it -- even our Wikipedia page did

- But for many -- perhaps most --  sites, the important content is still defined in HTML that's sent back in the response

- For others though, there's no useful HTML to be pulled back for scraping until the JavaScript runs

  - Almost any site that completely changes its interface over time and as you interact with it is likely to be very JavaScript-driven

  - These sites are **bad news for scraping**
