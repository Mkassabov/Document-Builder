# Document Builder

## Project description
Rough document builder made with vue.js and bootstrap through bootstrap-vue.js.
Save feature currently prints a JS object to the console describing the document.
Rows can't currently be moved or removed. In order to remove a Row the entire document needs to be scrapped. Adding a feature to remove individual rows shouldn't be dificult.
Text and Headings are editable, all other elements are not. Images get a random image from picsum.photos. Dropdown menu's have 3 preset options, input fields have preset placeholders. Making all components editable shouldn't be difficult to do.

Rows are based on bootstrap rows and their width of 12. Due to the program structure allowing multiple components side by side wouldn't be difficult to implement. Each document component is its own vue component, adding more is a simple task.


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
