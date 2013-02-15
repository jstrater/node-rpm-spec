node rpm specfile
=================
Node.js does not come with RPMs for CentOS 5. Here are instructions to build node rpms from source.

*This branch (python26) is meant for systems like CentOS 5 that have an old version of python installed and need to use the python26 package to build the node RPM.*

Steps to build
--------------------------------------------------------
1. sudo yum groupinstall 'Development Tools'
2. sudo yum install openssl-devel python26
3. mkdir -p ~/rpmbuild/BUILD ~/rpmbuild/RPMS ~/rpmbuild/RPMS/i386 ~/rpmbuild/RPMS/noarch ~/rpmbuild/RPMS/x86_64 ~/rpmbuild/RPMS/ ~/rpmbuild/SOURCES ~/rpmbuild/SPECS ~/rpmbuild/SRPMS
4. echo '%_topdir %(echo $HOME)/rpmbuild' >> ~/.rpmmacros
5. wget -P ~/rpmbuild/SOURCES http://nodejs.org/dist/v0.8.20/node-v0.8.20.tar.gz
6. wget -P ~/rpmbuild/SPECS https://github.com/jstrater/node-rpm-spec/raw/python26/nodejs.spec
7. rpmbuild -ba ~/rpmbuild/SPECS/nodejs.spec
8. rm ~/.rpmmacros
