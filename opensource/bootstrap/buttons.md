1. 按钮样式
```less
.btn {
  display: inline-block;
  margin-bottom: 0; // For input.btn
  font-weight: @btn-font-weight;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none; // Firefox自带背景图
  border: 1px solid transparent;
  white-space: nowrap;
  .button-size(@padding-base-vertical; @padding-base-horizontal; @font-size-base; @line-height-base; @btn-border-radius-base);
  .button-size(@padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius) {
    padding: @padding-vertical @padding-horizontal;
    font-size: @font-size;
    line-height: @line-height;
    border-radius: @border-radius;
  }
  
  .user-select(none);

  &,
  &:active,
  &.active {
    &:focus,
    &.focus {
      .tab-focus();
    }
  }

  &:hover,
  &:focus,
  &.focus {
    color: @btn-default-color;
    text-decoration: none;
  }

  &:active,
  &.active {
    outline: 0;
    background-image: none;
    .box-shadow(inset 0 3px 5px rgba(0,0,0,.125));
  }

  &.disabled,
  &[disabled],
  fieldset[disabled] & {
    cursor: @cursor-disabled;
    .opacity(.65);
    .box-shadow(none);
  }

  a& {
    &.disabled,
    fieldset[disabled] & {
      pointer-events: none; // Future-proof disabling of clicks on `<a>` elements
    }
  }
}
```

2. 大小颜色不同的按钮
```less
.btn-lg {
  // line-height: ensure even-numbered height of button next to large input
  .button-size(@padding-large-vertical; @padding-large-horizontal; @font-size-large; @line-height-large; @btn-border-radius-large);
}
.btn-sm {
  // line-height: ensure proper height of button next to small input
  .button-size(@padding-small-vertical; @padding-small-horizontal; @font-size-small; @line-height-small; @btn-border-radius-small);
}
.btn-xs {
  .button-size(@padding-xs-vertical; @padding-xs-horizontal; @font-size-small; @line-height-small; @btn-border-radius-small);
}

.btn-default {
  .button-variant(@btn-default-color; @btn-default-bg; @btn-default-border);
}
.btn-primary {
  .button-variant(@btn-primary-color; @btn-primary-bg; @btn-primary-border);
}
// Success appears as green
.btn-success {
  .button-variant(@btn-success-color; @btn-success-bg; @btn-success-border);
}
// Info appears as blue-green
.btn-info {
  .button-variant(@btn-info-color; @btn-info-bg; @btn-info-border);
}
// Warning appears as orange
.btn-warning {
  .button-variant(@btn-warning-color; @btn-warning-bg; @btn-warning-border);
}
// Danger and error appear as red
.btn-danger {
  .button-variant(@btn-danger-color; @btn-danger-bg; @btn-danger-border);
}
.button-variant(@color; @background; @border) {
  color: @color;
  background-color: @background;
  border-color: @border;

  &:focus,
  &.focus {
    color: @color;
    background-color: darken(@background, 10%);
        border-color: darken(@border, 25%);
  }
  &:hover {
    color: @color;
    background-color: darken(@background, 10%);
        border-color: darken(@border, 12%);
  }
  &:active,
  &.active,
  .open > .dropdown-toggle& {
    color: @color;
    background-color: darken(@background, 10%);
        border-color: darken(@border, 12%);

    &:hover,
    &:focus,
    &.focus {
      color: @color;
      background-color: darken(@background, 17%);
          border-color: darken(@border, 25%);
    }
  }
  &:active,
  &.active,
  .open > .dropdown-toggle& {
    background-image: none;
  }
  &.disabled,
  &[disabled],
  fieldset[disabled] & {
    &:hover,
    &:focus,
    &.focus {
      background-color: @background;
          border-color: @border;
    }
  }

  .badge {
    color: @background;
    background-color: @color;
  }
}
```

3. btn-link
```less
.btn-link {
  color: @link-color;
  font-weight: normal;
  border-radius: 0;

  &,
  &:active,
  &.active,
  &[disabled],
  fieldset[disabled] & {
    background-color: transparent;
    .box-shadow(none);
  }
  &,
  &:hover,
  &:focus,
  &:active {
    border-color: transparent;
  }
  &:hover,
  &:focus {
    color: @link-hover-color;
    text-decoration: @link-hover-decoration;
    background-color: transparent;
  }
  &[disabled],
  fieldset[disabled] & {
    &:hover,
    &:focus {
      color: @btn-link-disabled-color;
      text-decoration: none;
    }
  }
}
```

4. btn-block
```less
.btn-block {
  display: block;
  width: 100%;
}

// Vertically space out multiple block buttons
.btn-block + .btn-block {
  margin-top: 5px;
}

// Specificity overrides
input[type="submit"],
input[type="reset"],
input[type="button"] {
  &.btn-block {
    width: 100%;
  }
}
```
