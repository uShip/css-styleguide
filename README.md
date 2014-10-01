# uShip CSS Style Guide {

*A mostly reasonable approach to writing CSS*

## <a name='TOC'>Table of Contents</a>

  1. [Syntax](#syntax)
  1. [Naming](#naming)
  1. [CSS3 Compatibility](#css3)
  1. [Performance](#performance)
  1. [Resources](#resources)
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
    ∙∙margin: 0;
    ∙∙padding: 4px;
    }

    /* bad */
    .input {
    ____margin: 0;
    ____padding: 4px;
    }

    /* good */
    .input {
    ∙∙∙∙margin: 0;
    ∙∙∙∙padding: 4px;
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

- Use a `js-` prefix for elements that will be selected and used in Javascript. This lets developers know not to remove or modify these, or risk breaking JS. **Do not style these classes.**

    ```html
    <!-- bad -->
    <div class="user-avatar"></div>

    <!-- good -->
    <div class="js-user-avatar"></div>
    ```

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

- Use [BEM naming conventions](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) - 'block / element / modifier'. See the linked article for a more detailed overview.

    ```css
    /* bad */
    .user-panel {

    }
    .field {

    }
    .active {

    }

    /* good */
    .user-panel {  /* block */

    }
    .user-panel__field {  /* element */

    }
    .user-panel--active {  /* modifier or state */

    }
    ```

- Avoid deeply nesting selectors. This results in very specific rules, which are both not reusable and impossible to override. See BEM guidelines above for a better approach.

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

**Other style guides**

  - [BEM (block, element, modifier)](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
  - [Medium.com's CSS is actually pretty f***ing good.](https://medium.com/@fat/mediums-css-is-actually-pretty-fucking-good-b8e2a6c78b06)

**Books**

  - [HTML & CSS: The Good Parts](http://shop.oreilly.com/product/9780596157616.do) - Ben Henick

**Blogs**

  - [CSS Wizardry](http://csswizardry.com/)

  **[[⬆]](#TOC)**


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