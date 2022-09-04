# Mixins
반복되는 코드를 묶어서 관리, 함수처럼 인자를 넘길 수 있음. 코드 반복을 줄이고 HTML 내에서 non-semantic 클래스 사용 빈도를 줄여줌 (ex: .float-left 등등)
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
위 예제에서 mixin보다 @extend를 사용하는 것이 css로 컴파일 되었을 때 불필요한 코드를 줄일 수 있을 것으로 보인다
```scss 
.btn {
  text-decoration: none;
  cursor: pointer;
  display: inline-block;
  border: 0;
  background-color: transparent;
}

@each $k, $v in $colors {
  .btn-#{$k} {
    @extend .btn;
    background-color: $v;
  }
}
```


