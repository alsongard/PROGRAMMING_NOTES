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
