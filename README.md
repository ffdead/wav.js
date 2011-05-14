wav.js - a javascript audiolib for reading WAVE files
======

Description
-----
wav.js is a javascript library to parse headers of WAVE files following the RIFF specification.

It also supports slicing uncompressed PCM files into smaller files - which can be handy if you don't want to load the whole file into memory to play just a small chunk.

Usage:
----

* Read format header

    var wavFile = new wave(in Blob blob);
    wavFile.onloadend = function () {
        // 'this' refers to the wav instance
        console.log(this);
    }; 

* Slice file into a smaller wav chunk

    // returns the first 30 seconds 
    wavFile.slice(0, 30, success); 

    // returns a 60 second chunk, starting 30 seconds in
    wavFile.slice(30, 60, success); 

The success callback is passed the resulting slice as an ArrayBuffer - this buffer represents a new WAVE file of the slice (with WAVE headers).

Example
-----

* Read format of file: http://jsbin.com/ffdead-audio-wav/231/

Requirements
-----
Reading binary files in Javascript requires support for the FileAPI and Typed Arrays. was.js uses File, Blob, FileReader, BlobBuilder, ArrayBuffer. 

http://dev.w3.org/2006/webapi/FileAPI/

http://www.khronos.org/registry/typedarray/specs/latest/

Limitations
-----
wav.js only supports the Canonical Wave format for now, which assumes that the sample data chunk starts directly after the file header.

http://www.lightlink.com/tjweber/StripWav/Canon.html