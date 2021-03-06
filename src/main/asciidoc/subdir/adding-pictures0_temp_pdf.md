= CODAPPS: Advanced styling
Clément Levallois <levallois@em-lyon.com>
2018-01-15

last modified: {docdate}

:icons!:
:source-highlighter: rouge
:iconsfont:   font-awesome
:revnumber: 1.0
:example-caption!:
:sourcedir: ../../../../main/java


:title-logo-image: EMLyon_logo_corp.png[width="242" align="center"]

image::EMLyon_logo_corp.png[width="242" align="center"]
{nbsp} +

//ST: 'Escape' or 'o' to see all sides, F11 for full screen, 's' for speaker notes


//ST: !
== 1. Importing a picture into the app

Before a picture can be shown on the screen of your app, you must add the picture to the files of your app.

Importing a picture in the files of the app should be done from the GUI Builder, in one click:

//ST: !
image::Importing-from-the-GUI-Builder---does-not-work-at-the-moment.png[align="center",title="Importing from the GUI Builder - does not work at the moment"]
{nbsp} +

//ST: !
But this simple way does not work at the moment (it will probably be fixed soon).

//ST: !
So the alternative is to go somewhere else: in a place that used to be important to create the app, but which is now rarely used, except for cases like this.

//ST: !
- in the files of your project in NetBeans, spot the file named "theme.res" and double click on it:

//ST: !
image::Clicking-on-the-file-theme.res.png[align="center",title="Clicking on the file theme.res"]
{nbsp} +

//ST: !
-> It launches a new window. Be patient, it takes a bit of time to open!

Here is how the new window should look:

//ST: !
image::A-new-window-opened.png[align="center",title="A new window opened"]
{nbsp} +

//ST: !
There, just go in the top menu, select 'Images' and choose "Add images":

//ST: !
image::Selecting-Add-Images.png[align="center",title="Selecting Add Images"]
{nbsp} +

//ST: !
Simply choose the image that you would like to insert in your app. Guidelines:

- choose an image in '.jpg' or '.png' format
- *choose a small sized image*: a file not bigger than 300kb.

//ST: !
Done! Save (File -> Save) before you close this window, as we don't need it anymore.

You are now ready to use this pic in your app. Let's see how to add it onto a Form:

== 2. Adding a picture to a Form

The general idea is very simple: place a Component onto the Form, then set the picture as the background of this Component.

Let's try this with a Label. Open the GUI Builder of the Form, then place a Label on the Form:

//ST: !
image::Dragging-a-Label-onto-the-Form.png[align="center",title="Dragging a Label onto the Form"]
{nbsp} +

//ST: !
If you have clicked on this little icon, you should now see many properties of the Label that you can modify:

//ST: !
image::Discovering-how-to-change-the-style-of-a-Label.png[align="center",title="Discovering how to change the style of a Label"]
{nbsp} +

//ST: !
So many properties that we can change! Feel free to explore them. For the moment, we want to add a picture:

//ST: !
- Click on the right of the line of 'Bg Image', where there are 3 dots.
- If you imported correctly your image in the previous step (see above), you should see your picture available.
- Select it
- Click on its name at the bottom of the menu to close the window.

//ST: !
You should now see your picture on the Form:

//ST: !
image::Resizing-and-fitting-the-picture.png[align="center",title="Resizing and fitting the picture"]
{nbsp} +

== 3. Setting a picture as the background of a Form

//ST: !
So, we have seen how to add a pic on the screen. But often we also want to set a background for the entire of the phone, like this:

image::Nexus_4-smaller.png[align="center",title="An example of an app with a colored background"]
{nbsp} +

//ST: !
In this case, we could create a Label and then resize it to take the entire space of the Form, but there is a better way:

//ST: !
We can simply set the picture we want to the background of the Form itself. In the following, I am using a picture by https://www.flickr.com/photos/zooboing/5405160553[user Patrick Hoesly on Flickr]:

//ST: !
image::green_background-smaller.png[align="center",title="a green background"]
{nbsp} +

//ST: !
Just like we have seen, we need first to import this picture through the file 'theme.res' (see the top of this lesson for how to).

Then, set this picture as the "Bg Image" of the Form:

//ST: !
image::Setting-an-image-as-the-background-of-the-Form.png[align="center",title="Setting an image as the background of the Form"]
{nbsp} +

//ST: !
To see the result, make sure to save the GUI Builder then launch the preview of the app (big green arrow in NetBeans.).

You should get something like:

//ST: !
image::background-preview-1.png[align="center",title="Background of the app - but with the top remaining blank"]
{nbsp} +

//ST: !
This is quite good but we see that some room on the top of the app is not covered, because it is reserved space for the title of the Form.

//ST: !
We can remove this white space on the top by adding two lines of code to the file 'MyApplication.java'.

In the file 'MyApplication.java', spot the lines that say:

//ST: !
[[anchor-2]]
.MyApplication.java
[source,java]
----
public void start() {
    if (current != null) {
        current.show();
        return;
    }
    Form1 myForm1 = new Form1();
    myForm1.show();
}
----

//ST: !
Just add two lines of code precisely like this:

//ST: !
[[anchor-2]]
.MyApplication.java
[source,java]
----
public void start() {
    if (current != null) {
        current.show();
        return;
    }
    Form1 myForm1 = new Form1();
    myForm1.getToolbar().setUIID("Container");
    myForm1.getToolbar().hideToolbar();
    myForm1.show();
}
----

//ST: !
Now, if you launch the preview, your background should nicely cover the entire space of your screen:

//ST: !
image::background-preview-2.png[align="center",title="Background of the app - covering the entire screen"]
{nbsp} +

//ST: !
Congratulations! You learned how to place a picture onto a Form, and how to set a picture as the background of your app. It will look great! 🎉🎉🎉


//ST: !
*This is the end of the second module. You should now be able to:*

//ST: !
1. understand what a Component is.
2. understand what an Action is.
3. understand what a Form is.

//ST: !
[start=4]
4. create a Form using simple lines of code.
5. create a Form using the Graphical User Interface (GUI).
6. understand what are the different panels of the GUI.

//ST: !
[start=7]
7. trigger with a couple lines of code the opening of the Form you created with the GUI.
8. create a Label
9. create a Button and attach an action to it.

//ST: !
[start=10]
10. add a picture to the files of your app through theme.res
11. add a picture onto a Form
12. set a picture as the background of a Form.

//ST: !
You are now well equipped to build apps with beautiful UI (user interface). Go and create something beautiful!

//ST: !
*In the next module, we are going to learn how test and release your app for Android an iPhones!*

== The end
//ST: The end

//ST: !
Questions? Want to open a discussion on this lesson? Visit the forum https://github.com/seinecle/codapps/issues[here] (need a free Github account).

//ST: !
Find references for this lesson, and other lessons, https://seinecle.github.io/codapps/[here].

//ST: !
Licence: Creative Commons, https://creativecommons.org/licenses/by/4.0/legalcode[Attribution 4.0 International] (CC BY 4.0).
You are free to:

- copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material

=> for any purpose, even commercially.

//ST: !
image:round_portrait_mini_150.png[align="center", role="right"]
This course is designed by Clement Levallois.

Discover my other courses in data / tech for business: http://www.clementlevallois.net

Or get in touch via Twitter: https://www.twitter.com/seinecle[@seinecle]
