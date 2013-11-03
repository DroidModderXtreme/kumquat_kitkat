android_device_sony_kumquat-4.4
=============================

Unoficial aosp-4.4 for Sony Xperia U

Unoficial Android 4.4 (KitKat) for Sony Xperia U

Getting Started :

    curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > /root/bin/repo
    chmod 755 /root/bin/repo
    mkdir android4.4
    cd android4.4
    repo init -u www.github.com/XperiaNovathor/manifest.git -b kitkat
    repo sync
    cd device
    mkdir sony
    cd sony
    git clone https://github.com/XperiaNovathor/android_device_sony_kumquat -b kitkat
    cd kumquat

Now connect your phone which have runing FXP CM10 :

    ./extract-files.sh
    cd ../../..
    cd hardware
    git clone https://github.com/kumquat/hardware_semc.git -b master semc
    cd ..

Patch android source code :

    patch -p1 < device/sony/kumquat/patches/framework_av.patch
    patch -p1 < device/sony/kumquat/patches/framework_native.patch
    patch -p1 < device/sony/kumquat/patches/framework_base.patch
    patch -p1 < device/sony/kumquat/patches/hardware_libhardware.patch
    patch -p1 < device/sony/kumquat/patches/hardware_libhardware_legacy.patch
    patch -p1 < device/sony/kumquat/patches/system_core.patch
    patch -p1 < device/sony/kumquat/patches/system_netd.patch
    patch -p1 < device/sony/kumquat/patches/frameworks_opt_telephony.patch
    patch -p1 < device/sony/kumquat/patches/build.patch

Our step is optional!!! Use only if you going to sync AOSP source code daily, than simple revert each patch before you sync AOSP source code :

    patch -p1 -R < device/sony/kumquat/patches/framework_av.patch
    patch -p1 -R < device/sony/kumquat/patches/framework_native.patch
    patch -p1 -R < device/sony/kumquat/patches/framework_base.patch
    patch -p1 -R < device/sony/kumquat/patches/hardware_libhardware.patch
    patch -p1 -R < device/sony/kumquat/patches/hardware_libhardware_legacy.patch
    patch -p1 -R < device/sony/kumquat/patches/system_core.patch
    patch -p1 -R < device/sony/kumquat/patches/system_netd.patch
    patch -p1 -R < device/sony/kumquat/patches/frameworks_opt_telephony.patch
    patch -p1 -R < device/sony/kumquat/patches/build.patch
    repo forall -p -c 'git checkout -f'
    repo sync
    patch -p1 < device/sony/kumquat/patches/framework_av.patch
    patch -p1 < device/sony/kumquat/patches/framework_native.patch
    patch -p1 < device/sony/kumquat/patches/framework_base.patch
    patch -p1 < device/sony/kumquat/patches/hardware_libhardware.patch
    patch -p1 < device/sony/kumquat/patches/hardware_libhardware_legacy.patch
    patch -p1 < device/sony/kumquat/patches/system_core.patch
    patch -p1 < device/sony/kumquat/patches/system_netd.patch
    patch -p1 < device/sony/kumquat/patches/frameworks_opt_telephony.patch
    patch -p1 < device/sony/kumquat/patches/build.patch

You are ready to build :

    . build/envsetup.sh
    lunch aosp_kumquat-userdebug (eng)
    make otapackage

ENJOY!
