CodePipeline là một dịch vụ phân phối liên tục mà bạn có thể sử dụng để mô hình hóa, trực quan hóa và tự động hóa các bước cần thiết để phát hành phần mềm của bạn.

Code commit là một dịch vụ kiểm soát source được quản lý toàn phần, giúp lưu trữ bảo mật các kho dữ liệu Git. Dịch vụ này giúp các nhóm dễ dàng phối hợp với nhau the mã trong một hệ sinh thái có khả năng thay đổi quy mô linh hoạt và bảo mật.

Code deploy là một dịch vụ triển khai được quản lý toàn phần có khả năng tự động hóa việc triển khai phần mềm trên các dịch vụ AWS như EC2, AWS Fargate, AWS Lamda và on-premise servers.

A deployment group là một tài nguyên xác định các cài đặt liên quan đến triển khai như trường hợp nào sẽ triển khai và tốc độ triển khai chúng.
Deployment type:
  - In-place: cập nhật các phiên bản trong nhóm triển khai với các phiên bản ứng dụng mới nhất. Trong quá trình triển khai, mỗi phiên bản sẽ được đưa ra ngoại tuyền trong thời gian ngắn để cập nhật
  - Blue/Green: Thay thế các phiên bản trong nhóm triển khai bằng các phiên bản mới và triển khai sửa đổi ứng dụng mới nhất cho chúng. Sau khi các phiên bản trong môi trường thay thế được đăng ký với bộ cân bằng tải, các phiên bản từ môi trường ban đầu được hủy đăng ký và có thể được chấm dứt.

Trong CodeDeploy, một ứng dụng là một tài nguyên chứa ứng dụng phần mềm bạn muốn triển khai. Sau đó, bạn sử dụng ứng dụng này với CodePipeline để tự động triển khai ứng dụng mẫu vào ví dụ Amazon EC2 của bạn.

  Deployment settings
Deployment configuration
Choose from a list of default and custom deployment configurations. A deployment configuration is a set of rules that determines how fast an application is deployed and the success or failure conditions for a deployment.

Evaluation order in load balancer for container: quy định thứ tự ưu tiên cho path pattern, chỉ số càng thấp thì độ ưu tiên càng cao. Có thể định tuyến lưu lượng truy cập từ trình nghe này đến các dịch vụ trung gian bằng cách tạo đường dẫn cho mỗi dịch vụ


AWS Batch:
  - là service dùng để xử lý các job cụ thế
  - Không cần cài đặt, quản lý backend
  - Chạy bằng ECS, sử dụng container để xử lý process
  - Có 2 dạng on-demand và spot
