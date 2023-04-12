# JavaScript and jQuery app structure
JavaScript and jQuery app structure is an app directory, file naming, and code design convention, designed to help you in simple web app development. It gives a solid base for JavaScript and jQuery organization by suggesting an intentionally-limited set of patterns and rules to be combined in a meaningful way.

## Background
JavaScript and jQuery app structure is inspired by Jon Ducket's [Javascript & jQuery](https://javascriptbook.com), and James Padolsey's [Clean Code in JavaScript](https://www.sitepoint.com/premium/books/clean-code-in-javascript) books, and promotes JavaScript architectural  best practices.

JavaScript and jQuery app structure is designed for simple, basic web apps, and doesn't assume the use of modern frameworks like Angular or React, which would benefit likely from a different setup.

## Usage
### App directory structure
- Create a file for all JavaScript and jQuery projects e.g. `app.js`. For simple apps with only a few lines of code you might not need other files.

```
.
└── js
    └── app.js
```

- Create additional files for code that is self-contained, or doesn't run on all pages, e.g.  `feature.js` .
```
.
└── js
    ├── app.js
    └── feature.js
```

### File naming
- Name files accordingly to their feature within your app, e.g. `feature.js`.
- Name files with a prefix when writing a jQuery plugin, e.g. `jquery.plugin.js`.
- We consider all files are modules.

### Code design
- Put file contents in an IIFE to prevent conflicts between two scripts that might use the same variable names.
``` js
(function() {
  // Content
}());
```

- Create objects to group together a set of variables and functions to create a model of data that belong together.
``` js
var activity = {
  kilometers: 10,
  minutes: 40,
  name: 'Running',
  checkPace: function() {
    return this.minutes / this.kilometers . 'minutes per kilometer';
  }
};
```
- Declare named functions for repeating parts of a script by function declarations.
``` js
function doSomething() {
  // Code
}
```

- Declare an initializing function if there're multiple named funtions in your file.
``` js
function init() {
  doSomethingFirst();
  doSomethingElse();
}

$(init);
```

- Initialize functions and methods in the file they were declared in, if possible.
- Use the module pattern design pattern to write code that contains both public and private logic. (Modules reference here any piece of code that is distinct, and not _Modules_ as prescribed by ECMASript specifications.)

Declare the module object, and create its methods by an IIFE.

``` js
var feature = (function() {
  // Private code
  return {
    // Public code
    method: function () {
      // Code
    }
  };
}());
```

### Others
- Use classes to select items, if possible, e.g. `$('.js-item')`.
- Use classes prefixes in your HTML for JavaScript selectors, e.g. `js-`.
- Use JavaScript and jQuery for behavior only, even if a method is available for presentation. For example write `$('.js-item').addClass('d-none');` instead of `$('.js-item').hide();`.

## Roadmap
- Add naming conventions variables
- Add related resources
- TODO

## Contributing
Pull requests are not yet welcome. For support requests, please open an issue first to discuss what you would like to change.

## License
[MIT](https://github.com/martonlente/javascript-and-jquery-app-structure/blob/main/LICENSE)
