# Supported audio formats

{{ speechkit-name }} enables you to recognize and synthesize the following audio formats:
* LPCM
* OggOpus
* MP3

#### LPCM {#lpcm}

[Linear pulse-code modulation](https://en.wikipedia.org/wiki/Pulse-code_modulation) without a WAV header.

Audio features in this format:

* Sampling frequency:

   | API version | Acceptable values |
   | --- | --- |
   | [Speech synthesis API v1](tts/index.md) | 8, 16, or 48 kHz |
   | [Speech synthesis API v3](tts-v3/api-ref/grpc/index.md) | Any value between 8 and 48 kHz |
   | [Speech recognition API v2](stt/index.md) | 8, 16, or 48 kHz |
   | [Speech recognition API v3](stt-v3/api-ref/grpc/index.md) | Any value between 8 and 48 kHz |

* Bit depth: 16-bit.
* Byte order: Reversed (little-endian).
* Audio data is stored as signed integers.

#### OggOpus {#OggOpus}

[OggOpus](https://wiki.xiph.org/OggOpus): Data is encoded using the OPUS audio codec and compressed using the OGG container format.

{{ speechkit-short-name }} recognizes and synthesizes OggOpus without audio file quality and header restrictions.

#### MP3 {#MP3}

[MP3](https://en.wikipedia.org/wiki/MP3): Data is encoded using the MPEG-1/2/2.5 Layer III audio codec and packaged in an MP3 container.

{{ speechkit-short-name }} recognizes MP3 without audio file quality and header restrictions.


{% note warning %}

MP3 format is not supported by API v2 recognition in [streaming](./stt/api/streaming-api.md) or [synchronous](./stt/api/request-api.md) modes.

{% endnote %}
