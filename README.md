# Crowd Analyzer Javascript Style Guide

# [Table of Contents](#table-of-contents)
---

1. [Naming Conventions](#naming)
2. [Whitespace](#whitespace)
3. [Blocks](#blocks)
4. [Commas](#commas)
5. [Semicolons](#semicolons)
6. [Comments](#comments)
7. [Variables](#variables)
8. [References](#references)
9. [Type Casting](#casting)
10. [Strings](#strings)
11. [Arrays](#arrays)
12. [Functions](#functions)
13. [Classes](#classes)
14. [Objects](#objects)
15. [Properties](#properties)
16. [Comparison Operators ](#comparison)
---

# [1.](#naming) Naming Conventions
---

## 1.1 **Avoid single letter** names. Be descriptive with your naming.  ([id-length](http://eslint.org/docs/rules/id-length))
```javascript
// bad
function t() {}

// good
function transform() {}
```

## 1.2 Use **camelCase** when naming objects, functions, and instances. ([camelCase](http://eslint.org/docs/rules/camelcase))
```javascript
// bad
function Transform() {}
let TRANSFORMED_VARIABLE;
let TransformObject = new Transform()

// good
function transform() {}
let transformedVariable;
let transformObject = new Transform();
```

## 1.3 Use **PascalCase** when naming classes. ([new-cap](http://eslint.org/docs/rules/new-cap))
```javascript
// bad
class whiteTransformer {}
class WHITE_TRANSFORMER {}

// good
class WhiteTransformer {}
```

## 1.4 Use **CAPS_UNDERSCORE** when naming constants.
```javascript
// bad
const maxNumberOfAllowedCharacters = 80;

// good
const MAX_NUMBER_OF_ALLOWED_CHARACTERS = 80;
```

## 1.5 Use a **leading _** to denote private methods.
```javascript
// bad
class Transformer {

    // private method
    privateFormatData() {}
}

// good
class Transformer {

    // private method
    _formatData() {}
}
```

## 1.6 **Avoid** saving references to **this**. Use arrow functions or Function#Bind instead.
```javascript
// bad
function transform() {
    let self = this;
    return function() {
        self.innerTransform();
    }
}

// good
function transform() {
    return () => {
        this.innerTransform();
    }
}
```

## 1.7 A base **filename** should exactly match the name of its **default export**.
Use **camelCase** when exporting a function. Use **PascalCase** when exporting class or bare object.
```javascript
// bad
module.exports = {
    BaseTransformer
};

require('./baseTransformer'); // camelCase filename matches a PascalCase exported class

// good
module.exports = {
    BaseTransformer
};

require('./BaseTransformer'); // PascalCase filename matches a PascalCase exported class
```

## 1.8 Use PascalCaps with folders’ names.
```javascript
// bad
require('./transformers/BaseTransformer'); // camelCase folders' names

// good
require('./Transformers/BaseTransformer'); // PascalCase folders' names
```

**[Back to Top](#table-of-contents)**
