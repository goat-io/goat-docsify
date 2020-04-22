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

Fluent.config({
  REMOTE_CONNECTORS: [{}],
  LOCAL_CONNECTORS: [{}],
  MERGE_CONNECTORS: [{}]
});
```

## Connectors

All Fluent connectors are independent libraries, so you will need to download them separetly.

Here is an example of a REMOTE connector using @gotlab/fluent-formio

```javascript
import formio from "@gotlab/fluent-formio";

Fluent.config({
  REMOTE_CONNECTORS: [
    {
      name: "formio",
      baseUrl: "https://ydrahgggqviwquft.form.io/",
      connector: formio
    }
  ],
  LOCAL_CONNECTORS: [{}],
  MERGE_CONNECTORS: [{}]
});
```

You can use as many connectors as you like. All available connectors are listed bellow.

### REMOTE

Remote connectors give you access to API's or Databases, such as MongoDB, Formio

| Provider | Library                 |
| -------- | ----------------------- |
| Formio   | @gotlab/fluent-formio   |
| Loopback | @gotlab/fluent-loopback |

### LOCAL

Local connectors give you access to in Browser/Memory DB's such as LokiJs, IndexedDB, LocalStorage

| Provider | Library             |
| -------- | ------------------- |
| LockiJS  | @gotlab/fluent-loki |

### MERGE

Merge connectors will pull from both Local and Remote storage providers and will merge results
to give you access to all your data from one call

| Provider    | Library            |
| ----------- | ------------------ |
| Loki-Formio | fluent-loki-formio |
