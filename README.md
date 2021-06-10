# Intro

A Twine document to collaborate on the story for our IGD730 project.


# Editing

Windows: right-click on the HTML doc, and open with Twine.

# Dev notes

## Ken Burns effect

Examples:

https://codepen.io/hkfoster/pen/kechC
https://codepen.io/ibanez182/pen/LZPgrY
https://codepen.io/SaijoGeorge/pen/LxeGgY

### Outcomes

What did NOT work for the Ken Burns effect was

```
<<script>>
$(document).one(":passagedisplay", function (e) {
  var backgroundSpan = document.createElement("span");
  backgroundSpan.className += ' background';
  backgroundSpan.style.backgroundImage = 'url(https://example.org/image.png)';
  e.content.appendChild(backgroundSpan);
  e.content.classList.toggle('loaded');
});
<</script>>
```

but instead having:

```
<<script>>
$(document).one(":passagedisplay", function (e) {
  e.content.classList.toggle('loaded');
});
<</script>>

<span
  class="background"
  style="background-image: url(https://example.org/image.png"
  ></span>
```

Something about dynamically adding the SPAN tag didn't work.
