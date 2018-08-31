
# Simple File Server via Nginx


## build

    docker build -t file-server .


## run

    docker run -it --rm -p 8080:80 -v `pwd`/shared:/opt/files file-server

or background

    docker run  -d --rm -p 8080:80 -v `pwd`/shared:/opt/files file-server


## upload

    echo foobar | curl -T - localhost:8080/upload/hello.txt

or

    curl -T ./README.md localhost:8080/upload/hello.txt


## test

    curl localhost:8080/public/hello.txt

