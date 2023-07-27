Follow the Next Js App Router Deploying section to create the production build -> https://nextjs.org/docs/app/building-your-application/deploying

1. Ensure the following code is in the package.json file
```js
{ "scripts": { "dev": "next dev", "build": "next build", "start": "next start" }}
```
2. Run `npm run build` to build the project in the .next folder of the project directory.
3. Run `npm run start` to run the application

Follow the Nginx reverse proxy page to configure Nginx -> https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/
Setup Nginx as a reverse proxy by setting the server and port the app is running on.