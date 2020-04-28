# FLUENT

Lightweight JS query builder for APIs. Build your own connectors and enjoy quering your services in a similar fasion.
Fluent works for both Local and Remote Storage/API providers

### Installing

To install this package in your project, you can use the following command within your terminal.

```
npm install --save @gotlab/fluent
```

# Config

Fluent offers a handy configuration method that will get you up and running in seconds.

```javascript
import { Fluent } from "@gotlab/fluent";

new Fluent().config({
  LOCAL_CONNECTORS: [],
  MERGE_CONNECTORS: [],
  REMOTE_CONNECTORS: [BackendConnector]
});
```

## Connectors

All Fluent connectors are independent from each other, so you will need to download them separetly.

Here is an example of a REMOTE connector using Loopback

```javascript
import { Fluent } from "@gotlab/fluent";
import { Loopback } from "@goatlab/fluent/dist/Providers/Loopback/LoopbackConnector";

const BackendConnector = {
  baseUrl: "http://localhost:3001",
  connector: Loopback,
  default: true,
  name: "backend"
};

new Fluent().config({
  LOCAL_CONNECTORS: [],
  MERGE_CONNECTORS: [],
  REMOTE_CONNECTORS: [BackendConnector]
});
```

You can use as many connectors as you like. All available connectors are listed bellow.

### REMOTE

Remote connectors give you access to API's or Databases, such as MongoDB, Formio

| Provider | Import path                                                                              |
| -------- | ---------------------------------------------------------------------------------------- |
| Formio   | import { FormioConnector } from "@goatlab/fluent/dist/Providers/Formio/FormioConnector"; |
| Loopback | import { Loopback } from "@goatlab/fluent/dist/Providers/Loopback/LoopbackConnector";    |

### LOCAL

Local connectors give you access to in Browser/Memory DB's such as LokiJs, IndexedDB, LocalStorage

| Provider | Import path                                                                        |
| -------- | ---------------------------------------------------------------------------------- |
| LockiJS  | import { LokiConnector } from "@goatlab/fluent/dist/Providers/Loki/LokiConnector"; |
| Memory   | import { Loopback } from "@goatlab/fluent/dist/Providers/Memory/MemoryConnector";  |

### MERGE

Merge connectors will pull from both Local and Remote storage providers and will merge results
to give you access to all your data from one call
