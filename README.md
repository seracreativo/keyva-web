# keyva.seracreativo.com

The Keyva website and its update feed, at keyva.seracreativo.com. Deployed by
Vercel on every push.

The disk images are **not** here: they live in the `downloads` release of this
repository. Keeping 14 MB per version in git would grow the history for good,
and a release is what GitHub means for binaries. `/download` redirects to the
current one, so the link on the page never changes.

This repository holds only what is published. It is generated from the Keyva
repository, which is private — the app signs its subscription verdict with a key
that lives in that source tree, and publishing it would give away the thing it
protects.

## What is here

    index.html          the product page
    buy/                how to get a licence
    terms/  privacy/    the legal pages the App Store listing links to
    appcast.xml         the update feed Sparkle reads
    vercel.json         /download, and the content type of the feed

**Old disk images stay in the release.** The appcast lists them, and somebody
who skipped a version updates through them. Deleting one strands whoever is
behind.

## Publishing

From the Keyva repository:

    scripts/build-direct.sh <version>     # builds, signs, notarises
    scripts/build-dmg.sh dist/direct/Keyva.app
    scripts/build-appcast.sh dist/dmg     # signs the feed

then here:

    git add -A && git commit -m "Keyva <version>" && git push
