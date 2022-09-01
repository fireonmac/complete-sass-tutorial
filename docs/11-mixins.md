# Mixins
반복되는 코드를 함수처럼 묶어서 관리, 인자를 넘길 수 있음. 기본적으로 코드 반복을 줄이고 자연스레 non-semantic 클래스 사용이 적어지게 됨 (ex: .float-left 등등)
## Syntax
### Baisc Usage without argument
```scss
@mixin btn {
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: 0;
}

.btn {
  @include btn
}
```
### Argument
```scss 
@mixin btn($bg-color: transparent) { // can pass a default value
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: 0;
  background-color: $bg-color;
}

.btn {
  @include btn($primary);
}
```

## Caution
Sass 파일 내에서의 불필요한 반복을 줄여주는 것은 좋지만 컴파일 된 CSS 파일의 최적화가 힘들어질지도, 이에 관한 적절한 사용 예시 분석 및 실제 퍼포먼스에 얼마나 영향이 어떻게 미칠지 확인 및 정리가 추가적으로 필요함
### Before Compilation (Sass)
```scss
@each $key, $val in $colors {
  .btn-#{$key} {
    @include btn($val)
  }
}
```
### After Compilation (CSS)
```scss
.btn-primary {
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: 0;

  background-color: #326dee;
}

.btn-secondary {
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: 0;

  background-color: #326dee;
}

// other btn theme classes will continue ...
// the only difference between these classes is background-color
// removing repeatition in sass can lead to creating new one in css :(
```

### My Perspective 
mixin은 유틸리티 클래스를 대체하는 용도로 사용하는 효율적일 것으로 예상함
```scss 
@mixin flex-center($direction: 'both') {
  display: flex;

  @if ($direction == 'horizontal') {
    justify-content: center;
  } @else if ($direction == 'vertical') {
    align-items: center;
  } @else {
    justify-content: center;
    align-items: center;
  }
}
```


