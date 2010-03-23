CodaClips
=========

A simple import/export script for syncing Coda clips.


WARNING
-------

This script fiddles with undocumented preference settings. It relies on
the current Coda clip implementation staying (relatively) the same. In other
words, Panic could change things and break this script at any time.

If things do change in a future version of Coda, nothing should go seriously
wrong, other than this script (possibly) not working anymore. Also, things
might get a little strange if you're syncing between two different Coda
versions.

**Consider yourself warned.**


Requirements
------------

This script assumes that you have a (free!) Dropbox account. If you don't have
one, feel free to [use my referral code][1] and get a little extra space while
you're at it.

  [1]: https://www.dropbox.com/referrals/NTQzOTE3NDk


Usage
-----

0.  Install this script. Copy it somewhere like `/usr/local/bin` or `$HOME/bin`.
    Now `chmod a+x codaclips` to make it executable.

1.  Quit Coda. Yeah, really. Coda can't deal with preferences changing while the
    app is running, so you've gotta quit before you sync.

3.  Export your current clips:
   
        `codaclips export`
   
    Optionally, give it a filename or path for export. By default it imports and
    exports your clips using a hidden file in your Dropbox. This is prob'ly what
    you want to do...

4.  Wait for Dropbox to sync the file. Follow steps 0 and 1 on your second
    computer then import your Coda clips:
   
        `codaclips import`
   
    Note: This step **erases all existing clips on your second computer.** If you
    want to save them first, open the clip panel, right click on each group, and 
    select "Export Group". You can now re-import these clips after your initial sync.

5.  Make sure to keep changes synced. When you exit Coda on either computer, run
    `codaclips export`. This will save your current clips to the Dropbox file. When
    you get back to your other computer, run `codaclips import` before starting
    Coda again.

6.  Extra credit: You could set up a folder action to run `codaclips export` any
    time `~/Library/Preferences/com.panic.Coda.plist` changes... That would take
    away half of the manualness of this process :-)


Tips
----

 *  **Try to only change clips on one machine at a time.** If you create a clip
    on `machine A`, then create a clip on `machine B` before you sync the new
    clip from `machine A`, your new clips are going to conflict. This means a
    manual merge, and it's a bit annoying.