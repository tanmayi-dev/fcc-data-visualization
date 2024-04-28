# Data Visualization

## Data Visualization with D3

- D3 has several methods that let us add and change elements in document
- D3 library focuses on a data-driven approach. When you have a set of data, you can apply D3 methods to display it on the page.

- `select()` :
  - This method selects one element from the document.
  - It takes an argument for the name of the element and returns an HTML node for the first element in the document that matches the name.
- `append()` :
  - This method takes an argument for the element you want to add to the document.
  - It appends an HTML node to a selected item, and returns a handle to that node.
- `text()` :
  - This method either sets the text of the selected node, or gets the current text.
  - To set the value, you pass a string as an argument inside the parentheses of the method.
  - It can also take a callback function as an argument.
  - `selection.text((d) => d)`
- `selectAll()` :
  - Method to select a group of elements.
  - It returns an array of HTML nodes for all the items in the document that match the input string.
  - It supports method chaining like `select()`
- `data()` :
  - This method is used on a selection of DOM elements to attach the data to those elements.
  - The data set is passed as an argument to the method.
- `enter()` :
  - A common workflow pattern is to create a new element in the document for each piece of data in the set.
  - `enter()` is combined with the `data()` method, it looks at the selected elements fromt the page and compares them to the number of data items in the set.
  - If there are fewer elements than data items, it creates the missing elements.
- `text()` for dynamic data:
  - It can also take a callback function as an argument.
  - Example : `selection.text((d) => d)`
- `style()` :

  - D3 allows to add inline CSS styles on dynamic elements with this method.
  - The `style()` method takes a comma-separated key-value pair as an argument.
  - Example: `selection.style("color","blue");`
  - Example: `selection.style("font-family","verdana");`
  - To apply css properties conditionally on particular data, use a _a callback function_ in the `style()` method and include the conditional logic.
  - The callback function uses the `d` parameter to represent the data point.
  - Example:

    ```js
    selection.style("color". (d) => {

    })
    ```

- `attr()` :
  - This method is used to add any HTML attribute to an element, including a class name.
  - The `attr()` method works the same way that `style()` does.
  - It takes comma-separated values, and use a callback function.
  - Example to add a class of `container` to a selection:
    ```js
    selection.attr("class", "container");
    ```
  - Note that the `class` parameter will remain the same whenever you need to add a class and only the `container` parameter will change.

### Creating Simple Bar Chart

1. Create a `div` for each data point in the array
2. Give each `div` a dynamic height, using a callback function in the `style()` methods that sets height equal to the data value

- Example:
  ```js
  selection.style("cssProperty", (d) => d);
  ```

## SVG - Scalable Vector Graphics

### SVG Description

- SVG stands for Scalable Vector Graphics.

- Here "scalable" means that, if you zoom in or out on an object, it would not appear pixelated. It scales with the display system, whether it's on a small mobile screen or a large TV monitor.

- SVG is used to make common geometric shapes. Since D3 maps data into a visual representation, it uses SVG to create the shapes for the visualization. SVG shapes for a web page must go within an HTML `svg` tag.

- CSS can be scalable when styles use relative units (such as `vh`, `vw`, or percentages), but using SVG is more flexible to build data visualizations.

### SVG Shapes

- Shapes in SVG : There are number of supported shapes in SVG, such as rectangles and circles. They are used to display data.

- For example, a rectangle (`<rect>`) SVG shape could create a bar in a bar chart.

- When you place a shape into the `svg` area, you can specify where it goes with `x` and `y` coordinates. The origin point of (0,0) is in the upper-left corner. Positive values for `x` push the shape to the right, and positive values for `y` push the shape down from the origin point.

- The `rect` elements must be appended to an `svg` element, not directly to the `body`. To tell D3 where to place each `rect` within the `svg` area, define the `x` and `y` attributes

- The placement of a rectangle is handled by the `x` and `y` attributes. They tell D3 where to start drawing the shape in the `svg` area. The last challenge set them each to 0, so every bar was placed in the upper-left corner.

- For a bar chart, all of the bars should sit on the same vertical level, which means the `y` value stays the same (at 0) for all bars. The `x` value, however, needs to change as you add new bars. Remember that larger `x` values push items farther to the right. As you go through the array elements in `dataset`, the `x` value should increase.

### SVG Properties

- The `attr()` method in D3 accepts a callback function to dynamically set that attribute. The callback function takes two arguments, one for the data point itself (usually `d`) and one for the index of the data point in the array. The second argument for the index is optional. Here's the format:

```js
selection.attr("property", (d, i) => {});
```

- It's important to note that you do NOT need to write a `for` loop or use `forEach()` to iterate over the items in the data set. Recall that the `data()` method parses the data set, and any method that's chained after `data()` is run once for each item in the data set.

### Invert SVG Elements

- In SVG, the origin point for the coordinates is in the upper-left corner. An `x` coordinate of 0 places a shape on the left edge of the SVG area. A `y` coordinate of 0 places a shape on the top edge of the SVG area. Higher `x` values push the rectangle to the right. Higher `y` values push the rectangle down.

- To make the bars right-side-up, you need to change the way the `y` coordinate is calculated. It needs to account for both the height of the bar and the total height of the SVG area.

- The height of the SVG area is 100. If you have a data point of 0 in the set, you would want the bar to start at the bottom of the SVG area (not the top). To do this, the `y` coordinate needs a value of 100. If the data point value were 1, you would start with a `y` coordinate of 100 to set the bar at the bottom. Then you need to account for the height of the bar of 1, so the final `y` coordinate would be 99.

- The `y` coordinate that is `y = heightOfSVG - heightOfBar` would place the bars right-side-up.

### Change Color of SVG elements

- In SVG, a `rect` shape is colored with the `fill` attribute. It supports hex codes, color names, and rgb values, as well as more complex options like gradients and transparency.

### Add and Style Labels to D3 Elements

- D3 lets you label a graph element, such as a bar, using the SVG `text` element.

- Like the `rect` element, a `text` element needs to have `x` and `y` attributes, to place it on the SVG. It also needs to access the data to display those values.

- D3 gives you a high level of control over how you label your bars.

- D3 methods can add styles to the bar labels. The `fill` attribute sets the color of the `text` for a text node. The `style()` method sets CSS rules for other styles, such as `font-family` or `font-size`.

### Add a Hover Effect to a D3 element

- It's possible to add effects that highlight a bar when the user hovers over it with the mouse. So far, the styling for the rectangles is applied with the built-in D3 and SVG methods, but you can use CSS as well.

- You set the CSS class on the SVG elements with the `attr()` method. Then the `:hover` pseudo-class for your new class holds the style rules for any hover effects.s

### Add a Tooltip to a D3 element

- A tooltip shows more information about an item on a page when the user hovers over that item. There are several ways to add a tooltip to a visualization. This challenge uses the SVG `title` element.

- `title` pairs with the `text()` method to dynamically add data to the bars.

### Scatterplot with SVG Circles

- A scatter plot is another type of visualization. It usually uses circles to map data points, which have two values each. These values tie to the `x` and `y` axes, and are used to position the circle in the visualization.

- SVG has a `circle` tag to create the circle shape. It works a lot like the `rect` elements you used for the bar char

### Add Attributes to the Circle Elements

- The last challenge created the `circle` elements for each point in the `dataset`, and appended them to the SVG. But D3 needs more information about the position and size of each `circle` to display them correctly.

- A `circle` in SVG has three main attributes. The `cx` and `cy` attributes are the coordinates. They tell D3 where to position the center of the shape on the SVG. The radius (`r` attribute) gives the size of the `circle`.

- Just like the `rect` y coordinate, the `cy` attribute for a `circle` is measured from the top of the SVG, not from the bottom.

- All three attributes can use a callback function to set their values dynamically. Remember that all methods chained after `data(dataset)` run once per item in `dataset`. The `d` parameter in the callback function refers to the current item in `dataset`, which is an array for each point. You use bracket notation, like `d[0]`, to access the values in that array.

### Add Labels to Scatter Plot Circles

- You can add text to create labels for the points in a scatter plot.

- The goal is to display the comma-separated values for the first (`x`) and second (`y`) fields of each item in dataset.

- The `text` nodes need `x` and `y` attributes to position it on the SVG. In this challenge, the `y` value (which determines height) can use the same value that the `circle` uses for its `cy` attribute. The `x` value can be slightly larger than the `cx` value of the `circle`, so the label is visible. This will push the label to the right of the plotted point.

## Scales - Linear Scale with D3

- The bar and scatter plot charts both plotted data directly onto the SVG. However, if the height of a bar or one of the data points were larger than the SVG height or width values, it would go outside the SVG area.

- In D3, there are scales to help plot data. `scales` are functions that tell the program how to map a set of raw data points onto the pixels of the SVG.

- For example, say you have a 100x500-sized SVG and you want to plot Gross Domestic Product (GDP) for a number of countries. The set of numbers would be in the billion or trillion-dollar range. You provide D3 a type of scale to tell it how to place the large GDP values into that 100x500-sized area.

- It's unlikely you would plot raw data as-is. Before plotting it, you set the scale for your entire data set, so that the `x` and `y` values fit your SVG width and height.

- D3 has several scale types. For a linear scale (usually used with quantitative data), there is the D3 method `scaleLinear()`:

```js
const scale = d3.scaleLinear();
```

- By default, a scale uses the identity relationship. The value of the input is the same as the value of the output. A separate challenge covers how to change this.
