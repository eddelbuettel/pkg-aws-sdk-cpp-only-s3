
## build in Docker:

cmake .. -DBUILD_SHARED_LIBS=OFF  -DCMAKE_MODULE_PATH=/usr/lib/x86_64-linux-gnu/cmake:/usr/lib/x86_64-linux-gnu/aws-c-common/cmake -DBUILD_DEPS=OFF -DBUILD_ONLY="s3;core;identity-management;sts"

## build via pdebuild

- uses /var/cache/pbuilder/local-deps
- needs five last lines in /etc/pbuilderrc uncommented to use 'hooks'
- in particular /etc/pbuilder/hooks/D05local-deps which updates the packages list

## detection of root directory

- using `export AWSSDK_ROOT_DIR="/usr"` works sometimes
- possibly more effective to patch cmake file in package
  installed path:  /usr/lib/x86_64-linux-gnu/cmake/AWSSDK/AWSSDKConfig.cmake
  line 65:  set(AWSSDK_ROOT_DIR "/usr")
