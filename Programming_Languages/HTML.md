## Font-size
### rem
``rem`` stand for "root em". The rem  is a relative unit of measurement that is relative to the font-size of the root element.  The default font-size of the  root element in most browsers is 16px. ``1rem`` is equal to ``16px``. Mostly used for designing responsive web pages.

## box-shadow 
Used to add a shadow to an element. The first value is for the horizontal offset and the second value is for the vertical offset. By default it inherits the color of the text.
``box-shadow: 5px 10px;``
One can also define the color of the shadow:
``box-shadow: 5px 10px red;``

## linear-gradient()

```
background-color:linear-gradient(colorValue1, colorValue2);
background-color:linear-gradient(to right, colorVAlue1, colorValue2, colorValue3)
```

## Form
The form is used to gather information from the user and submit/transfer these data to a server.
```
<form action="submiting_url" method="POST">
	<textarea cols="20" rows="8"></textarea>
</form>
```
The `textarea` is used to enter comments or blogs, about yourself in a form


The fractional unit can be used to resize the items of a grid container depending on their size.

## Text-underline
To add space in between the underline and the text property use ``text-underline-offset`` property.
```
<h1 style="text-decoration:underline; text-underline-offset=5px">Global</h1>
```

## COLOR
#### color properties:
* hsl() - takes in 3 arguments one for hue,saturation and lightness. lightness and saturation are given in percentage.

* hex value uses 6 values 1 pair representing each main color code RGB it starts with ``#00FF00`` FF means 100% of color, 00 is 0% of color.   

* rgb() is also used for setting the color property, it takes in 3 arguments each representing the 3 main color codes having values between 0-255.  

* linear-gradient - works with background{} property. It takes in 3 arguments the first being the degree of change and the secong and third being the color to change from and to second color.  
E.g changes from red to green with a 90 deg change 
``background:linear-gradient(90deg, rgb(255,0,0),rgb(0,255,0)) `` 
it can also take another argument, also color stops.

example:
class name = "mine"
.mine background:linear-gradient(180, hsl(75,55%,89%)50%/*stop*/, hsl(10,88%,22%),hsl(80,52%,89%))
by default the line is 180 degree change.
DIV
div elements have a block property: take the space of the whole line
BORDER
the border propery is used for designing the border of an element and one can decide which side to be applied.
border-left, border-right , border
border-left(size type color) it takes in 3 arguments size given in px(pixel value) , type can be solid , double and color for color.
#BOX-SHADOW
add a shadow for an element
it can take up 4 arguments
box-shadow : offsetX offsetY blurRadius Color;
box-shadow : 5px 5px 5px Green;
it can take up 5 args
box-shadow:offsetX offsetY blurRadius spreadRadius Color;

# CSS FLEXBOX
***********************************
## border-box propery
the border-box propery uses 2 models one  being content-box and the other border-box.With content-box which is the default is, padding and margin values are added to the width of the element content e.g img , while with the border-box model the entire width is calculated by adding both the padding,margin and width of the content.

## flexbox
The flexbox has 2 axis mainly the main axis and the cross axis.
the main axis which is the flex-direction property can take in 4 values that define the direction of the flex items or of the flex container.
>> these are :
>>> * column 
>>> * column-reverse
>>> * row(default)
>>> * row-reverse
 
## wrap
the wrap method is used to push elements to the next line ``flex-wrap:wrap;``. However this can be removed by assiging ***none***.

## submit
When using the submit button ensure to set the height to place the value | text submit to center

## CSS POSITIONING
positioning propery allows a user to place elements / position an element in a webpage. It can take 4 properties namely:
static, fixed, absolute, relative and sticky
Once you set the position propery for the element you can move it by setting the top,right,bottom,left properties in pixels or percentage
the defualt position propery of elements is static and with these the element cannot be moved
observation: did not affect the position even with top and left propery set.
relative element:The element is still position to the normal flow of the document, but the top,left,right and bottom properties become active.
absolute property: with the absolute property the element is taken off the normal document flow and it's positionis dtrmnd by the top, right, left and bottom properties
fixed property: the fixed property makes an element to remian at it's position no matter the changes done to the width or the user scrolls
observation: the element does not move even in scrolling in takes the same top,left values 
sticky property: sticky property is a combination of both the fixed and realtive property. it remain to that position even if u scroll however it is not fixed
One way to center an item horizontally is to first:
set the position of the element to absolute:, set th etop,bottom,left,right to 0 and then set margin to auto;

## PSEUDO-SELECTORS
### not() pseudo-selector
pseudo-selector used to select elements that do not have the specified class. e.g
`` span:not(.sr-only) `
`will select all span elements that do not have the class .sr-only

### attribute target selector
the attribute target selector - it nonly selects elements that have a target attribute with a specific value. e.g
``span[class~="sr-only"] {...}``
the above code will only select span which have the class sr-only and not any other names

### !important
the !important keywork ensures that the styles of an element are not overwritten.E.g
``tr[class="total"]{
    color:#fff !important
}``

### nth-of-type()
the nth-of-type is a pseudo-selector that only selects an element based on its index value of the number. E.g
``span:nth-of-type(3){..}``
will select only the span element which is the third

### last-of-type
the last-of-type will select the last element of the element specified
``span:last-of-type{..}``
will select the last element of span
### first-of-type
It is used to select the first appearance of the element
``span:first-of-type{..}``
## Centering elements in a page
to center an element in a page, one can use the following options
### setting margin
for the margin, use
``margin:0 auto``
### setting position
set the position the absolute, and ensure the top,right,bottom,left values are 0.
>>```position:absolute;
>>top:0
>>right:0
>>bottom:0
>>left:0

### CSS VARIABLES
To declare a css variable use the syntax  ``--variableName-property:value``
```root:{
    --builing-color:rgb | hsl | color;
}
```
to use the variable name use the syntax ``var(--variableName)``
example:
```
    .home{
        background-color:var(--builidng-color);
    }
```

### img attribures
* #### loading
the loading attribute is used to set how the image of the img loads. Setting it to lazy enables other elements of the page to load and only the image to load when the user scrolls through the image.
``<img src="file-location" loading="lazy">``

## backup font
to add a backup font if the first font fails, add the backup font after the primary font:
``font-family:Helvetica, sans-serif;``

## grid layout
The grid layout is used display items in grid mannaer, having rows and columns
>>>``fr`` : Flexible Track Size - Used to give a specified fixed value to the grid. 

## forms  
### input types  
- Radio buttons  
when using radio buttons, always set the name for the specific radio buttons the same. This groups the radio buttons and the value can have different values.  
Example:
```
<input type="radio" name="gender" value="male">
<input type="radion" name="female" value="female">
```
By grouping them only one radio button can be selected and it's value is sent to the back-end server.

## anchor tag
the anchor tag ``target`` attribute is used to open to open links on different tabs or frame or window based on the following values.

| targetProperty | property                                              |
| -------------- | ----------------------------------------------------- |
| _blank         | open the link on a new window                         |
| _self          | open on the same window                               |
| _top           | opens the link on the current full body of the window |
| _parent        | opens the link  in the parent frame                   |

## **Box shadow**
the box shadow property can take several values:
``box-shadow: 10px 10px 10px black;``
In the above line: 
first value is used for the :horizontal
the second value is used : :vertical
the third value sets the : blur the higher the value the more blur will be applied
the last value is used for specifying the shadow color for the element
If no color is given it takes the color for the text

## **animation**
animation: animations are used to change the style of an element from one style to another.
To use animation we must use keyframes. Keyframes define the styles and at what moment the styles change should happen
when you specify the CSS styles inside the keyframes using @keyframes rule, the css will change from the current style to another style
To get the animation to work you must find bind the animation to the element using the ``animation-name:`` keyword
Example:

```
@keyframes{
	from {background-color:red;}
	to {background-color: yellow;}
}

div{
	width:100px;
	height:100px;
	background-color:red;
	animation-name:example;
	animation-duration;:4s;
}
```

- animation-duration
The animation-duration specifies how long the animation should take to complete. If no animation-duration value is given no effect of the animation will be done as the default value is 0.

In the above example we have used the ``from{}`` and ``to{}`` to change the animation. However this can also be achieved using percentage values that is
0%, 100%. One can also add values such as 0%, 25%, 50%, 75%, 100%.

- animation-delay:
the animation-delay will delay the start of the animation. The value it takes is seconds:
```
	animation-delay:2s
```

Negative values are also allowed but the animation will start as if it had already started playing.
Example: if animation duration is 10s and animation-delay is 4s. the animation will start at 6th second, however this will not change the animation duration.
- animation-iteration-count
animation-iteration-count specifies the number of times the animation should run. if the value is ``animation-iteration:3`` it will run 3 times.
It there ``animation-iteration-count: infinite`` this means that it will continue to run

- animation-timing-function:
the animation-timing-function specifies the speed of the animation.
It can take several values:

| values                | description                                                      |
| --------------------- | ---------------------------------------------------------------- |
| ease                  | animation will begin with a slow start, then fast and end slowly |
| linear                | animation will have the same speed from the beginning to the ned |
| ease-in               | animation with a slow start                                      |
| ease-out              | animation witha slow end                                         |
| ease-in-out           | animation with a slow start and end                              |
| cubic-bezier(n,n,n,n) | Lets you define your own values in a cubic-bezier function       |

### **Opacity**
the opacity is used to set the opacity level for an element. It describes the transparency-level where 1 is not transparent and 0.5 is 50 percent see through and 0 is completely transparent.
When applying opacity to a parent element sometimes it makes the text hard to read, to counter this it is recommended to use rgba values for the background-color of the property.

There are 2 types of shadow effects namely:

- text shadow

- box shadow

  

# text-shadow
In it's simplest use you can specify the horizontal shadow and vertical shadow
syntax: ``text-shadow: horizontalValue verticalValue``
Example:
```
<p style="text-shadow:0 10px">Welcome</p>
```
To add a Color you specify as the last value if the total values are 3;
Syntax: ``text-shadow: horValue vertValue color``
```
<p style="text-shadow:2px 2px red">Good Day</p>
```
One can also add a blur to the text
syntax: ``text-shadow: horValue verValue blurValue color;``
```
<p style="text-shadow:0 2px 5px blue">Project Mars</p>
```
One can also add multiple shadow effects to a text as shown:
```
.p{
text-shadow: 1px 5px black, -1px -5px black, 1px 0 black, 0 -1px black;
}
```


# box-shadow

- to use box-shadow property in its simplest form:
Although by default the box-shadow property takes the color of the text, you can also change the color of the box-shadow or you can also specify the text color. However when using the second option, that is the text apply the change of the color in the parent element and not the text, paragraph element

example 1:

```
#firstBox
{
color:red;
}
<div id="firstBox">
<p>I need to know now to know now can you love me again</p>
</div>
```
in the example above the shadow will be red

**Changing the color**
Syntax: ``box-shadow: horValue vertValue color;``
```
<div style="box-shadow:10px 10px black;height:100px;width:100px;">
</div>
```

**Blur radius**
the blur value specifies the blur around the element. A higher value will result in a higher blur value

```

  
  

```