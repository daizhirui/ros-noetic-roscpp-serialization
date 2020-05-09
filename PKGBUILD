pkgdesc="ROS - roscpp_serialization contains the code for serialization as described in MessagesSerializationAndAdaptingTypes."
url='https://wiki.ros.org/roscpp_serialization'

pkgname='ros-noetic-roscpp-serialization'
pkgver='0.7.1'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-noetic-roscpp-traits
	ros-noetic-cpp-common
	ros-noetic-rostime
	ros-noetic-catkin
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
)

ros_depends=(
	ros-noetic-roscpp-traits
	ros-noetic-cpp-common
	ros-noetic-rostime
)

depends=(
	${ros_depends[@]}
)

_dir="roscpp_core-${pkgver}/roscpp_serialization"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/roscpp_core/archive/${pkgver}.tar.gz")
sha256sums=('8fddbafd3fc76470e4a706f7923b7a03f914943d7edb0b70273d8b98e003b108')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCMAKE_BUILD_TYPE=Release \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python3 \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
