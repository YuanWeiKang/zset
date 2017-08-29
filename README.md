# zset
Implementing sorted set in Redis with golang.

## Installation
```bash
go get -u github.com/XanthusL/zset
```

## Usage
```go
s := zset.New()
// add data
s.Add(66, 1001, "test1")
s.Add(77, 1002, "test2")
s.Add(88, 1003, "test3")
s.Add(100, 1004, "liyiheng")
s.Add(99, 1005, "test4")
s.Add(44, 1006, "test5")
// update data
s.Add(44, 1001, "test1")

// get rank by id
rank, score, extra := s.GetRank(1004, false)
// get data by rank
id, score, extra := s.GetDataByRank(0, true)

// delete data by id
s.Delete(1001)
```

## Benchmark

```bash
go test -test.bench=".*"
BenchmarkSortedSet_Add-4                 1000000              4100 ns/op
BenchmarkSortedSet_GetRank-4              500000              3683 ns/op
BenchmarkSortedSet_GetDataByRank-4       2000000               714 ns/op
PASS
ok      zset    12.602s
```