# Kernel: debian compilation
----------------------------
To compile a kernel the debian way(does not matter if it's downloaded from
[kernel.org](https://kernel.org) or not) it's usefull to compile with the
following command line:
```shell
$ time CC=<compiler> LLVM=<bolean_attribute> make deb-pkg \
    -j$(nproc) LOCALVERSION=-<version_name> \
    KDEB_PKGVERSION=$(make kernelversion)-<package_version_number>
```
## Explanation
time
    : is a shell profiling utility on time, at the end of the compilation
    shows how long has it taken.

CC=&lt;compiler&gt;
    : sets the default compiler to compile the kernel, it is important that
    this option is set when menuconfig is made and when compiling. Not all
    versions of compilers are supported.

LLVM=&lt;bolean\_attribute&gt;
    : sets if LLVM utilities should be used in place of GNU utils.

-j$(nproc)
    : sets how many cores should be used for compilation, in conjuction with
    $(nproc) gets all the machine cores.

LOCALVERSION=-&lt;version\_name&gt;
    : sets a string to be appended to the version name. The analogous
    variable during `make menuconfig` SHOULD NOT BE USED, since it
    appends twice when `make deb-pkg` is used to compile the kernel.

KDEB\_PKGVERSION=$(make kernelversion)-&lt;package\_version\_number&gt;
    : increments the debian packaging version when debian package is generated.
