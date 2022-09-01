## Building [ React SPA - Node - Mongo ] docker application

### Network creation:

/ $ `docker network create goals-net`

---

### MongoDB

/ $ `docker run -d --rm --name mongodb -v data:/data/db --network goals-net -e MONGO_INITDB_ROOT_USERNAME=sharan -e MONGO_INITDB_ROOT_PASSWORD=password mongo`

Any issues: try to remove volumes by -> `docker volume rm`

---

### Node:

/backend $ `docker build -t goals-node .`

/backend $ `docker run -d --rm --name goals-backend -p 80:80 -v /Users/sharan/Desktop/Sharan/Git/multi-01-starting-setup/backend:/app -v logs:/app/logs -v /app/node_modules -e MONGODB_USERNAME=sharan -e MONGODB_PASSWORD=password --network goals-net goals-node`

---

### React SPA:

/frontend $ `docker build -t goals-react .`

/frontend $ `docker run -d --rm -p 3000:3000 --name goals-frontend -v /Users/sharan/Desktop/Sharan/Git/multi-01-starting-setup/frontend/src:/app/src --network goals-net goals-react`
