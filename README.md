# node-vtt-to-srt

Convert [WebVTT](http://dev.w3.org/html5/webvtt/) (The Web Video Text Tracks Format, aka html5 video subtitles) into SubRip SRT.


## Setting up

```bash
npm install node-vtt-to-srtt
# or set it up globally
npm install node-vtt-to-srt --global
```

## Command line

You may use it from the terminal if vtt-to-str was installed globally

```bash
node-vtt-to-srt example.vtt example.srt
cat example.vtt | vtt-to-srt > example.str
node-vtt-to-srt example.str < example.vtt
```

## Usage

If converting from a text file:

``` js
import fs from 'fs';
import vtt2srt from 'node-vtt-to-srt';

fs.createReadStream(__dirname + '/subtitles.vtt')
  .pipe(vtt2srt())
  .pipe(fs.createWriteStream(__dirname + '/subtitles.srt'));

```

If converting from an string:

``` js
import fs from 'fs';
import vtt2srt from 'node-vtt-to-srt';

const vttString = 'WEBVTT FILE\r\n1\r\n00:00:01.000 --> 00:00:02.000\r\nthis is WebVTT';

const srtStream = vtt2srt();

srtStream.write(vttString);
srtStream.end();
srtStream.pipe(fs.createWriteStream(__dirname + '/subtitles.srt'));

```

If converting to an string:

``` js
import fs from 'fs';
import vtt2srt from 'node-vtt-to-srt';

const vttString = 'WEBVTT FILE\r\n1\r\n00:00:01.000 --> 00:00:02.000\r\nthis is WebVTT';

const srtStream = vtt2srt();

srtStream.write(vttString);
srtStream.end(() => console.log(srtStream.read().toString('utf-8'));

```

Note: these examples are available in the `examples` folder. Run them with `babel-node` 
 
## Test

```
npm run test
```