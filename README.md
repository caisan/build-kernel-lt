# build-kernel-lt
build kernel-lt like elrepo(http://elrepo.org/)

## How building kernel-lt(long term support) link elrepo
In following steps, i will show you how to build kernel-lt rpm packages and source rpm package(ie, src.rpm).
For example, i would link to build a kernel-lt rpm packages and src.rpm for CentOS 8
```
wget https://mirrors.tuna.tsinghua.edu.cn/elrepo/kernel/el8/SRPMS/kernel-lt-5.4.139-1.el8.elrepo.nosrc.rpm
```
```
rpm -ivh kernel-lt-5.4.139-1.el8.elrepo.nosrc.rpm
```
```
# cd ~/rpmbuild/SOURCES/
# ls
config-5.4.139-x86_64  cpupower.config  cpupower.service  filter-modules.sh  filter-x86_64.sh  generate_bls_conf.sh  mod-extra-blacklist.sh  mod-extra.list  mod-extra.sh
```
```
wget https://mirrors.tuna.tsinghua.edu.cn/kernel/v5.x/linux-5.4.139.tar.xz
```
```
cd ../SPECS
```
```
rpmbuild -ba kernel-lt-5.4.spec
```
building time depends on your hardware performence, the final package is located in `/root/rpmbuild/RPMS/x86_64/`.
Those built packages just like https://mirrors.tuna.tsinghua.edu.cn/elrepo/kernel/el8/x86_64/RPMS/, but you can build your own kernel-lt package which meets your requirements.

## NOTE
if you run `rpmbuild -bs kernel-lt-5.4.spec` without modifying the kernel-lt-5.4.spec,
you will get the `nosrc.rpm` in the `/root/rpmbuild/SRPMS`.

if you want get real soruce rpm, like `kernel-lt-5.4.139-1.el8.src.rpm` in `/root/rpmbuild/SRPMS`, try modify `kernel-lt-5.4.spec` just by deleting the line: `NoSource: 0` in the original `kernel-lt-5.4.spec`, save it and re-run:
`rpmbuild -bs kernel-lt-5.4.spec`, then you will find source rpm: `/root/rpmbuild/SRPMS/kernel-lt-5.4.139-1.el8.src.rpm` 



