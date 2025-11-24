# Clone an existing app from Github and dockerize the project
#### Assumptions:
- Windows 11 laptop
- Docker desktop is installed on the laptop
#### Steps:  
1. Browse the URL https://github.com/docker/awesome-compose
2. Create a folder on your laptop. Open the terminal at that folder.
3. 
   ```
   git clone https://github.com/docker/awesome-compose.git
   ```
4.
    ```
   cd nginx-flask-mysql
   ```
5.
    ```
   docker compose up -d
   ```
> [!NOTE]
> You should see similar output: 

   ```
    ...
    ✔ Container nginx-flask-mysql-db-1       Healthy                                                                  7.3s
    ✔ Container nginx-flask-mysql-backend-1  Started                                                                  7.8s
    ✔ Container nginx-flask-mysql-proxy-1    Started
   ```
> [!CAUTION]
####  Error: 

> I encountered this error on deplpoyment (after docker compose) found on Docker desktop with ``` nginx-flask-mysql-backend:latest ``` 
container:

> ``` ... ImportError: cannot import name 'url_quote' from 'werkzeug.urls' ...   ```

>  Also when browsed ``` localhost:80 ``` got this error ``` 502 Bad gateway ``` 

#### Fix: 
>  Explored that ``` Flask ``` and ``` Werkzeug ``` are NOT compatible

> Updated the ``` requirements.txt ``` file in the folder ``` backend ``` :

```
Flask==2.3.3
mysql-connector==2.2.9
Werkzeug==2.3.7
```
> Deleted all containers in Docker desktop.

> Ran ```docker compose up -d```

> It is solved.

6. Observe that all containers are running without error:
<img width="521" height="317" alt="image" src="https://github.com/user-attachments/assets/5cf12302-c0db-4291-a85a-02e8d03a4555" />

7. curl the URL and  observe similar output:
```
 curl http://localhost:80
```
<img width="1323" height="202" alt="image" src="https://github.com/user-attachments/assets/2a760811-70f8-4914-8f35-ad07b3d4d781" />

8. Browse ``` localhost:80 ``` and should see similar output:
<img width="285" height="150" alt="image" src="https://github.com/user-attachments/assets/54c0db37-3308-491f-aba6-038522e0fc4d" />

8. Stop and remove the containers
```
docker compose down
```













































































