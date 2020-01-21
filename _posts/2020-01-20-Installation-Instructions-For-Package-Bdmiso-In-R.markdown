---
title: "Installation Instructions For Package Bdmiso In R"
layout: post
date: 2020-01-20 19:44
image: /assets/images/markdown.jpg
headerImage: false
tag:
- Package Installation
- R
- Scripting
- Bdmiso
star: true
category: blog
author: Jiarui Chi
description: Package Bdmiso is used for "Functional Dynamic Multiple-Input Single-Output Models for Neural Spikes".
---

## Installation Instructions For Package Bdmiso In R

This note **shows** how to install package [Bdmiso][1] in R settings.

---

1 MacOS

# install Xcode command-line tool
xcode-select --install

# install clang-omp (no longer available in brew, try below)

brew tap homebrew/boneyard
brew install clang-omp

# Or install llvm using brew since it now includes openmp.

brew install llvm

# edit ~/.R/Makevars and enter the following lines
cd
mkdir .R
cd .R
vi Makevars

#Choice1: if you installed clang-omp (Press i for INSERT and set correct path by yourself)
CC=/usr/local/Cellar/clang-omp/2015-04-01/bin/clang-omp
CXX=/usr/local/Cellar/clang-omp/2015-04-01/bin/clang-omp++

PKG_CFLAGS=Wall -pedantic
PKG_CFLAGS= -I/usr/local/Cellar/clang-omp/2015-04-01/libexec/include -fopenmp
PKG_CXXFLAGS= -I/usr/local/Cellar/clang-omp/2015-04-01/libexec/include  -fopenmp
PKG_LIBS= -L/usr/local/Cellar/clang-omp/2015-04-01/libexec/lib  -fopenmp

#Choice2: Or You can make a symlink if you want to use llvm
ln -s /usr/local/opt/llvm/bin/clang /usr/local/bin/clang-omp
#My makefile looks like this(find your own path)
CPP = /usr/local/opt/llvm/bin/clang
CPPFLAGS = -I/usr/local/opt/llvm/include -fopenmp
LDFLAGS = -L/usr/local/opt/llvm/lib


# Press :x to save and exit

# install the package
R CMD INSTALL bdglm_0.9.tar.gz
R CMD INSTALL bdmiso_0.9.tar.gz

2 Linux

# OpenMP should already be installed

# install the package
R CMD INSTALL bdmiso_0.9.tar.gz
	



## Headings

There are six levels of headings. They correspond with the six levels of HTML headings. You've probably noticed them already in the page. Each level down uses one more hash character. But we are using just 4 of them.

# Headings can be small

## Headings can be small

### Headings can be small

#### Headings can be small

{% highlight raw %}
# Heading
## Heading
### Heading
#### Heading
{% endhighlight %}

---

## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3

{% highlight raw %}
1. Item 1
2. A second item
3. Number 3
{% endhighlight %}
