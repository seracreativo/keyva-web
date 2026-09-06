# keyva.seracreativo.com

The Keyva website, its downloads and its update feed. Served by GitHub Pages.

This repository holds only what is published. It is generated from the Keyva
repository, which is private — the app signs its subscription verdict with a key
that lives in that source tree, and publishing it would give away the thing it
protects.

## What is here

    index.html          the product page
    buy/                how to get a licence
    terms/  privacy/    the legal pages the App Store listing links to
    appcast.xml         the update feed Sparkle reads
    Keyva-<version>.dmg every released build

**Old disk images stay.** The appcast lists them, and somebody who skipped a
version updates through them. Deleting one strands whoever is behind.

## Publishing

From the Keyva repository:

    scripts/build-direct.sh <version>     # builds, signs, notarises
    scripts/build-dmg.sh dist/direct/Keyva.app
    scripts/build-appcast.sh dist/sitio   # signs the feed

then here:

    git add -A && git commit -m "Keyva <version>" && git push
