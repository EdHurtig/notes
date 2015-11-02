# APT

_A package manager_

## First things first

Always update with apt.  Updating pulls down the most recent list of packages.
If you don't do this every so often you will have a bad time. 

**Always update when you bring up a new box**

```bash
sudo apt-get update -y
```

## Find a package

To find a package by a keyword... like php

```bash
apt-cache search php
```

List currently installed packaged

```bash
sudo apt-get list
```

## Install

To install a package

```bash
sudo apt-get install php5-fpm
```

tag on a `-y` to make your life better

```bash
sudo apt-get install -y php5-fpm other-package another-package
```

## Removing packages

There are two commands `remove` and `purge`... `purge` _should_ remove everything including configs and data files

```bash
sudo apt-get remove php5-fpm
```
or
```bash
sudo apt-get purge php5-fpm
```
