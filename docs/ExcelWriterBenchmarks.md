# Excel Data Writer Benchmarks

These benchmarks measure writing a 65k row Excel file, with data read from in-memory objects.

| Method              | Mean        | Error      | Allocated     |
|-------------------- |------------:|-----------:|--------------:|
| SylvanXlsb          |    92.84 ms |   1.235 ms |     111.91 KB |
| SylvanXlsx          |   143.39 ms |   4.858 ms |     166.39 KB |
| LargeXlsx           |   193.02 ms |   4.443 ms |     137.63 KB |
| MiniXl              |   414.53 ms |  10.120 ms |  333641.86 KB |
| SwiftExcelXlsx      |   568.39 ms |   7.416 ms |  102040.44 KB |
| AsposeXlsx          | 1,160.77 ms |  38.183 ms |  248160.12 KB |
| AsposeXlsb          | 1,230.24 ms |  41.113 ms |  308161.17 KB |
| NpoiXlsx            | 1,483.17 ms |  24.820 ms |  579803.96 KB |
| OpenXmlXlsx         | 2,341.92 ms |  38.572 ms |  713594.19 KB |
| EPPlusViaDataReader | 2,611.41 ms |  41.326 ms |   400648.2 KB |
| EPPlusXlsx          | 2,850.94 ms |  30.791 ms |  642897.56 KB |
| NanoXlsxWrite       | 5,236.35 ms | 347.982 ms | 1995813.94 KB |
