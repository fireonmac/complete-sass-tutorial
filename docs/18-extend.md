# Using @extend
mixin과 비슷해보이지만 컴파일 된 CSS 파일의 코드에 차이가 있으며 mixin과 달리 argument를 넘길 수 없음
## Syntax 
```scss
// % notation is optional, this will separate extended classes from parent class in bundled CSS
// you can just use dot notation instead
%flex-layout { 
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
}

.navbar {
  padding: $base-padding $base-padding * 2;
  box-shadow: $base-box-shadow;

  .container {
    @extend %flex-layout;  
  }
}

// dot notation
@each $k, $v in $colors {
  .navbar-#{$k} {
    @extend .navbar;
    background-color: $v;
  }
}
```