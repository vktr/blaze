# Blaze

Are you running ElasticSearch? Want to take your data and get the heck outta
Dodge? **Blaze** provides everything you need in a neat, blazing fast package!

| **Linux / OSX** |
| --------------- |
| [![Build Status](https://travis-ci.org/vktr/blaze.svg?branch=master)](https://travis-ci.org/vktr/blaze) |


## Features

 - Uses the [ElasticSearch sliced scroll API](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-request-scroll.html) to get your data hella fast.
 - Written in modern C++ using [libcurl](https://github.com/curl/curl) and [RapidJSON](https://github.com/Tencent/RapidJSON).
 - Distributed as a single, tiny binary.


## Usage

Get the binary for your platform from the Releases page or compile it yourself. If you use it often it might make sense to put it in your `PATH` somewhere.

```sh
$ blaze --host=http://localhost:9200 --index=humongous_data_1
```

This will connect to ElasticSearch on the specified host and start downloading the `humongous_data_1` index to your local machine. The output will be split into a number of files depending on the number of slices (default: 5).


### Command line options

 - `--host` - the host where ElasticSearch is running.
 - `--index` - the index to dump.
 - `--slices` - the number of slices to split the scroll. Should be set to the number of shards for the index (as seen on `/_cat/indices`). Defaults to *5*.
 - `--size` - the size of the response (i.e, length of the `hits` array). Defaults to *5000*.


## Building

Building Blaze is easy.

### On Linux (and OSX)

```sh
$ make
```


## License

Copyright © Viktor Elofsson and contributors.

Blaze is provided as-is under the MIT license. For more information see [LICENSE](https://github.com/vktr/blaze/blob/master/LICENSE).

 - For libcurl, see https://curl.haxx.se/docs/copyright.html 
 - For RapidJSON, see https://github.com/Tencent/rapidjson/blob/master/license.txt
