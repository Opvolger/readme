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

There was no package for an installation in aarch64. So I made them.
Just enable UAR in pamac-manager

You can now install libxmp-aarch64-git and openarena-git and you are done!

Look in your menu, you will find OpenArena!
