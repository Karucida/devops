I use the port 9998 instead of 9000. To access via web.
Download docker-compose.yml

```
docker-compose up -d
```


```
http://localhost:9998/
```
default user/password 
```
admin / admin
```

Install [sonar-scanner](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)
Unzip and to use like variable system
```
$ export PATH=$PATH:$HOME/path/to/sonar-scanner/bin
```

Go to your project
```
$ cd /path/of/your/project
$ sonar-scanner
```

sonar-project.propierties on `/path/of/your/project`:
```
sonar.projectKey=<projectname>
sonar.projectName=<projectname>
sonar.projectVersion=1.0
sonar.host.url=http://localhost:9998
# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
# If not set, SonarQube starts looking for source code from the directory containing 
# the sonar-project.properties file.
sonar.sources=<path/to/analize>
sonar.sourceEncoding=UTF-8
sonar.login=<token_generate_on_sonar>
```

