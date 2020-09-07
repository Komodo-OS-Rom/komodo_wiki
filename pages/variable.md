---
title: Variable on source Komodo OS
permalink: help/variable/
---

## Introduction

These are the `variables` in the Komodo source that should be in your tree

## For Gapps

```
CURRENT_BUILD_TYPE := <value>
```
This variable is for builds with `GAPPS`, `no-GAPPS`, and `MicroG`

### With Gapps

Build with gapps you can fill in the `value` with `gapps`

```
CURRENT_BUILD_TYPE := gapps
```

### With no Gapps

Build without gapps you can fill in the `value` with `nogapps`

```
CURRENT_BUILD_TYPE := nogapps
```

### With MicroG

Build With MicroG you can fill in the `value` with `microg`

```
CURRENT_BUILD_TYPE := microg
```