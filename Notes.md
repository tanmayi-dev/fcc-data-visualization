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
