# Games compiles on the Pinebook Pro

## IOQuake3

Edit the PKGBUILD file before building ioquake3-git

add aarch64 to arch:

`arch=('i686' 'x86_64' 'aarch64' )`

build de AUR package.

Why? no idea, but ioquake3 has no execute-rights, add them:

sudo chmod +x /opt/quake3/ioquake3

To play Q3 with the Retail Version:
  Move the pak0.pk3 file from the original game CD to:
     /opt/quake3/baseq3/

To play Q3 with the Demo Version:
  Move the demoq3/pak0.pk3 from the demo installer to:
     /opt/quake3/demoq3/

When you have the .pk3 file(s) installed, run the game:
     quake3

Or for the Demo Version:
    quake3 +set fs_game demoq3

or all pak0 till pak8 in
~/.q3a/baseq3/

for a valid cd-key google 22222222222 it :) (I have the pak0 from steam, no-cd-key)

## YQuake2

Copy your quake2 (old windows-files) files to ~/.yq2/

```bash
git clone git@github.com:yquake2/yquake2.git
cd yquake2
make
cd release
./quake2
```

## Xonotic

This was very simple, use link from xonotic [link](https://gitlab.com/xonotic/xonotic/-/wikis/Git)

Xonotic only used 1 core (not multi). So i only got 30 FPS and 1 core with 100% CPU load

```bash
git clone https://gitlab.com/xonotic/xonotic.git
cd xonotic
 ./all update -l best
 # -r == release nog debug, debug == slow
 ./all compile -r
 # start the game
 ./all run
```

## OpenArena

There was no package for an installation in aarch64. So I made them.
Just enable UAR in pamac-manager

You can now install libxmp-aarch64-git and openarena-git and you are done!

Look in your menu, you will find OpenArena!

## HalfLife (1)

I tried multiple ways, but this was the most stable.

A tip, do not use the flashlight. (buggie)

You can put the "code-block" below in a file, e.g. create_hl.sh

It will give you halflife (xash3d) in the dir ~/hl you can then start halflife with "xash3d.sh"

I've had 3 crashes before "the explosion" happened. So be warned

```bash
mkdir ~/hl

#COPY your "valve" folder from (windows or linux system steam/cd install) to ~/hl/valve
#on steam it is $HOME/.steam/steam/steamapps/common/Half-Life/

# create re-writen hl-engine.
git clone --recursive https://github.com/FWGS/xash3d-fwgs.git
cd xash3d-fwgs
git checkout tags/v0.20
git submodule update

./waf configure -T release --prefix ~/out
./waf build
./waf install

cd ..

cp ~/out/lib/xash3d/* ~/hl/

# create hl-sdk (improved).
git clone https://github.com/FWGS/hlsdk-xash3d.git
cd hlsdk-xash3d
./waf configure -T release
./waf build

cp build/cl_dll/*.so ~/hl/valve/cl_dlls
cp build/dlls/*.so ~/hl/valve/dlls

cd ~/hl

# get a startup script from a older re-writen engine. (stil works)
wget https://raw.githubusercontent.com/FWGS/xash3d/master/scripts/xash3d.sh

# make it executable.
chmod +x xash3d.sh
```
