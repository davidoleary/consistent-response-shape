# Matches Fashion NPM Response Module
NPM module providing full unit test coverage of both types of responses.

# Commands
- `npm install` - Setup.
- `npm run test` - Run tests.
- `npm run build` - Compile es6 code into es5 code.
- `npm run prepublish` - Hook for npm. Do checks and build before publish.

# Usage and result:
## Valid response
``` javascript
import { Response } from 'mf-response';   
const r = new mfResponse.Response();
const expected = {
  a: 'hello',
  b: 'world',
};
r.setContent(expected);
const response = r.getResponse();
console.log(JSON.stringify(response, undefined, 2))

{
  "head": {},
  "content": {
    "a": "hello",
    "b": "world"
  }
}
```

## Error response
``` javascript
import { ErrorResponse } from 'mf-response';
const r = new ErrorResponse();
r.setError('this is an error', 999);
const response = r.getResponse();
console.log(JSON.stringify(response, undefined, 2))

{
  "head": {},
  "content": {
    "error": {
      "message": "this is an error",
      "code": 999,
      "uuid": "1234"
    }
  }
}
```