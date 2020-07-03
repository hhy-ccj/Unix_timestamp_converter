# Epoch Unix Timestamp Converter 
[![Build Status](https://travis-ci.org/hhy-ccj/Unix_timestamp_converter.svg?branch=master)](https://travis-ci.org/hhy-ccj/Unix_timestamp_converter)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/772958417@qq.com)
## 概述
- `32 Bit`限制

:clock12: `Unix Time Start` | :end: `Unix Time End`
:-:|:-:
`1970/1/1 00:00:00 Thursday` | `2106/2/7 06:28:15 Sunday`

- 转换方向

 `Unix time` :arrow_right: `UTC` | `Unix time` :arrow_right: `UTC BeiJing`
:-:|:-:
:heavy_check_mark: | :heavy_check_mark:

- `C` 语言实现

## Start
> 接口
```C
struct UTC_TIME unix32_to_UTC(u32 unix_time);
struct UTC_TIME unix32_to_UTC_beijing(u32 unix_time);
```
> 测试代码
```C
int main(int argc, char const *argv[])
{
    struct UTC_TIME cur_utc;

    // For test
    cur_utc = unix32_to_UTC(0);
    log_info("unix32_to_UTC: %d/%d/%d %02d:%02d:%02d, weekday %d",
              cur_utc.year, cur_utc.month, cur_utc.day,
              cur_utc.hour, cur_utc.minute, cur_utc.second,
              cur_utc.weekday);

    cur_utc = unix32_to_UTC(0xFFFFFFFF);
    log_info("unix32_to_UTC: %d/%d/%d %02d:%02d:%02d, weekday %d",
              cur_utc.year, cur_utc.month, cur_utc.day,
              cur_utc.hour, cur_utc.minute, cur_utc.second,
              cur_utc.weekday);

    cur_utc = unix32_to_UTC_beijing(1593532800);
    log_info("UTC BeiJing: %d/%d/%d %02d:%02d:%02d, %s",
              cur_utc.year, cur_utc.month, cur_utc.day,
              cur_utc.hour, cur_utc.minute, cur_utc.second,
              weekday[cur_utc.weekday]);

    return 0;
}
```
> 编译
```bash
gcc unix_timestamp.c -o unix_timestamp
```
> `Linux terminal`下执行
```bash
./unix_timestamp
```
> `Windows cmd` 或者 `powershell` 下执行
```bash
unix_timestamp.exe
```
> 输出结果
```C
unix32_to_UTC: 1970/1/1 00:00:00, weekday 4
unix32_to_UTC: 2106/2/7 06:28:15, weekday 0
UTC BeiJing: 2020/7/1 00:00:00, Wednesday
```

## 在线转换工具
- UTC
> https://www.unixtimestamp.com/index.php
- UTC BeiJing
> http://tool.chinaz.com/Tools/unixtime.aspx?jdfwkey=zfpdi&qq-pf-to=pcqq.c2c
