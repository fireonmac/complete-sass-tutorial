# Loops

## Syntax
### Iterating Map with @each
```scss
@each $key, $val in $colors {
  .text-#{$key} {
    color: $val;
  }

  .bg-#{$key} {
    background-color: $val;
  }
}
```

### For Loop
```scss
@for $i from 1 through 9 {
  .bg-#{$key}-light-#{$i} {
    background-color: mix(#fff, $val, $i * 10);
  }  

  .bg-#{$key}-dark-#{$i} {
    background-color: mix(#000, $val, $i * 10);
  }
}
```


