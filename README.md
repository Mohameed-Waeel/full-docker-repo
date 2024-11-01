# full-docker-repo
A complete setup for deploying and managing Docker containers. Includes Docker Compose configurations, custom networks, volumes for persistent storage, and environment management. Ideal for streamlining containerized applications and simplifying deployment.

- index.html with pure js and css styles
- nodejs backend with express module
- mongodb for data storage

# With Docker
![01-primary-blue-docker-logo_rl8tst](https://github.com/user-attachments/assets/df6ae12b-5647-4f54-97e1-aaabb96ea6d2)

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

![2](https://github.com/user-attachments/assets/5e0d0dad-b562-4474-9adb-7c7ddc59ae86)


Step 2: start mongodb 
```
    docker run -d \
  --name mongodb \
  --net mongo-network \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  -v mongo-data:/data/db \
  mongo
``` 

Step 3: start mongo-express
```
    docker run -d \
  --name mongo-express \
  --net mongo-network \
  -p 8080:8081 \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
  -e ME_CONFIG_MONGODB_SERVER=mongodb \
  mongo-express
```
![1](https://github.com/user-attachments/assets/917d9d9d-cbae-4ed6-9d68-26cf175f405d)


Step 4: open mongo-express from browser

    http://localhost:8080

Step 5: create `my-db` and `users` in mongo-express

![0](https://github.com/user-attachments/assets/36dcfc6c-4e73-422c-9223-0567dc83e6a1)

![00](https://github.com/user-attachments/assets/f65fe992-f407-48ea-842b-616669a1652e)


Step 6: Start your nodejs application locally - go to `app` directory of project 

    cd app
    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000
    
### Result
![3](https://github.com/user-attachments/assets/0fe234b5-868e-4eff-9250-cbe66a15ec45)

![4](https://github.com/user-attachments/assets/6fd51e22-704d-432e-b5db-5f4298acd09b)

![5](https://github.com/user-attachments/assets/1897f760-07ee-4b3f-b743-7fc343c0fd35)

![6](https://github.com/user-attachments/assets/bbcfeb37-0375-4812-bf93-eda9a056a3f1)


# With Docker Compose
![docker-compose-button](https://github.com/user-attachments/assets/d231a0aa-f10f-4ff4-bebb-63c012de04a4)

#### To start the application

Step 1: start mongodb and mongo-express

    docker compose -f docker-compose.yaml up
    
![170](https://github.com/user-attachments/assets/0431efa8-b066-492a-abf1-2ef74b92fd21)

![60](https://github.com/user-attachments/assets/1a5e8b25-7a7e-4e34-8ecf-e9d4433ac145)

![70](https://github.com/user-attachments/assets/32100c7e-513a-4393-a8e1-a43ded0c7bad)

### Docker Volumes
![80](https://github.com/user-attachments/assets/cd0f9dd0-4aab-44d6-84e7-1c1453b0f633)

![90](https://github.com/user-attachments/assets/ec569d9d-3547-4986-8d00-48dcd702829a)


_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: in mongo-express UI - create a new database "my-db"

Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"   

![40](https://github.com/user-attachments/assets/3f2c5328-5c6d-4c5f-86ed-6abe06fb1993)

    
Step 4: start node server 

    cd app
    npm install
    node server.js
    
Step 5: access the nodejs application from browser 

    http://localhost:3000
![50](https://github.com/user-attachments/assets/db2e7a7f-90fd-4fa0-a8e2-48533b6193e4)


#### To build a docker image from the application

    docker build -t my-app-wael:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.

## Push to Docker Hub
![011](https://github.com/user-attachments/assets/55840619-4423-410a-9b9f-992e2b2666e3)

![0111](https://github.com/user-attachments/assets/34a44e1c-fc48-4da6-b6b3-168d1844af7f)

![01111](https://github.com/user-attachments/assets/1d81e4d8-89b0-4990-a46c-dfc6df179a00)

# Private Docker Repositry with [ECR](Elastic Container Registry)
![images](https://github.com/user-attachments/assets/062ec642-0e75-465b-8142-1be0fa7aeb78)

### Create ECR
![20](https://github.com/user-attachments/assets/159804c8-7e2f-4eb3-9310-42d316d72f07)

### Commands used
![10](https://github.com/user-attachments/assets/50f2d9d6-47e8-4097-8aa7-102b7fa6a3c7)

### Result
![100](https://github.com/user-attachments/assets/c8e31c5c-bb7d-427e-83c5-3b695446455f)

![30](https://github.com/user-attachments/assets/096acb9e-4c18-4ec7-9c4d-9a9c135a276e)

# Docker with Nexus Repository OSS (Open Source Software)
![Rt1mT1vKp](https://github.com/user-attachments/assets/e9b11269-5bfb-4756-9651-993f057d2030)

### create docker-hosted 
![130](https://github.com/user-attachments/assets/549f9bd5-ca36-477c-9da1-ebe90328f7d7)

### create user
![140](https://github.com/user-attachments/assets/361be8d9-ce7d-401e-ae5a-c51875747422)

### create realms
![150](https://github.com/user-attachments/assets/2cf1b1e2-f816-49d2-a18e-1a202e867831)

### Docker login to Nexus
![160](https://github.com/user-attachments/assets/e23c4837-8734-4900-9f00-5581550632dc)

### result
![110](https://github.com/user-attachments/assets/8fb16100-f952-467f-8487-b66bc4395e92)

![120](https://github.com/user-attachments/assets/b9c0ba67-a597-4b5a-9cde-46a57d99ce18)



