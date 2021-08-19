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
Interestingly this image 'python:2.7' larger file than any of the Python3 images. It can take about a miute or so to download so be patient. When it finishes it will start a python session automatically so there is no further action necessary from the developer at this stage. Since we did not specify a micro version in the major.minor.micro python versioning paradign, Docker defaults to providing us with the most recent version of the image available, which happens to be 2.7.18. Taken to the extreme, this means we could simply type in 

```$ docker run -it --rm python``` This command would initiate an installation of the latest python released to the public (not as new as the rc version installed in the first command above), OR, if we already have the image, it would instantly start a Python session in that Python Version, whatever it may be. 

The downloading of the image is actually a side effect it falls back to if it fails to start the image, as seen here:

```Unable to find image 'python:2.7' locally```

Enjoy the stability and replication benefits with your specific python session now

```
2.7: Pulling from library/python
7e2b2a5af8f6: Pull complete 
...
...
acb4a89489fc: Pull complete 
Digest: sha256:cfa62318c459b1fde9e0841c619906d15ada5910d625176e24bf692cf8a2601d
Status: Downloaded newer image for python:2.7
Python 2.7.18 (default, Apr 20 2020, 19:27:10) 
[GCC 8.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```
