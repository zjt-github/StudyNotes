> 排版
1. 标题
```css
h1, h2, h3, h4, h5, h6,
.h1, .h2, .h3, .h4, .h5, .h6 {
  font-family: @headings-font-family;
  font-weight: @headings-font-weight;
  line-height: @headings-line-height;
  color: @headings-color;

  small,
  .small {
    font-weight: normal;
    line-height: 1;
    color: @headings-small-color;
  }
}

h1, .h1,
h2, .h2,
h3, .h3 {
  margin-top: @line-height-computed;
  margin-bottom: (@line-height-computed / 2);

  small,
  .small {
    font-size: 65%;
  }
}
h4, .h4,
h5, .h5,
h6, .h6 {
  margin-top: (@line-height-computed / 2);
  margin-bottom: (@line-height-computed / 2);

  small,
  .small {
    font-size: 75%;
  }
}

h1, .h1 { font-size: @font-size-h1; }
h2, .h2 { font-size: @font-size-h2; }
h3, .h3 { font-size: @font-size-h3; }
h4, .h4 { font-size: @font-size-h4; }
h5, .h5 { font-size: @font-size-h5; }
h6, .h6 { font-size: @font-size-h6; }
```

2. body文本
```less
p {
  margin: 0 0 (@line-height-computed / 2); //段落下方留出一点空间
}

.lead { // 下方空间大一些，字体大一些，行高高一些
  margin-bottom: @line-height-computed;
  font-size: floor((@font-size-base * 1.15));
  font-weight: 300;
  line-height: 1.4;

  @media (min-width: @screen-sm-min) {
    font-size: (@font-size-base * 1.5);
  }
}
```

3. 强调
```less
small,
.small {
  font-size: floor((100% * @font-size-small / @font-size-base));
}

mark,
.mark {
  background-color: @state-warning-bg;
  padding: .2em;
}
```

4. 对齐
```less
.text-left           { text-align: left; }
.text-right          { text-align: right; }
.text-center         { text-align: center; }
.text-justify        { text-align: justify; }
.text-nowrap         { white-space: nowrap; }
```

5. 变形
```less
.text-lowercase      { text-transform: lowercase; } //小写
.text-uppercase      { text-transform: uppercase; } //大写
.text-capitalize     { text-transform: capitalize; } //首字母大写
```

6. 颜色
```less
.text-muted {
  color: @text-muted;
}
.text-primary {
  .text-emphasis-variant(@brand-primary);
}
.text-success {
  .text-emphasis-variant(@state-success-text);
}
.text-info {
  .text-emphasis-variant(@state-info-text);
}
.text-warning {
  .text-emphasis-variant(@state-warning-text);
}
.text-danger {
  .text-emphasis-variant(@state-danger-text);
}

.bg-primary {
  // Given the contrast here, this is the only class to have its color inverted
  // automatically.
  color: #fff;
  .bg-variant(@brand-primary);
}
.bg-success {
  .bg-variant(@state-success-bg);
}
.bg-info {
  .bg-variant(@state-info-bg);
}
.bg-warning {
  .bg-variant(@state-warning-bg);
}
.bg-danger {
  .bg-variant(@state-danger-bg);
}
```

7. 文章头部
```less
.page-header { // 有一个下划线
  padding-bottom: ((@line-height-computed / 2) - 1);
  margin: (@line-height-computed * 2) 0 @line-height-computed;
  border-bottom: 1px solid @page-header-border-color;
}
```

8. 列表
```less
ul,
ol {
  margin-top: 0;
  margin-bottom: (@line-height-computed / 2);
  ul,
  ol {
    margin-bottom: 0;
  }
}

.list-unstyled { // 去除基本样式
  padding-left: 0;
  list-style: none;
}

.list-inline { // 行排列的列表
  .list-unstyled();
  margin-left: -5px;

  > li {
    display: inline-block;
    padding-left: 5px;
    padding-right: 5px;
  }
}
// 自定义的列表
dl {
  margin-top: 0; // Remove browser default
  margin-bottom: @line-height-computed;
}
dt,
dd {
  line-height: @line-height-base;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0; // Undo browser default
}

// 水平自定义列表
.dl-horizontal {
  dd {
    &:extend(.clearfix all); // Clear the floated `dt` if an empty `dd` is present
  }

  @media (min-width: @dl-horizontal-breakpoint) {
    dt {
      float: left;
      width: (@dl-horizontal-offset - 20);
      clear: left;
      text-align: right;
      .text-overflow();
    }
    dd {
      margin-left: @dl-horizontal-offset;
    }
  }
}
```

9. 其他
```less
// 首字母缩写
abbr[title],
// Add data-* attribute to help out our tooltip plugin, per https://github.com/twbs/bootstrap/issues/5257
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted @abbr-border-color;
}
.initialism {
  font-size: 90%;
  .text-uppercase();
}

// 引用
// 左边有一道很粗的线
blockquote {
  padding: (@line-height-computed / 2) @line-height-computed;
  margin: 0 0 @line-height-computed;
  font-size: @blockquote-font-size;
  border-left: 5px solid @blockquote-border-color;

  p,
  ul,
  ol {
    &:last-child {
      margin-bottom: 0;
    }
  }

  // Note: Deprecated small and .small as of v3.1.0
  // Context: https://github.com/twbs/bootstrap/issues/11660
  footer,
  small,
  .small {
    display: block;
    font-size: 80%; // back to default font-size
    line-height: @line-height-base;
    color: @blockquote-small-color;

    &:before {
      content: '\2014 \00A0'; // em dash, nbsp
    }
  }
}

// 右对齐的引用
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid @blockquote-border-color;
  border-left: 0;
  text-align: right;

  // Account for citation
  footer,
  small,
  .small {
    &:before { content: ''; }
    &:after {
      content: '\00A0 \2014'; // nbsp, em dash
    }
  }
}

// 地址
address {
  margin-bottom: @line-height-computed;
  font-style: normal;
  line-height: @line-height-base;
}
```