<article class="post-220668 post type-post status-publish format-standard has-
post-thumbnail hentry category-design tag-css tag-flexbox tag-layouts
">
CSS floats and clears define web layout today. Based on principles derived from
centuries of print design, they’ve worked well enough — even if, strictly 
speaking, floats weren’t meant for that purpose. Neither were tables, but that 
didn’t stop us in the 1990s.

Nevertheless, the **future of web layout is bright**, thanks to [flexbox][1]
[1][2]. The CSS layout mechanism lets us arrange elements in a truly web-like
way. Some elements can be fixed, while others scroll. The order in which they 
appear can be independent of the source order. And everything can fit a range of
screen sizes, from widescreen TVs to smartphones — and even devices as yet 
unimagined.[Browser support is fantastic][3][2][4] (except *you-know-who*). Yep
, it’s a great time to jump into flexbox if you haven’t done so yet.

But changing our ways isn’t easy. **Flexbox has a dizzying array of features**

### The Flexbox Mindset [Link][5]  {#the-flexbox-mindset}

Flexbox requires a new way of thinking. Instead of arranging items in left-to-
right, top-to-bottom rows and columns, we arrange blocks on a line — two lines, 
in fact, a main axis and a cross axis, the first of which we’ll use today. Think
of the**main axis as a rope** along which boxes (divs or other HTML elements)
are strung. The metaphorical rope runs from one end of its container to the 
other, a taut and invisible axis. This leads to four interesting concepts.

#### Alignment [Link][6]  {#alignment}

First, we can slide the “boxes” to one side of the “rope” or the other
, center them or distribute them evenly. That means objects can stick to one 
side of a layout or the other — say, to the left or right edge of the screen, no
matter the screen’s width. Even distribution means they will adapt well to any 
size screen, which is ideal in our[multi-screen world][7][3][8].<figure>

![Illustration of boxes pushed to the left.][9]  
<figcaption>Flexbox allows designers to push HTML elements to either end of the
“rope.
”</figcaption></figure>
#### Direction [Link][10]  {#direction}

We can also **reverse** the string, so that boxes run in the opposite direction
, without editing the HTML. This is similar to the[sort-order technique][11]
[4][12] that lets us flip columns around — except the third trait takes that
a step further.<figure>

![Illustration of boxes pushed to the right.][13]  
<figcaption>Both the order and position of elements may be flipped.</figcaption
></figure>
#### Orientation [Link][14]  {#orientation}

Thirdly, we can turn the rope by 90 degrees to dangle from the top of its
container, instead of running from side to side. Media queries and flexbox’s 
ability make it possible to run items — say, a header, article and footer — down
a smartphone’s screen but left to right on a desktop computer. What used to be 
called rows can now run top to bottom or bottom to top with a dash of CSS.<
figure
>

![Illustration of boxes hanging from the top of a box.][15]  
<figcaption>The entire arrangement can turn 90 degrees, “hanging” from the
top of the container.</figcaption></figure>
#### Order [Link][16]  {#order}

Finally, we can control which boxes come first, second, third and so forth on
the rope**without editing the HTML**. This is huge. It means we can structure
an HTML document for, say,[SEO][17][5][18], [accessibility][19][6][20] or plain
ol
’ [semantics][21][7][22] — independent of layout. Want to center elements
vertically? No problem. Want navigation at the end of your HTML but at the 
beginning of your layout? Sure. Want to experiment with different layouts? It’s 
all in the CSS. And just like that, we’re already thinking in terms of content 
and devices, not rigid grids.<figure>

![Illustration of boxes in random order.][23]  
<figcaption>The exact order of elements can change with CSS — and without
changing the HTML.</figcaption></figure>
There’s more, but this covers the basics for now. To recap:

1.  Blocks are strung along an invisible line.
2.  We can push them to and fro along that line.
3.  We can reverse the line, thus reversing the boxes’ order.
4.  The line can turn 90 degrees.
5.  We can shuffle things along the line in any order we please, regardless of
    the HTML.
   

### Order [Link][16]  {#order}

Order is an important concept in flexbox. Let’s take a basic HTML document: A
typical blog post would include certain bits of information.

*   **header**  
    website title, description, search form (These frame the content and inform
    people where they are.
    )
*   **meta data**  
    author/publisher, date, topic(s) (These help people decide whether the
    content is relevant to their needs.
    )
*   **main content**  
    what the page is all about (the reason the page exists)
*   **supplemental content**  
    related information (teasers, links, “See also”)
*   **navigation**  
    links to elsewhere on the website (high-level topics)
*   **footer**  
    copyright, RSS, social media, newsletter registration

These elements are listed in order of what search engines or screen readers
might scan. Now, let’s dangle a “rope” from the top of a mobile device and 
reorder them to put content first.

1.  main content
2.  meta data
3.  supplemental content
4.  header
5.  navigation
6.  footer

Meanwhile, desktop computers would have a different view.

1.  header
2.  meta data
3.  main content
4.  supplemental content
5.  navigation
6.  footer

Wait, that’s not quite right. We want navigation at the top, and flexbox
makes that a snap.

It follows that you can also put “ropes” inside of boxes, and all of the
rules apply anew. But first, let’s talk about order. Here’s where things get 
tricky.

### Nesting Ropes And Boxes [Link][24]  {#nesting-ropes-and-boxes}

Each flexbox layout — each box — can contain another set of boxes strung
along their own rope. That rope can run from left to right or vice versa, from 
top to bottom or vice versa, and push objects to either end, center them or 
distribute them. And while that flexibility opens up many possibilities, it also
means we need to plan our layouts carefully.<figure>

![Illustration of boxes within a box.][25]  
<figcaption>Elements along a flexbox rope may, in turn, contain other flexbox
ropes.</figcaption></figure>
Let’s start with some content to understand why things get complicated; this
isn’t necessarily in order of layout (i.e. the order in which people see it). 
Imagine giving a presentation to an audience. You tell them what you’re going to
say, then you say it, and you wrap up with a summary of what you’ve said. Our 
hypothetical page follows a familiar structure:

*   header
*   the current message
*   message list
*   links to inbox(es), archive, etc.
*   footer

### Sketch A Design [Link][26]  {#sketch-a-design}

To keep things simple, we’ll work with a familiar layout.<figure>

![Illustration of an email app layout][27]  
<figcaption>A typical arrangement for an email app.</figcaption></figure>
There are two flexbox layouts here. The first has three boxes from top to
bottom. The second layout resides inside the middle box, from right to left.

The header and footer span the width of the viewport. The navigation fits in a
small column to the left, and the content area lets the user scroll when it 
contains more information than can be displayed. We could achieve this with a 
few floats and fixed positions, but flexbox gives us more options with less 
markup. Let’s take a look.

### Set Up The Document [Link][28]  {#set-up-the-document}

The outer container has only three sections, wrapped in a `.flex-container`
element:

    <body>
      <div class="flex-container">
        <header>…</header>
        <main class="flex-container">…</main>
        <footer>…</footer>
      </div>
    </body>
    

We call it `flex-container` to describe its purpose in a somewhat semantic way
. At least our CSS will make sense.

Inside the `main` element, we need three blocks:

    <main class="flex-container content">
      <article class="message">…</article>
      <div class="message-list">…</div>
      <nav class="mailbox-list">…</nav>
    </main>
    

This example uses `article` as an independent entity, 
[not in the magazine sense][29][8][30].

### Declare These Elements As Flexbox [Link][31]  {#declare-these-elements-as-
flexbox
}

We need to tell browsers that these elements will be, um, flexible.

    .flex-container,
    .flex-container header,
    .flex-container footer {
      display: -webkit-box;
      display: -moz-box;
      display: -ms-flexbox;
      display: -webkit-flex;
      display: flex;
    }
    

Note that this applies flexbox to the major containers, not the content.

### Add Some Dimensions [Link][32]  {#add-some-dimensions}

Based on the design sketch, we know that certain elements will have widths and
heights. The`body`’s header and footer, for example, will be long, thin
strips compared to the`main`’s tall, relatively narrow left-hand navigation
bars. The`article`’s content area fills the rest of the space. In the
interest of staying flexible regardless of screen size (and clarity in this 
tutorial), these areas won’t have fixed widths.

    .message {
      flex-basis: 70%;
    }
    .message-list {
      flex-basis: 15%;
    }
    .mailbox-list {
      flex-basis: 15%;
    }
    .flex-container header,
    .flex-container footer {
      width: 100%;
      height: 5rem;
    }

Here, `flex-basis` is like width — as long as the main axis is horizontal. If
we dangle the rope from the top, then`flex-basis` becomes height automatically
. Handy!

### Make The Main Section Scrollable [Link][33]  {#make-the-main-section-
scrollable
}

This one’s easy. Just add `overflow: scroll` to the `main` element to keep it
from overriding the header and footer.**Handy tip:** Try `overflow: auto` to
hide scroll bars (when they’re unnecessary
) [in most browsers][34][9][35].

    .message {
      flex-basis: 70%;
      overflow: scroll;
    }

### Test The Content [Link][36]  {#test-the-content}

At this point, the header’s form should float with a little margin, even when
the browser is resized. The content should flow well in browser windows of any 
size. And if a browser doesn’t support flexbox, then the page will turn into a 
content-first layout.

That’s important because [you-know-who doesn’t support flexbox][3][10][37] yet
. Every modern version does, however, so it’s a matter of when users update 
their software. So, where is flexbox supported?

Clicky has a graph of the [marketshare of assorted mobile browsers.][38]
[15][39]

What about older browsers? Solutions vary wildly depending on the layout you’
re trying to achieve, although we can derive a few tips.

The safest way to support flexbox-incapable browsers is to write CSS in the
order in which you want it to appear. Start by[thinking semantically][40]
[16][41]. Old versions of Internet Explorer will ignore flexbox properties —
thankfully, good ol
’ [conditional comments][42][17][43] enable us to apply floats and clears to
semantic layouts. Old versions of other browsers tend to give you mobile-
friendly layouts that stack content in a logical order. So flexbox can co-exist 
with floats,`display: table-cell` and positioning, so that smart browsers will
apply flexbox properties while legacy browsers will ignore them. Finally, if you
’re feeling experimental, then try[Flexie][44][18][45], which amends old
browsers with a JavaScript-based polyfill.

Give flexbox a go. While it offers many options, most — such as alignment
— come into play after you’ve settled on how elements are arranged. The central 
techniques, which we’ve covered here, are alignment, direction, orientation, 
order and nesting. We’ve found these to be critical in Foundation’s new layout 
framework: If you can wrap your head around alignment, direction, orientation 
and order, then you’re well on your way to a flexible future.
[Check out my demo][46][19][47] to see it in action (keep in mind that it’s
not responsive just yet
).

### Further Reading [Link][48]  {#further-reading}

To learn more about flexbox, check out the following:

*(da, ml, al)*

[↑ Back to top][49] [Tweet it][50][Share on Facebook][51]</article>

 [1]: https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes/

 [2]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#1
 [3]: http://caniuse.com/#search=flexbox

 [4]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#2

 [5]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#the-flexbox-mindset

 [6]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#alignment

 [7]: http://www.smashingmagazine.com/2011/01/12/guidelines-for-responsive-web-design/

 [8]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#3
 [9]: img/01-push-left-opt.png

 [10]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#direction
 [11]: http://foundation.zurb.com/docs/components/grid.html#source-ordering

 [12]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#4
 [13]: img/02-flip-horizontal-opt.png

 [14]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#orientation
 [15]: img/03-vertical-hang-opt.png

 [16]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#order
 [17]: http://www.smashingmagazine.com/2013/11/15/seo-for-responsive-websites/

 [18]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#5

 [19]: http://zurb.com/university/lessons/five-minutes-towards-an-accessible-page

 [20]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#6
 [21]: http://html5doctor.com/lets-talk-about-semantics/

 [22]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#7
 [23]: img/04-reordered-horizontal-opt.png

 [24]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#nesting-ropes-and-boxes
 [25]: img/05-nested-horizontal-opt.png

 [26]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#sketch-a-design
 [27]: img/06-gmail-diagram-opt.png

 [28]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#set-up-the-document

 [29]: http://html5doctor.com/lets-talk-about-semantics/#what-about-adding-more-elements

 [30]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#8

 [31]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#declare-these-elements-as-flexbox

 [32]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#add-some-dimensions

 [33]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#make-the-main-section-scrollable
 [34]: http://caniuse.com/#search=overflow

 [35]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#9

 [36]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#test-the-content

 [37]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#10
 [38]: https://clicky.com/marketshare/global/web-browsers/mobile/

 [39]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#15

 [40]: http://www.smashingmagazine.com/2013/08/20/semantic-css-with-intelligent-selectors/

 [41]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#16
 [42]: http://www.quirksmode.org/css/condcom.html

 [43]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#17
 [44]: http://flexiejs.com

 [45]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#18
 [46]: http://codepen.io/benthinkin/pen/wadabR

 [47]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#19

 [48]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#further-reading

 [49]: http://www.smashingmagazine.com/2015/08/flexible-future-for-web-design-with-flexbox/#top

 [50]: https://twitter.com/intent/tweet?original_referer=http%3A%2F%2Fwww.smashingmagazine.com%2F2015%2F08%2Fflexible-future-for-web-design-with-flexbox%2F&source=tweetbutton&text=Laying%20Out%20A%20Flexible%20Future%20For%20Web%20Design%20With%20Flexbox&url=http%3A%2F%2Fwww.smashingmagazine.com%2F2015%2F08%2Fflexible-future-for-web-design-with-flexbox%2F&via=smashingmag

 [51]: http://www.facebook.com/sharer/sharer.php?u=http%3A%2F%2Fwww.smashingmagazine.com%2F2015%2F08%2Fflexible-future-for-web-design-with-flexbox%2F