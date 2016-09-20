# Crowd Analyzer Javascript Style Guide

# [Table of Contents](#table-of-contents)

1. [Naming Conventions](#naming-conventions)
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

## [Naming Conventions](#naming-conventions)

1.1 **Avoid single letter** names. Be descriptive with your naming.  ([id-length](http://eslint.org/docs/rules/id-length))
```javascript
// bad
function t() {}

// good
function transform() {}
```

1.2 Use **camelCase** when naming objects, functions, and instances. ([camelCase](http://eslint.org/docs/rules/camelcase))
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

1.3 Use **PascalCase** when naming classes. ([new-cap](http://eslint.org/docs/rules/new-cap))
```javascript
// bad
class whiteTransformer {}
class WHITE_TRANSFORMER {}

// good
class WhiteTransformer {}
```

1.4 Use **CAPS_UNDERSCORE** when naming constants.
```javascript
// bad
const maxNumberOfAllowedCharacters = 80;

// good
const MAX_NUMBER_OF_ALLOWED_CHARACTERS = 80;
```

1.5 Use a **leading _** to denote private methods.
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

1.6 **Avoid** saving references to **this**. Use arrow functions or Function#Bind instead.
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

1.7 A base **filename** should exactly match the name of its **default export**.
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

1.8 Use PascalCaps with folders’ names.
```javascript
// bad
require('./transformers/BaseTransformer'); // camelCase folders' names

// good
require('./Transformers/BaseTransformer'); // PascalCase folders' names
```

**[Back to Top](#table-of-contents)**

## [Whitespace](#whitespace)

2.1 Use soft **tabs** set to **4 spaces**. ([indent](http://eslint.org/docs/rules/indent))
```javascript
// bad (2 spaces soft tab)
function transform() {
  let transformedVariable;
}

// even worse (no indentation at all)
function transform() {
let transformedVariable;
}

// good (4 spaces soft tab)
function transform() {
    let transformedVariable;
}
```

2.2 Place **one space** before the **leading brace**. ([space-before-blocks](http://eslint.org/docs/rules/space-before-blocks))
```javascript
// bad
function transform(){
}
transformer.set('key',{
    'field': 'value'
});

// good
function transform() {
}
transformer.set('key', {
    'field': 'value'
});
```

2.3 Place **no space** **before** the **opening parenthesis** in control statements. Place no space **between** the **argument list** and the **function name** in function calls & declarations. ([keyword-spacing](http://eslint.org/docs/rules/keyword-spacing))
```javascript
// bad
if (variable > value) {
}
transform (var1, var2);

// good
if(variable > value) {
}
transform(var1, var2);
```

2.4 Set off **operators** with **spaces**. ([space-infix-ops](http://eslint.org/docs/rules/space-infix-ops))
```javascript
// bad
let z=x+y;

// good
let z = x + y;
```

2.5 **End files** with a **new line** character. ([eol-last](http://eslint.org/docs/rules/eol-last))
```javascript
// bad
module.exports = {
    Transformer
};
// good
module.exports = {
    Transformer
};

```

2.6 Use **indentation** with **leading dot** when making **long method chains**. ([newline-per-chained-call](http://eslint.org/docs/rules/newline-per-chained-call), [no-whitespace-before-property](http://eslint.org/docs/rules/no-whitespace-before-property))
```javascript
// bad
_.chain(data).flatten().uniqu().map(item => _.upperCase(item)).filter(item => item.isActive).values();

// bad
_.chain(data).
    flatten().
    uniqu().
    map(item => _.upperCase(item)).
    filter(item => item.isActive).
    values();

// good
_.chain(data)
    .flatten()
    .uniqu()
    .map(item => _.upperCase(item))
    .filter(item => item.isActive)
    .values();
```

2.7 **Use** **I****ndentation** when **chaining** methods ([indent](http://eslint.org/docs/rules/indent))
```javascript
// bad
return this._call("GET", interactionId, params)
.then(response => {
    return this._formatInteraction(response);
});

// good        
return this._call("GET", interactionId, params)
    .then(response => {
        return this._formatInteraction(response);
    });
```

2.8 Leave a **blank line** **after** a **block** and before the next statement
```javascript
// bad
if(variable > value) {
}
return value;

// bad
let obj = {
    property1: {
    },
    property2: {
    }
}

// good
if(variable > value) {
}

return value;

// good
let obj = {
    property1: {
    },

    property2: {
    }
}
```

2.9 **Do not pad** your **blocks** with **blank lines**. ([padded-blocks](http://eslint.org/docs/rules/padded-blocks))
```javascript
// bad
function transform() {

    let variable = value;
}

// bad
if(variable > value) {

    variable -= value;

}

// good
function transform() {
    let variable = value;
}

// good
if(variable > value) {
    variable -= value;
}
```

2.10 **Do not** add **spaces** inside **parentheses** or **brackets**. ([space-in-parens](http://eslint.org/docs/rules/space-in-parens), [array-bracket-spacing](http://eslint.org/docs/rules/array-bracket-spacing))
```javascript
// bad
function transform( variable ) {
}

// bad
transform( variable1, variable2 );

// bad
let numbers = [ 1, 2, 3 ];

// bad
numbers[ 0 ] = 3;

// good
function transform(variable) {
}

// good
transform(variable1, variable2);

// good
let numbers = [1, 2, 3];

// good
numbers[0] = 3;
```

2.11 Add **spaces** inside curly **braces**. ([object-curly-spacing](http://eslint.org/docs/rules/object-curly-spacing))
```javascript
// bad
transform({property: value});

// good
trasnform({ property: value });
```

2.12 **Avoid** having **lines** of code that are **longer** than **100 characters**. ([max-len](http://eslint.org/docs/rules/max-len))
```javascript
// bad
_.chain(data).flatten().uniqu().map(item => _.upperCase(item)).filter(item => item.isActive).values();

// good
_.chain(data).flatten().uniqu()
    .map(item => _.upperCase(item))
    .filter(item => item.isActive).values();
```

**[Back to Top](#table-of-contents)**
