# DockerRunPython-x.y.z
How to use Docker to install and run any Python version including Python 2 up to the newest Release Candidate (RC), and any x.y.z in between

```$ docker run -it --rm python:3.7.9```

```
Python 3.7.9 (default, Feb  9 2021, 08:33:04) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
```

```$ docker run -it --rm python:2.7```

```
Unable to find image 'python:2.7' locally
2.7: Pulling from library/python
7e2b2a5af8f6: Downloading  507.1kB/50.38MB
09b6f03ffac4: Downloading  1.403MB/7.812MB
dc3f0c679f0f: Downloading  1.342MB/9.996MB
fd4b47407fc3: Waiting 
b32f6bf7d96d: Waiting 
6f4489a7e4cf: Waiting 
af4b99ad9ef0: Waiting 
39db0bc48c26: Waiting 
acb4a89489fc: Waiting 
```
Interestingly this Python2 is a larger file than any of the Python3 images.
Watch as it will start itself a Python2.7 session right away:
```
2.7: Pulling from library/python
7e2b2a5af8f6: Pull complete 
09b6f03ffac4: Pull complete 
dc3f0c679f0f: Pull complete 
fd4b47407fc3: Pull complete 
b32f6bf7d96d: Pull complete 
6f4489a7e4cf: Pull complete 
af4b99ad9ef0: Pull complete 
39db0bc48c26: Pull complete 
acb4a89489fc: Pull complete 
Digest: sha256:cfa62318c459b1fde9e0841c619906d15ada5910d625176e24bf692cf8a2601d
Status: Downloaded newer image for python:2.7
Python 2.7.18 (default, Apr 20 2020, 19:27:10) 
[GCC 8.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```


```$ docker run -it --rm python:rc```

```$ docker images python```

```
REPOSITORY   TAG               IMAGE ID       CREATED         SIZE
python       rc                6541016e3458   6 days ago      889MB
python       3.7.9             65d5b6c539fd   6 months ago    877MB
python       2.7               68e7be49c28c   16 months ago   902MB
```
