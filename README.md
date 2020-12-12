# ejemplo-gradle

## Windows

### Compile Code ### Test Code ### Jar Code
* ./mvnw.cmd gradle build

### Run Jar
* Local:      ./mvnw.cmd  gradle bootRun
* Background: nohup bash mvnw.cmd spring-boot:run &

### Testing Application
* Abrir navegador: http://localhost:8081/rest/mscovid/test?msg=testing

## Linux

### Compile Code ### Test Code ### Jar Code
* gradle clean build

### Run Jar
* Local:      gradle bootrun 
* Background: nohup gradle bootrun &

### Testing Application
* curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'