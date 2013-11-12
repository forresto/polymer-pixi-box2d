A simple game demo using Polymer custom elements as a scene graph with Pixi.js rendering and ASM Box2D.js for physics.

Sample Use
----------

```html
<!-- yaccel="294" (default 30 pixels per meter) is 9.8m/s^2 -->
<game-world id="world" width="800" height="600" friction="0" yaccel="294" xaccel="0" debug>
  <!-- 
  	Floor
    fixed: means that the floor will stay put 
    dom: render html instead of pixi webgl for this element 
    tile: tile the texture image 
    x & y: centered
  -->
  <game-entity id="floor" fixed x="400" y="600" width="600" height="50" restitution="0.5" 
  	texture="elements/bunny.png" tile dom padding="3"></game-entity>
  <!-- Main character -->
  <game-entity id="character4" circle x="400" y="400" width="50" height="50" xvelocity="0" yvelocity="0" rotation="0.05" texture="elements/bunny.png" movable>
    <!-- 
      This particular bunny is keyboard-controllable
      key: "w,up" = bind to w and up
        "shift+a" = key combination
        "up up down down" = key sequence
      attribute: if a function, call it with amount
        otherwise, setAttribute(attribute, amount) 
    -->
    <key-binding press="keydown" key="w,up"    attribute="impulseY" amount="-200"></key-binding>
    <key-binding press="keydown" key="s,down"  attribute="impulseY" amount="200"></key-binding>
    <key-binding press="keydown" key="a,left"  attribute="impulseX" amount="-200"></key-binding>
    <key-binding press="keydown" key="d,right" attribute="impulseX" amount="200"></key-binding>
  </game-entity>
</game-world>

```

Todo
----------

+ Composite bodies / polygons
+ Joints between entities
+ More demos
+ much breaking
+ wow