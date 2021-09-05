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
```
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```
## 4. Deployment ##
```
npm install -g caprover
caprover serversetup
caprover deploy
```
## 5. Auto Deploy ##
