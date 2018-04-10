<p align="center">
    <a href="http://kitura.io/">
        <img src="https://raw.githubusercontent.com/IBM-Swift/Kitura/master/Sources/Kitura/resources/kitura-bird.svg?sanitize=true" height="100" alt="Kitura">
    </a>
</p>


<p align="center">
    <a href="http://www.kitura.io/">
    <img src="https://img.shields.io/badge/docs-kitura.io-1FBCE4.svg" alt="Docs">
    </a>
    <a href="https://travis-ci.org/IBM-Swift/Kitura-Compression">
    <img src="https://travis-ci.org/IBM-Swift/Kitura-Compression.svg?branch=master" alt="Build Status - Master">
    </a>
    <img src="https://img.shields.io/badge/os-macOS-green.svg?style=flat" alt="macOS">
    <img src="https://img.shields.io/badge/os-linux-green.svg?style=flat" alt="Linux">
    <img src="https://img.shields.io/badge/license-Apache2-blue.svg?style=flat" alt="Apache 2">
    <a href="http://swift-at-ibm-slack.mybluemix.net/">
    <img src="http://swift-at-ibm-slack.mybluemix.net/badge.svg" alt="Slack Status">
    </a>
</p>

# Kitura-Compression
Kitura compression middleware

## Summary
Kitura compression middleware for compressing body data sent back to the client. Supports `deflate` and `gzip` compression methods. Uses [zlib](http://zlib.net/).


## Table of Contents
* [Swift version](#swift-version)
* [API](#api)
* [License](#license)

## Swift version
The latest version of Kitura-Compression requires **Swift 4.0** or newer. You can download this version of the Swift binaries by following this [link](https://swift.org/download/). Compatibility with other Swift versions is not guaranteed.


## API
In order to use compression middleware, create an instance of `Compression`, and connect it to the desired path:

```swift
import KituraCompression

router.all(middleware: Compression())
```
You can configure `Compression` with optional arguments:
```swift
    public init (threshold: Int = 1024, chunkSize: Int = 16384, compressionLevel: CompressionLevel = CompressionLevel.defaultCompression, compressionStrategy: CompressionStrategy = CompressionStrategy.defaultStrategy, memoryLevel: Int32 = 8)
```
**Where:**
   - *threshold* is the byte threshold for the response body size before compression is considered for the response, defaults to 1024.

   - *chunkSize* is the size of internal output slab buffer in bytes, defaults to 16384

   - *compressionLevel* is the level of zlib compression to apply. The supported values are:  
   .noCompression, .bestSpeed, .bestCompression, .defaultCompression

   - *compressionStrategy* is used to tune the compression algorithm. Here are its possible values:  
   .defaultStrategy, .filtered, .huffmanOnly, .rle, .fixed
   - *memoryLevel* specifies how much memory should be allocated
   for the internal compression state. The default value is 8.

For more information on compression parameters, see  [zlib manual](http://www.zlib.net/manual.html).



## License
This library is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE.txt).
