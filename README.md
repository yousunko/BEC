# BEC analysis

Bit-level Error Coalescing (BEC) analysis is a static analysis that
tracks and classifies the effect of the program corruption due to soft errors.

This repository contains an LLVM implementation of BEC and its application
to the LLVM instruction scheduler.


# Contacts

* Yousun Ko <yousun.ko@yonsei.ac.kr>
* Bernd Burgstaller <bburg@yonsei.ac.kr>

# How to apply patches to LLVM

The implementation is based on LLVM 16.0.0. Clone the LLVM of the right version. 

```
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
git checkout tags/llvmorg-16.0.0
```

Apply patches on top of the repository by using ``git apply``.
For example, the command below applies the first patch on to the repository.

```
git apply 0001-BEC-Generate-auxiliary-register-infor-in-assembly.patch
```


Apply patches up to ``0005-BEC-RISCV-Add-post-ra-Fault-Index-Coalescer-for-RISC.patch`` to obtain the BEC analysis implementation for RISC-V without affecting the instruction scheduler.

The patch ``0006-BEC-RISCV-Add-reliability-aware-post-ra-instruction-.patch`` enables the vulnerability-aware instruction scheduler to minimize the susceptibility to soft errors based on the BEC analysis.

Apply the patch ``0007-BEC-RISCV-Activate-the-worst-reliability-aware-post-.patch`` on top of all the other patches to enables the vulnerability-aware instruction scheduler, but to **maximize** the susceptibility to soft errors.

Find the [Getting Started with the LLVM System](https://llvm.org/docs/GettingStarted.html) page for further information on how to build and install LLVM from source codes.
