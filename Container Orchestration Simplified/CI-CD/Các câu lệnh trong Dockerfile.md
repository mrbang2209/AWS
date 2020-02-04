Link tham khảo:
https://docs.docker.com/engine/reference/builder/#from
https://docker-ghichep.readthedocs.io/en/latest/dockerfile/
https://kipalog.com/posts/Cac-lenh-trong-Dockerfile

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

ARG
  ARG  CODE_VERSION=latest
  
  -> Định nghĩa biến cho quá trình build docker image. Biến chỉ có scope khi build image, không sử dụng được khi docker container running.

RUN
RUN has 2 forms:
  - RUN <command> (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
  - RUN ["executable", "param1", "param2"] (exec form)
  {{{
    FROM ubuntu
    RUN apt-get update
    RUN apt-get install curl -y
  }}}
  -> Sử dụng khi muốn thực thi 1 command trong quá trình build.
  
CMD
  CMD ["curl", "ipinfo.io"]
  CMD curl ifconfig.io
  
  -> CMD dùng để truyền một lệnh của Linux mỗi khi thực hiện khởi tạo 1 container từ image được build từ dockerfile.
  
 LABEL
  LABEL <key>=<value> <key>=<value> <key>=<value> ...
  -> Dùng để add các metadata vào image
  -> Để xem các label của images, dùng lệnh docker inspect 
 
 MAINTAINER
  MAINTAINER <name>
  -> Dùng để đặt tên tác giả
  
 EXPOSE
    EXPOSE 80/udp
    - Lệnh thiết định Docker Image sẽ listener trên các cổng chỉ định khi chạy
  
