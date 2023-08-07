when using the default session store for nextauth, only the session callback is needed. Maybe the jwt callback is needed for only the jwt strategy.

### Identity Provider Sign In Page
To implement a custom sign in page when using next-auth, use the sign in function from next-auth/react and then call that function, for example when a button is clicked, and set the variable to the Identity Provider's string.
See the following example:
```jsx
'use client'

import Script from 'next/script'
import { signIn } from 'next-auth/react';

export default function Home() {
  const myVariable = 'Hello, world!';
  return (
    <div>
      <p>Hello World!</p>
      <div id="myScriptContainer" data-variable={myVariable} />
      <Script src="/script.js" />
      <button onClick={() => signIn('keycloak')}>Sign in</button>
    </div>
  )
}
```

The callback URL for the Oauth Authentication Providers should be `{url-where-next-auth-is}/api/auth/callback/{provider}`.