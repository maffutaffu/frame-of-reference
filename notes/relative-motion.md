## Relative motion

### TitleScreen

say nothing 

### DemonstrationOfRelativeMotion

```python
# Adding number line
self.play(ShowCreation(number_line))
self.add(label)
self.wait()
```

To demonstrate relative motion, let's say that the red stationary observer is asked to describe the motion of a ball inside the car relative to a number line. The red observer is not moving with respect to that number line.

```python
# Adding stationary object
self.add(stationary_observer)
self.wait()
# adding car and positon label
self.play(ShowCreation(car))
self.play(ShowCreation(ball))
self.play(ShowCreation(position_label), ShowCreation(position_number))
self.wait()
```



On this car, the blue observer is also asked to observe the motion of the same ball. 

```python
# adding moving observer
self.add(moving_observer)
self.wait()
```



The car will start travelling at a constant velocity without acceleration.

>  TODO: animation: a box around the observer and the moving car. An arrow from the stationary observer to the moving observer 
>
> animation: and an arrow from the moving observer to the stationary observer, but with a big cross to indicate that the moving observer IS NOT allowed to use the reference frame of the stationary observer.

 ```python
# Playing animation
self.play(MoveAlongPath(car, moving_car_path), rate_func=linear, run_time=4)
self.wait()
 ```

Now, let's ask the two observers to describe the motion of the ball.

### StationaryPerspective

```python
# adding number line
self.play(ShowCreation(number_line))
self.add(label)
self.wait()
```

When we ask the stationary observer the motion of the ball, it will say that the ball has moved from the position -4 to the position of 7 on the number line.

```python
# adding ball, brace and the number for the ball's position
self.play(ShowCreation(ball), ShowCreation(brace_to_ball), ShowCreation(ball_position))
self.add(stationary_observer)
self.wait()
```



### MovingPerspectiveHideNumberLine

However, when we ask the observer in the moving car, it will say that the ball seems to be stationary relative to it. 

I'm going to be removing the number line because it is irrelevant to us for now.

```python
# adding number line
self.play(ShowCreation(number_line))
self.add(label)
self.wait()
# zooming in
self.play(self.camera_frame.animate.scale(0.5).move_to(ball))
# adding ball and observer
self.play(ShowCreation(ball))
self.add(moving_observer)
self.wait()
# moving camera
self.camera_frame.add_updater(lambda d: d.move_to(ball.get_center()))
# If you are reading this code, think about why I didn't need to animate the ball moving
# removing number line
self.remove(number_line)
self.wait(4)  # this is the amount of time that the movement would usually take
self.play(Restore(self.camera_frame))
self.wait()
```



### Confusion

> animation: the two observers are confused with question marks.

why is it that the two observers have different descriptions of the motions of the same object?



### ExplanationOfConflict 

Let's put a number line on the observer, this number line is used to describe the position of the object relative to the observer.

> animation: add everything to the scene and add the reference frame

The observer and the ball are travelling at a constant velocity. Therefore the ball appears stationary relative to the blue observer

> animation: the car moving to the right, but this time there will be a number line attached to the moving observer.

### WhichReferenceFrame
```
However, the conflict of the motion and position of the object still remains. What is the velocity of the object? Which reference frame should be used?

The answer is that which reference frame you use can be based off of context and convenience. For example, if you want to describe your displacement after taking a 15 minute walk,

would you use the surface of the Earth as a reference frame and say that your position has a 1000 meter change? 

or would you use the sun as a reference frame and say that your position has changed for approximately 27000 km?
```

You may be asking yourself which description of the velocity is correct. The answer is that both the stationary observer and the moving observer's descriptions can be used based on the context. Motion is relative, therefore both measurements can be useful based on practicality and the objects that we are observing.