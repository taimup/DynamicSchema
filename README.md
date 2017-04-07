# Dynamic Schema 

_taimup_ _v0.1_

Validate inputs against pre-defined data schema

### Installation 

`DynamicSchema` is available at `npm`. To install:

`$ npm install --save DynamicSchema`

### Basic Usage

Create an `DynamicSchema` instance then use it to validate objects, return value includes an array of `errors`

##### Example

```javascript
const bookSchema = {
  title: {
    type: String,
    label: 'Title',
    max: 200,
  },
  author: {
    type: ()=> String,
    label: ()=> 'Author',
  },
  copies: {
    type: Number,
    label: 'Number of copies',
    min: 0,
  },
  lastCheckedOut: {
    type: Date,
    label: 'Last date this book was checked out',
    optional: true
  },
  summary: {
    type: String,
    label: 'Brief summary',
    optional: true,
    max: 1000
  }
}
// validation object
const book = { title: 'Lord of Rings', author: 'Dont know', copies: 100 }
// errors is [] because book is a valid object
const { errors } = bookSchema.validate(book);

const book = { title: 'Lord of Rings', author: 'Dont know'}
// errors contains a list of errors, errors = [{msgKey: 'required', key: copies}]
const { errors} = bookSchema.validate(book);

```





