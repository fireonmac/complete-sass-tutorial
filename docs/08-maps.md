# Maps

## Syntax
### Creating Map
```scss
$colors: (
  'primary': $primary;
  'blue': #00f;
);
```
### Getting a Value
```scss
map-get($colors, "purple");
```

### Cheking If a Key Exist
```scss
map-has-key($colors, "secondary");
```

### Removing a Key
```scss 
map-remove($colors, "primary");  
```

### Merging Maps
```scss
map-merge($colors, ("secondary": $secondary));

$pastel-colors: ("pink": #ffc0cb);

$new-palette: map-merge($colors, $pastel-colors);
```

