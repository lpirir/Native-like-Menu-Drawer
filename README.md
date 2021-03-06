# Native-like Menu Drawer
Native-like menu implementation for angular mobile apps.
Build with hammer.js fot touch support

<p data-height="393" data-theme-id="8844" data-slug-hash="bdmVpM" data-default-tab="result" data-user="vincurekf" class='codepen'>See the Pen <a href='http://codepen.io/vincurekf/pen/bdmVpM/'>Native-like Menu Drawer</a> by Filip Vincůrek (<a href='http://codepen.io/vincurekf'>@vincurekf</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

## What is this for?
If you are developing application for android with phogep or ionic or other alternative,
this is exactly for you. 
I've been struggling with menu implementations, found some but never got the feel and usability i wanted. No touch support or slow/no animations, if there was animations, they mostly have lags.

With this menu you have touch support, slide open/close, toggle function and all with smooth hardware accelerated animations.

# Usage

Add **ng-nativeDrawer.js** and **hammer.js** to your project:
```
<script src="hammer.js"></script>
<script src="ng-nativeDrawer.js"></script>
```

**needed elements**
Add drawer, drawer dimm, swipe stripe and menu toggle button to your projects index.html (or what represents your index)
```
<!-- toggle icon for toggling menu -->
<a id="nav-toggle" class="menu-icon" href="#"><span></span></a>
<!-- stripe on the left of the screen to detect slide from side of the screen -->
<div id="swipe-stripe"></div>
<!-- body of the menu drawer -->
<div id="drawer" ng-click="drawer.hide()">
  <div id="topbar" class="drawer large">
    <img class="gravatar depth z1" src="http://placehold.it/150x150">
    <div class="username">
      <strong>John</strong><br>
      Doe
    </div>
  </div>
  <ul class="nav">
    <li><a href="#app">Overview</a></li>
    <li><a href="#settings">Settings</a></li>
    <div class="bottom">
      <li><a href="#settings">Settings</a></li>
    </div>
  </ul>
</div>
<!-- takes care of the overlay dimming -->
<div id="drawer-dimm" ng-click="drawer.hide(); drawer.togglePlus(true);"></div>
<!-- your part of the code, views etc.. -->
<ion-scroll id="view-content" zooming="false" direction="y">
  <div ng-view=""></div>
</div> 
```
So you have four elements:

```#drawer```: the main elements which is toggled

```#drawer-dimm```: dimms the background when drawer is shown

```#swipe-stripe```: small stripe to detect swipe from edge

and ```#view-content``` which is where you content belongs

## Functions
Drawer has some basic functions:

```init()```: initializes the drawer

```show()```: shows the drawer (slide in)

```hide()```: hides the drawer (slide out)

## Settings
You can set some options when initializing drawer with ```init()```:
```
options: {
  maxWidth: 300,
  marginTop: 0,
  speed: 0.2,
  animation: 'ease-out'
}
drawer.init( options );
```
Now you just need to initialize your drawer. In your main javascript file where you start your angulat app you need to call the drawer:
```
var exampleApp = angular.module('exampleApp', ['ionic', 'nativeDrawer']);

exampleApp.run(function($rootScope, $ionicPlatform, $nativeDrawer ) {

  $ionicPlatform.ready(function() {

    // Native-like Drawer is HERE! ---------------------------
    // the drawer initialization
    $rootScope.drawer = $nativeDrawer;
    // default options (all of them)
    var options = {
      maxWidth: 300,
      marginTop: 0,
      speed: 0.2,
      animation: 'ease-out'
    }
    // initialize with options
    $rootScope.drawer.init( options );
    // Done! -------------------------------------------------

  });
});
```

# Example

There is example in the example folder, based on ionic framework, with action button bonus to explore and use. You can checkout the example source code which is in the example folder ;)

I hope this will help you.
