# DockerRunPython-x.y.z
How to use Docker to install and run any Python version including Python 2 up to the newest Release Candidate (RC), and any x.y.z in between

```$ docker run -it --rm python:3.7.9```
```$ docker run -it --rm python:2.7```
```$ docker run -it --rm python:rc```

```$ docker images python```

```
REPOSITORY   TAG               IMAGE ID       CREATED         SIZE
python       rc                6541016e3458   6 days ago      889MB
python       3.7.9             65d5b6c539fd   6 months ago    877MB
python       2.7               68e7be49c28c   16 months ago   902MB
```
