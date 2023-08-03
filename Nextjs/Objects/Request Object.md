The request object in nextjs looks like the following:
```json
{
  cookies: RequestCookies {},
  geo: {},
  ip: undefined,
  nextUrl: {
  href: 'http://localhost:3000/page',
  origin: 'http://localhost:3000',
  protocol: 'http:',
  username: '',
  password: '',
  host: 'localhost:3000',
  hostname: 'localhost',
  port: '3000',
  pathname: '/page',
  search: '',
  searchParams: URLSearchParams {  },
  hash: ''
},
  url: 'http://localhost:3000/page',
  bodyUsed: false,
  cache: 'default',
  credentials: 'same-origin',
  destination: '',
  headers: {
  accept: 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7',
  accept-language: 'en-US,en;q=0.9',
  connection: 'keep-alive',
  host: 'localhost:3011',
  purpose: 'prefetch',
  sec-ch-ua: '"Not/A)Brand";v="99", "Google Chrome";v="115", "Chromium";v="115"',
  sec-ch-ua-mobile: '?0',
  sec-ch-ua-platform: '"Windows"',
  sec-fetch-dest: 'document',
  sec-fetch-mode: 'navigate',
  sec-fetch-site: 'none',
  sec-fetch-user: '?1',
  sec-purpose: 'prefetch;prerender',
  upgrade-insecure-requests: '1',
  user-agent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0.0.0 Safari/537.36',
  x-forwarded-for: '::ffff:172.17.0.1',
  x-forwarded-host: 'localhost:3011',
  x-forwarded-port: '3011',
  x-forwarded-proto: 'http',
  x-invoke-path: '',
  x-invoke-query: '',
  x-middleware-invoke: '1'
},
  integrity: '',
  keepalive: false,
  method: 'GET',
  mode: 'cors',
  redirect: 'follow',
  referrer: 'about:client',
  referrerPolicy: '',
  signal: AbortSignal {
  [Symbol(kAborted)]: false,
  [Symbol(kReason)]: undefined,
  [Symbol(kOnabort)]: undefined,
  [Symbol(realm)]: {
  settingsObject: {
  baseUrl: undefined,
  origin: [Getter],
  policyContainer: { referrerPolicy: 'strict-origin-when-cross-origin' }
}
}
}
}
```

### To get the Pathname of the URL
Use `request.nextUrl.pathname` to get the pathname of the URL