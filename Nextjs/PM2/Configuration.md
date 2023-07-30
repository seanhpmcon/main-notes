#nodejs
### Install pm2
Use the command `npm install pm2 -g` to install pm2 globally in the application.

### Add pm2 files
Use the command `pm2 init simple` to create the `ecosystem.config.js` file and modify it with the following script:
```js
module.exports = {
  apps: [
    {
      name: 'NextAppName',
      exec_mode: 'cluster',
      instances: 1, // Or a number of instances
      script: 'node_modules/next/dist/bin/next',
      args: 'start',
      env_local: {
        APP_ENV: 'local' // APP_ENV=local
      },
      env_development: {
        APP_ENV: 'dev' // APP_ENV=dev
      },
      env_production: {
        APP_ENV: 'prod' // APP_ENV=prod
      }
    }
  ]
}
```
Add the following code to the `package.json` file:
```json
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "deploy:local": "next build && pm2 startOrRestart ecosystem.config.js --env local"
  },
```

Then build and run the app using pm2 with the following command: `npm run deploy:local`