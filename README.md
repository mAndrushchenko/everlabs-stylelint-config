# Everlabs stylelint config
The [``.stylelintrc.yml``](.stylelintrc.yml) includes the list of rules for SCSS that help you avoid errors and enforce conventions in your styles.


## Installation


### 1. Stylelint
```
npm install stylelint --save-dev
```


### 2. CSS and SCSS stylelint configs
```
npm install stylelint-config-standard-scss --save-dev
```


### 3. Stylelint rules order
```
npm install stylelint-config-rational-order --save-dev
```


### 4. Also need to install ``postcss``
```
npm install postcss --save-dev
```
This library is needed to read custom rules


### 5. Copy file [``.stylelintrc.yml``](.stylelintrc.yml) and paste it to the root folder in the project


### 6. Now need to enable linter in the IDE


#### For JetBrains (Webstorm, Rubymine)
Open **File/settings**. In search input type **stylelint**. Then check **Enable**:

![jet_brains_step_1](assets/jetbrains_step_1.png)

Click on 3 dots and select``node-modules/stylelint``. Than click on **Apply** and **OK**:

![jet_brains_step_1](assets/jetbrains_step_2.png)

Now linter should working.


#### For Visual Code
First need to install plugins **Prettier** and **Stylelint**:

![jet_brains_step_1](assets/vs_step_1.png)

Open **file/preferences/settings**. Then turn on the JSON mode for the settings (as on screen below)

![jet_brains_step_1](assets/vs_step_2.png)

Now need to add (don't replace) to the ``settings.json`` next rules:
```json
{
  "stylelint.enable": true,
  "stylelint.validate": [
    "css",
    "scss"
  ],
  "css.validate": false,
  "scss.validate": false,
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```
Don't forget to save file and then linter should works.


### 7. Add script to ``package.json``

```json
{
  "scripts": {
    "lint-css": "npx stylelint '[YOUR_PATH]/**/*.scss' --fix"
  }
}
```

Replace ``[YOUR_PATH]`` to path from your root folder of the project to folder where you store styles. If you don't need autofix, delete ``--fix``.


### 8. Lets test!
For start testing your project, run the command below:
```
npm run lint-css
```


## Customisation


You can extend [``.stylelintrc.yml``](.stylelintrc.yml) file by adding other rules. For example your project has SCSS files that should not be linted. You can add this files to the list:

```yaml
ignoreFiles: [
  # Exclude all min.scss files
  "**/*.min.scss",

  # Exclude vendors
  "**/vendors/**/*.scss",
  
  # Your files
  "**/example_file.scss"
]
```

Also you can disable or enable some rules that doesn't fit to your project:

```yaml
rules:
  color-named: null
  # other rules...
```

The list of rules:
- [CSS](https://stylelint.io/user-guide/rules/list)
- [SCSS](https://github.com/stylelint-scss/stylelint-scss#list-of-rules)
- [Rules order](https://github.com/hudochenkov/stylelint-order)
- [Example config with order rules](https://github.com/maxdenaro/maxgraph-youtube-source/blob/master/stylelint/.stylelintrc)

 For disabling specific line write ``/* stylelint-disable-next-line [RULE_NAME] */``:
```scss
.list-item {
  /* stylelint-disable-next-line color-named */
  color: green;
}
```
More about ignoring rules in the files you can find [here](https://stylelint.io/user-guide/ignore-code/)


## Extends


Everlabs config extends:
- [stylelint-config-standard-scss](https://github.com/stylelint-scss/stylelint-config-standard-scss)
- [stylelint-config-rational-order](https://github.com/constverum/stylelint-config-rational-order)

The ``stylelint-config-standard-scss`` in turn under hood extends others:
- [stylelint-config-recommended](https://stylelint.io/user-guide/rules/list/#avoid-errors)
- [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard/blob/main/index.js)
- [stylelint-config-recommended-scss](https://github.com/stylelint-scss/stylelint-config-recommended-scss)


## Rules
- [alpha-value-notation](#alpha-value-notation) (autofixable)
- [at-rule-empty-line-before](#at-rule-empty-line-before) (autofixable)
- [at-rule-name-case](#at-rule-name-case) (autofixable)
- [at-rule-name-space-after](#at-rule-name-space-after) (autofixable)
- [at-rule-no-vendor-prefix](#at-rule-no-vendor-prefix) (autofixable)
- [at-rule-semicolon-newline-after](#at-rule-semicolon-newline-after) (autofixable)
- [block-closing-brace-empty-line-before](#block-closing-brace-empty-line-before) (autofixable)
- [block-closing-brace-newline-after](#block-closing-brace-newline-after) (autofixable)
- [block-closing-brace-newline-before](#block-closing-brace-newline-before) (autofixable)
- [block-closing-brace-space-before](#block-closing-brace-space-before) (autofixable)
- [block-opening-brace-newline-after](#block-opening-brace-newline-after) (autofixable)
- [block-opening-brace-space-after](#block-opening-brace-space-after) (autofixable)
- [block-opening-brace-space-before](#block-opening-brace-space-before) (autofixable)
- [color-hex-case](#color-hex-case) (autofixable)
- [color-hex-length](#color-hex-length) (autofixable)
- [comment-empty-line-before](#comment-empty-line-before) (autofixable)
- [comment-whitespace-inside](#comment-whitespace-inside) (autofixable)
- [custom-property-empty-line-before](#custom-property-empty-line-before) (autofixable)
- [custom-media-pattern](#custom-media-pattern)
- [custom-property-pattern](#custom-property-pattern)
- [declaration-bang-space-after](#declaration-bang-space-after) (autofixable)
- [declaration-bang-space-before](#declaration-bang-space-before) (autofixable)
- [declaration-block-semicolon-newline-after](#declaration-block-semicolon-newline-after) (autofixable)
- [declaration-block-semicolon-space-after](#declaration-block-semicolon-space-after) (autofixable)
- [declaration-block-semicolon-space-before](#declaration-block-semicolon-space-before) (autofixable)
- [declaration-block-single-line-max-declarations](#declaration-block-single-line-max-declarations)
- [declaration-block-trailing-semicolon](#declaration-block-trailing-semicolon) (autofixable)
- [declaration-block-no-redundant-longhand-properties](#declaration-block-no-redundant-longhand-properties)
- [declaration-colon-newline-after](#declaration-colon-newline-after) (autofixable)
- [declaration-colon-space-after](#declaration-colon-space-after) (autofixable)
- [declaration-colon-space-before](#declaration-colon-space-before) (autofixable)
- [declaration-empty-line-before](#declaration-empty-line-before) (autofixable)
- [font-family-name-quotes](#font-family-name-quotes) (autofixable)
- [function-comma-newline-after](#function-comma-newline-after) (autofixable)
- [function-comma-space-after](#function-comma-space-after) (autofixable)
- [function-comma-space-before](#function-comma-space-before) (autofixable)
- [function-max-empty-lines](#function-max-empty-lines) (autofixable)
- [function-name-case](#function-name-case) (autofixable)
- [function-parentheses-newline-inside](#function-parentheses-newline-inside) (autofixable)
- [function-parentheses-space-inside](#function-parentheses-space-inside) (autofixable)
- [function-url-quotes](#function-url-quotes)
- [function-whitespace-after](#function-whitespace-after) (autofixable)
- [hue-degree-notation](#hue-degree-notation) (autofixable)
- [import-notation](#import-notation) (autofixable)
- [indentation](#indentation) (autofixable)
- [keyframes-name-pattern](#keyframes-name-pattern)
- [length-zero-no-unit](#length-zero-no-unit) (autofixable)
- [max-empty-lines](#max-empty-lines) (autofixable)
- [max-line-length](#max-line-length)
- [media-feature-colon-space-after](#media-feature-colon-space-after) (autofixable)
- [media-feature-colon-space-before](#media-feature-colon-space-before) (autofixable)
- [media-feature-name-case](#media-feature-name-case) (autofixable)
- [media-feature-name-no-vendor-prefix](#media-feature-name-no-vendor-prefix) (autofixable)
- [media-feature-parentheses-space-inside](#media-feature-parentheses-space-inside) (autofixable)
- [media-feature-range-operator-space-after](#media-feature-range-operator-space-after) (autofixable)
- [media-feature-range-operator-space-before](#media-feature-range-operator-space-before) (autofixable)
- [media-query-list-comma-newline-after](#media-query-list-comma-newline-after) (autofixable)
- [media-query-list-comma-space-after](#media-query-list-comma-space-after) (autofixable)
- [media-query-list-comma-space-before](#media-query-list-comma-space-before) (autofixable)
- [no-empty-first-line](#no-empty-first-line) (autofixable)
- [no-eol-whitespace](#no-eol-whitespace) (autofixable)
- [no-missing-end-of-source-newline](#no-missing-end-of-source-newline) (autofixable)
- [number-leading-zero](#number-leading-zero) (autofixable)
- [number-max-precision](#number-max-precision)
- [number-no-trailing-zeros](#number-no-trailing-zeros) (autofixable)
- [property-case](#property-case) (autofixable)
- [property-no-vendor-prefix](#property-no-vendor-prefix) (autofixable)
- [rule-empty-line-before](#rule-empty-line-before) (autofixable)
- [selector-attribute-brackets-space-inside](#selector-attribute-brackets-space-inside) (autofixable)
- [selector-attribute-operator-space-after](#selector-attribute-operator-space-after) (autofixable)
- [selector-attribute-operator-space-before](#selector-attribute-operator-space-before) (autofixable)
- [selector-attribute-quotes](#selector-attribute-quotes)
- [selector-class-pattern](#selector-class-pattern)
- [selector-combinator-space-after](#selector-combinator-space-after) (autofixable)
- [selector-combinator-space-before](#selector-combinator-space-before) (autofixable)
- [selector-descendant-combinator-no-non-space](#selector-descendant-combinator-no-non-space) (autofixable)
- [selector-id-pattern](#selector-id-pattern)
- [selector-list-comma-newline-after](#selector-list-comma-newline-after) (autofixable)
- [selector-list-comma-space-before](#selector-list-comma-space-before) (autofixable)
- [selector-max-empty-lines](#selector-max-empty-lines) (autofixable)
- [selector-no-vendor-prefix](#selector-no-vendor-prefix) (autofixable)
- [selector-not-notation](#selector-not-notation) (autofixable)
- [selector-pseudo-class-case](#selector-pseudo-class-case) (autofixable)
- [selector-pseudo-class-parentheses-space-inside](#selector-pseudo-class-parentheses-space-inside) (autofixable)
- [selector-pseudo-element-case](#selector-pseudo-element-case) (autofixable)
- [selector-type-case](#selector-type-case) (autofixable)
- [shorthand-property-no-redundant-values](#shorthand-property-no-redundant-values) (autofixable)
- [string-quotes](#string-quotes) (autofixable)
- [unit-case](#unit-case) (autofixable)
- [value-keyword-case](#value-keyword-case) (autofixable)
- [value-list-comma-newline-after](#value-list-comma-newline-after) (autofixable)
- [value-list-comma-space-after](#value-list-comma-space-after) (autofixable)
- [value-list-comma-space-before](#value-list-comma-space-before) (autofixable)
- [value-list-max-empty-lines](#value-list-max-empty-lines) (autofixable)
- [value-no-vendor-prefix](#value-no-vendor-prefix) (autofixable)


## Examples


### [alpha-value-notation](https://stylelint.io/user-guide/rules/list/alpha-value-notation/#percentage)

```yaml
'alpha-value-notation': [
  'percentage',
  {
    exceptProperties: ['opacity'],
  }
]
```


```scss
// doesn't pass the test
a { opacity: 0.5 }

a { color: rgb(0 0 0 / 0.5) }

// passes the test
a { opacity: 50% }

a { color: rgb(0 0 0 / 50%) }
```


### [at-rule-empty-line-before](https://stylelint.io/user-guide/rules/list/at-rule-empty-line-before#always)

```yaml
'at-rule-empty-line-before': [
  'always',
  {
    except: ['blockless-after-same-name-blockless', 'first-nested'],
    ignore: ['after-comment']
  }
]
```


```scss
// doesn't pass the test
a {} @media {}

a {}
@media {}

// passes the test
a {}

@media {}
```


### [at-rule-name-case](https://stylelint.io/user-guide/rules/list/at-rule-name-case#lower)

```yaml
'at-rule-name-case': 'lower'
```


```scss
// doesn't pass the test
@Media (min-width: 50em) {}

@MEDIA (min-width: 50em) {}

// passes the test
@media (min-width: 50em) {}
```


### [at-rule-name-space-after](https://stylelint.io/user-guide/rules/list/at-rule-name-space-after/#always-single-line)

```yaml
'at-rule-name-space-after': 'always-single-line'
```


```scss
// doesn't pass the test
@media(min-width: 700px) {}

@media  (min-width: 700px) {}

// passes the test
@media (min-width: 700px) {}
```


### [at-rule-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/at-rule-no-vendor-prefix#true)

```yaml
'at-rule-no-vendor-prefix': true
```


```scss
// doesn't pass the test
@-webkit-keyframes anim { 0% { top: 0; } }

@-ms-viewport { orientation: landscape; }

// passes the test
@keyframes anim { 0% { top: 0; } }

@viewport { orientation: landscape; }
```


### [at-rule-semicolon-newline-after](https://stylelint.io/user-guide/rules/list/at-rule-semicolon-newline-after#always)

```yaml
'at-rule-semicolon-newline-after': 'always'
```


```scss
// doesn't pass the test
@import url("x.css"); @import url("y.css");

@import url("x.css"); a {}

// passes the test
@import url("x.css");
@import url("y.css");

@import url("x.css"); /* end-of-line comment */
a {}

@import url("x.css");

a {}
```


### [block-closing-brace-empty-line-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-empty-line-before#never)

```yaml
'block-closing-brace-empty-line-before': 'never'
```


```scss
// doesn't pass the test
a {
  color: pink;

}

// passes the test
a {
  color: pink;
}
```


### [block-closing-brace-newline-after](https://stylelint.io/user-guide/rules/list/block-closing-brace-newline-after#always)

```yaml
'block-closing-brace-newline-after': 'always'
```


```scss
// doesn't pass the test
a { color: pink; }b { color: red; }

a { color: pink;
} b { color: red; }

// passes the test
a { color: pink; }
b { color: red; }
```


### [block-closing-brace-newline-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-newline-before/#always-multi-line)

```yaml
'block-closing-brace-newline-before': 'always-multi-line'
```


```scss
// doesn't pass the test
a {
  color: pink;}

// passes the test
a { color: pink; }

a {
  color: pink;
}
```


### [block-closing-brace-space-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-space-before#always-single-line)

```yaml
'block-closing-brace-space-before': 'always-single-line'
```


```scss
// doesn't pass the test
a { color: pink;}

// passes the test
a { color: pink; }
```


### [block-opening-brace-newline-after](https://stylelint.io/user-guide/rules/list/block-opening-brace-newline-after#always-multi-line)

```yaml
'block-opening-brace-newline-after': 'always-multi-line'
```


```scss
// doesn't pass the test
a{color: pink;
}

// passes the test
a { color: pink; }
```


### [block-opening-brace-space-after](https://stylelint.io/user-guide/rules/list/block-opening-brace-space-after#always-single-line)

```yaml
'block-opening-brace-space-after': 'always-single-line'
```


```scss
// doesn't pass the test
a {color: pink; }

// passes the test
a { color: pink; }
```


### [block-opening-brace-space-before](https://stylelint.io/user-guide/rules/list/block-opening-brace-space-before#always)

```yaml
'block-opening-brace-space-before': 'always'
```


```scss
// doesn't pass the test
a{ color: pink; }

// passes the test
a { color: pink; }
```


### [color-hex-case](https://stylelint.io/user-guide/rules/list/color-hex-case#lower)

```yaml
'color-hex-case': 'lower'
```


```scss
// doesn't pass the test
a { color: #FFF; }

// passes the test
a { color: #000; }

a { color: #fff; }
```


### [color-hex-length](https://stylelint.io/user-guide/rules/list/color-hex-length#short)

```yaml
'color-hex-length': 'short'
```


```scss
// doesn't pass the test
a { color: #ffffff; }

a { color: #ffffffaa; }

// passes the test
a { color: #fff; }

a { color: #fffa; }

a { color: #a4a4a4; }
```


### [comment-empty-line-before](https://stylelint.io/user-guide/rules/list/comment-empty-line-before#always)

```yaml
'comment-empty-line-before': [
  'always',
  {
    except: ['first-nested'],
    ignore: ['stylelint-commands']
  }
]
```


```scss
// doesn't pass the test
a {}
/* comment */

// passes the test
a {}

/* comment */

a {} /* comment */
```


### [comment-whitespace-inside](https://stylelint.io/user-guide/rules/list/comment-whitespace-inside#always)

```yaml
'comment-whitespace-inside': 'always'
```


```scss
// doesn't pass the test
/*comment*/

/*comment */

/** comment**/

// passes the test
/* comment */

/** comment **/
```


### [custom-property-empty-line-before](https://stylelint.io/user-guide/rules/list/custom-property-empty-line-before#always)

```yaml
'custom-property-empty-line-before': [
  'always',
  {
    except: ['after-custom-property', 'first-nested'],
    ignore: ['after-comment', 'inside-single-line-block']
  }
]
```


```scss
// doesn't pass the test
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}

// passes the test
a {
  top: 10px;

  --foo: pink;
  --bar: red;
}
```


### [custom-media-pattern](https://stylelint.io/user-guide/rules/list/custom-media-pattern)

```yaml
'custom-media-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected custom media query name to be kebab-case',
  }
]
```


```scss
// doesn't pass the test
@custom-media fooBar (min-width: 30em);

@custom-media foo_bar (min-width: 30em);


// passes the test
@custom-media foo-bar (min-width: 30em);
```


### [custom-property-pattern](https://stylelint.io/user-guide/rules/list/custom-property-pattern/)

```yaml
'custom-property-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected custom property name to be kebab-case',
  }
]
```


```scss
// doesn't pass the test
:root { --foo_bar: 0; }

// passes the test
:root { --foo-bar: 0; }
```


### [declaration-bang-space-after](https://stylelint.io/user-guide/rules/list/declaration-bang-space-after#never)

```yaml
'declaration-bang-space-after': 'never'
```


```scss
// doesn't pass the test
a { color: pink ! important; }

a { color: pink! important; }

// passes the test
a { color: pink !important; }
```


### [declaration-bang-space-before](https://stylelint.io/user-guide/rules/list/declaration-bang-space-before#always)

```yaml
'declaration-bang-space-before': 'always'
```


```scss
// doesn't pass the test
a { color: pink!important; }

a { color: pink  ! important; }

// passes the test
a { color: pink !important; }
```


### [declaration-block-semicolon-newline-after](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-newline-after#always-multi-line)

```yaml
'declaration-block-semicolon-newline-after': 'always-multi-line'
```


```scss
// doesn't pass the test
a {
  color: pink; top: 0;
}

// passes the test
a { color: pink; }

a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```


### [declaration-block-semicolon-space-after](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-after#always-single-line)

```yaml
'declaration-block-semicolon-space-after': 'always-single-line'
```


```scss
// doesn't pass the test
a { color: pink;top: 0; }

// passes the test
a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```


### [declaration-block-semicolon-space-before](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-before#never)

```yaml
'declaration-block-semicolon-space-before': 'never'
```


```scss
// doesn't pass the test
a { color: pink ; }

a { color: pink ; top: 0 ; }

// passes the test
a { color: pink; }

a { color: pink; top: 0; }
```


### [declaration-block-single-line-max-declarations](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-before#never)

```yaml
'declaration-block-single-line-max-declarations': 1
```


```scss
// doesn't pass the test
a { color: pink; top: 3px; }

a,
b { color: pink; top: 3px; }

// passes the test
a { color: pink; }

a,
b { color: pink; }

a {
  color: pink;
  top: 3px;
}
```


### [declaration-block-trailing-semicolon](https://stylelint.io/user-guide/rules/list/declaration-block-trailing-semicolon#always)


```yaml
'declaration-block-trailing-semicolon': 'always'
```


```scss
// doesn't pass the test
a { color: pink }

a { background: orange; color: pink }

a { @include foo }

// passes the test
a { color: pink; }

a { background: orange; color: pink; }

a { @include foo; }
```


### [declaration-block-no-redundant-longhand-properties](https://stylelint.io/user-guide/rules/list/declaration-block-no-redundant-longhand-properties#true)


```yaml
'declaration-block-no-redundant-longhand-properties': true
```


```scss
// doesn't pass the test
a {
  margin-top: 1px;
  margin-right: 2px;
  margin-bottom: 3px;
  margin-left: 4px;
}

// passes the test
a {
  margin: 1px 2px 3px 4px;
}
```


### [declaration-colon-newline-after](https://stylelint.io/user-guide/rules/list/declaration-colon-newline-after#always-multi-line)


```yaml
'declaration-colon-newline-after': 'always-multi-line'
```


```scss
// doesn't pass the test
a {
  box-shadow: 0 0 0 1px #5b9dd9,
  0 0 2px 1px rgba(30, 140, 190, 0.8);
}

// passes the test
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  color: pink;
}
```


### [declaration-colon-space-after](https://stylelint.io/user-guide/rules/list/declaration-colon-space-after#always-single-line)


```yaml
'declaration-colon-space-after': 'always-single-line'
```


```scss
// doesn't pass the test
a {
  box-shadow:0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}

// passes the test
a {
  box-shadow: 0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}

a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```


### [declaration-colon-space-before](https://stylelint.io/user-guide/rules/list/declaration-colon-space-before#never)


```yaml
'declaration-colon-space-before': 'never'
```


```scss
// doesn't pass the test
a { color : pink }

a { color :pink }

// passes the test
a { color: pink }
```


### [declaration-empty-line-before](https://stylelint.io/user-guide/rules/list/declaration-empty-line-before#always)


```yaml
'declaration-empty-line-before': [
  'always',
  {
    except: ['after-declaration', 'first-nested'],
    ignore: ['after-comment', 'inside-single-line-block']
  }
]
```


```scss
// doesn't pass the test
a {
  --foo: pink;
  top: 5px;
}

// passes the test
a {
  --foo: pink;

  top: 5px;
}
```


### [font-family-name-quotes](https://stylelint.io/user-guide/rules/list/font-family-name-quotes#always-where-recommended)


```yaml
'font-family-name-quotes': 'always-where-recommended'
```


```scss
// doesn't pass the test
a { font-family: Times New Roman, Times, serif; }

a { font-family: MyFontVersion6, sake_case_font; }

a { font-family: 'Arial', sans-serif; }

a { font: 1em Times New Roman, Times, serif; }

// passes the test
a { font-family: 'Times New Roman', Times, serif; }

a { font-family: "MyFontVersion6", "sake_case_font"; }

a { font-family: Arial, sans-serif; }

a { font: 1em 'Times New Roman', Times, serif; }
```


### [function-comma-newline-after](https://stylelint.io/user-guide/rules/list/function-comma-newline-after#always-multi-line)


```yaml
'function-comma-newline-after': 'always-multi-line'
```


```scss
// doesn't pass the test
a { transform: translate(100%
,100%) }

// passes the test
a { transform: translate(100%,100%) }

a { transform: translate(100% ,100%) }

a {
  transform: translate(100%,
          100%)
}
```


### [function-comma-space-after](https://stylelint.io/user-guide/rules/list/function-comma-space-after#always-single-line)


```yaml
'function-comma-space-after': 'always-single-line'
```


```scss
// doesn't pass the test
a { transform: translate(100%,100%) }

a { transform: translate(100% ,100%) }

// passes the test
a { transform: translate(100%, 100%) }
```


### [function-comma-space-before](https://stylelint.io/user-guide/rules/list/function-comma-space-before#never)


```yaml
'function-comma-space-before': 'never'
```


```scss
// doesn't pass the test
a { transform: translate(100% , 100%) }

a { transform: translate(100% ,100%) }

// passes the test
a { transform: translate(100%, 100%) }

a { transform: translate(100%,100%) }
```


### [function-comma-space-before](https://stylelint.io/user-guide/rules/list/function-max-empty-lines#options)


```yaml
'function-max-empty-lines': 0
```

```scss
// doesn't pass the test
a { 
  transform: 
    translate(
      100%,
            
      100%
    ) 
}

// passes the test
a {
  transform:
    translate(
      100%,
      100%
  )
}
```


### [function-name-case](https://stylelint.io/user-guide/rules/list/function-name-case#lower)


```yaml
'function-name-case': 'lower'
```

```scss
// doesn't pass the test
a {
  width: Calc(5% - 10em);
}

a {
  width: cAlC(5% - 10em);
}

// passes the test
a {
  width: calc(5% - 10em);
}
```


### [function-parentheses-newline-inside](https://stylelint.io/user-guide/rules/list/function-parentheses-newline-inside#always-multi-line)


```yaml
'function-parentheses-newline-inside': 'always-multi-line'
```

```scss
// doesn't pass the test
a { transform: translate(1,
    1) }

// passes the test
a { transform: translate(1, 1) }

a { transform: translate( 1, 1 ) }

a {
  transform: translate(
    1, 1
  );
}

a {
  transform: translate(
    1,
    1
  );
}
```


### [function-parentheses-space-inside](https://stylelint.io/user-guide/rules/list/function-parentheses-space-inside#never-single-line)


```yaml
'function-parentheses-space-inside': 'never-single-line'
```

```scss
// doesn't pass the test
a { transform: translate( 1, 1 ) }

a { transform: translate(1, 1 ) }

// passes the test
a { transform: translate(1, 1) }
```


### [function-url-quotes](https://stylelint.io/user-guide/rules/list/function-url-quotes#always)


```yaml
'function-url-quotes': 'always'
```

```scss
// doesn't pass the test
a { background: url(x.jpg); }

@import url(foo.css);

@document domain(http://www.w3.org/);

// passes the test
a { background: url('x.jpg'); }

@import url("foo.css");

@document domain('http://www.w3.org/');
```


### [function-whitespace-after](https://stylelint.io/user-guide/rules/list/function-whitespace-after#always)


```yaml
'function-whitespace-after': 'always'
```

```scss
// doesn't pass the test
a { transform: translate(1, 1)scale(3); }

// passes the test
a { transform: translate(1, 1) scale(3); }
```


### [function-whitespace-after](https://stylelint.io/user-guide/rules/list/hue-degree-notation#angle)


```yaml
'hue-degree-notation': 'angle'
```

```scss
// doesn't pass the test
a { color: hsl(198 28% 50%) }

a { color: lch(56.29% 19.86 10 / 15%) }

// passes the test
a { color: hsl(198deg 28% 50%) }

a { color: lch(56.29% 19.86 10deg / 15%) }
```


### [import-notation](https://stylelint.io/user-guide/rules/list/import-notation#string)


```yaml
'import-notation': 'string'
```

```scss
// doesn't pass the test
@import url(foo.css);

@import url('foo.css');

// passes the test
@import 'foo.css';

@import "foo.css";
```


### [indentation](https://stylelint.io/user-guide/rules/list/indentation#2)


```yaml
indentation: 2
```

```scss
// doesn't pass the test
@media print {
a {
background-position: top left;
}
}

@media print {
  a {
  background-position: top left;
  }
}

// passes the test
@media print {
  a {
    background-position: top left;
  }
}
```


### [keyframes-name-pattern](https://stylelint.io/user-guide/rules/list/keyframes-name-pattern#options)


```yaml
'keyframes-name-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected keyframe name to be kebab-case',
  }
]
```

```scss
// doesn't pass the test
@keyframes fooBaz {}

@keyframes foo_baz {}

// passes the test
@keyframes foo-baz {}
```


### [length-zero-no-unit](https://stylelint.io/user-guide/rules/list/length-zero-no-unit#true)


```yaml
'length-zero-no-unit': true
```

```scss
// doesn't pass the test
a { top: 0px }

a { top: 0.000em }

// passes the test
a { top: 0 } /* no unit */

a { transition-delay: 0s; } /* dimension */
```


### [max-empty-lines](https://stylelint.io/user-guide/rules/list/max-empty-lines#options)


```yaml
'max-empty-lines': 1
```

```scss
// doesn't pass the test
a {}


b {}

// passes the test
a {}

b {}
```


### [max-line-length](https://stylelint.io/user-guide/rules/list/max-line-length#options)


```yaml
'max-line-length': 120
```

```scss
// doesn't pass the test
a { color: pink; background: orange; margin-left: 10px; margin-top: 24px; padding-left: 20px; padding-right: 20px}

// passes the test
a {
  color: pink;
  background: orange;
  margin-left: 10px;
  margin-top: 24px;
  padding-left: 20px;
  padding-right: 20px
}
```


### [media-feature-colon-space-after](https://stylelint.io/user-guide/rules/list/media-feature-colon-space-after#always)


```yaml
'media-feature-colon-space-after': 'always'
```

```scss
// doesn't pass the test
@media (max-width:600px) {}

@media (max-width :600px) {}

// passes the test
@media (max-width: 600px) {}
```


### [media-feature-colon-space-before](https://stylelint.io/user-guide/rules/list/media-feature-colon-space-before#never)


```yaml
'media-feature-colon-space-before': 'never'
```

```scss
// doesn't pass the test
@media (max-width :600px) {}

@media (max-width : 600px) {}

// passes the test
@media (max-width: 600px) {}
```

### [media-feature-name-case](https://stylelint.io/user-guide/rules/list/media-feature-name-case#lower)


```yaml
'media-feature-name-case': 'lower'
```

```scss
// doesn't pass the test
@media (MIN-WIDTH: 700px) {}

@media (min-width: 700px) and (ORIENTATION: landscape) {}

// passes the test
@media (min-width: 700px) {}

@media (min-width: 700px) and (orientation: landscape) {}
```


### [media-feature-name-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/media-feature-name-no-vendor-prefix#true)


```yaml
'media-feature-name-no-vendor-prefix': true
```

```scss
// doesn't pass the test
@media (-webkit-min-device-pixel-ratio: 1) {}

// passes the test
@media (min-resolution: 96dpi) {}
```


### [media-feature-parentheses-space-inside](https://stylelint.io/user-guide/rules/list/media-feature-parentheses-space-inside#never)


```yaml
'media-feature-parentheses-space-inside': 'never'
```

```scss
// doesn't pass the test
@media ( max-width: 300px ) {}

@media ( max-width: 300px) {}

// passes the test
@media (max-width: 300px) {}
```


### [media-feature-range-operator-space-after](https://stylelint.io/user-guide/rules/list/media-feature-range-operator-space-after#always)


```yaml
'media-feature-range-operator-space-after': 'always'
```

```scss
// doesn't pass the test
@media (width>=600px) {}

@media (width >=600px) {}

// passes the test
@media (width >= 600px) {}
```


### [media-feature-range-operator-space-before](https://stylelint.io/user-guide/rules/list/media-feature-range-operator-space-before#always)


```yaml
'media-feature-range-operator-space-before': 'always'
```

```scss
// doesn't pass the test
@media (width>=600px) {}

@media (width>= 600px) {}

// passes the test
@media (width >= 600px) {}
```


### [media-query-list-comma-newline-after](https://stylelint.io/user-guide/rules/list/media-query-list-comma-newline-after#always-multi-line)


```yaml
'media-query-list-comma-newline-after': 'always-multi-line'
```

```scss
// doesn't pass the test
@media screen and (color)
, projection and (color) {}

// passes the test
@media screen and (color), projection and (color) {}

@media screen and (color),
projection and (color) {}
```


### [media-query-list-comma-space-after](https://stylelint.io/user-guide/rules/list/media-query-list-comma-space-after#always-single-line)


```yaml
'media-query-list-comma-space-after': 'always-single-line'
```

```scss
// doesn't pass the test
@media screen and (color),projection and (color) {}

// passes the test
@media screen and (color), projection and (color) {}
```


### [media-query-list-comma-space-before](https://stylelint.io/user-guide/rules/list/media-query-list-comma-space-before#never)


```yaml
'media-query-list-comma-space-before': 'never'
```

```scss
// doesn't pass the test
@media screen and (color) ,projection and (color) {}

// passes the test
@media screen and (color), projection and (color) {}
```


### [no-empty-first-line](https://stylelint.io/user-guide/rules/list/no-empty-first-line#true)


```yaml
'no-empty-first-line': true
```

```scss
// doesn't pass the test
\n
a { color: pink; }

// passes the test
a { color: pink; }
```


### [no-eol-whitespace](https://stylelint.io/user-guide/rules/list/no-eol-whitespace#true)


```yaml
'no-eol-whitespace': true
```

```scss
// doesn't pass the test
a { color: pink; }·

a { color: pink; }····

// passes the test
a { color: pink; }
```


### [no-missing-end-of-source-newline](https://stylelint.io/user-guide/rules/list/no-missing-end-of-source-newline#true)


```yaml
'no-missing-end-of-source-newline': true
```

```scss
// doesn't pass the test
a { color: pink; }

// passes the test
a { color: pink; }
\n
```


### [number-leading-zero](https://stylelint.io/user-guide/rules/list/number-leading-zero#always)


```yaml
'number-leading-zero': 'always'
```

```scss
// doesn't pass the test
a { line-height: .5; }

a { transform: translate(2px, .4px); }

// passes the test
a { line-height: 0.5; }

a { transform: translate(2px, 0.4px); }
```


### [number-max-precision](https://stylelint.io/user-guide/rules/list/number-max-precision#options)


```yaml
'number-max-precision': 4
```

```scss
// doesn't pass the test
a { top: 3.245634px; }

// passes the test
a { top: 3.2456px; }

a { top: 3.25px; }
```


### [number-no-trailing-zeros](https://stylelint.io/user-guide/rules/list/number-no-trailing-zeros#true)


```yaml
'number-no-trailing-zeros': true
```

```scss
// doesn't pass the test
a { top: 1.0px }

// passes the test
a { top: 1px }
```


### [property-case](https://stylelint.io/user-guide/rules/list/property-case#lower)


```yaml
'property-case': 'lower'
```

```scss
// doesn't pass the test
a { Width: 1px }

a { WIDTH: 1px }

// passes the test
a { width: 1px }
```


### [property-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/property-no-vendor-prefix#true)


```yaml
'property-no-vendor-prefix': true
```

```scss
// doesn't pass the test
a { -webkit-transform: scale(1); }

a { -moz-columns: 2; }

// passes the test
a { transform: scale(1); }

a { columns: 2; }

a { -webkit-touch-callout: none; }
```


### [rule-empty-line-before](https://stylelint.io/user-guide/rules/list/rule-empty-line-before#always-multi-line)


```yaml
'rule-empty-line-before': [
  'always-multi-line',
  {
    except: ['first-nested'],
    ignore: ['after-comment'],
  }
]
```

```scss
// doesn't pass the test
a {
  color: red;
}
b {
  color: blue;
}

// passes the test
a {
  color: red;
}

b {
  color: blue;
}
```


### [selector-attribute-brackets-space-inside](https://stylelint.io/user-guide/rules/list/selector-attribute-brackets-space-inside#never)


```yaml
'selector-attribute-brackets-space-inside': 'never'
```

```scss
// doesn't pass the test
[ target] {}

[target ] {}

[ target ] {}

// passes the test
[target] {}
```


### [selector-attribute-operator-space-after](https://stylelint.io/user-guide/rules/list/selector-attribute-operator-space-after#never)


```yaml
'selector-attribute-operator-space-after': 'never'
```

```scss
// doesn't pass the test
[target= _blank] {}

// passes the test
[target=_blank] {}
```


### [selector-attribute-operator-space-before](https://stylelint.io/user-guide/rules/list/selector-attribute-operator-space-before#never)


```yaml
'selector-attribute-operator-space-before': 'never'
```

```scss
// doesn't pass the test
[target =_blank] {}

// passes the test
[target=_blank] {}
```


### [selector-attribute-quotes](https://stylelint.io/user-guide/rules/list/selector-attribute-quotes#always)


```yaml
'selector-attribute-quotes': 'always'
```

```scss
// doesn't pass the test
[title=flower] {}

// passes the test
[title="flower"] {}
```


### [selector-class-pattern](https://stylelint.io/user-guide/rules/list/selector-class-pattern#options)


```yaml
  'selector-class-pattern': ["^(--[a-z][a-z0-9]*)(-[a-z0-9]+)*$|^([a-z][a-z0-9]*)(((-)|(__))[a-z0-9]+)*$", {
  'message': "Expected format: .foo-bar | .--foo-bar | .foo-bar__baz (selector-class-pattern)",
  'resolveNestedSelectors': true
}]
```

```scss
// doesn't pass the test
.foo_bar {}

.fooBar {}

.foo--bar {}

// passes the test
.foo-bar {}

.--foo-bar {}

.foo__bar {}

.foo-bar__baz {}
```


### [selector-combinator-space-after](https://stylelint.io/user-guide/rules/list/selector-combinator-space-after#always)


```yaml
'selector-combinator-space-after': 'always'
```

```scss
// doesn't pass the test
a +b { color: pink; }

a>b { color: pink; }

// passes the test
a + b { color: pink; }

a > b { color: pink; }
```


### [selector-combinator-space-before](https://stylelint.io/user-guide/rules/list/selector-combinator-space-before#always)


```yaml
'selector-combinator-space-before': 'always'
```

```scss
// doesn't pass the test
a+ b { color: pink; }

a>b { color: pink; }

// passes the test
a + b { color: pink; }

a > b { color: pink; }
```


### [selector-descendant-combinator-no-non-space](https://stylelint.io/user-guide/rules/list/selector-descendant-combinator-no-non-space#true)


```yaml
'selector-descendant-combinator-no-non-space': true
```

```scss
// doesn't pass the test
.foo  .bar {}

.foo
.bar {}

// passes the test
.foo .bar {}
```


### [selector-id-pattern](https://stylelint.io/user-guide/rules/list/selector-id-pattern#options)


```yaml
'selector-id-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected id selector to be kebab-case'
  }
]
```

```scss
// doesn't pass the test
#foo_bar {}

#foo--bar {}

#fooBar {}

// passes the test
#foo-bar {}
```


### [selector-list-comma-newline-after](https://stylelint.io/user-guide/rules/list/selector-list-comma-newline-after#always)


```yaml
'selector-list-comma-newline-after': 'always'
```

```scss
// doesn't pass the test
a, b { color: pink; }

a
, b { color: pink; }

// passes the test
a,
b { color: pink; }
```


### [selector-list-comma-space-before](https://stylelint.io/user-guide/rules/list/selector-list-comma-space-before#never)


```yaml
'selector-list-comma-space-before': 'never'
```

```scss
// doesn't pass the test
a ,b { color: pink; }

a , b { color: pink; }

// passes the test
a,
b { color: pink; }
```


### [selector-max-empty-lines](https://stylelint.io/user-guide/rules/list/selector-max-empty-lines#options)


```yaml
'selector-max-empty-lines': 0
```

```scss
// doesn't pass the test
a,

b {
  color: red;
}

// passes the test
a,
b {
  color: red;
}
```


### [selector-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/selector-no-vendor-prefix#true)


```yaml
'selector-no-vendor-prefix': true
```

```scss
// doesn't pass the test
input::-moz-placeholder {}

// passes the test
input::placeholder {}
```


### [selector-not-notation](https://stylelint.io/user-guide/rules/list/selector-not-notation#complex)


```yaml
'selector-not-notation': 'complex'
```

```scss
// doesn't pass the test
:not(a):not(div) {}

// passes the test
:not(a, div) {}
```


### [selector-pseudo-class-case](https://stylelint.io/user-guide/rules/list/selector-pseudo-class-case#lower)


```yaml
'selector-pseudo-class-case': 'lower'
```

```scss
// doesn't pass the test
a:Hover {}

a:hOvEr {}
// passes the test
a:hover {}
```


### [selector-pseudo-class-parentheses-space-inside](https://stylelint.io/user-guide/rules/list/selector-pseudo-class-parentheses-space-inside#never)


```yaml
'selector-pseudo-class-parentheses-space-inside': 'never'
```

```scss
// doesn't pass the test
input:not( [type="submit"] ) {}

input:not( [type="submit"]) {}
// passes the test
input:not([type="submit"]) {}
```


### [selector-pseudo-element-case](https://stylelint.io/user-guide/rules/list/selector-pseudo-element-case#lower)


```yaml
'selector-pseudo-element-case': 'lower'
```

```scss
// doesn't pass the test
a:Before {}

a:bEfOrE {}
// passes the test
a:before {}
```


### [selector-type-case](https://stylelint.io/user-guide/rules/list/selector-type-case#lower)


```yaml
'selector-type-case': 'lower'
```

```scss
// doesn't pass the test
A {}

LI {}
// passes the test
a {}

li {}
```


### [shorthand-property-no-redundant-values](https://stylelint.io/user-guide/rules/list/shorthand-property-no-redundant-values#true)


```yaml
'shorthand-property-no-redundant-values': true
```

```scss
// doesn't pass the test
a { margin: 1px 1px; }

a { margin: 1px 1px 1px 1px; }

// passes the test
a { margin: 1px; }

a { margin: 1px 1px 1px 2px; }
```


### [string-quotes](https://stylelint.io/user-guide/rules/list/string-quotes#double)


```yaml
'string-quotes': 'double'
```

```scss
// doesn't pass the test
a { content: 'x'; }

// passes the test
a { content: "x"; }
```


### [unit-case](https://stylelint.io/user-guide/rules/list/unit-case#lower)


```yaml
'unit-case': 'lower'
```

```scss
// doesn't pass the test
a { width: 10PX; }

a { width: 10Px; }

// passes the test
a { width: 10px; }
```


### [value-keyword-case](https://stylelint.io/user-guide/rules/list/value-keyword-case#lower)


```yaml
'value-keyword-case': 'lower'
```

```scss
// doesn't pass the test
a { display: Block; }

a { display: bLoCk; }

// passes the test
a { display: block; }
```


### [value-list-comma-newline-after](https://stylelint.io/user-guide/rules/list/value-list-comma-newline-after#always-multi-line)


```yaml
'value-list-comma-newline-after': 'always-multi-line'
```

```scss
// doesn't pass the test
a { background-size: 0
, 0; }

// passes the test
a { background-size: 0, 0; }

a { background-size: 0,
      0; 
}
```


### [value-list-comma-space-after](https://stylelint.io/user-guide/rules/list/value-list-comma-space-after#always-single-line)


```yaml
'value-list-comma-space-after': 'always-single-line'
```

```scss
// doesn't pass the test
a { background-size: 0,0; }

// passes the test
a { background-size: 0, 0; }
```


### [value-list-comma-space-before](https://stylelint.io/user-guide/rules/list/value-list-comma-space-before#never)


```yaml
'value-list-comma-space-before': 'never'
```

```scss
// doesn't pass the test
a { background-size: 0 ,0; }

// passes the test
a { background-size: 0, 0; }
```


### [value-list-max-empty-lines](https://stylelint.io/user-guide/rules/list/value-list-max-empty-lines#options)


```yaml
'value-list-max-empty-lines': 0
```

```scss
// doesn't pass the test
a {
  box-shadow: inset 0 2px 0 #dcffa6,

  0 2px 5px #000;
}

// passes the test
a {
  box-shadow: inset 0 2px 0 #dcffa6,
  0 2px 5px #000;
}
```


### [value-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/value-no-vendor-prefix#true)


```yaml
'value-no-vendor-prefix': [true, { ignoreValues: ["box"] }]
```

```scss
// doesn't pass the test
a { display: -webkit-flex; }

a { max-width: -moz-max-content; }

// passes the test
a { display: flex; }

a { max-width: max-content; }
```


# END_OF_THE_FILE
