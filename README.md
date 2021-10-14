# PUFFY WEB
		
> WARNING: Only supported by NodeJS >= 13. To use this package with NodeJS 12, use the `--experimental-modules` flag.
		
A collection of ES6 modules with zero-dependencies to help manage common programming tasks in Web projects only. This package is designed to work along side [`puffy-core`](https://github.com/nicolasdao/puffy-core) which exposes an extra set of [usefull APIs](https://github.com/nicolasdao/puffy-core#table-of-contents) that are compatible with both NodeJS and native JS.

```
npm i puffy-web
```

# Table of contents

> * [APIs](#apis)
>	- [`fetch`](#fetch)
> * [Unit test](#unit-test)
> * [License](#license)

# APIs
## `fetch`

```js
import { fetch as _fetch } from 'puffy-web/fetch'

const main = async () => {
  // fetch
  const { status, data } = await _fetch.get({
    uri: 'http://localhost:4220/entry/32',
    headers: {
      'Content-Type': 'multipart/form-data'
    },
    body: {
      hello: 'World',
      myFile: document.querySelector('input[type="file"]').files[0]
    }
  })

  // POST URL encoded data
  const { status:status2, data:data2 } = await _fetch.post({
    uri: 'http://localhost:4220/entry/32',
    headers: {
      'Content-Type': 'application/x-www-form-urlencoded'
    },
    body: {
      hello: 'World'
    }
  })

  // GraphQL
  const { status:status3, data:data3 } = await _fetch.graphql.query({ 
    uri: 'http://localhost:4220/graphql', 
    headers:{}, 
    query: `{ 
      users(where:{ id:1 }){ 
        id 
        name 
      } 
    }` 
  })

  const { status:status4, data:data4 } = await _fetch.graphql.mutate({ 
    uri: 'http://localhost:4220/graphql', 
    headers:{}, 
    query: `{ 
      userInsert(input:{ name:"Nic" }){ 
        id 
        name 
      } 
    }` 
  })
}

main()
```

# Unit test

```
npm test
```

# License

BSD 3-Clause License

Copyright (c) 2019-2021, Cloudless Consulting Pty Ltd
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
