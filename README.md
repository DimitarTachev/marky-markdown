# marky-markdown 

The thing npm uses to clean up READMEs and other markdown files

## Installation

Download node at [nodejs.org](http://nodejs.org) and install it, if you haven't already.

```sh
npm install marky-markdown --save
```

## Usage

```js
var marky = require("marky-markdown")

// Clean up a regular old markdown string
var html = marky("# hello, I'm markdown").html()

// Or pass in an npm `package` object to do stuff like:
// - rewrite relative URLs to their absolute equivalent on github;
// - normalize package metadata with redundant readme content;
var html = marky("# hello, I am the foo readme", {
  package: {
    name: "foo"
    name: "foo is a thing"
    repository: {
      type: "git",
      url: "https://github.com/kung/foo"
    }
  }
}).html()

```

## Tests

```sh
npm install
npm test
```
```

> marky-markdown@1.0.4 test /Users/z/personal/marky-markdown
> mocha
  marky-markdown
    ✓ is a function 
    ✓ accepts a markdown string and returns a cheerio DOM object 
    ✓ throws an error if first argument is not a string 
    ✓ throws an error if second argument is present but not an object 
  markdown processing and syntax highlighting
    ✓ preserves query parameters in URLs when making them into links 
    ✓ converts github flavored fencing to code blocks 
    ✓ adds js class to javascript blocks 
    ✓ adds sh class to shell blocks 
    ✓ adds sh class to shell blocks 
    ✓ adds hljs class to all blocks 
    ✓ applies inline syntax highlighting classes to javascript 
    ✓ applies inline syntax highlighting classes to shell 
    ✓ applies inline syntax highlighting classes to coffeesript 
  sanitize
    ✓ removes script tags 
    ✓ allows img tags 
    ✓ allows h1/h2/h3/h4/h5/h6 tags to preserve their dom id 
    ✓ removes classnames from elements 
    ✓ allows classnames on code tags 
    ✓ disallows iframes from sources other than youtube 
  badges
    ✓ adds a badge class to img tags containing badge images 
    ✓ adds a badge-only class to p tags containing nothing more than a badge 
  gravatar
    ✓ replaces insecure gravatar img src URLs with secure HTTPS URLs 
    ✓ leaves secure gravatar URLs untouched 
    ✓ leaves non-gravtar URLs untouched 
  github
    when package repo is on github
      ✓ rewrites relative links hrefs to absolute 
      ✓ rewrites slashy relative links hrefs to absolute 
      ✓ leaves protocol-relative URLs alone 
      ✓ leaves hashy URLs alone 
    when package repo is NOT on github
      ✓ leaves relative URLs alone 
      ✓ leaves slashy relative URLs alone 
      ✓ leaves protocol-relative URLs alone 
      ✓ leaves hashy URLs alone 
  youtube
    ✓ wraps iframes in a div for stylability 
    ✓ removes iframe width and height properties 
    ✓ preserves src, frameborder, and allowfullscreen properties 
  packagize
    name
      ✓ prepends an h1.package-name element into readme with value of package.name 
      ✓ adds .package-name-redundant class to first h1 if it's similar to package.name 
      ✓ leaves first h1 alone if it differs from package.name 
    description
      ✓ prepends package.description in a p.package-description element 
      ✓ adds .package-description-redundant class to first h1 if it's similar to package.description 
      ✓ leaves first h1 alone if it differs from package.description 
      ✓ adds .package-description-redundant class to first p if it's similar to package.description 
      ✓ leaves first p alone if it differs from package.description 
  fixtures
    ✓ is a key-value object 
    ✓ contains stringified markdown files as values 
  headings
    ✓ injects hashy anchor tags into headings that have DOM ids 
    ✓ adds deep-link class to modified headings 
    ✓ doesn't inject anchor tags into headings that already contain anchors 
  frontmatter
    ✓ rewrites HTML frontmatter as <meta> tags 
  cdn
    when serveImagesWithCDN is true
      ✓ replaces relative img URLs with npm CDN URLs 
      ✓ replaces slashy relative img URLs with npm CDN URLs 
      ✓ leaves protocol relative URLs alone 
      ✓ leaves HTTPS URLs alone 
    when serveImagesWithCDN is false (default)
      ✓ leaves relative img along 
      ✓ leaves slashy relative img URLs alone 
      ✓ leaves protocol relative URLs alone 
      ✓ leaves HTTPS URLs alone 
  real readmes in the wild
    express
      ✓ successfully parses readme.md 
      ✓ syntax highlights javascript 
      ✓ adds package name h1 
      ✓ identifies and marks redundant package description, even when it is not the the first paragraph 
    benchmark
      ✓ successfully parses 
      ✓ linkifies headings 
  63 passing (2s)

```

## Dependencies

- [cheerio](https://github.com/cheeriojs/cheerio): Tiny, fast, and elegant implementation of core jQuery designed specifically for the server
- [github-url-to-object](https://github.com/zeke/github-url-to-object): Extract user, repo, and other interesting properties from GitHub URLs
- [highlight.js](https://github.com/isagalaev/highlight.js): Syntax highlighting with language autodetection.
- [html-frontmatter](https://github.com/zeke/html-frontmatter): Extract key-value metadata from HTML comments
- [lodash](https://github.com/lodash/lodash): A utility library delivering consistency, customization, performance, &amp; extras.
- [marked](https://github.com/chjj/marked): A markdown parser built for speed
- [sanitize-html](https://github.com/punkave/sanitize-html): Clean up user-submitted HTML, preserving whitelisted elements and whitelisted attributes on a per-element basis
- [similarity](https://github.com/zeke/similarity): How similar are these two strings?

## Dev Dependencies

- [mocha](https://github.com/mochajs/mocha): simple, flexible, fun test framework


## License

ISC

_Generated by [package-json-to-readme](https://github.com/zeke/package-json-to-readme)_
