# docker-giscli

GIS CLI tools

The following tools are here installed:
* [LAStools](https://rapidlasso.com/lastools/)
* [PDal](https://pdal.io/)


## LAStools license

If you try to clone-n-build this image it will not work. 
The reason is because LAStools is not (yet) included in this repo, and at some point of the building -- [Dockerfile](https://github.com/chbrandt/docker-giscli/blob/11893e346dea5646491bf4f1f0b078592de24ea0/dockerfile/Dockerfile#L19) -- _LAStools_ is expected to be there.
The solution is the simplest possible, you have to download LAStools -- http://lastools.org/download/LAStools.zip -- and place it, as it is, the `.zip` file, at `~/docker-giscli/dockerfile/LAStools/LAStools.zip`.

Now you're good to go:
```bash
$ cd ~/docker-giscli/dockerfile
$ docker build -t giscli .
```

The reason for this uncomfortable situation I made you pass through is because I don't understand the license LAStools is under.
On one hand they say it is proprietary and we should pay for it, but the tools are free to download -- the ones I linked before.
Apparently, some tools are under private/payed use, while the core tools are free to use.
In any case, until it is clear to me how it works, I will kindly ask you to download and build it on your own.


/.\
