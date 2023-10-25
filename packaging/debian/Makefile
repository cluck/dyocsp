DYOCSP_DEBPKGVER := $(shell awk -F': ' '/^Version: / {print $$2}' dyocsp/DEBIAN/control)
DEB_TARGET_ARCH  := $(shell dpkg-architecture -qDEB_TARGET_ARCH)

all:
	mkdir -p dyocsp/usr/bin
	go build -o dyocsp/usr/bin/dyocspd -ldflags="-s -w" ../../cmd/dyocsp
	dpkg-deb --root-owner-group --build dyocsp dyocsp-$(DYOCSP_DEBPKGVER)_$(DEB_TARGET_ARCH).deb

