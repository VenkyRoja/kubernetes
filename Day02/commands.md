# Docker Commands
| Command                   | Explanation                                           | Switches                       |
| ------------------------- |-------------------------------------------------------| -------------------------------|
| ```docker init```         | Creates Docker-related starter files for your project | ```--version```                |
| ```docker pull```         | Download an image from a registry                     |    ```-a```  ```-q```          |
| ```docker push```         | Upload an image to a registry                         |    ```-a```  ```-q```          |
| ```docker build```        | Start a build                                         |    ```-t``` and many           |
| ```docker run```          | Create and run a new container from an image          |    ```-d```  ```-p``` and many |
| ```docker exec```         | Execute a command in a running container              |    ```-i```  ```-t``` and many |
| ```docker login```        | Authenticate to a registry                            |    ```-p```  ```-u```          |
| ```docker tag```          | Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE |    No switches                 | 
| ```docker images```       | List images                                           |    many                        |
| ```docker logs```         | Fetch the logs of a container                         |    many                        |
| ```docker inspect```      | Return low-level information on Docker objects        |    ```-f```  ```-s```          |
| ```docker ps```           | List containers                                       |    many                        |
| ```docker compose up```   | Create and start containers                           |    ```-d``` and many           |
| ```docker compose down``` | Stop and remove containers, networks                  |    many                        |
