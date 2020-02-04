1. Công nghệ containerlization
- là một công nghệ ảo hóa, trong đó 1 máy chủ có thể sinh ra được nhiều máy con nhưng các máy con dùng chung phần nhân của máy mẹ và chia sẻ
với nhau tài nguyên của mẹ. Khi napf cần tài nguyên mới được cấp và cấp đúng với phần cần sử dụng -> tối ưu tối đa tài nguyên sử dụng.

2. Docker
- là một công cụ để đáp ứng công việc việc của containerlization - công cụ ảo hóa cho container.
- Chỉ chạy trên môi trường Linux
* AWS định nghĩa: Docker pagkages software into standardized units called containers that have everything your software needs to run including libararies, system tool, code, and runtime.
* Lets you quickly deploy and scale applications into any enviroment and know your code will run.

3. Container
- Một docker container là một đơn vị chuẩn của phát triển phần mềm nó chứa tất cả các phần mềm cần thiết để chạy code, runtime, systemtool,
  system libaries... Container được tạo ra từ read-only template(image)

4.Docker Image
- Tương tự như 1 bản snapshot. -> Dùng để khởi tạo các Docker container.
-> Những image này được lưu vào trong một registry, chúng có thể được download và chạy trong cluster
* POINT IN TIME CAPTURE OF CODE AND DEPENDENCIES

5. Task definition
- Là một dạng text file. Mô tả 1 hoặc nhiều container để hình thành nên ứng dụng của bạn.
- Task definition sẽ chỉ ra một vài parameter cho ứng dụng container nào sẽ được sử dụng, launch type sẽ được dùng những port nào sẽ được
mở cho ứng dụng và data volume gì sẽ được với container trong task.
AWS core concept: It is template for running one or more tasks.

  * An Amazon ECS task definition specifies:
    - Docker image for each container
    - CPU and Memory requirements for each container
    - Link between containers
    - networking and port settings
    - Data staorage volumes
    - Security (IAM) roles

* POINT IN TIME CAPTURE OF THE CONFIGURATION FOR RUNNING THE IMAGEW
6. Task
  - Deploys containers onto EC2 instances in your cluster

6. Amazon EC2 Container Registry(AWS ECR)
  - Full managed docker container registry
  - Store, manage, and deploy container images
  - Integrated with Amazon ECS
  - Encrypted, redendant, and HA
  - Gắn các quyền bảo mật với AWS IAM(Granular security permissons with AWS IAM)
  
  7. Amazon EC2 Container Service(Amazon ECS)
    - Run and manages docker-enabled applications across a logical group of Amazon EC2 instances
 
 8. Amazon ECS Cluster
  - Nhóm logic các EC2 mà ở đó mà có thể cài đặt container trên đó.
  - có nhiều phương thức thanh toán: on-demand,....
  - Bao gồm các loại EC2 khác nhau theo vùng cụ thể
  - EC2 instances are linked in a VPC
 
 9. ECS agent
  - Quản lý trạng thái của các container trên các một EC2
  - Giúp ECS communicates with docker daemon on the EC2.(Docker Daemon)

10. RUN-TASK
  - Find EC2 in cluster that meet requirements in the task definition
  - Defines how tasks are distributed onto EC2 instances in the cluster
  - Communicates with ecs-agent and docker daemin to run containers on eligible ec2 instances in the cluster
  - Can be executed via the ecs console, cli, or apis
  
  11. Services:
    - Manage long-running workloads
    - automate the run-task process
    - actively monitor running tasks
    - restart tasks if they fail
