wav.js
======

Description
-----
wav.js is a javascript library to parse headers of RIFF/WAVE files 

It also supports slicing uncompressed PCM files into smaller files.

Usage:
----

    var wavFile = new wave(in Blob blob);
    wavFile.onloadend = function () {
        // 'this' refers to the wav instance
        console.log(this);
    }; 

Example
-----

* Show wav format: http://jsbin.com/ffdead-audio-wav/231/

