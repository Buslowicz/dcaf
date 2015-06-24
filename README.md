# DCAF

**D**CAF **C**SS **A**nimation **F**ramework

DCAF is a CSS animation framework for more complex (though non-interactive) animations without the usage of javascript. 
It allows to use the queue of frames based on time instead of seconds (still supporting the % though). It is relatively 
easy to use, here is an example:

```
@keyframes element1 {
  @include set-time(0s);

  @include frame-after(1s) {
    opacity: 0;
  }
  @include frame-after(500ms, 2s) {
    opacity: 1;
  }
  @include frame-after(250ms) {
    opacity: 0;
  }
}

@keyframes element2 {
  @include frame-after(500ms) {
    opacity: 0;
  }
  @include frame-after(500ms, true) {
    opacity: 1;
  }
}
```

In the above example, `element1` will start animating after 1s from the beginning of the animation. After the start,
it will change opacity from 0 to 1 for 500ms and hold it (opacity: 1) for 2s. After that time, it will start changing
the opacity to 0 for 250ms. `element2` will start animating 500ms after the `element1` animation (last frame) has ended.
It will animate the opacity from 0 to 1 for 500ms, but this time it will keep it till the end of full animation.

**HEADS UP!**
If the second parameter of frame-after or frame-at is `true`, it has to be the last frame in the `keyframes` rule.

### More documentation coming soon :)
