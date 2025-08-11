## **4 fundamental categories** of  selectors

- Basic selectors   
 :(universal, type, class, id, attribute)
- Combinators    
 :(descendant, child, sibling)
- Pseudo-classes is element based on its specific state or position   
:(:hover, :focus, :nth-child, :first-child, etc)
- Pseudo-elements                                                    
 :(::before, ::after)

## The align-items Property

Definition: This property is used to distribute items along the cross axis. 
Remember that the cross axis is perpendicular to the main axis.

- align-items: center;
This is used to center the items along the cross axis.
- align-items: flex-start;
This aligns the items at the start of the cross axis.
- align-items: flex-end; 
This aligns the items at the end of the cross axis.
- align-items: stretch; 
This is used to stretch the flex items along the cross axis.

## The justify-content Property

Definition: This property aligns the child elements along the main axis of the flex container.

- justify-content: flex-start; 
In this case, the flex items will be aligned to the start of the main axis. This could be horizontal or vertical.
- justify-content: flex-end
In this case, the flex items are aligned to the end of the main axis, horizontally or vertically.
- justify-content: center;
This centers the flex items along the main axis.
- justify-content: space-between;
This will distribute the elements evenly along the main axis.
- justify-content: space-around; 
This will distribute flex items evenly within the main axis, adding a space before the first item and after the last item.
- justify-content: space-evenly;
This will distribute the items evenly along the main axis.

## Absolute Units

- px (Pixels)  
This absolute unit is a fixed-size unit of measurement in . It is the most common absolute unit and provides precise control over dimensions. 1px is always equal to 1/96th of an inch.
- in (Inch) 
This absolute unit is equal to 96px.
- cm (Centimeters)
This absolute unit is equal to 25.2/64 of an inch.
- mm (Millimeters)
This absolute unit is equal to 1/10th of a centimeter.
- q (Quarter-Millimeters)
This absolute unit is equal to 1/40th of a centimeter.
- pc (Picas) 
This absolute unit is equal to 1/6th of an inch.
- pt (Points)    
This absolute unit is equal to 1/72th of an inch.

## Relative Units

- Percentages
These relative units allow you to define sizes, dimensions, and other properties as a proportion of their parent element. For example, if you set width: 50%; on an element, it will occupy half the width of its parent container.
- em Uni
These units are relative to the font size of the element. If you are using ems for the font-size property, the size of the text will be relative to the font size of the parent element.
- rem Unit
These units are relative to the font size of the root element, which is the html element.
- vh Unit  
vh stands for "viewport height" and 1vh is equal to 1% of the viewport's height.
- vw Unit
vw stands for "viewport width" and 1vw is equal to 1% of the viewport's width.

## The flex-direction Property

Definition: This property sets the direction of the main axis.

- flex-direction  : row;            
Places all the flex items on the same row, in the direction of your browser's default language (left to right or right to left).
- flex-direction  : row-reverse;      
This reverses the items in the row.
- flex-direction  : column;    
This will align the flex items vertically instead of horizontally.
- flex-direction  : column-reverse;  
This reverses the order of the flex items vertically.

## The flex-wrap Property

Definition: This property determines how flex items are wrapped within a flex container to fit the available space. flex-wrap can take three possible values: nowrap, wrap, and wrap-reverse.

- flex-wrap       : nowrap; 
This is the default value. Flex items won't be wrapped onto a new line, even if their width exceed the container's width.
- flex-wrap       : wrap;         
This property will wrap the items when they exceed the width of their container.
- flex-wrap       : wrap-reverse;
This property will wrap flex items in reverse order.

## Pixel to rem calc

4	= 0.25
8	= 0.5
12	= 0.75
16	= 1
20	= 1.25
28	= 1.75
40	= 2.5
60	= 3.75
100	= 6.25
160	= 10
240	= 15

To size an important element use Size Weight and Color

Main axis = horizontal
Cross axis = vertical

## All in one group of setting format

```
:root {
/* Color */
--colora: #ffe537;
--colora2: #537fe7;
--background-color: #f0f0f0;
--background-hover: #f0f0f0;
--primary-color: #1976d2;
--primary-hover: #0d47a1;
--green-button-color: #4caf50;
--green-button-hover: #388e3c;
--blue-button-color: #2196f3;
--blue-button-hover: #1976d2;
--black: #000;
--gray10: hsla(0, 0%, 10%);
--gray20: hsla(0, 0%, 20%);
--gray30: hsla(0, 0%, 30%);
--gray50: hsla(0, 0%, 50%);
--gray70: hsla(0, 0%, 70%);
--gray90: hsla(0, 0%, 90%);
--white: #fff;
```

```
/* Font-size family and Line Height */
--font-family: Arial, Helvetica, sans-serif;
--h1-X: bold 4rem/1em var(--font-family);
--h2-X: bold 3rem/1.2em var(--font-family);
--h3-X: bold 2.25rem/1.2em var(--font-family);
--h4-X: bold 1.5rem/1.6em var(--font-family);
--font-size-large-X: 1.25rem/1.6em var(--font-family);
--font-size-medium-X: 1rem/1.6em var(--font-family);
--font-size-small-X: .75rem/2em var(--font-family);
--h1: bold 3rem/1.2em var(--font-family);
--h2: bold 2.25rem/1.2em var(--font-family);
--h3: bold 1.5rem/1.2em var(--font-family);
--h4: bold 1.25rem/1.6em var(--font-family);
--font-size-large: 1rem/1.6em var(--font-family);
--font-size-medium: .8rem/1.6em var(--font-family);
--font-size-small: 0.75rem/1.8em var(--font-family);
```

```
/* Margin and Padding */
--margin-xxs: 0.25rem;
--margin-xs: 0.5rem;
--margin-s: 0.75rem;
--margin-m: 1rem;
--margin-l: 1.25rem;
--margin-xl: 1.75rem;
--margin-xxl: 2.5rem;
--padding-xxs: 0.25rem;
--padding-xs: 0.5rem;
--padding-s: 0.75rem;
--padding-m: 1rem;
--padding-l: 1.25rem;
--padding-xl: 1.75rem;
--padding-xxl: 2.5rem;
```

```
/* Effect */
--shadow: 0 2px 8px rgba(0,0,0,0.05);
--shadow-img: 0 2px 8px rgba(0,0,0,0.08);
--shadow-video: 0 2px 8px rgba(0,0,0,0.10);
--border: 1px solid #bbb;
--border-radius: 10px;
```

```
/* Resetting to Default */
* {
margin: 0;
padding: 0;
font-size: var(--font-size-medium);
font-family: var(--font-family);
box-sizing: border-box;
}
```