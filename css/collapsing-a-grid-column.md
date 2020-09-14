# Collapsing a grid column

Just found out that `grid-template-columns` accepts `auto` as a value!

Which means that if you need a collapsable sidebar you can define it in the css as follows:

```css
body {
  display: grid;
  grid-template-columns: auto 1fr;
}

.sidebar {
  width: 0;
  transition: all 1s;
}

.sidebar.open {
  width: 300px;
}
```

Now, as soon as the class `open` is added to the sidebar it will be `300px` wide,
and of course the other `div`, will take up the rest of the screen width because of the `1fr`. 
