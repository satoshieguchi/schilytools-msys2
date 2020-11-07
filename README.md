# Schily-Tools-MSYS2

This repository provides a patch to build [Schily-Tools](http://schilytools.sourceforge.net/) with [MSYS2](https://www.msys2.org/).


## Introduction

[Schily-Tools](http://schilytools.sourceforge.net/) is a collection of tools inspired by SunOS developed and maintained by [Joerg Schilling](http://cdrtools.sourceforge.net/private/).
This software package is also famous for cdrtools.
The patch file distributed via this repository allows you to build [Schily-Tools](http://schilytools.sourceforge.net/) on the [MSYS2](https://www.msys2.org/) (neither MinGW32 nor MinGW64) environment.


## Preparation

Please install the following packages in advance:

* base-devel,
* msys2-devel,
* msys2-runtime-devel.

This document also assumes that

* you are working in the home directory ($HOME) in MSYS2,
* [the tarball](https://sourceforge.net/projects/schilytools/) is saved as ~/schily-2020-11-04.tar.bz2,
* the local copy of this repository locates in ~/schilytools-msys2.


## Installation

```console
$ tar xvjf ~/schily-2020-11-04.tar.bz2
$ cd ~/schily-2020-11-04
$ patch -p1 < ~/schilytools-msys2/schily-msys2.patch
$ cd ~/schily-2020-11-04/psmake
$ ./MAKE-all
$ cd ..
$ psmake/smake
$ psmake/smake install
```

In default, the tools are installed into /opt/schily.
Please issue

```console
$ psmake/smake INS_BASE=/usr/local/schily install
```

if you want the tools to be installed in /usr/local/schily.


## Notices

This patch makes a file named os-msys_nt-10.0-19042.id in the RULES directory of [Schily-Tools](http://schilytools.sourceforge.net/) (~/schily-2020-11-04/RULES for example).
The file name comes from
```console
$ uname
MSYS_NT-10.0-19042
```
, this meaning that

* the operating system is Windows 10,
* the [MSYS2](https://www.msys2.org/) version is 19042.

You would have to rename this file according to your [MSYS2](https://www.msys2.org/) environment.
