# @moeenn/fetch
Native Fetch with better ergonomics and error reporting. All the features of `fetch` are supported with the following additional features

- Header `Content-Type` with value `application/json` is automatically added, if not explicitly provided.
- A default timeout of 10 seconds is added on all requests, unless explicitly provided.
- In case of request timeout, an instance of Error is thrown instead of the weird DOMException.
- Errors are thrown in case response status code is 400 or above.
- Error messages may be returned from the server in case of error status codes. This library will attempt to read them in keys `error` or `message`. If a `string` value is found in the (JSON) response, that value will be thrown as Error.


## Installation

```bash
$ npm i @moeenn/fetch
```

## Usage

```ts
import { fetchJSON } from "@moeenn/fetch"

async function getUser(id: number): Promise<User> {
  const url = BASE_API_URL + "/user/" + id
  const res: unknown = await fetchJSON(url, {
    // any fetch option can go here
    method: "GET",

    // provide a custom request timeout
    timeout: 20_000,
  })

  // do something with the response
}
```