# Field string parser

A library that consumes strings and converts them into string definitions.

Additionally, it formats and adds an argument string for easy code generating.

## Installation

`npm i --save field-string-parser` or `yarn add field-string-parser`

## Usage

Usage is pretty straight forward. You can reuse instances, or use the static method.

Fields can be passed in using JSON, or the [ezon](https://github.com/SpoonX/ezon) format.

Examples of valid formats:

`'username,password:(size:50),active:boolean'`

or

`'username:string,password:field(size:50),active:field(type:boolean)'`

### Static example

Here's an example using the static parse method.

```js
const parsedFields = FieldStringParser.parse('username,password:(size:50),active:boolean');

console.log(parsedFields);

// Generates the following
{
  username: {
    argumentString: '{ type: \'string\' }',
    definition    : { type: 'string' }
  },
  password: {
    argumentString: '{ size: 50, type: \'string\' }',
    definition    : { size: 50, type: 'string' }
  },
  active  : {
    argumentString: '{ type: \'boolean\' }',
    definition    : { type: 'boolean' }
  }
}
```

### Instance example

Here's an example using the instance approach.

```js
const fieldParser  = new FieldParser('username,password:(size:50),active:boolean');
const parsedFields = fieldStringParser.parse();

console.log(parsedFields);

// Generates the following
{
  username: {
    argumentString: '{ type: \'string\' }',
    definition    : { type: 'string' }
  },
  password: {
    argumentString: '{ size: 50, type: \'string\' }',
    definition    : { size: 50, type: 'string' }
  },
  active  : {
    argumentString: '{ type: \'boolean\' }',
    definition    : { type: 'boolean' }
  }
}
```

## License

MIT
