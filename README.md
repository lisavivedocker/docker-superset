# Superbe projet - Docker - Contenerization

# contributors
Sara Lehtitet et la géniale Lisa Hourmand

# docker-superset
Repository for building [Docker](https://www.docker.com/) container of [Apache Superset](https://superset.incubator.apache.org/tutorial.html).

[<img src="https://cloud.githubusercontent.com/assets/130878/20946612/49a8a25c-bbc0-11e6-8314-10bef902af51.png" alt="Superset" width="500"/>](https://superset.incubator.apache.org/tutorial.html)

# Git FLOW 
we used the git flow for this project. The structure of our repository is the following : 
3 branchs : - featsara
            - featlisa
            - dev
and the remote 'master'

![image](https://user-images.githubusercontent.com/48882137/155838038-6d7aebed-8ed0-4f23-a62d-8b4e86679983.png)

## How to run using docker commands
* Through general docker commands -
    * first pull a docker-superset image from [docker-hub](https://hub.docker.com/r/abhioncbr/docker-superset/) using either
        ```shell
        docker pull abhioncbr/docker-superset
        ```    
      or for specific superset version by providing version value    
        ```shell
        docker pull abhioncbr/docker-superset:<version-tag>
        ```   
    
    * Copy [superset_config.py](config/superset_config.py), [docker-compose.yml](docker-files/docker-compose.yml), and [.env](docker-files/.env) files. I am considering directory structure like below
        ```
        docker-superset
             |_ config
             |    |_superset_config.py
             |
             |_docker-files
             |    |_docker-compose.yml
             |    |_.env
        
        ```   

    * using `docker-compose`:
        * starting a superset image as a `superset` container in a **local** mode:
            ```shell
            cd docker-superset/docker-files/ && docker-compose up -d
            ```
          or for passing some different environment variables values like below
            ```shell
            cd docker-superset/docker-files/ && SUPERSET_ENV=local SUPERSET_VERSION=<version-tag> docker-compose up -d
            ```           
        
        * starting a superset image as a `superset` container in a **prod** mode:
            ```shell
            cd docker-superset/docker-files/ && SUPERSET_ENV=prod SUPERSET_VERSION=<version-tag> docker-compose up -d
            ```
            
    * using `docker run`:    
        * starting a superset image as a `server` container:
            ```shell
            cd docker-superset && docker run -p 8088:8088 -v config:/home/superset/config/ abhioncbr/docker-superset:<version-tag> cluster server <superset_metadata_db_url> <redis_url>
            ```        
        * starting a superset image as a `worker` container:
            ```shell
             cd docker-superset && docker run -p 5555:5555 -v config:/home/superset/config/ abhioncbr/docker-superset:<version-tag> cluster worker <superset_metadata_db_url> <redis_url>
            ```    
       
    [<img src="docker-superset_execution.png" alt="Superset">](docker-superset_execution.png)   
         
   
   
   
