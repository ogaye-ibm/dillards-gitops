# cp4a-ocp-liberty-certs-poc

October 2020  - Omar

### Build
- run command:
```yaml
./gradlew clean build -x test
```
- demo.jar uber/fat jar will be created under build/libs


### Run
- On Default port 8080: 

```bash 
./gradlew bootRun
```
- On Custom port (e.g. 8081): 

```bash
PORT=8081 ./gradlew bootRun

```


### Test

- http://localhost:8080/demo/hello
  - Output will be: Hello CP4A
- http://localhost:8080/demo/hello/Bob
  - Output will be: Hello Bob

Containerizing Spring Boot, best practice: https://spring.io/guides/gs/spring-boot-docker/
