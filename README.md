<div align="center">
  <a href="https://elementary.io" align="center">
    <center align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/elementary/brand/main/logomark-white.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/elementary/brand/main/logomark-black.png">
  <img src="https://raw.githubusercontent.com/elementary/brand/main/logomark-black.png" alt="elementary" align="center" height="200">
</picture>
    </center>
  </a>
  <br>
  <h1 align="center"><center>elementary OS</center></h1>
  <h3 align="center"><center>Build scripts for image creation</center></h3>
  <br>
  <br>
</div>

---

## Building Locally

This fork adds the [T2 Linux kernel](https://github.com/t2linux/T2-Debian-and-Ubuntu-Kernel) build for Debian/Ubuntu.

Choose your build file:

`etc/terraform-amd64-t2.conf`
`etc/terraform-amd64-t2-lts.conf`
`etc/terraform-amd64-t2-xanmod.conf`
`etc/terraform-amd64-t2-xanmod-lts.conf`

The pass it to build:

```sh
docker run --rm --privileged -it \
  -e DEBIAN_FRONTEND=noninteractive \
  -v "$PWD":/working_dir \
  -w /working_dir \
  --tmpfs /run:exec,nosuid,size=512m \
  --tmpfs /tmp:exec,nosuid,size=1g \
  debian:latest \
  ./build.sh etc/terraform-amd64-t2.conf
```

Find the build iso int the `builds` directory.

NOTE: There are issue building from macos better use a virtual machine or native Debian install.

## Further Information

More information about the concepts behind `live-build` and the technical decisions made to arrive at this set of tools to build an .iso can be found [on the wiki](https://github.com/elementary/os/wiki/Building-iso-Images).
