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



# END_OF_THE_FILE
