# markdown-utils [![NPM version](https://badge.fury.io/js/markdown-utils.svg)](http://badge.fury.io/js/markdown-utils)  [![Build Status](https://travis-ci.org/jonschlinkert/markdown-utils.svg)](https://travis-ci.org/jonschlinkert/markdown-utils) 

> Micro-utils for creating markdown snippets.

**Heads up!** `.list()` was removed in 0.6.0. If you still need this functionality use [bullets] instead.

## Install with [npm](npmjs.org)

```bash
npm i markdown-utils --save
```

## Table of Contents

<!-- toc -->

- [Usage](#usage)
- [API](#api)
- [Related](#related)
- [Running tests](#running-tests)
- [Contributing](#contributing)
- [Author](#author)
- [License](#license)

<!-- tocstop -->

## Usage

```js
var mdu = require('markdown-utils');
```

## API
### [.anchor](./index.js#L29)

Create a markdown-formatted anchor link from the given values.

* `anchor` **{String}**    
* `href` **{String}**    
* `title` **{String}**    

```js
utils.anchor('embed', 'assemble/handlebars-helpers/lib/code.js', 25, 'v0.6.0');
//=> [embed](https://github.com/assemble/handlebars-helpers/blob/v0.6.0/lib/helpers/code.js#L25)
```

### [.badge](./index.js#L62)

Create a markdown-formatted badge.

* `alt` **{String}**    
* `img_url` **{String}**    
* `url` **{String}**    

```js
utils.badge(alt, img_url, url);
//=> [![Build Status](https://travis-ci.org/jonschlinkert/template.svg)](https://travis-ci.org/jonschlinkert/template)
```

### [.blockquote](./index.js#L79)

Create a markdown-formatted blockquote.

* `str` **{String}**    

```js
utils.blockquote('This is a blockquote');
//=> '> This is a blockquote'
```

### [.code](./index.js#L96)

Create a markdown-formatted `<code></code>` snippet.

* `str` **{String}**    

```js
utils.code('var foo = bar;');
//=> '`var foo = bar;`'
```

### [.del](./index.js#L113)

Create markdown-formatted `<del></del>`.

* `str` **{String}**    

```js
utils.del('text');
//=> '~~text~~'
```

### [.em](./index.js#L130)

Create a markdown-formatted em.

* `str` **{String}**    

```js
utils.em('This is emphasized');
//=> '_This is emphasized_'
```

### [.h](./index.js#L148)

Create a markdown-formatted heading.

* `str` **{String}**    
* `level` **{Number}**    

```js
utils.h(1, 'This is a heading');
//=> '# This is a heading'
```

### [.h1](./index.js#L165)

Create a markdown-formatted h1 heading.

* `str` **{String}**    

```js
utils.h1('This is a heading');
//=> '# This is a heading'
```

### [.h2](./index.js#L182)

Create a markdown-formatted h2 heading.

* `str` **{String}**    

```js
utils.h2('This is a heading');
//=> '## This is a heading'
```

### [.h3](./index.js#L199)

Create a markdown-formatted h3 heading.

* `str` **{String}**    

```js
utils.h3('This is a heading');
//=> '### This is a heading'
```

### [.h4](./index.js#L216)

Create a markdown-formatted h4 heading.

* `str` **{String}**    

```js
utils.h4('This is a heading');
//=> '#### This is a heading'
```

### [.h5](./index.js#L233)

Create a markdown-formatted h5 heading.

* `str` **{String}**    

```js
utils.h5('This is a heading');
//=> '##### This is a heading'
```

### [.h6](./index.js#L250)

Create a markdown-formatted h6 heading.

* `str` **{String}**    

```js
utils.h6('This is a heading');
//=> '###### This is a heading'
```

### [.heading](./index.js#L268)

Create a markdown-formatted heading.

* `str` **{String}**    
* `level` **{Number}**    

```js
utils.heading('This is a heading', 1);
//=> '# This is a heading'
```

### [.hr](./index.js#L285)

Create a markdown-formatted horizontal rule.

* `str` **{String}**: Alternate string to use. Default is `***` to avoid collision with `---` which is used for front matter.    

```js
utils.hr();
//=> '***'
```

### [.image](./index.js#L307)

Create a markdown-formatted image from the given values.

* `alt` **{String}**    
* `src` **{String}**    
* `title` **{String}**    

```js
utils.image(alt, src);
//=> ![Build Status](https://travis-ci.org/jonschlinkert/template.svg)

utils.image(alt, src, title);
//=> ![Build Status](https://travis-ci.org/jonschlinkert/template.svg "This is title of image!")
```

### [.link](./index.js#L327)

Create a markdown-formatted link from the given values.

* `anchor` **{String}**    
* `href` **{String}**    
* `title` **{String}**    

```js
utils.link('fs-utils', 'https://github.com/assemble/fs-utils', 'hover title');
//=> [fs-utils](https://github.com/assemble/fs-utils "hover title")
```

### [.li](./index.js#L358)

Returns a function to generate a plain-text/markdown list-item, allowing options to be cached for subsequent calls.

* `options` **{String}**  
    - `nobullet` **{Boolean}**: Pass true if you only want the list iten and identation, but no bullets.
    - `indent` **{String}**: The amount of leading indentation to use. default is `  `.
    - `chars` **{String|Array}**: If a string is passed, [expand-range] will be used to generate an array of bullets (visit [expand-range] to see all options.) Or directly pass an array of bullets, numbers, letters or other characters to use for each list item. Default `['-', '*', '+', '~']`
      
* `fn` **{Function}**: pass a function [expand-range] to modify the bullet for an item as it's generated. See the [examples].    

```js
var li = listitem(options);

li(0, 'Level 0 list item');
//=> '- Level 0 list item'

li(1, 'Level 1 list item');
//=> '  * Level 1 list item'

li(2, 'Level 2 list item');
//=> '    + Level 2 list item'
```

### [.pre](./index.js#L382)

Create a markdown-formatted `<pre><code></code></pre>` snippet with or without lang.

* `str` **{String}**    
* `language` **{String}**    

```js
utils.pre('var foo = bar;');
```

Results in:

<pre>
```js
var foo = bar;
```

</pre>

### [.reference](./index.js#L406)

Create a markdown-formatted reference link from the given values.

* `id` **{String}**    
* `url` **{String}**    
* `title` **{String}**    

```js
utils.reference('template', 'https://github/jonschlinkert/template', 'Make stuff!');
//=> [template]: https://github/jonschlinkert/template "Make stuff!"
```

### [.strong](./index.js#L424)

Create markdown-formatted bold text.

* `str` **{String}**    

```js
utils.strong('This is bold');
//=> '**This is bold**'
```

### [.todo](./index.js#L444)

Create a markdown-formatted todo item.

* `str` **{String}**    

```js
utils.todo('this is a todo.');
//=> '- [ ] this is a todo'

utils.todo('this is a completed todo.', true);
//=> '- [x] this is a todo'
```

## Related
* [remarkable](https://github.com/jonschlinkert/remarkable): Markdown parser, done right. 100% Commonmark support, extensions, syntax plugins, high speed - all in one.
* [markdown-toc](https://github.com/jonschlinkert/markdown-toc): Generate a markdown TOC (table of contents) with Remarkable.
* [markdown-link](https://github.com/jonschlinkert/markdown-link): Micro util for generating a single markdown link.
* [gfm-code-blocks](https://github.com/jonschlinkert/gfm-code-blocks): Extract gfm (GitHub Flavored Markdown) fenced code blocks from a string.

## Running tests
Install dev dependencies.

```bash
npm i -d && npm test
```

## Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/markdown-utils/issues)

## Author

**Jon Schlinkert**
 
+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

## License
Copyright (c) 2015 Jon Schlinkert  
Released under the MIT license

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on March 18, 2015._

[bullets]: https://github.com/jonschlinkert/bullets
