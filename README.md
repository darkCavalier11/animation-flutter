# animatioon in flutter
flutter animation works in three steps
1) defining the controller and animation properties. 
```
_arrowAnimationController = AnimationController(
    vsync: this,
    duration: Duration(milliseconds: 300),
);

_arrowAnimation =
    Tween(begin: 0.0, end: pi).animate(_arrowAnimationController);
```
the animation controller provide duration of the animation and acts like a hook that bind to widget that animation is intended. The animation is where we the animation of values. for Tween it has a begin and end property. by default it returns a linear transition value to its controller.

2) We wrap the widget need to animate in AnimatedBuilder, which takes a animation controller and a builder function. the animation controller is the hook that mentioned above, which provide values in for animation.

3) the builder function take context and a child. it returns a Transform widget. it maybe rotation, scale, translate etc.
```
AnimatedBuilder(
    animation: _arrowAnimationController,
    builder: (context, child) => Transform.rotate(
    angle: _arrowAnimation.value,
    child: IconButton(
        ...
```
the transform.rotate take here an angle which take value from animation that initialized before, which is dynamic and the widget rerenders for the duration and take the state from begin to end.

some built in animation that hide these complexities (https://flutter.dev/docs/development/ui/widgets/animation "Built in animation widget")

page transition can be done with custom page transitions.