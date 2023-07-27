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

<<<<<<< HEAD
### Build Process
use the command `npx next build` to create a production build of the next js app.

### Start the app
Use the command `npx next start` to start the build of the app.

=======
### Running the Production build in the background and ending it when needed

To run an npm script in the background, you can use the `&` operator at the end of the command. The `&` operator allows the command to run in the background, allowing you to continue using the terminal for other tasks.

Here's how you can run an npm script in the background:

```bash
npm run start &
```

This will start the npm script defined in your `package.json` file with the name "start" in the background.

Keep in mind that running a script in the background means it will continue running even after you close the terminal or log out of the session. If you want to stop the background process later, you can find its process ID (PID) using the `ps` command and then terminate it using the `kill` command.

For example, to stop the background process, you can use the following commands:

1. Find the process ID of the background process:

```bash
ps aux | grep "npm run start"
```

This will display information about all running processes that include "npm run start". Look for the process ID (second column) of the background process.

2. Terminate the background process using its process ID (replace `<PID>` with the actual process ID):

```bash
kill <PID>
```

Please note that running background processes comes with its own considerations and you should ensure that it's appropriate for your specific use case and environment.
>>>>>>> origin2/main
