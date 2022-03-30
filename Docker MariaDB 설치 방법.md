```
docker --version                          // 도커 버전 확인

docker search mariadb                     // 이미지 조회
docker pull mariadb                       // 이미지 다운로드(버전을 지정하지 않을 경우 최신 버전 다운로드)
docker images                             // 다운로드한 이미지 확인

// MariaDB 컨테이너 생성 및 실행
docker run --name mariadb_container -d -p 3306:3306 -e MARIADB_ROOT_PASSWORD={password} -e MARIADB_USER={user} -e MARIADB_PASSWORD={password} mariadb --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

```
docker ps                                 // 실행 중인 컨테이너 출력
docker ps -a                              // 컨테이너 리스트 출력

docker start mariadb_container            // 컨테이너 실행
docker stop mariadb_container             // 컨테이너 중단
docker restart mariadb_container          // 컨테이너 재시작
```

```
docker exec -i -t mariadb_container bash  // 컨테이너 접속
mariadb -u root -p                        // MariaDB 접속

show databases;

use {database name};

show tables;

select * from {table name};

exit
```

## Reference
- https://hub.docker.com/_/mariadb
