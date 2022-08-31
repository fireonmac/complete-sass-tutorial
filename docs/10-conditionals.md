# Conditionals (@if)

## Syntax
```scss
// case 1
@if (5 < 10) {
  .test-if { ... }
} @else {
  .test-if-2 { ... }
}

// case 2
@if ($val != #000 and $val != #fff) {
  .test-if-3 { ... }
}

// case 3
@if ($val != #000 or math.floor(math.div($base-padding , $base-margin)) == 1) {
  .test-if-3 { ... }
}

// case 4
@if (map-has-key($colors, "white")) {
  .test-if-3 { ... }
}

// case 5
@if (
  math.floor(math.div($base-padding, $base-margin)) == 1
  or math.floor(math.div($base-padding, $base-margin)) > 10
) {
  .test-if-4 { ... }
} @else if (...) {
  .test-if-5 { ... }
} @else {
  .test-if-6 { ... }
}
```