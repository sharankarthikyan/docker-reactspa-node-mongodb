## Building [ React SPA - Node - Mongo ] docker application

### Network creation:

/ $ `docker network create goals-net`

---

### MongoDB

/ $ `docker run -d --rm --name mongodb --network goals-net mongo`

---

### Node:

/backend $ `docker build -t goals-node .`

/backend $ `docker run -d --rm -p 80:80 --name goals-backend --network goals-net goals-node`

---

### React SPA:

/frontend $ `docker build -t goals-react .`

/frontend $ `docker run -d --rm -p 3000:3000 --name goals-frontend --network goals-net goals-react`
