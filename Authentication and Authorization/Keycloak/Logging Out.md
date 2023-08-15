To properly log out of keycloak, you have to call the API endpoint to kill the user session on keycloak as well. This API endpoint is:
`http://keyclock-server/realms/keycloak-realm/protocol/openid-connect/logout` with `x-www-form-urlencoded` parameters:
```json
'refresh_token': refresh_token,
'client_id': client_id,
'client_secret': client_secret
```

### Nextjs Nextauth implementation
Create a sign-out button that first ends the keycloak session and signs out the user from the nextjs app and remove its cookies from the browser.

Use an API route that contains the logic to end the keycloak session and return a response. After that response is returned, sign out the use from the nextjs app by simply calling the nextauth sign-out function.

Route logic `route.js`:
```js
import { authOptions } from "../[...nextauth]/route";
import { getServerSession } from "next-auth"

export async function GET() {
  const session = await getServerSession(authOptions);

  if (session) {

    const formData = new URLSearchParams({
        'refresh_token': session.refresh_token,
        'client_id': 'testclient',
        'client_secret': 'SO1nZwn5TCNZpRrR6ucCC72O2mTQT13S'
    });

    // this will log out the user on Keycloak side
    //const url = `${process.env.KEYCLOAK_ISSUER}?id_token_hint=${idToken}&post_logout_redirect_uri=${encodeURIComponent(process.env.NEXTAUTH_URL)}`;

    const url = `http://172.24.160.1:8099/realms/test-auth/protocol/openid-connect/logout`;

    try {
      const resp = await fetch(url, {  method: 'POST',
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
      },
      body: formData });
    } catch (err) {
        console.log(err)
      return new Response({ status: 500 });
    }
  }
  return new Response({ status: 200 });
}
```

The client side page with sign-out button `paage.jsx`:
```jsx
'use client'

import Script from 'next/script'
import { signIn, signOut } from 'next-auth/react';
import { useSession } from "next-auth/react"

async function keycloakSessionLogOut() {
  try {
    await fetch(`/api/auth/logout`, { method: "GET" });
  } catch (err) {
    console.error(err);
  }
}

export default function Home() {
  const myVariable = 'Hello, world!';
  const { data: session, status } = useSession()
  return (
    <div>
      <p>Hello World!</p>
      <div id="myScriptContainer" data-variable={myVariable} />
      <Script src="/script.js" />
      {status === "authenticated" ? (
        <button onClick={() => {
          keycloakSessionLogOut().then(() => signOut());
        }}>Sign Out</button>
      ) : (
        <button onClick={() => signIn('keycloak')}>Sign in</button>
      )}
    </div>
  )
}
```