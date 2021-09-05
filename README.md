## Deploy using Caprover ##
## 1. APP ##
```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})
```
## 2. Docker File ##
https://nodejs.org/de/docs/guides/nodejs-docker-webapp/
```
FROM node:14
WORKDIR /usr/src/app
COPY package*.json ./

RUN npm install
COPY . .
EXPOSE 3000
CMD [ "node", "index.js" ]
```
## 3. Caprover ##
https://caprover.com/docs/get-started.html
```
apt install docker.io
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```
## 4. Deployment ##
https://caprover.com/docs/deployment-methods.html
```
npm install -g caprover
caprover serversetup
caprover deploy
```

```
ssh-keygen -m PEM -t rsa -b 4096 -C "caprover" -f ./deploykey -q -N ""
```
