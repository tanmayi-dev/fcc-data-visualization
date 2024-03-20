# Data Visualization

## Data Visualization with D3

- D3 has several methods that let us add and change elements in document

- `select()` :
  - This method selects one element from the document.
  - It takes an argument for the name of the element and returns an HTML node for the first element in the document that matches the name.
- `append()` :
  - This method takes an argument for the element you want to add to the document.
  - It appends an HTML node to a selected item, and returns a handle to that node.
- `text()` :
  - This method either sets the text of the selected node, or gets the current text.
  - To set the value, you pass a string as an argument inside the parentheses of the method.
- `selectAll()` :
  - Method to select a group of elements.
  - It returns an array of HTML nodes for all the items in the document that match the input string.
  - It supports method chaining like `select()`
