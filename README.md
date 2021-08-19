#DockerRunPython-x.y.z
##How to use Docker to install and run any Python version including Python 2 up to the newest Release Candidate (RC)

If we do not have a python image installed on Docker we can do so very easily without risking other techniques like manipulating the system $PATH which can have unintended side effects down the road. In comparison, using Docker to switch between versions of Python is easy as it should be in Python, and in my opinion is the obvious way to do it. This method involves a simple one-line terminal command. D

```$ docker run -it --rm python*:<major>.<minor>.<micro>*```

Docker will start a Python session in the specified version immediately, but if we don't have it, Docker will recognize this and download the image for us which could take about a minute.

Let's say I want to code in Python 3.7.9 because a coding challenge issued by a prospective employer contained documentation instructions specified as being current as of Python 3.7.9 - in this case 'downgrading' is something I actually want to do, albeit temporarily, and I will do this by simply typing in - >

```$ docker run -it --rm python:2.7.9```

```
Python 3.7.9 (default, Feb  9 2021, 08:33:04) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
```

Perfect. I had that installed already and it was trivially easy. What if I need to go all the way back to Python 2.7 but I have never downloaded Python 2 because I learned Python after Python 3 came out?


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
Since we did not specify a micro version in the major.minor.micro python versioning paradigm introduced in PEP 440, Docker defaults to providing us with the most recent version of the image available, which happens to be 2.7.18


Enjoy the stability of replicating a perfect copy of a previous version of Python, or even try out the newest Release Candidate (RC) before it is released to the general public. Creating an isolated image separate from the rest of your operating system is the exact type of problem Docker is good at solving, as well as the most secure and low risk.

Your downloaded image is installed and you are now in a Python 2 time machine!

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
