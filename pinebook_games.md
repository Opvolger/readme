# Games compiles on the Pinebook Pro

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

Download the zip-file (full version 0.8.8) [download](http://www.openarena.ws/download.php?list.61)

unzip it.

### compile libxmp

We need libxmp, so compile/make it.

[github libxmp](https://github.com/cmatsuoka/libxmp)

```bash
git clone git@github.com:cmatsuoka/libxmp.git
cd libxmp
autoconf
# we use not the default (old) prefix, not working in manjaro
./configure --prefix=/usr
make
sudo make install
```

### compile openarena

We need to add aarch64 as a platform, I have made a pull request for that: [github pull-request](https://github.com/OpenArena/engine/pull/64).
If my pull-request is not yet accepted, you will have to add 2 line (see pull-request).

```bash
git clone git@github.com:OpenArena/engine.git
cd engine
make
```

The release (compiled-files) will by in `build/release-linux-aarch64/` copy oa_ded.aarch64 and openarena.aarch64 to the unzipped folder. Now you can play OpenArena!
