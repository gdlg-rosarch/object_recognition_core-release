# Script generated with Bloom
pkgdesc="ROS - object_recognition_core contains tools to launch several recognition pipelines, train objects, store models ..."
url='http://wg-perception.github.io/object_recognition_core/'

pkgname='ros-kinetic-object-recognition-core'
pkgver='0.6.7_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('boost'
'curl'
'ros-kinetic-catkin'
'ros-kinetic-cmake-modules'
'ros-kinetic-ecto'
'ros-kinetic-ecto-image-pipeline'
'ros-kinetic-sensor-msgs'
'ros-kinetic-visualization-msgs'
)

depends=('boost'
'couchdb'
'curl'
'ros-kinetic-ecto'
'ros-kinetic-ecto-image-pipeline'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=object_recognition_core
source=()
md5sums=()

prepare() {
    cp -R $startdir/object_recognition_core $srcdir/object_recognition_core
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

