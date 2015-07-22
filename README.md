wav.js - a javascript audiolib for reading WAVE files
======

Description
-----
wav.js is a javascript library to parse headers of WAVE files following the RIFF specification.

It also supports slicing uncompressed PCM files into smaller files - which can be handy if you don't want to load the whole file into memory to play just a small chunk.

Usage
----

Read format header:

    var wavFile = new wav(in Blob blob);
    wavFile.onloadend = function () {
        // 'this' refers to the wav instance
        console.log(this);
    }; 

Slice file into a smaller wav chunk:

    // slice out the first 30 seconds 
    wavFile.slice(0, 30, success); 

    // slice out a 60 second chunk, starting 30 seconds in
    wavFile.slice(30, 60, success); 

The success callback is passed the resulting slice as an ArrayBuffer - this buffer represents a new WAVE file of the slice (with WAVE headers).

Read samples from a wav file:

    var fileInput = document.getElementById('fileInput');
    var file = fileInput.files[0];
    var wavFile = new wav(file);
    
    wavFile.onloadend = function () {
        //Print out all the samples
        console.log(wavFile.dataSamples);
    };


Example
-----

* Read format of file: http://jsbin.com/ffdead-audio-wav/241
* Slice file into smaller wavs: http://jsbin.com/ffdead-audio-wav-slice/233

Requirements
-----
Reading binary files in Javascript requires support for the FileAPI and Typed Arrays. was.js uses File, Blob, FileReader, ArrayBuffer. 

http://dev.w3.org/2006/webapi/FileAPI/

http://www.khronos.org/registry/typedarray/specs/latest/

Limitations
-----
wav.js only supports the Canonical Wave format for now, which assumes that the sample data chunk starts directly after the file header.

http://www.lightlink.com/tjweber/StripWav/Canon.html
