
## Minimally viable unofficial Debian packaging for the AWS SDK for C++

Taken as a complete snapshot on 2020-02-15 at sha1 dfd0b02d95 from
https://github.com/aws/aws-sdk-cpp
and _removed everything_ not need to build only 's3;core'

### Changes

No changes made other than

- downloading / copying all retained files _as is_ into `pkg/`
- addition of `pkg/debian/` directory for unofficial / informal Debian packaging
- addition of this README.md to document the changes

### Usage

Create yourself a `.orig.tar.gz` and use it with `dpkg-buildpackage` as for example via 

```sh
tar cvz --exclude=.git --exclude=debian --file aws-sdk-cpp-only-s3_1.7.275.orig.tar.gz pkg
cd pkg && dpkg-buildpackage -rfakeroot -us -uc -tc
```

which will create the `.deb` package you can install, the related
changes, dsc, ... files (which you can ignore), not sign them and run
`make clean` at the end.

### Copyright

All the actual upstream code in this repository is copyrighted by
Amazon as stated in the their repository, and licensed under Apache-2.0.

The Debian packaging is copyright Dirk Eddelbuettel and GPL'ed as usual.
