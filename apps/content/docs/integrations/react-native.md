---
title: React Native Integration
description: Seamlessly integrate oRPC with React Native
---

# React Native Integration

[React Native](https://reactnative.dev/) is a framework for building native apps using React.

## Fetch Link

React Native includes a [Fetch API](https://reactnative.dev/docs/network), so you can use oRPC out of the box.

::: warning
However, the Fetch API in React Native has limitations. oRPC features like `File`, `Blob`, and `AsyncIteratorObject` aren't supported. Follow [Support Stream #27741](https://github.com/facebook/react-native/issues/27741) for updates.
:::

```ts
import { RPCLink } from '@orpc/client/fetch'

const link = new RPCLink({
  url: 'http://localhost:3000/rpc',
  headers: async ({ context }) => ({
    'x-api-key': context?.something ?? ''
  })
  // fetch: <-- polyfill fetch if needed
})
```

::: info
The `link` can be any supported oRPC link, such as [RPCLink](/docs/client/rpc-link), [OpenAPILink](/docs/openapi/client/openapi-link), or another custom link.
:::
