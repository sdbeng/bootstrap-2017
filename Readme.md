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

## 
