# Dynamic Background Images Using Only CSS

Sometimes you can't get away from images. Even with a focus on designing for the web there are times when the design simply calls for an image based background. Thanks to the incredible array of different screen sizes and resolution, getting that background image to seamlessly flow across experiences can be quite difficult.

![Different screen dimension examples](intro.jpg)

While media queries can also be way to tackle the larger issue of image size, it can be harder to make the images completely fluid. Most solutions that I have seen for this issue involve some not-so-pretty javascript. This javascript finds the screen width on load and resizes the image accordingly. Usually the script will also recalculate each time the user resizes the browser window. 

<div class="demobtns">
  <a href="#">Demo</a> <a href="#">Download</a>
</div>

## Our Example

This example uses no javascript and relies on simple percentage based widths along with absolute positioning. This is by far the smallest code example I have ever used in a tutorial.

### HTML

    <body>
      <img class="bg" src="webbies.jpg" />
    </body>

Here we are putting an image into our markup. It simply needs to be a child of the element that will receive the background image. In our case we are scaling this to the size of the entire page; so it is just inside the <code><body></code> tag.

### CSS

    .bg {
      position: absolute;
        left: 0;
        top: 0;
      width: 100%;
    }

Here we are simply positioning the image absolutely. This removes it from the normal flow of the document so that it will not affect the positioning of other elements. Setting the left and top values anchor it to the (you guessed it) top left corner of the body. Finally, we set the width to 100%, causing the image to automatically scale to the full width of the parent element.

*Note: Fixed position also works but it isn't supported on iOS devices prior to iOS 5.*

### What To Watch

1\. When an element is positioned absolutely, the values set will be factored relative to the next parent element with either absolute or relative positioning applied. If none are found, it will climb up the DOM all the way back to the <code><html></code> element. So if you were using this technique to set the background on a specific div, that specific div would need to have an absolute or relative positionin applied to it.

2\. Be wary of how your page is most likely to be viewed. As seen in the demo, depending on the dimensions of the background image, the image can easily be too short or too narrow in certain experiences. Also, you wouldn't actually want to load a 2560x1600 image on a mobile device.

3\. Along with making sure your image is not too big, be careful that it is not too small. An extremely pixelated image as the page background can easily make a good design look bad.


## Before you pull out your semantic soapbox...

I am absolutely prudish about keeping my code clean and semantic. I understand that this is technically putting an element of style into your markup rather than keeping it within the CSS. Unfortunately, sometimes in real-world situations, the developers do not have all the power and compromises must be made. I personally much prefer this solution to the javascript solutions (which most likely would be injecting something into the DOM anyway).
