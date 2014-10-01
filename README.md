# uShip CSS Style Guide {

*A mostly reasonable approach to writing CSS*

## <a name='TOC'>Table of Contents</a>

  1. [Syntax](#syntax)
  1. [Naming](#naming)
  1. [Strings](#strings)
  1. [Whitespace](#whitespace)
  1. [CSS3 Compatibility](#css3)
  1. [Performance](#performance)
  1. [Resources](#resources)
  1. [In the Wild](#in-the-wild)
  1. [The CSS Style Guide Guide](#guide-guide)
  1. [License](#license)


## <a name='syntax'>Syntax</a>
- End all property/value pairs with a semicolon

    ```css
    /* bad */
    h3 {
        margin-top: 0
    }

    /* good */
    h3 {
        margin-top: 0;
    }
    ```

- Keep 0-values unitless (no px or em)

    ```css
    /* bad */
    .nav-description {
        margin: 0px;
        padding: 0px;
    }

    /* good */
    .nav-description {
        margin: 0;
        padding: 0;
    }
    ```

- Put a single space between keys and value

    ```css
    /* bad */
    .callout-icon {
        max-height: 80px;
        width:      60px;
        background: #333;
    }

    /* good */
    .callout-icon {
        max-height: 80px;
        width: 60px;
        background: #333;
    }
    ```

- Put a single space between comma-separated values
- Stack combined selector declaration with a new line
    
    ```css
    /* bad */
    h1, h2, h3 { 
        margin: 10px 0;
        padding: 0;
        color: #000;
    }

    /* good */
    h1, 
    h2, 
    h3 { 
        margin: 10px 0;
        padding: 0;
        color: #000;
    }
    ```

- Indent with 4 spaces (not hard tabs). If you're using [Sublime Text](http://www.sublimetext.com/) as your editor, you can enable a setting to have it use spaces when pressing tab.
    ```css
    /* bad */
    .input {
      margin: 0;
      padding: 4px;
    }

    /* good */
    .input {
        margin: 0;
        padding: 4px;
    }
    ```

- Each style key/value pair should be on a new line
    ```css
    /* bad */
    .input {
      margin: 0; padding: 4px; color: rgb(33, 33, 33);
    }

    /* good */
    .input {
        margin: 0;
        padding: 4px;
        color: rgb(33, 33, 33);
    }
    ```

- Use single quotes for quoted values

    ```css
    /* bad */
    p {
        font-family: "Comic Sans", Verdana;
    }

    /* good */
    p {
        font-family: 'Comic Sans', Verdana;
    }
    ```

## <a name='naming'>Naming</a>
- Use semantic class names and IDs. Don't descibe what the element looks like – describe its purpose.

    ```css
    /* bad */
    .red-text {
        color: rgb(255, 0, 0);
    }

    /* good */
    .error {
        color: rgb(255, 0, 0);
    }
    ```

- Avoid deeply nesting selectors. This results in very specific rules, which are both not reusable and impossible to override

    ```css
    /* bad */
    .article .sidebar .caption {

    }

    /* good */
    .article__sidebar__caption {

    }
    ```

- Don't use IDs for styling. They are overly specific and difficult to override. Use classes for almost all styling – class names are the contract between your HTML and CSS.

    ```css
    /* bad */
    #widget {

    }

    /* good */
    .widget {

    }
    ```

## <a name='variables'>Variables</a>

  - Always use `var` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace. Captain Planet warned us of that.

    ```javascript
    // bad
    superPower = new SuperPower();

    // good
    var superPower = new SuperPower();
    ```

  - Assign variables at the top of their scope. This helps avoid issues with variable declaration and assignment hoisting related issues.

    ```javascript
    // bad
    function () {
        test();
        console.log('doing stuff..');

        //..other stuff..

        var name = getName();

        if (name === 'test') {
            return false;
        }

        return name;
    }

    // good
    function () {
        var name = getName();

        test();
        console.log('doing stuff..');

        //..other stuff..

        if (name === 'test') {
            return false;
        }

        return name;
    }

    // bad
    function () {
        var name = getName();

        if (!arguments.length) {
            return false;
        }

        return true;
    }

    // good
    function () {
        if (!arguments.length) {
            return false;
        }

        var name = getName();

        return true;
    }
    ```

    **[[⬆]](#TOC)**


## <a name='comments'>Comments</a>

  - Use `/** ... */` for multiline comments. Include a description, specify types and values for all parameters and return values.

    ```javascript
    // bad
    // make() returns a new element
    // based on the passed in tag name
    //
    // @param <String> tag
    // @return <Element> element
    function make (tag) {

        // ...stuff...

        return element;
    }

    // good
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param <String> tag
     * @return <Element> element
     */
    function make (tag) {

        // ...stuff...

        return element;
    }
    ```

  - Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment.

    ```javascript
    // bad
    var active = true;  // is current tab

    // good
    // is current tab
    var active = true;

    // bad
    function getType () {
        console.log('fetching type...');
        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }

    // good
    function getType () {
        console.log('fetching type...');

        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }
    ```

  - Prefixing your comments with `FIXME` or `TODO` helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented. These are different than regular comments because they are actionable. The actions are `FIXME -- need to figure this out` or `TODO -- need to implement`.

  - Use `// FIXME:` to annotate problems

    ```javascript
    function Calculator () {

        // FIXME: shouldn't use a global here
        total = 0;

        return this;
    }
    ```

  - Use `// TODO:` to annotate solutions to problems

    ```javascript
    function Calculator () {

        // TODO: total should be configurable by an options param
        this.total = 0;

        return this;
    }
  ```

    **[[⬆]](#TOC)**


## <a name='whitespace'>Whitespace</a>

  - In general, keep lines short. Use newlines between blocks or chunks of related code.

    ```javascript
    // bad
    self.weightUnits = ko.computed(function () {
        return (self.systemOfMeasurement() === 'Metric') ? uship.localization['MainKg'] : uship.localization['MainLbs'];
    });
    function anotherFunction () {
        var foo = 1;
    }

    // good
    self.weightUnits = ko.computed(function () {
        return (self.systemOfMeasurement() === 'Metric') ? 
            uship.localization['MainKg'] : 
            uship.localization['MainLbs'];
    });

    function anotherFunction () {
        var foo = 1;
    }
    ```

  - Use soft tabs set to 4 spaces. Don't mix hard tabs and spaces.

    ```javascript
    // bad
    function() {
    ____var name;
    }

    // bad
    function() {
    ∙∙var name;
    }

    // bad
    function() {
    ∙var name;
    }

    // good
    function() {
    ∙∙∙∙var name;
    }
    ```

  - Place 1 space before the leading brace. For function declarations, place 1 space between the function keyword and the arguments list.

    ```javascript
    // bad
    function test(){
        console.log('test');
    }

    // bad
    function test() {
        console.log('test');
    }

    // good
    function test () {
        console.log('test');
    }

    // bad
    dog.set('attr',{
        age: '1 year',
        breed: 'Bernese Mountain Dog'
    });

    // good
    dog.set('attr', {
        age: '1 year',
        breed: 'Bernese Mountain Dog'
    });
    ```

  - Set off operators with spaces.

    ```javascript
    // bad
    var x=y+5;

    // good
    var x = y + 5;
    ```

  - Use a newline between key/value pairs in an object literal. Place 1 space between keys and values. You can choose to tab-align values as long as the result is more readable.

    ```javascript
    // bad
    var dog = { breed: 'Maltese', color: 'white', age: '3 years' };

    // bad
    var dog = { 
        breed:'Maltese',
        color:'white',
        age:'3 years' 
    };

    // good
    var dog = { 
        breed: 'Maltese',
        color: 'white',
        age: '3 years' 
    };

    // bad
    var dog = { 
        breed:                                             'Maltese',
        color:                                             'white',
        age:                                               '3 years',
        aReallyLongPropertyNameMakesAlignmentHardToRead: true
    };

    // acceptable
    var dog = { 
        breed:    'Maltese',
        color:    'white',
        age:      '3 years',
        adorable: 'obviously'
    };
    ```

  - Use indentation when making long method chains.

    ```javascript
    // bad
    $('#items').find('.selected').highlight().end().find('.open').updateCount();

    // good
    $('#items')
        .find('.selected')
            .highlight()
            .end()
        .find('.open')
            .updateCount();

    // bad
    var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
        .attr('width',  (radius + margin) * 2).append('svg:g')
        .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
        .call(tron.led);

    // good
    var leds = stage.selectAll('.led')
            .data(data)
        .enter().append('svg:svg')
            .class('led', true)
            .attr('width',  (radius + margin) * 2)
        .append('svg:g')
            .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
            .call(tron.led);
    ```

    **[[⬆]](#TOC)**


## <a name='naming-conventions'>Naming Conventions</a>

  - Avoid single letter names. Be descriptive with your naming.

    ```javascript
    // bad
    function q () {
        // ...stuff...
    }

    // good
    function query () {
        // ..stuff..
    }
    ```

  - Use camelCase when naming objects, functions, and instances

    ```javascript
    // bad
    var OBJEcttsssss = {};
    var this_is_my_object = {};
    function c () {};
    var u = new user({
        name: 'Bob Parr'
    });

    // good
    var thisIsMyObject = {};
    function thisIsMyFunction () {};
    var user = new User({
        name: 'Bob Parr'
    });
    ```

  - Use PascalCase when naming constructors or classes

    ```javascript
    // bad
    function user (options) {
        this.name = options.name;
    }

    var bad = new user({
        name: 'nope'
    });

    // good
    function User (options) {
        this.name = options.name;
    }

    var good = new User({
        name: 'yup'
    });
    ```

  - Use a leading underscore `_` when naming private properties

    ```javascript
    // bad
    this.__firstName__ = 'Panda';
    this.firstName_ = 'Panda';

    // good
    this._firstName = 'Panda';
    ```

    **[[⬆]](#TOC)**

## <a name='modules'>Modules</a>

  - Wrap the function expression in parentheses.
  - The module should start with a `;`. This ensures that if a malformed module forgets to include a final semicolon there aren't errors in production when the scripts get concatenated. [Explanation](https://github.com/airbnb/javascript/issues/44#issuecomment-13063933)
  - The file name should match the name of the single export. Casing should follow the same rules as the export -- e.g. a module that exports a constructor should be PascalCase.
  - Add a method called noConflict() that sets the exported module to the previous version and returns this one.
  - Always declare `'use strict';` at the top of the module.

    ```javascript
    // fancyInput/fancyInput.js

    ;(function (global) {
        'use strict';

        var previousFancyInput = global.FancyInput;

        function FancyInput (options) {
            this.options = options || {};
        }

        FancyInput.noConflict = function noConflict () {
            global.FancyInput = previousFancyInput;
            return FancyInput;
        };

        global.FancyInput = FancyInput;
    })(this);
    ```

    **[[⬆]](#TOC)**


## <a name='css3'>CSS3 Compatibility</a>

  - Refer to this [CSS3 compatibility table](http://caniuse.com/#cats=CSS)

  **[[⬆]](#TOC)**


## <a name='performance'>Performance</a>

  - [Writing efficient CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS)
  - [CSS performance revisited](http://benfrain.com/css-performance-revisited-selectors-bloat-expensive-styles/)
  - [css-perf](https://github.com/mdo/css-perf)
  - [Prioritize visible content](https://developers.google.com/speed/docs/insights/PrioritizeVisibleContent)

  **[[⬆]](#TOC)**


## <a name='resources'>Resources</a>

**Other Style guides**

  - [BEM (block, element, modifier)](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
  - [Medium.com's CSS is actually pretty f***ing good.](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)

**Books**

  - [HTML & CSS: The Good Parts](http://shop.oreilly.com/product/9780596157616.do) - Ben Henick

**Blogs**

  - [CSS Wizardry](http://csswizardry.com/)

  **[[⬆]](#TOC)**

## <a name='guide-guide'>The JavaScript Style Guide Guide</a>

  - [Reference](https://github.com/airbnb/javascript/wiki/The-JavaScript-Style-Guide-Guide)


## <a name='license'>License</a>

(The MIT License)

Copyright (c) 2014 uShip

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#TOC)**

# }