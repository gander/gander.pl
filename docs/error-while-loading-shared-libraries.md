---
title: 'Ubuntu: error while loading shared libraries'
tags: [ubuntu, linux, error, shared, libraries]
---
# {{ $frontmatter.title }}

1.  Run `ldd <executable>` to find missing libraries.
2.  Run `dpkg -S <missing lib>` to find packages, containing them.
3.  Install missing libs. Sometimes use `:i386` instead `:amd64`.
