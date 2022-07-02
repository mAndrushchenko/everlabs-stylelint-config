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
- [alpha-value-notation](#alpha-value-notation)
- [at-rule-empty-line-before](#at-rule-empty-line-before)


## Examples


### [alpha-value-notation](https://stylelint.io/user-guide/rules/list/alpha-value-notation/#percentage) (autofixable)

#### Config:
```yaml
'alpha-value-notation': [
  'percentage',
  {
    exceptProperties: ['opacity'],
  },
]
```

#### Example:

```scss
// bad
a { opacity: 0.5 }

a { color: rgb(0 0 0 / 0.5) }

// good
a { opacity: 50% }

a { color: rgb(0 0 0 / 50%) }
```

### [at-rule-empty-line-before](https://stylelint.io/user-guide/rules/list/at-rule-empty-line-before#always) (autofixable)

#### Config:
```yaml
'at-rule-empty-line-before': [
  'always',
  {
    except: ['blockless-after-same-name-blockless', 'first-nested'],
    ignore: ['after-comment'],
  },
],
```

#### Example:

```scss
// bad
a {} @media {}

a {}
@media {}

// good
a {}

@media {}
```