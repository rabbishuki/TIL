# max-width for @media query not working

It doesn't happen a lot when you need to build a simple webpage, but that's what I needed.

As I finished the page, I noticed that on mobile it would be better to hide the left header.

So I quickly added the following `css` code:

```css
@media only screen and (max-width: 768px)  {
  .heading-left {
    display: none;
  }
}
```
To my dismay it didn't do anything!

As usual, the solution was simple, I just needed to add the following line to my `html`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

The viewport helps tell the CSS what the actual device-width is.

Without this tag, media queries just MATCH regardless of the condition. 
