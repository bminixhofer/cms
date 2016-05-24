# atomicms

Static html cms inspired by [atomic design](http://bradfrost.com/blog/post/atomic-web-design).

## Example
````
const express = require('express');
let app = express();

const atomicms = require('atomicms');
let cms = new atomicms();

app.get('/', cms.requestHandler);
````

## API
Atomicms takes an `opts` object specifing the paths of `key.json`, templates, organisms and content.
**Default `opts` object:**
````
{
  key: 'key.json',
  content: 'content',
  template: 'templates',
  organism: 'organisms'
}
````

### key.json
`key.json` is where it comes all together. One `template` and `content` are assigned to one url respectively.

**Example:**
````
{
  '/index': {
    'template': 'index.html',
    'content': 'index.json'
  }
}
````

### Organisms
Organisms can reside in templates and are referenced using ``markup-js`` syntax.

**Example:**

*template [index.html]*
``
<body>
    {{oHeader as header}}
</body>
``

*organism [oHeader.html]*
````
<h1>{{title}}</h1>
<img src={{img}}>
<p><strong>{{content}}</strong></p>
````

*content [index.json]*
````
{
  'header': {
    'title': ...,
    'img': ...,
    'content': ...
  }
````

## Installation
````
npm install atomicms
````