= CODAPPS: Using layouts and containers
Clément Levallois <levallois@em-lyon.com>
2018-01-15

last modified: {docdate}

:icons!:
:source-highlighter: rouge
:iconsfont:   font-awesome
:revnumber: 1.0
:example-caption!:


:title-logo-image: EMLyon_logo_corp.png[width="242" align="center"]

[.stretch]
image::EMLyon_logo_corp.png[width="242" align="center"]


==  'Escape' or 'o' to see all sides, F11 for full screen, 's' for speaker notes


==  1. Organizing things on screen: why is it an issue?

==  !
So far, we have learned how to put Labels and Buttons onto a Form.
But things are pretty disorganized on the screen.

See what happens when we create an empty Form, and put 5 Labels on it:

==  !
[.stretch]
image::Putting-5-Labels-on-an-empty-Form.png[align="center",title="Putting 5 Labels on an empty Form"]


==  !
I delete the title of the Form (which is "Form1" by default):

==  !
[.stretch]
image::Deleting-the-title-of-the-Form.png[align="center",title="Deleting the title of the Form"]


==  !
*Make sure to save the GUI Builder (File -> Save)*, you can keep it open. Then launch the preview of the app (big green arrow in NetBeans):

==  !
[.stretch]
image::layout-2.png[align="center",title="Previewing your app with the default layout"]


==  !
We see that *by default, the Components are organized from left to right on the screen*.
When there is no more space on the line, the next Components is placed on the line below.

==  !
What if we would have preferred to organize the Labels from top to bottom? Or in a mozaic?

==  !
The concepts of *Container* and *Layout* are there to provide you with the capacity to organize Components differently, exactly as you want.

These concepts are not specific to the plugin we use in NetBeans.
Pretty much every web or mobile framework use them, or their equivalent.

==  !
Before we start explaining what are Containers, Layouts and how they work, let's just answer a question you might have:

Why not just drag and drop Components where we want on the GUI Builder, and this is how the app will look like?

==  !
This is indeed tempting. But we must remember that our mobile app will be used on phones and even tablets that each have *different screen sizes and pixel resolutions*.

For this reason, the result we see in the GUI Builder would look different (and messy) on the screen on a small iPhone 3 and on a big Samsung from the latest generation.

==  !
Layouts and Containers have precisely been invented to solve this issue of placement of Components, in such a way that we can make sure the overall look of our app will remain stable across screen sizes and resolutions.

==  !
A little footnote: the developers of Codename One work hard at cracking this issue of making Layouts easier.

When you create a Form, you can have "AutoLayout" selected: this will smartly help you manage the layout.

==  !
But this is still an experimental feature so *do not select* Auto Layout when you create Forms:

==  !
[.stretch]
image::An-experimental-feature-to-make-layout-easier---but-dont-use-it-yet.png[align="center",title="An experimental feature to make layout easier - but dont use it yet"]



==  !
With these explanations made, we can discover how layouts and containers work. Let's start with layouts:

==  1. Discovering layouts and using them

==  !
A Layout is *a set of rules governing how Components are organized in a region of the screen*.

Codename One, the tool we use in this course, provides 7 different types of Layout.

==  !
==== a. The Flow Layout

==  !
You already now this one, because when we create a new Form, the "Flow Layout" is applied to it by default:

==  !
[.stretch]
image::Form-adopt-by-default-a-Flow-layout.png[align="center",title="Form adopt by default a Flow layout"]


==  !
The Flow Layout is easy to understand: when a Form is set to "Flow Layout", the Components it contains will be set from left to right, and then place on the next line when there is no more room on the screen, etc.

==  !
We also learned something there: *a Layout can be applied to some very specific Components: only those which can contain other Components.*

When you think of it it makes complete sense:

==  !
- it would be weird to apply a Layout to a Label: since a Label cannot contain anything, it would be nonsensical to organize it in a "Flow Layout" or another Layout.
- a Form is specialized in containing Components: so of course we can apply a Layout to it.

==  !
Let's review other useful layouts:

==  !
==== b. The Box Y Layout

==  !
This one does this:

- every Component will be organized on top of each other, *vertically* (along the Y axis, hence the name)
- every Component will take as much space as it can horizontally.

==  !
How to apply to the Form? Simply select the Form and then spot the icon managing Layout parameters:

==  !
[.stretch]
image::Applying-a-Box-Y-Layout-to-the-Form.png[align="center",title="Applying a Box Y Layout to the Form"]


==  !
Small digression here: if you remember, when you created the project in NetBeans, a Form had been created automatically with some lines of code.

We had to delete these lines of code to make our Form visible in the app.

Let's look again at what these lines of code where:

==  !
.MyApplication.java
[source,java]
----
public void start() {
    if(current != null){
        current.show();
        return;
    }
    Form hi = new Form("Hi World", BoxLayout.y()); <1>
    hi.add(new Label("Hi World"));
    hi.show();
}
----
<1> Even if we don't know how to code, this line of code starts to make sense: it creates a new Form, with title "Hi World" and with a Box Y Layout.

==  !
(end of the parenthesis and let's explore the next layout in the GUI Builder!)

==  !
==== c. The Box X Layout

==  !
This Layout is similar to the Box Y Layout, except that this time every Component will be placed horizontally from left to right (along the X axis), and *each Component will take as much space as it can on the vertical axis (this is a difference with the Flow layout):

==  !
[.stretch]
image::Applying-a-Box-X-Layout-to-the-Form.png[align="center",title="Applying a Box X Layout to the Form"]



==  !
==== d. The Grid Layout

==  !
We will examine last the Grid Layout, as the other layouts are more powerful but also quite complex, so out of scope for this intro course (you are of course free to explore them by yourself, https://www.codenameone.com/manual/basics.html#_flow_layout[looking at the documentation of the plugin here].)

==  !
The Grid Layout makes it possible to arrange Components on the screen as a grid (duh!), or tiles / mozaic / table if you prefer.

==  !
The logic is simple: you provide a number of columns and rows, and the space of the Form will be divided accordingly.
Each Component will occupy the space of a cell in this table.

==  !
For example: 3 rows and 3 columns? 9 cells. If you have less than 9 Components, some cells will remain empty:

==  !
[.stretch]
image::Applying-a-Grid-Layout-to-the-Form.png[align="center",title="Applying a Grid Layout to the Form"]


==  !
We leave here the different layouts and move on to the next tool / concept we need to organize the space on the screen exactly as we want it:

==  3. Containers: the tool to organize a Form in subspaces

==  !
We will introduce the notion of Containers by showing one limit of Forms and Layouts:

Layouts help us organize the space of the Form but... the whole Form gets impacted.

==  !
What if we prefer to have, say, the top of the Form organized as a Grid, and the bottom part of th Form organized with a Box Y Layout?

This is what Containers will help us achieve.

==  !
Containers are basically a way to group some Components together, so that a Layout can be applied specifically to them.

Creating several containers on a Form allows to have several layouts applied to different regions of a Form!

==  !
To illustrate: what if we want to have this kind of layout on our screen?

==  !
[.stretch]
image::Another-of-a-layout.png[align="center",title="Another of a layout"]


==  !
What we need is to


==  The end

==  !
Questions? Want to open a discussion on this lesson? Visit the forum https://github.com/seinecle/codapps/issues[here] (need a free Github account).

==  !
Find references for this lesson, and other lessons, https://seinecle.github.io/codapps/[here].

==  !
Licence: Creative Commons, https://creativecommons.org/licenses/by/4.0/legalcode[Attribution 4.0 International] (CC BY 4.0).
You are free to:

- copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material

=> for any purpose, even commercially.

==  !
image:round_portrait_mini_150.png[align="center", role="right"]
This course is designed by Clement Levallois.

Discover my other courses in data / tech for business: http://www.clementlevallois.net

Or get in touch via Twitter: https://www.twitter.com/seinecle[@seinecle]
pass:[    <!-- Start of StatCounter Code for Default Guide -->
    <script type="text/javascript">
        var sc_project = 11592657;
        var sc_invisible = 1;
        var sc_security = "11592657";
        var scJsHost = (("https:" == document.location.protocol) ?
            "https://secure." : "http://www.");
        document.write("<sc" + "ript type='text/javascript' src='" +
            scJsHost +
            "statcounter.com/counter/counter.js'></" + "script>");
    </script>
    <noscript><div class="statcounter"><a title="site stats"
    href="http://statcounter.com/" target="_blank"><img
    class="statcounter"
    src="//c.statcounter.com/11592657/0/11592657/1/" alt="site
    stats"></a></div></noscript>
    <!-- End of StatCounter Code for Default Guide -->]
