- [Tailwind CSS](#tailwind-css)
  - [Cheat sheet](#cheat-sheet)
  - [Class guide](#class-guide)
- [4 fundamental categories of selectors](#4-fundamental-categoriesof-selectors)
- [The align-items Property](#the-align-items-property)
- [The justify-content Property](#the-justify-content-property)
- [Absolute Units](#absolute-units)
- [Relative Units](#relative-units)
- [The flex-direction Property](#the-flex-direction-property)
- [The flex-wrap Property](#the-flex-wrap-property)
- [Pixel to rem calc](#pixel-to-rem-calc)
- [All in one group of setting format](#all-in-one-group-of-setting-format)
- [Optional Resetting to Default](#optional-resetting-to-default)

## Tailwind CSS

Tailwind is a CSS framework that gives you pre-made utility classes.
Without Tailwind:

```jsx
<div className="my-box">Hello</div>

/* App.css */
.my-box {
  padding: 16px;
  font-size: 20px;
  font-weight: bold;
}
```

With Tailwind:

```jsx
<div className="p-4 text-xl font-bold">Hello</div>
```

### Cheat sheet

1. Colors
   Tailwind uses a palette with shades from 50 → 900.

   ```css
   bg-red-100  bg-red-500  bg-red-900
   bg-blue-100 bg-blue-500 bg-blue-900
   bg-green-100 bg-green-500 bg-green-900
   ```

   Visual representation (simplified):

   ```scss
   Light → Medium → Dark
   █ bg-red-100   █ bg-red-500   █ bg-red-900
   █ bg-blue-100  █ bg-blue-500  █ bg-blue-900
   █ bg-green-100 █ bg-green-500 █ bg-green-900
   ```

   Usage:

   ```html
   <div class="bg-red-500 text-white p-4">Red Box</div>
   <div class="bg-blue-100 text-blue-900 p-4">Blue Box</div>
   ```

2. Spacing (Padding & Margin)

   Tailwind spacing is multiples of 0.25rem (1 unit = 4px).

   | Class         | Pixels |
   | ------------- | ------ |
   | `p-1` / `m-1` | 4px    |
   | `p-2` / `m-2` | 8px    |
   | `p-4` / `m-4` | 16px   |
   | `p-8` / `m-8` | 32px   |

   Visual box representation:

   ```
   +----------------------+
   |  p-4 padding inside  |
   |   +--------------+   |
   |   | content      |   |
   |   +--------------+   |
   +----------------------+
   ```

   ```html
   <div class="m-4 p-2 bg-gray-200">Box with margin 16px and padding 8px</div>
   ```

3. Flex & Grid Layouts
   Flex Example:

   ```html
   <div class="flex flex-row justify-between items-center p-4 bg-gray-100">
     <div class="p-2 bg-red-300">Item 1</div>
     <div class="p-2 bg-green-300">Item 2</div>
     <div class="p-2 bg-blue-300">Item 3</div>
   </div>
   ```

   Diagram:

   ```
   Flex container: flex-row justify-between items-center
   [Item 1]      [Item 2]      [Item 3]

   ```

   Grid Example:

   ```html
   <div class="grid grid-cols-3 gap-4 p-4 bg-gray-100">
     <div class="p-2 bg-red-300">1</div>
     <div class="p-2 bg-green-300">2</div>
     <div class="p-2 bg-blue-300">3</div>
   </div>
   ```

   Diagram:

   ```
   Grid container: 3 columns
   +-----+-----+-----+
   |  1  |  2  |  3  |
   +-----+-----+-----+
   ```

4. Typography
   | Category | Class Examples | Effect |
   | -------------- | --------------------------- | ------------------ |
   | Font size | `text-xs` → `text-4xl` | Sets font size |
   | Font weight | `font-thin` → `font-black` | Sets font boldness |
   | Text color | `text-red-500` | Sets text color |
   | Text alignment | `text-left` / `text-center` | Aligns text |

   ```html
   <h1 class="text-2xl font-bold text-blue-500">Heading</h1>
   <p class="text-sm text-gray-700">Paragraph</p>
   ```

5. Borders & Rounding
   | Class | Effect |
   | ---------------- | ---------------------- |
   | `border` | Adds 1px border |
   | `border-2` | 2px border |
   | `border-red-500` | Red border color |
   | `rounded` | Slight corner radius |
   | `rounded-full` | Fully rounded (circle) |

   ```
   <div class="border-2 border-blue-500 rounded p-4">Rounded Box</div>
   ```

6. State & Interactivity
   | Class | Effect |
   | -------------------- | --------------------------- |
   | `hover:bg-blue-500` | Changes background on hover |
   | `focus:outline-none` | Removes focus outline |
   | `cursor-pointer` | Changes cursor to pointer |
   | `transition` | Smooth animation on change |

   ```html
   <button class="p-2 bg-green-500 hover:bg-green-700 text-white transition">
     Click Me
   </button>
   ```

7. Quick Visual Map (Combine)
   ```html
   <div class="flex flex-col gap-4 p-4 bg-gray-100 rounded shadow">
     <h1 class="text-xl font-bold text-red-500">Heading</h1>
     <p class="text-gray-700">Paragraph text</p>
     <button
       class="p-2 bg-blue-500 hover:bg-blue-700 text-white rounded transition"
     >
       Click
     </button>
   </div>
   ```
   Diagram:
   ```
   Copy code
   Flex container (vertical, gap 16px, padding 16px, gray background)
   ├─ Heading (red, bold, xl)
   ├─ Paragraph (gray text)
   └─ Button (blue, hover darker, rounded)
   ```

### Class guide

1. Layout & Box Model

   | Category       | Class Examples                                                   | Description / Effect                                   |
   | -------------- | ---------------------------------------------------------------- | ------------------------------------------------------ |
   | Display        | `block`, `inline-block`, `flex`, `grid`                          | Sets the element’s display type                        |
   | Flexbox        | `flex`, `flex-row`, `flex-col`, `justify-center`, `items-center` | Flex container direction, alignment, and justification |
   | Box Sizing     | `box-border`, `box-content`                                      | Controls whether padding/border are included in size   |
   | Width & Height | `w-4`, `w-1/2`, `h-10`, `h-screen`                               | Sets width/height (pixels, fractions, viewport units)  |
   | Margin         | `m-2`, `mt-4`, `mb-1`                                            | Margin on all sides or specific sides                  |
   | Padding        | `p-2`, `px-4`, `py-3`                                            | Padding on all sides or specific sides                 |
   | Overflow       | `overflow-auto`, `overflow-hidden`                               | Controls scroll/overflow behavior                      |

2. Typography
   | Category | Class Examples | Description / Effect |
   | --------------- | -------------------------------------------------------- | -------------------------------------- |
   | Font Size | `text-xs`, `text-sm`, `text-lg`, `text-xl`, `text-2xl` | Controls font size |
   | Font Weight | `font-thin`, `font-normal`, `font-bold`, `font-black` | Sets font weight |
   | Text Alignment | `text-left`, `text-center`, `text-right`, `text-justify` | Aligns text horizontally |
   | Text Color | `text-red-500`, `text-blue-700` | Sets text color using Tailwind palette |
   | Line Height | `leading-none`, `leading-tight`, `leading-loose` | Sets vertical spacing between lines |
   | Letter Spacing | `tracking-tight`, `tracking-wide` | Adjusts space between characters |
   | Text Decoration | `underline`, `line-through`, `no-underline` | Adds underline or strike-through |

3. Backgrounds
   | Category | Class Examples | Description / Effect |
   | ------------------- | ---------------------------------- | ----------------------------------------- |
   | Background Color | `bg-red-500`, `bg-gray-100` | Sets background color |
   | Background Opacity | `bg-opacity-50` | Controls transparency of background color |
   | Background Position | `bg-center`, `bg-top`, `bg-bottom` | Sets the background image position |
   | Background Size | `bg-cover`, `bg-contain` | How background image scales |
   | Background Repeat | `bg-no-repeat`, `bg-repeat` | Sets background repeat behavior |

4. Borders & Effects
   | Category | Class Examples | Description / Effect |
   | ------------- | --------------------------------------- | --------------------- |
   | Border Width | `border`, `border-2`, `border-t-4` | Sets border thickness |
   | Border Color | `border-red-500`, `border-gray-200` | Sets border color |
   | Border Radius | `rounded`, `rounded-full`, `rounded-lg` | Rounds corners |
   | Box Shadow | `shadow`, `shadow-lg`, `shadow-inner` | Adds shadow effects |
   | Opacity | `opacity-50`, `opacity-100` | Controls transparency |

5. Positioning
   | Category | Class Examples | Description / Effect |
   | --------------------- | --------------------------------------------------- | -------------------------------------------- |
   | Position | `static`, `relative`, `absolute`, `fixed`, `sticky` | Sets element positioning method |
   | Top/Right/Bottom/Left | `top-0`, `left-2`, `bottom-4` | Moves element relative to parent or viewport |
   | Z-Index | `z-10`, `z-50`, `z-auto` | Controls stacking order |

6. Interactivity & State
   | Category | Class Examples | Description / Effect |
   | ------------ | ------------------------------------------- | ------------------------------ |
   | Cursor | `cursor-pointer`, `cursor-default` | Sets cursor style |
   | Hover States | `hover:bg-blue-500`, `hover:text-white` | Changes appearance on hover |
   | Focus States | `focus:outline-none`, `focus:ring` | Styles when element is focused |
   | Transition | `transition`, `duration-300`, `ease-in-out` | Animates changes smoothly |

7. Grid System
   | Category | Class Examples | Description / Effect |
   | -------------- | ------------------------------------ | ---------------------------------------------- |
   | Grid Container | `grid`, `grid-cols-3`, `grid-rows-2` | Defines grid layout and number of columns/rows |
   | Gap | `gap-2`, `gap-x-4`, `gap-y-6` | Sets spacing between grid items |
   | Column Span | `col-span-1`, `col-span-2` | Controls how many columns an item spans |

8. Miscellaneous Utilities
   | Category | Class Examples | Description / Effect |
   | ----------- | --------------------------------------------- | ------------------------------- |
   | Overflow | `overflow-hidden`, `overflow-auto` | Controls scroll behavior |
   | Visibility | `visible`, `invisible` | Shows or hides elements |
   | Flex Wrap | `flex-wrap`, `flex-nowrap` | Controls wrapping of flex items |
   | Place Items | `place-items-center`, `place-content-between` | Aligns items within a container |

## 4 fundamental categories of selectors

- Basic selectors

```css
:(universal, type, class, id, attribute)
```

- Combinators

```css
:(descendant, child, sibling)
```

- Pseudo-classes is element based on its specific state or position

```css
:(:hover, :focus, :nth-child, :first-child, etc)
```

- Pseudo-elements

```css
:(::before, ::after)
```

```css
Element Selector: p {} → styles all <p> tags
Class Selector: .class-name {} → styles elements with class="class-name"
ID Selector: #id-name {} → styles a specific element with id="id-name"
```

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

- flex-direction : row;  
  Places all the flex items on the same row, in the direction of your browser's default language (left to right or right to left).
- flex-direction : row-reverse;  
  This reverses the items in the row.
- flex-direction : column;  
  This will align the flex items vertically instead of horizontally.
- flex-direction : column-reverse;  
  This reverses the order of the flex items vertically.

## The flex-wrap Property

Definition: This property determines how flex items are wrapped within a flex container to fit the available space. flex-wrap can take three possible values: nowrap, wrap, and wrap-reverse.

- flex-wrap : nowrap;
  This is the default value. Flex items won't be wrapped onto a new line, even if their width exceed the container's width.
- flex-wrap : wrap;  
  This property will wrap the items when they exceed the width of their container.
- flex-wrap : wrap-reverse;
  This property will wrap flex items in reverse order.

## Pixel to rem calc

4 = 0.25
8 = 0.5
12 = 0.75
16 = 1
20 = 1.25
28 = 1.75
40 = 2.5
60 = 3.75
100 = 6.25
160 = 10
240 = 15

To size an important element use Size Weight and Color

Main axis = horizontal
Cross axis = vertical

## All in one group of setting format

```css
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

/* Font-size family and Line Height */
--font-family: Arial, Helvetica, sans-serif;
--h1-X: bold 4rem/1em var(--font-family);
--h2-X: bold 3rem/1.2em var(--font-family);
--h3-X: bold 2.25rem/1.2em var(--font-family);
--h4-X: bold 1.5rem/1.6em var(--font-family);
--font-size-large-X: 1.25rem/1.6em var(--font-family);
--font-size-medium-X: 1rem/1.6em var(--font-family);
--font-size-small-X: 0.75rem/2em var(--font-family);
--h1: bold 3rem/1.2em var(--font-family);
--h2: bold 2.25rem/1.2em var(--font-family);
--h3: bold 1.5rem/1.2em var(--font-family);
--h4: bold 1.25rem/1.6em var(--font-family);
--font-size-large: 1rem/1.6em var(--font-family);
--font-size-medium: 0.8rem/1.6em var(--font-family);
--font-size-small: 0.75rem/1.8em var(--font-family);

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

/* Effect */
--shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
--shadow-img: 0 2px 8px rgba(0, 0, 0, 0.08);
--shadow-video: 0 2px 8px rgba(0, 0, 0, 0.1);
--border: 1px solid #bbb;
--border-radius: 10px;
```

## Optional Resetting to Default

```css
* {
  margin: 0;
  padding: 0;
  font-size: var(--font-size-medium);
  font-family: var(--font-family);
  box-sizing: border-box;
}
```
