Link tham khảo:
https://docs.docker.com/engine/reference/builder/#from
https://docker-ghichep.readthedocs.io/en/latest/dockerfile/
https://kipalog.com/posts/Cac-lenh-trong-Dockerfile

# $docker build -f /path/to/a/Dockerfile .
-> You use -f flag with docker build to point to a Dockerfile anywhere in your file system.

# $docker build -t path .
-> chỉ định nơi lưu trữ nếu quá trình xây dựng thành công

# $docker build -t path/test:1 -t path/test:latest .
-> Gán nhiều tag cho imgae

# FROM
FROM [--platform=<platform>] <image> [AS <name>]
Or
FROM [--platform=<platform>] <image>[:<tag>] [AS <name>]
Or
FROM [--platform=<platform>] <image>[@<digest>] [AS <name>]

  - cài đặt base image cho các bước tiếp theo.(base image là server/môi trường) 
  - có thể xuất hiện nhiều lần trong 1 file Dockerfile để tạo nhiều image hoặc sử dụng 1 build stage như là điều kiện cho các giai đoạn khác phụ thuộc.

# ARG
  ARG  CODE_VERSION=latest
  
  -> Định nghĩa biến cho quá trình build docker image. Biến chỉ có scope khi build image, không sử dụng được khi docker container running.

# RUN
RUN has 2 forms:
  - RUN <command> (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
  - RUN ["executable", "param1", "param2"] (exec form)
  {{{
    FROM ubuntu
    RUN apt-get update
    RUN apt-get install curl -y
  }}}
  -> Sử dụng khi muốn thực thi 1 command trong quá trình build.
  
# CMD
  CMD ["curl", "ipinfo.io"]
  CMD curl ifconfig.io
  
  -> CMD dùng để truyền một lệnh của Linux mỗi khi thực hiện khởi tạo 1 container từ image được build từ dockerfile.
  
# LABEL
  LABEL <key>=<value> <key>=<value> <key>=<value> ...
  -> Dùng để add các metadata vào image
  -> Để xem các label của images, dùng lệnh docker inspect 
 
# MAINTAINER
  MAINTAINER <name>
  -> Dùng để đặt tên tác giả
  
# EXPOSE
    EXPOSE 80/udp
    - Lệnh thiết định Docker Image sẽ listener trên các cổng chỉ định khi chạy. Câu lệnh chỉ dể khai náo, không có chức năng NAT port từ host vào container.
    - Muốn NAT port thì phải sử dụng -p hoặc -P trong quá trình khởi tạo container.
    
# ENV
  ENV myName John Doe
  ENV myDog Rex The Dog
  ENV myCat fluffy
  
  - Khai báo các biến môi trường.
  
USER
  Thiết định user name(UID) và user group(GID) khi chạy các lệnh RUN, CMD, ENTRYPOINT trong dockerfile.
  
# WORKIR
    ENV DIRPATH /path
    WORKDIR $DIRPATH/$DIRNAME
    RUN pwd
    -> set the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instruction that follow it in the Dockerfile.
    - Nếu không tồn tại câu lệnh thì dockerfile sẽ tự tạo ngay cả khi không được sử dụng.
    - Có thể được viết nhiều lần. Ví dụ
        WORKDIR /a
        WORKDIR b
        WORKDIR c
        RUN pwd
      -> Lúc đấy lệnh RUN sẽ được xử lý ở thư mục a/b/c\
    Có thể sử dụng được các biến môi trường. Ví dụ:
        ENV DIRPATH /path
        WORKDIR $DIRPATH/$DIRNAME
        RUN pwd
     -> Run chạy trong folder /path/$DIRNAME

# SHELL
  - Cho phép các shell form khác ghi đè lên shell mặc định
  Mặc định trên Linux là ["/bin/sh", "-c"] và Windows là ["cmd", "/S", "/C"].
      FROM microsoft/windowsservercore
       -- Executed as cmd /S /C echo default--
      RUN echo default

      // Executed as cmd /S /C powershell -command Write-Host default
      RUN powershell -command Write-Host default

      // Executed as powershell -command Write-Host hello
      SHELL ["powershell", "-command"]
      RUN Write-Host hello

      // Executed as cmd /S /C echo hello
      SHELL ["cmd", "/S"", "/C"]
      RUN echo hello
     
    
  
