# spring-boot-oracledb-logstash
## Introduction



## Build Oracle Database as Container

1. Clone git `https://github.com/oracle/docker-images`

2. Navigate to `/OracleDatabase/SingleInstance/dockerfiles`

3. Inside the Dockerfiles directory, it's going to show the list of available Oracle database versions. Choose the version that you want. 

4. Download Oracle Database Enterprise Edition or Standard Edition, which matches the version and OS that you want. (For ARM64 support: Oracle Database 19c Enterprise Edition)
`https://www.oracle.com/database/technologies/oracle-database-software-downloads.html`

5. Put the LINUX.ARM64_xxxxxx_db_home.zip file in the same directory version that you chose. Ex. `/OracleDatabase/SingleInstance/dockerfiles/19.3.0`

6. Back to  `/OracleDatabase/SingleInstance`

7. Build images: `./buildContainerImage.sh -v 19.3.0 -t oracle-db:19.3.0 -e` This process might take a long time to create a cappy file and then build images.

8. Docker run
```docker
docker run -d -it --name oracledb -p 1521:1521 -p 5500:5500 \
  -e ORACLE_PDB=TESTDB -e ORACLE_PWD=zxcv1234 \
  -v /your/local/path:/opt/in/container oracle-db:19.3.0
```
