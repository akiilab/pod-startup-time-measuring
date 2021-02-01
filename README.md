# Pod Startup Time Measuring

## Install Go

```shell
export GO111MODULE=on
```

## Build

```shell
docker pull alpine
go build main.go
```

## Usage

```shell
./main 2     # execute 2 times
```

Output

```shell
#No.         CreateAt             ReadyAt            DeleteAt
1 1612171985296137049 1612171989194275853 1612171989290896465
2 1612171989338686532 1612171991193007656 1612171991213887913
```

## Measuring

```shell
sudo apt update
sudo apt install -y gawk datamash
```

```shell
./main 100 | awk '{print $3-$2}' | datamash --header-out mean 1 median 1 perc:90 1 perc:95 1 perc:99 1
```

Output

```shell
mean(field-1)	median(field-1)	perc:90(field-1)	perc:95(field-1)	perc:99(field-1)
2241857103.36	1935321856	2960865100.8	2999558656	3046800279.04
```
