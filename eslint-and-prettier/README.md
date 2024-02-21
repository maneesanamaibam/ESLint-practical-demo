### Requirements

1. Install prettier
2. Configure .prettierrc file
3. Install prettier VS Code Extension
4. How to resolve conflicts between eslint rules and prettier rules


### Basic Prettier configuration

```json
{
  
  "trailingComma": "es5",
  "tabWidth": 4,
  "semi": false,
  "singleQuote": true,
  "arrowParens":"always"

}

```


## Conflicting code example
```js
"use strict"
const hello=(message)=>{
    return `hello ${message}`
}
```