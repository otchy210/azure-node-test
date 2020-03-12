# azure-node-test

## Trying to update README.md

Update it, save it, `git add` it, and `git commit` it in the Online VS Code Terminal.

And `git push` prompts you to authorize your Github account, after that, you can push it.

## I don't know how to install Node in this instance.

Node v12 is the default!

## Next thing I want to confirm is how to run node server from here and test it.

Just run it. For example,

```
$ npm init
$ npm install express --save
$ touch app.js

# edit app.js and package.json

$ npm start
```

Once you start listing certain port, Azure detects the port and configure port forwarding _automatically_. Then you can find temporary URL in the `Remote Explorer > Environment Details > Forwareded Ports`.

## Sounds awesome! So, how can I publish it? In other words, how to tie the master branch to a concrete domain?

- Create new Web App from [Azune Portal](https://portal.azure.com/).
    - `App Services > Create app service`
    - Default settings are mostly fine, but make sure choosing `Node 12 LTS` as Runtime stack
    - Get `<your-domaing-name>.azurewebsites.net`
- Get listening port from environment variables
    - app.js: `const port = process.env.PORT || 3000;`
- Connect the Web App to the Github repo
    - Open the new service
    - `Deployment Center > GitHub > Authorize > App Service build service`
    - Select code to deploy from GitHub

Next time you update your master branch, the Web App will automatically capture it and update itself.

## Fantastic! However, I want to use my own domain, rather than *.azurewebsites.net
