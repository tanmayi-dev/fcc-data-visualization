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
  - `selection.text((d) => d)`
