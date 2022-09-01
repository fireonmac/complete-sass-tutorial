# Functions
mixin과 function의 차이는 mixin은 코드 블록을, function은 하나의 값을 리턴한다는 것
## Syntax
```scss
@function light-comp($color) {
  $complement: complement($color);
  $light-complement: lighten($complement, 30%);
  @return $light-complement;
}
```