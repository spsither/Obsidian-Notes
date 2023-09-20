## using `pm2`
install `pm2`
`npm install pm2 -g`
go to `Next.js` project `dir` and scaffold a deployment script
`pm2 init simple`
put the following in the `ecosystem.config.js`
```javascript
module.exports = {
  apps: [
    {
      name: 'NextAppName',
      exec_mode: 'cluster',
      instances: 'max', // Or a number of instances
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

add the following lines to `package.json`
```json
...
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "deploy:local": "next build && pm2 startOrRestart ecosystem.config.js --env local"
    "deploy:dev": "next build && pm2 startOrRestart ecosystem.config.js --env development"
    "deploy:prod": "next build && pm2 startOrRestart ecosystem.config.js --env production"
  },
  ...
```

run it
`npm run deploy:prod`

check if success
`pm2 ls`

save the running processes and have to run on system restart
`pm2 save`
`pm2 startup`

## for local
`npm run build`
`npm run start`

## background and disown
If you want to "background" already running tasks, then Ctrl+Z then run `bg` to put your most recent suspended task to background, allowing it to continue running. `disown` will keep the process running after you log out. The `-h` flag prevents hangup.
_ctrl+z_
`bg`
`disown -h`

## use [[how to tmux]]

[apache and node with pm2](https://dev.to/tikam02/how-to-deploy-node-server-on-apache2-23d7)
[next.js deploy with pm2](https://dykraf.com/blog/deploying-nextjs-web-application-with-pm2)
[on DigitalOcean](https://docs.digitalocean.com/tutorials/app-nextjs-deploy/#:~:text=29%20Sep%202021-,Next.,splitting%20and%20Bundling%20and%20more.)
[full stack books](https://www.fullstackbook.com/guides/how-to-deploy-nextjs-with-pm2/)