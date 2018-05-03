#### 35-sluggram-frontend
This lab 35, is prepping lab 33 for Heroku Deployment.


#### How to get up and running:
Fork and clone 

Here is my heroku front end url: https://sluggram401-frontend.herokuapp.com/

#### Additions/changes necessary for deployment:
- We added the following to the package.json, the -p flips our webpack.config to production:
```
    "heroku-postbuild": "webpack -p --progress"
```

- We changed the following:
From this:
```
  "main": "webpack.config.js",
```
To this:
```
  "main": "server.js",
```

- Added that server.js at the root level with the following:
```js
const express = require('express');

const app = express()

app.use(express.static(`${__dirname}/build`))
app.get('*', (req, res)=> res.sendFile(`${__dirname}/build/index.html`))

app.listen(process.env.PORT, () => console.log(`SERVER RUNNING ON: ${process.env.PORT}`))
```
