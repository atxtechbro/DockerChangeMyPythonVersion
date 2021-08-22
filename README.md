# $ docker run -it python:3.2.1
## How to use Docker to install and run any Python version including Python 2 up to the newest Release Candidate (RC)
### Motivation
Let's imagine the problem facing a developer needing to use Python 3.7.9 in order to replicate a clients' environment, or a student needing to utilize Python 2.7.18 to complete an assignment. These are just two of many scenarios in which 'downgrading' is something the developer wants to do, albeit temporarily.

There are many ways to do this, all of which entail additional implementations decisions the developer must confront. For example, before Docker you had to change the PYTHONPATH, and manually download either a Gzipped source tarball or XZ compressed source tarball from python.org. Then the next thing you know, valuable time is wasted Googling which tarball to use instead of time spent developing. According to the Zen of Python, There should be one— and preferably only one —obvious way to do it.

In the spirit of this sentiment, the Docker way will demonstrate the simplest and least costly solution to the version-change problem. It makes it easy to switch from one version to another, and then easily revert back. The developer does not need to worry about the way it is orchestrated behind the scenes. Essentially, what is happening is Docker is allowing the developer to invoke an isolated image containing a specific version of Python, and that image is quarantined from the rest of their operating system. Indeed, this is the exact problem Docker is made for. However, the subject of containerization and even the installation of Docker are outside the scope of this simple demonstration.  Before proceeding further, please understand that it is assumed you should have a Linux operating system with Docker installed already at this point.

```$ docker run -it python:<major>.<minor>.<micro>*```

Docker will start a Python session in the specified version immediately, but if we don't have it, Docker will recognize this and download the image for us which could take about a minute.


If either *major*, *minor*, or *micro* is not specified, Docker will default to downloading the most recent version available within the boundaries the developer has specified. To get the newest version of python type *python* without the colon


```$ docker run -it python:3.7.9```


```
Python 3.7.9 (default, Feb  9 2021, 08:33:04) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
```


Perfect. I had that installed already and it was trivially easy. What if I need to go all the way back to Python 2.7 but I have never downloaded Python 2 because I learned Python after Python 3 came out?


```$ docker run -it python:2.7.18```

Unable to find image 'python:2.7.18' locally
2.7.18: Pulling from library/python
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
Status: Downloaded newer image for python:2.7.18
Python 2.7.18 (default, Apr 20 2020, 19:27:10) 
[GCC 8.3.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.



Let's imagine a developer just finished reading PEP 618 -- Add Optional Length-Checking To zip

Wouldn't it be nice to be able to switch back and forth with ease so we can better understand the proposed change? Reading the PEP in it's entirety is great if you're up for it, but running the code in a quick python:rc session and then seeing how it behaves differently is really a cool thing to experience. 

```
docker run -it python:rc
Python 3.10.0rc1 (default, Aug  3 2021, 19:28:36) [GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.

>>> zipper = zip(['with', 'we', 'version'], ['docker', 'redefine', 'control', 'a straggler appeared'], strict = False)
>>> list(zipper)
```


```[('with', 'docker'), ('we', 'redefine'), ('version', 'control')]```


```
>>> zipper = zip(['with', 'we', 'version'], ['docker', 'redefine', 'control', 'a straggler appeared'], strict = True)
>>> list(zipper)
```


```ValueError: zip() argument 2 is longer than argument 1```

Enjoy the stability of replicating a perfect copy of a previous version of Python, or even try out the newest Release Candidate (RC) before it is released to the general public. Creating an isolated image separate from the rest of your operating system is the exact type of problem Docker is good at solving, as well as the most secure and low risk.

You can use Docker & Python release switching as a time machine to the future and past
