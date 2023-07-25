Install a new project
`npx create-next-app@latest`
Use `npx create-next-app@latest .` to create the project the current folder.

### Nextjs in Node Containers
[[Initializing dev containers]]

### Create the production build in a build folder
Add the following code to the next.config.js file
```js
module.exports = { distDir: 'build',}
```

### Build Process
use the command `npx next build` to create a production build of the next js app.

### Start the app
Use the command `npx next start` to start the build of the app.

