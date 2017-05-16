# Link Bootstrap
Before Bootstrap can work, we need to load it into the browser.

Linking to Bootstrap is done the same way as linking to any other CSS stylesheet - point the href of a <link> tag to the URL where the stylesheet is stored. The Bootstrap library can be stored locally or accessed remotely.

LOCALLY

Bootstrap can be downloaded from getbootstrap and saved to a website's directory on your local machine.

The Bootstrap folder comes with additional code we will not cover in this lesson. To use the Bootstrap CSS classes, the bootstrap.css file must be moved to your project's directory and linked in the head of each HTML document. It should be linked before any other local CSS documents; we will discuss why in Exercise 10.

<link href="resources/bootstrap.css" type="text/css" rel="stylesheet" />
<link href="css/style.css" type="text/css" rel="stylesheet" />
In the example above, the bootstrap.css file is linked before the local stylesheet, style.css. The CSS rules in both bootstrap.css and style.css are responsible for styling elements in the HTML document.

REMOTELY

Bootstrap can be linked from a remote content delivery network (CDN). CDNs store content on a network of servers. The library is linked to the HTML document from a remote URL. The Bootstrap CDN URL is linked using the same format as a local file:

<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<link rel="stylesheet" type="text/css" href="style.css"/>
In the example above, the remote bootstrap.css file is linked above the link to the local stylesheet, style.css. The only difference between this example and the locally stored CSS file is that the href value is a remote URL instead of a local URL.

The integrity and crossorigin properties in the example above ensure that the file has not been replaced with malware.

The next logical question is, why use one over the other? Each method has its benefits and shortfalls.

Hosting bootstrap.css locally ensures the website will have access to it when downloaded by the browser. This is because the HTML, CSS, and Bootstrap files are all coming from the same location.
The Bootstrap CDN is quicker to set up, maintain, and is often faster for a user to load. Users who frequently visit sites that use Bootstrap, will usually have a copy of Bootstrap stored on their computer (this is called caching). When a library is cached, the user's browser won't have to request that file at all; it will already be downloaded, which makes loading the web page even faster.
It is important to understand the pros and cons of each linking strategy. For now, we recommend linking to the Bootstrap CDN.

## Containers
Although website appearances vary, most share an organizational structure: a navigation bar, a large landing section (called a jumbotron), and the main content of the site. With the Bootstrap library, each of these sections can be styled with built-in classes. Before applying these classes, each Bootstrap-styled section must have one of two Bootstrap classes assigned to it: container or container-fluid.

These classes are responsive and will adjust to a resizing viewport . There is one significant difference between these two classes:

container - sets a responsive, fixed-width container. For each of four viewport ranges, the container width will remain the same until it is narrowed or widened to the next range. The ranges include:

less than 768px — extra small

768-991px — small

992-1199px — medium

greater than 1199px — large
container-fluid - sets a responsive container that fills the viewport, regardless of the viewport's width.
<div class="container"></div>
<div class="container-fluid"></div>
In the example above, the first div is set to class container and the second div is set to class container-fluid. Each div will be responsive to the viewport width. While the container div is a fixed width over a specific range, the container-fluid div will fill the entire viewport.

## Navigation Bar
In the last exercise, we created Bootstrap container divs. In this exercise we will turn one of these containers into a navigation bar. The navbar and navbar-default classes provide the styling necessary to turn a container into a navigation bar.

<nav class="navbar navbar-default">
  <div class="container">
  </div>
</nav>
In the example above, a container element is wrapped in a nav element with classes navbar and navbar-default. The navbar class applies specific navigation bar styles to everything within its container. The navbar-default class contains a color scheme for the navigation bar.

There are two pieces of content we can add to a Bootstrap navigation bar: a header (navbar-header) and navigation links (nav and navbar-nav). Each of these Bootstrap classes must be wrapped inside of the container div, which is inside of the navbar navbar-x div.

<nav class="navbar navbar-default">
  <div class="container">
    <div class="navbar-header">
      <a class="navbar-brand" href="#">Project name</a>
    </div>
    <ul class="nav navbar-nav">
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </div>
</nav>
In the example above, the navbar wraps the container, which wraps the navbar-header and nav navbar-nav. The organization of the elements and classes provides the position, size, color-scheme, and format for all of the navigation bar's content. The navigation links inside of the nav navbar-nav div must always be anchor tags. These anchor tags are usually placed inside of an unordered list.

## NAVBAR POSITIONING
Bootstrap also makes it easy to position the navigation bar. Like any other HTML element, the default position of the navbar is where it is created in the flow of the HTML document (static positioning). Bootstrap however, has four navbar classes that are used to position the navigation bar:

navbar-fixed-top positions and fixes the navigation bar to the top of the viewport. The navigation bar remains visible, even when scrolling down the page.
navbar-fixed-bottom positions and fixes the navigation bar to the bottom of the viewport.
navbar-left positions an element in the navigation bar to the left side of the navbar.
navbar-right positions an element in the navigation bar to the right side of the navbar.
<nav class="navbar navbar-default navbar-fixed-top">
  <div class="container">
    <div class="navbar-header">
      <a class="navbar-brand" href="#">Project name</a>
    </div>
    <ul class="nav navbar-nav">
      <li class="active"><a href="#">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
  </div>
</nav>
In the example above, the navbar nav is styled with the navbar-fixed-top class. This class positions and fixes the contents of the navigation bar to the top of the viewport. It also sets the navigation bar to fill the width of the browser window.

## Grid system I
When creating a responsive website with Bootstrap, supporting content is often positioned with Bootstrap's built-in grid system. The grid system is useful for spacing content left to right across the viewport.

All content in a Bootstrap grid should be wrapped in a container or container-fluid div. Although columns can be added to containers without these classes, they provide the styling necessary to support the grid system.

The direct children of a grid container div should only be class row divs. Each of these Bootstrap row divs has 12 columns. The content of a row, usually more divs, can fill between one (col-md-1) and twelve (col-md-12) columns.

<div class="container">
  <!-- Start of the first row -->
  <div class="row">
    <div class="col-md-6">
      <p> Row 1, Cols 1-6 </p>
    </div>
    <div class="col-md-6">
      <p> Row 1, Cols 7-12 </p>
    </div>
  </div>
  <!-- Start of the second row -->
  <div class="row">
    <div class="col-md-4">
      <p> Row 2, Cols 1-4 </p>
    </div>
    <div class="col-md-4">
      <p> Row 2, Cols 5-8 </p>
    </div>
    <div class="col-md-4">
      <p> Row 2, Cols 9-12 </p>
    </div>
  </div>
</div>
In the example above, the container div has two rows. The first div in each row will start on the left side of the viewport. In the first row, each of the two column divs will take up half of the row. In the second row, each of the three column divs will take up one-third of the row. The grid will look something like Figure 1 in this image.

What would happen if we changed the code above so each of the three divs in the second row were five columns wide? The three divs would fill more than twelve columns.

<div class="container">
  <!-- Start of the first row -->
  <div class="row">
    <div class="col-md-6">
      <p> Row 1, Cols 1-6 </p>
    </div>
    <div class="col-md-6">
      <p> Row 1, Cols 7-12 </p>
    </div>
  </div>
  <!-- Start of the second row -->
  <div class="row">
    <div class="col-md-5">
      <p> Row 2, Cols 1-5 </p>
    </div>
    <div class="col-md-5">
      <p> Row 2, Cols 6-10 </p>
    </div>
    <div class="col-md-5">
      <p> Row 2, Cols 1-5 </p>
    </div>
  </div>
</div>
In the example above, the second row contains three divs, each five columns wide. The first two divs will fill five columns each. Because the third div would fill columns 11-15, it wraps and is displayed under the first two divs. The third div is still part of row two. The height of row two will increase to fit the wrapped div. If a third row were added to the container, the content would be displayed beneath this wrapped element. The grid will look something like Figure 2 in this image.

## Grid system II
Bootstrap has a set of classes designed specifically for creating responsive websites. This feature of the Bootstrap library is one of its most popular.

In the last exercise, we used the col-xs-x class to specify the width of a div, where x is a number between one and twelve. The xs in this class stands for extra small, and instructs the browser to use this class if the user is viewing the site on a viewport that is narrower than 768 pixels. In addition to md, there are three other class categories for common device width ranges:

col-xs-x - used when the width of the viewport is less than 768 pixels. This setting is for mobile phone display.
col-sm-x - used when the width of the viewport is between 768 pixels and 991 pixels. This setting is for tablet display.
col-md-x - used when the width of the viewport is between 992 pixels and 1199 pixels. This setting is for laptop display.
col-lg-x - used when the width of the viewport is greater than 1199 pixels. This setting is for larger screen displays.
If a Bootstrap column div has two of the above classes, Bootstrap will query the width of the viewport and display the content based on the number of columns assigned for the given browser width range.

<div class="container">
  <div class="row">
    <div class="col-xs-12 col-md-6">Row 1, Column 1</div>
    <div class="col-xs-12 col-md-6">Row 1, Column 2</div>
  </div>
</div>
In the example above, if the user were to view this HTML on a mobile device, "Row 1, Column 1" would be displayed above "Row 1, Column 2". If they were viewing this on a laptop, "Row 1, Column 1" and "Row 1, Column 2" would be displayed on the same line ( Figure ). The col-xs-12 class sets these divs to fill the width of the Bootstrap container at small screen widths. The col-md-6 class sets each div to fill half of its container when the width is above 992 pixels.

If a div's width is not defined for a specific range, the browser uses the nearest defined lower range.

If a user were to view the example above on a 900 pixel wide device (the sm size), the browser will display the content using the widths from the xs class. The content would be displayed on separate lines. If the window were larger than 992 pixels, however, the text would be displayed on the same line.

## Buttons
Bootstrap comes with a set of classes that are designed to make elements appear as buttons. These classes consist of btn- followed by a word that defines the class' color scheme.

The available button classes include: btn-default, btn-primary, btn-secondary, btn-success, btn-info, btn-warning, btn-danger, and btn-link.

The classes above create solid-colored buttons. Bootstrap also provides btn-outline-x, where x can be any of the button color scheme options above. The difference is that the background color of btn-outline-x buttons is white, while the outline and text matches the color scheme.

These classes are most often used to set the style for anchor tags.

<a class="btn btn-primary" href="www.codecademy.com">Home</a>
In the example above, an anchor tag is set to classes btn and btn-primary. The btn class is needed to add basic button styling. The btn-primary class sets the color scheme. This anchor tag will appear as a button with white text, a blue background, and a blue border.

Additional classes can be used to set the size of buttons. Buttons can be made extra small with btn-xs, small with btn-sm, or large with btn-lg.

<a class="btn btn-primary btn-sm" href="www.codecademy.com"> Home</a>
In the example above, the btn-sm class decreases the size of the button and text.

## Override styles
The Bootstrap library may feel limiting, with classes that have predefined fonts, color schemes, and positioning. Fortunately, any property in a Bootstrap class can be overwritten to create a custom appearance. This is done by loading a restyling CSS document after loading the Bootstrap library.

<!-- In the Head of the HTML Document -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="style.css">
In the example above, the browser will load the Bootstrap CSS document before style.css. All Bootstrap class properties can be overwritten by creating a rule with the Bootstrap selector in style.css — use Chrome DevTools to find out the exact selector name.

/* In style.css
.btn-primary {
  background-color: green;
}
In the example above, the background-color property of class btn-primary is overwritten in the style.css document. The normal color value for btn-primary is blue. However, any anchor tag with btn-primary in this HTML document will appear green, because the property was overwritten.

## Review
This lesson was an introduction to the Bootstrap CSS library. While there is a lot more depth to Bootstrap, you are ready to apply the concepts above to your own projects.

Let's review what you've learned:

The HTML document must be linked to a local or CDN hosted Bootstrap library.
The Bootstrap container and container-fluid classes are required for every section of a Bootstrap site.
The Bootstrap navbar class with navbar-default or navbar-inverse styles the appearance of the navigation bar.
The navigation bar can be fixed to the top or bottom of a webpage with the navbar-fixed-top or navbar-fixed-bottom class.
Elements in the navigation bar can be shifted to the left or right with the navbar-left and navbar-right classes.
The jumbotron class makes the content within its container appear more prominently.
The Bootstrap grid system requires a div of class row for each row in the grid.
The Bootstrap grid system requires content elements that take up anywhere from one to twelve columns.
The Bootstrap grid system can be used as a responsive layout framework by using a few of the following prefixes for each content element: xs, sm, md, or lg.
Bootstrap provides built-in button and button-sizing classes.
Built-in Bootstrap styles can be overwritten by setting property values with the same selectors in a local CSS document.
Take a look at the Bootstrap CSS documentation for additional features of the Bootstrap library.
