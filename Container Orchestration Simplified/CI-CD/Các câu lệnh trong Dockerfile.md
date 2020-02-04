Link tham khảo:
https://docs.docker.com/engine/reference/builder/#from

$docker build -f /path/to/a/Dockerfile .
-> You use -f flag with docker build to point to a Dockerfile anywhere in your file system.

$docker build -t path .
-> chỉ định nơi lưu trữ nếu quá trình xây dựng thành công

$docker build -t path/test:1 -t path/test:latest .
-> Gán nhiều tag cho imgae

FROM
FROM [--platform=<platform>] <image> [AS <name>]
Or
FROM [--platform=<platform>] <image>[:<tag>] [AS <name>]
Or
FROM [--platform=<platform>] <image>[@<digest>] [AS <name>]

  - cài đặt base image cho các bước tiếp theo.(base image là server/môi trường) 
  - có thể xuất hiện nhiều lần trong 1 file Dockerfile để tạo nhiều image hoặc sử dụng 1 build stage như là điều kiện cho các giai đoạn khác phụ thuộc.

