 Rosco Image build task SHA acton test  
    
[![Build Status](https://api.travis-ci.org/spinnaker/rosco.svg?branch=master)](https://travis-ci.org/spinnaker/rosco)

Rosco is Spinnaker's bakery, producing machine images with Hashicorp Packer and rendered manifests with templating engines Helm and Kustomize.
  
It presently supports producing Alibaba Cloud images, Google Compute Engine images, Huawei Cloud images, Tencent Cloud images, AWS AMI's and Azure images. It relies on [Hashicorp Packer](https://www.packer.io/) and can be easily extended to support additional platforms.

It exposes a REST api which can be experimented with via the Swagger UI: http://localhost:8087/swagger-ui.html
  
# Developing rosco
 
Need to run rosco locally for development? Here's what you need to setup and run:

## Environment Setup
```
git clone git@github.com:spinnaker/rosco.git
git clone git@github.com:spinnaker/spinnaker.git
```

## Docker Setup (runs redis locally)
```
docker-machine create --virtualbox-disk-size 8192 --virtualbox-memory 8192 -d virtualbox spinnaker
eval $(docker-machine env spinnaker)
cd spinnaker/experimental/docker-compose
docker-compose up -d redis
```

## Verify redis
```
docker run -it --link redis:redis --rm redis redis-cli -h redis -p 6379
(printf "PING\r\n";) | nc -v localhost 6379
```

## IDE setup

### Generate Intellij gradle project files
```
./gradlew idea
```

### Apply groovy code formatting scheme

1) Preferences -> Editor -> Code Style -> Manage ... -> Import -> select codestyle.xml from the project directory.
2) Apply the 'spinnaker' scheme.

## Running App
```
./gradlew
```

### Debugging

To start the JVM in debug mode, set the Java system property `DEBUG=true`:
```
./gradlew -DDEBUG=true
```

The JVM will then listen for a debugger to be attached on port 8187.  The JVM will _not_ wait for the debugger
to be attached before starting Rosco; the relevant JVM arguments can be seen and modified as needed in `build.gradle`.

## Verifying
```
curl -v localhost:8087/bakeOptions
```

## Swagger
```
http://localhost:8087/swagger-ui.html
```

## Docker teardown
```
docker-compose stop
docker-machine rm spinnaker
```



$${\color{lightblue} Recent \space commits:}$$ 

              CommitID                   |   Author      | Commit Message          | Commit Date
----------------------------------------------------------------------------------------------------



97703e6f5e22e33a2883e8e61585f8e5eb5f58bd | Yugandharkumar | Create commits-preserve.yml | 2023-08-09 



1b763969fbeef498f685094feabdb20de4516f90 | Yugandharkumar | Create Release_Build_Push.yml | 2024-03-11 



ae23bc8bb74565dfbc92949276b13a756c845fec | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 


b3640f1d1560119cd06eb55416bb4627717049c3 | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 



f6e349a23ae7a6caae283d4d94b9c2b864bd314d | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 



d6ab7b42a053e4fbbcf9ae9762dc1ecf70caec89 | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 


570641a02226d5a8cdab1b708080f493b926c477 | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 



ff7f1a9beefc790e4761d581aa04b6c5200f6c27 | Yugandharkumar | Merge pull request #27 from OpsMx/testing | 2024-03-12 


bf76c298cc3ac95cb7ec08bed46247a5f4dd96da | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 



f4042909d16f46fc6bb0ad16a0385fad270dfbc2 | Yugandharkumar | Update Release_Build_Push.yml | 2024-03-12 


429c39f6c8ebdce89b192a4e48635c477047ac72 | Yugandharkumar | Merge pull request #30 from OpsMx/testing | 2024-03-22 


1a48cf30d78bb52cbb291f08fda5e1222475162a | Yugandharkumar | Merge pull request #31 from OpsMx/testing | 2024-03-22 


24170c4d206cf653467535d35add962156ad32b7 | Yugandharkumar | Merge pull request #32 from OpsMx/testing | 2024-03-22 


70146e95976fc749a951472b2dadccfbcd0e94bd | Yugandharkumar | Merge pull request #33 from OpsMx/testing | 2024-03-22 