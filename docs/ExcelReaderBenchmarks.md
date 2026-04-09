# Excel Data Reader Benchmarks

These benchmarks measure reading a 65k row (max .xls row count) Excel file, 
and accessing each cell value as the type expected by the SalesRecord class.

SylvanXlsx_BindT is the only benchmark in the group that actually creates and binds
to SalesRecord instances, the other benchmarks only produce the required values.

These benchmarks are written to be as fair as possible. One requirement is that the
monetary values must be a decimal with two digit precision. Many librarys will
produce decimal values with incorrect precision without custom handling. Specifically,
the values must be accessed as a double, then cast to a decimal, which will produce the
expected precision. Many libraries provide decimal accessors that are a "pit of failure"
in this regard. See benchmark implementations for full details.

OpenXml is no longer included in these results. It is so difficult to use that I
cannot figure out how to write a correct and fair benchmark for it. Since ClosedXml
is a wrapper around OpenXml, one could assume that they'd have similar performance.

## Excel .xlsx Benchmarks

The `Baseline` in this group, measure the time taken to unzip the Sheet1.xml and using `XmlReader.Read` to process every node.
It represents the minimal work that must be done assuming those classes are used for processing.


| Method                | Mean       | Error    | Ratio | Allocated     | Alloc Ratio |
|---------------------- |-----------:|---------:|------:|--------------:|------------:|
| Baseline              |   221.1 ms |  3.69 ms |  1.00 |      252.8 KB |        1.00 |
| SylvanXlsx            |   336.4 ms |  3.94 ms |  1.52 |     670.14 KB |        2.65 |
| SylvanXlsx_BindT      |   346.9 ms | 12.55 ms |  1.57 |   10916.23 KB |       43.18 |
| SylvanXlsxDynamic     |   355.3 ms |  9.08 ms |  1.61 |   14469.57 KB |       57.25 |
| PrimeXlsx             |   387.2 ms |  7.10 ms |  1.75 |  83870.22 KB |      331.83 |
| XlsxHelperXlsx        |   430.9 ms | 11.89 ms |  1.95 |  93289.43 KB |      369.10 |
| HypeLabXlsx_SheetData |   468.5 ms | 33.49 ms |  2.12 |  85215.17 KB |      337.17 |
| AsposeXlsx            |   619.0 ms | 13.69 ms |  2.80 |  209861.9 KB |      830.40 |
| MiniExcelXlsx         |   857.3 ms | 17.08 ms |  3.88 |  648451.5 KB |    2,565.88 |
| ExcelDataReaderXlsx   |   881.9 ms | 17.27 ms |  3.99 |  267932.2 KB |    1,060.19 |
| Lightweight           | 1,033.2 ms | 14.98 ms |  4.67 |  168004.8 KB |      664.73 |
| EPPlusXlsx            | 1,288.3 ms | 18.40 ms |  5.83 |  423875.4 KB |    1,676.98 |
| ClosedXmlXlsx         | 2,082.8 ms | 29.75 ms |  9.42 |  727572.8 KB |    2,878.78 |
| FastExcelXlsx         | 2,407.3 ms | 41.89 ms | 10.89 | 1189954.5 KB |    4,708.18 |
| NpoiXlsx              | 2,898.2 ms | 50.72 ms | 13.11 | 1288167.2 KB |    5,096.88 |

## Excel .xlsb Benchmarks

| Method              | Mean        | Error     | Ratio  | Allocated    | Alloc Ratio |
|-------------------- |------------:|----------:|-------:|-------------:|------------:|
| SylvanXlsb          |    43.33 ms |  0.374 ms |   1.00 |    359.17 KB |        1.00 |
| PrimeXlsb           |   125.54 ms |  2.743 ms |   2.90 | 129818.72 KB |      361.44 |
| ExcelDataReaderXlsb |   239.01 ms |  2.888 ms |   5.52 | 150656.36 KB |      419.46 |
| AsposeXlsb          |   419.33 ms |  8.348 ms |   9.68 | 247976.12 KB |      690.42 |

## Excel .xls Benchmarks

| Method             | Mean      | Error     | Ratio | Allocated    | Alloc Ratio |
|------------------- |----------:|----------:|------:|-------------:|------------:|
| SylvanXls          |  27.48 ms |  0.377 ms |  1.00 |    190.51 KB |        1.00 |
| ExcelDataReaderXls | 226.76 ms |  2.813 ms |  8.25 | 237573.23 KB |    1,247.01 |
| AsposeXls          | 368.71 ms | 32.568 ms | 13.42 | 252021.59 KB |    1,322.85 |
| NpoiXls            | 988.64 ms | 60.718 ms | 35.98 | 657435.26 KB |    3,450.86 |
