dm-reader
----------

Reads a Daily Mail article from dailymail.co.uk

## Install

```
npm install nbc-reader --save
```

## Use

```
   var DMReader = require('dm-reader');
   var dmreader = new DMReader();

   // Promise
   dmreader.read('http://www.dailymail.co.uk/news/article-3286124/Four-injured-car-crashes-pavement-Guildford-Surrey.html').then(function(article) {
      // Do Something with Article
   });

   // Callback
   dmreader.read('http://www.dailymail.co.uk/news/article-3286124/Four-injured-car-crashes-pavement-Guildford-Surrey.html', function(article) {
      // Do Something with Article
   });
```

## Article

```
var Article = {
   title: '',
   datetime: '',
   body: {
      clean: '',
      minimal: ''
   },
   images: [
      {
         full: ''
      }
   ],
   source: ''
};
```

**title**
The title of the Article. What appears in the h1 on the page.

**datetime**
The datetime with timezone of the last update of the article. Format: `YY-mm-dd H:i:s GMT`. The datetime will always be `GMT+0000`.

**body**
The body of the article. Comes in two formats. *clean* and *minimal*. The clean format removes all html elements and separates paragraphs by two newlines. The minimal format uses `sanitize-html` to remove all html elements except for `'p', 'cite', 'b', 'i', 'em', 'strong', 'a'`.

**images**
An array of image urls found in the body. Comes in sizes `full` for each image.

**source**
The url of the dm article.