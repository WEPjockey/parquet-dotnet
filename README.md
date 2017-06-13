# parquet-dotnet

A .NET library to read and write [Apache Parquet](https://github.com/Parquet) files.

## Why

Parquet library is mostly available for Java, C++ and Python, which somewhat limits .NET/C# platform in big data applications. Whereas C# is a great language we still don't have anything good in this area.

This project is aimed to fix this problem.

## Roadmap

We have just started to work on this library, contributors are welcome.

|Phase|Description|State|
|-----|-----------|-----|
|1|Implement reader which can understand the first test file (alltypes_plain.parquet). This is using a variety of encodings an no compression. Inline columns are not supported. Understand how to return results with minimum of boxing/unboxing.|in progress|
|2|Implement readers for any types not mentioned in phase 1, support NULL values.|planning|
|3|Implement writer which can do the same types as in phase 1 and 2.|planning|
|4|Support GZIP decompression/compression|planning|
|5|Support Snappy decompression/compression. Must be managed.|planning| 

More to come once I understand the complexity of parquet.


## Notes

We use [Thrift for .NET Core](https://github.com/apache/thrift/tree/master/lib/netcore) project to read Thrift specification which is take from the official [parquet-format](https://github.com/Parquet/parquet-format) repository as is. This depends on .NET Standard 1.6 which makes it a requirement for this project as well.

To regenerate thrift classes use `scripts\thriftgen.ps1`. Project is set to define `SILVERLIGHT` constant as .NET Standard is not fully compatible with this generator, but tested to be working in silverlight compatibility mode.

Parquet compatibility samples: https://github.com/Parquet/parquet-compatibility