Nice work on Agile. Colors look good, too.

Your HTML looks very good. Be careful however with line breaks. You've done an excellent job of (almost) limiting your lines to 80 characters. But see how you pushed a `,` to the next line here:

```html
<p>
  The HTML Article Element (&lt;article&gt;) represents a self-
  contained composition in a document, page, application, or site,
  which is intended to be independently distributable or reusable (e.g.
  , in syndication). This could be a forum post, a magazine or newspaper
   article, a blog entry, an object, or any other independent item of
   content. Each &lt;article&gt;
  should be identified, typically by including a heading (h1-h6 element)
  as a child of the &lt;article&gt; element.
</p>
```

HTML is whitespace insensitive. It collapses space. Between the tag and the content, the space gets collapsed to zero, so there is no differencet between `<em> Hi! </em>` and `<em>Hi!</em>` (prefer the former).

But inside the content, multiple whitespace characters get collapsed to *a single whitespace character*. And the line return counts as a whitespace character. So instead of `e.g.,` you will end up with `e.g. ,` which is probably not what you want. Keep the comma with the content to which it's attached. Break only on whitespace:

```html
<p>
  The HTML Article Element (&lt;article&gt;) represents a self-
  contained composition in a document, page, application, or site,
  which is intended to be independently distributable or reusable (e.g.,
  in syndication). This could be a forum post, a magazine or newspaper
  article, a blog entry, an object, or any other independent item of
  content. Each &lt;article&gt; should be identified, typically by including
  a heading (h1-h6 element) as a child of the &lt;article&gt; element.
</p>
```

Also, try to keep the lines relatively even.

I'm guessing that you didn't pair program? Try to pair program this week.

Your JavaScript looks good! Mostly style issues here. We're using the [standard.js]() style guide. Check it for rules. But this:

```js
var avg(x, y) {
  return (x + y) / 2;
}

var avgOfThree(a, b, c) {
  return (a + b + c) / 3;
}

var isOdd = function (n) {
  if (n % 2 === 0 ) {
    return '0';
  } else {
    return '1';
  }
};
```

Should look like this:

```js
function avg (x, y) {
  return (x + y) / 2
}

function avgOfThree (a, b, c) {
  return (a + b + c) / 3
}

var isOdd = function (n) {
  return n % 2
}
```

Note: No semicolons. Spaces before the `(` on function *definition* and no space before the `(` when *calling* the function. Also note that you made `isOdd` much harder than it needs to be. If `n % 2` returns the 1 or 0 that you want, why bother to convert it to a boolean with `===` only to convert it back to an integer with `if...else`?

And you've kind of mixed up two styles of creating functions. There is the **named** function like this:

```js
function avg (x, y) { return (x + y) / 2 }
```

and the **anonymous** function assigned to a variable, like this:

```js
var avg = function (x, y) { return (x + y) / 2 }
```

See the difference? Also, given that your code is wrong, I'm guessing that you didn't test these in the REPL. *Always test your code*. Don't just assume you got it right. That's a sure path to embarrassment. Try popping the above into the node REPL and see how they work.

Also, you want your code to be readable, so we don't want to make things *too* terse. But we don't want them too verbose either.

By the way, normally a function name beginning with `is` will return a boolean, not an integer. So we could use the `===` operator:

```js
var isOdd = function (n) { return n % 2 === 1 }
```

Or we could use the trick of converting the "truthy" 1 into a `true` boolean by inverting it twice with the `!` (not) operator:

```js
var isOdd = function (n) { return !!(n % 2) }
```

That works, but notice how much more readable the first version is. Terse code isn't always the most readable. But you will see this `!!` trick in the wild, so good to be aware of it.

Glad you enjoyed the user-centered design stuff. Good work on that and the usability. Important stuff, and so often overlooked!

