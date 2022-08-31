# Maps
```scss
// create map
$colors: (
  'primary': $primary;
  'blue': #00f;
);

// get value 
map-get($colors, "purple");

// check if the key exist
map-has-key($colors, "secondary");

// remove key
map-remove($colors, "primary");

// merge maps
map-merge($colors, ("secondary": $secondary));

$pastel-colors: ("pink": #ffc0cb);
$new-palette: map-merge($colors, $pastel-colors);
```

