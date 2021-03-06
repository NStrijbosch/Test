
!!! info
     LEGO has published official docs on the hub-module: [https://lego.github.io/MINDSTORMS-Robot-Inventor-hub-API/](https://lego.github.io/MINDSTORMS-Robot-Inventor-hub-API/)


The display class controls all functions linked to the display. It can be used via `hub.display`. For more details see the examples below.

## show() (Image)

`hub.display.show(image)`

Show an image on the display.

__Parameters:__

*  [image](data_types.md#image) image. See [image](data_types.md#image) for all build in images and the [Image](image.md) class on how to create a custom image.

__Sample code:__

``` python
from hub import display, Image

display.show(Image.HAPPY)

```

## show() (Animation)

`hub.display.show(animation,delay=100, wait=False, loop=False, clear=False, fade=0)`

__Parameters:__

*  animation [list](data_types.md#list). List of [images](data_types.md#image), see, [images](data_types.md#image) for all build in images and the [Image](image.md) class on how to create a custom image.
*  delay ([int](data_types.md#int)). Delay between images in milliseconds
*  wait ([bool](data_types.md#bool)). `True`: Let the remainder of the program wait until animation stops; `False`: animation is played in the background
*  loop ([bool](data_types.md#bool)). `True`: after all images are display start with from the beginning; `False`: show all images only one time. 
*  clear ([bool](data_types.md#bool)). `True`: clear screen after animation; `False`: leave last image visible on screen.
*  fade ([int](data_types.md#int)). Transition effect between frames, value in range 0,...,6

__Sample code:__

``` python
from hub import Image, display

image1 = Image("99900:90900:99900:00000:00000")
image2 = image1.shift_right(1)
image3 = image1.shift_right(2)
image4 = image2

animation = [image1,image2,image3,image4]

display.show(animation, delay=100, wait=True, loop=True, clear=True)
```

## clear()

`display.clear()`

Set the light intensity of all pixels to 0. 

__Sample code:__

``` python
from hub import display, Image
from utime import sleep_ms

display.show(Image.HAPPY)
sleep_ms(1000)
display.clear()
```

## pixel()

`display.pixel(x, y, brightness)`

__Parameters:__

*  x ([int](data_types.md#int)): x coordinate: value between 0 and 4
*  y ([int](data_types.md#int)): y coordinate: value between 0 and 4
*  brightness ([int](data_types.md#int)): brightness: value between 0 and 9

__Sample code:__

``` python
from hub import display

display.clear()
display.pixel(0,0,9)  #Top left corner
```

## rotate()

`display.rotate(angle)`

Change the orientation of the display. 

!!! warning
    Keep in mind this rotation is not reset at the start of each program. 



!!! danger
    Not available in latest SPIKE 1.3.3 firmware?

__Parameters:__

*  angle in degrees ([int](data_types.md#int): value of either 0, 90, 180, or 270

__Sample code:__

``` python
from hub import display, Image

display.show(Image.HAPPY)

display.rotate(90)
```

## align()

`hub.display.align(direction)`

Set the orientation of display.

!!! info
     values of direction are not intuitive, there does not seem to be a relation between the direction and avilable [constants](data_types.md#constants).  

__Parameters:__

*  direction [int](data_types.md#int): value could be  
   1: default  
   2: 90 degrees clockwise with respect to default  
   4: 180 degrees with respect to default  
   5: 90 degrees counter clockwise with respect to default

!!! info
    Difference between rotate() and align(): align() is absolute rotation, rotate() is relative rotation to current orientation of display. 

__Sample code:__

``` python
from hub import display, Image

display.show(Image.HAPPY)

display.align(4)
```

## invert()

`display.invert(inv)`

Invert the brightness of all pixels: 9 -> 0, 8 -> 1, ...

__Parameters:__

*  inv [bool](data_types.md#bool): `True`: invert led brightness; `False`: keep default brightness.

__Sample code:__

``` python
from hub import display, Image

display.show(Image.HAPPY)

display.invert(True)
```

## callback()

`display.callback`

!!! todo
    not sufficiently tested


