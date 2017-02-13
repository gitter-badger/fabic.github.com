---
layout: post
title: "Draft - Linux syscalls"
tagline: "Supporting tagline"
category : notes
tags : [draft, Linux, syscalls]
---

## TL;DR

Yeah...


## Links

* <https://filippo.io/linux-syscall-table/>
* <http://syscalls.kernelgrok.com/>
* <http://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/> (2012)
* <http://www.digilife.be/quickreferences/qrc/linux%20system%20call%20quick%20reference.pdf> (Jialong He)
* <https://blog.packagecloud.io/eng/2016/04/05/the-definitive-guide-to-linux-system-calls/> (2016, article)
* <http://cs.lmu.edu/~ray/notes/linuxsyscalls/>


## Memory allocation

* <https://en.wikipedia.org/wiki/C_dynamic_memory_allocation>
* <https://en.wikipedia.org/wiki/Sbrk>
* <https://en.wikipedia.org/wiki/Mmap>
* <http://stackoverflow.com/a/3479496/643087> & <http://stackoverflow.com/a/3479570/643087>


### Implementations

* Heap-based ;
* [Doug Lea's __dlmalloc__](http://g.oswego.edu/dl/html/malloc.html)
  ([__malloc.c__](ftp://g.oswego.edu/pub/misc/malloc.c)) ;
  [Musl-libc's impl.](http://git.musl-libc.org/cgit/musl/tree/src/malloc)
* Musl-libc also has a `static void *__simple_malloc(size_t n)` ([lite_malloc.c](http://git.musl-libc.org/cgit/musl/tree/src/malloc/lite_malloc.c)), most probably used internally.
* Glibc's ptmalloc (variant of dlmalloc).
* phkmalloc, jemalloc
* __tcmalloc :__ “Thread-caching malloc” [github.com/gperftools/gperftools](https://github.com/gperftools/gperftools)
* [Hoard's malloc](https://en.wikipedia.org/wiki/Hoard_memory_allocator)
  ([official web site](http://www.hoard.org/about/), [emeryberger.github.io/Hoard/](http://emeryberger.github.io/Hoard/)).
* [OpenSIPS has 2/3 (maybe 4 ?) custom implementation for fast memory allocation](https://github.com/OpenSIPS/opensips/tree/master/mem)

__Note:__ Mac OS X do not support `brk()` since it is based on FreeBSD.


__EOF__