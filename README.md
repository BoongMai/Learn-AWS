#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1›" > /var/www/html/index.html

## ---------------- NGÀY 1: Mục: 3.Vid-1 ----------------
### <font color="#007bff">1.IAM quản lý 3 phần chính gồm: Compute, Storage và DataBase.</font>
#### 1.1: Compute bao gồm 6 phần:
- EC2 
- ECS
- Lambda
- Auto Scaling
- Elastic BeanStalk 
- ELB
#### 1.2: Storage bao gồm 4 phần: 
- S3
- Glacier
- Storage Gateway
- EFS
#### 1.3: DataBase bao gồm 5 phần:
- RDS
- DynamoDB
- RedShift
- ElasticCache
- DB Accelerator


## ----------------NGÀY 2/ Mục 3: Vid-4 IAM Groups, User, Roles ----------------

### IAM là gì ? 
- IAM cung cấp quyền cho người dùng đăng nhập vào hệ thống AWS 
- Trong đó IAM đc chia thành 2 nhánh:
    - Identities (danh tính của người đăng nhập). Identities có 3 loại identities đó là:
        - Users: have credentials (chỉ users và groups có thông tin xác thực)`
        - Groups: have credentials
        - Roles: not have credentials
    - Permissions (Quyền hạn của account); 
        - Ở phần quyền hạn thì sẽ được quản lý bằng __Policies__ và những __Policies__ này được tạo bằng những __Statement__

### Giải thích ý nghĩa Policies:
- Một cái IAM identity có thể có 1 hoặc nhiều cái __Policies__ thì cái Policies này nó sẽ 
    quyết định thằng đó được làm gì ở trên 1 cái resource nào đó

### IAM Users:
- Tạo cho người dùng 1 quyền hạn (Bao gồn tài khoảng, mật khẩu và 2 access key) để tương tác với service AWS bằng APIs và CLI.
### IAM Groups:   
- là tập hợp mấy thằng IAM Users lại,và quản lý bởi cái policies base....


### THực hành hiểu IAM Users và IAM Group.
- Tạo 1 thằng user: và khi tạo nó phải được assigned zo 1 cái __group__ hoặc 1 cái __permissions__ hoặc attach nó zo 1 cái  policy có sẳn.
- Case ở bài tập là tạo 1 cái group và add user vừa tạo vào
- Tạo thành công account __admin__:
    - Tài khoảng: admin/ mật khảu:ai cũng biết là gì.
    - Click detail thằng  user 'admin' vừa tạo và vào phần security credential thì nó sẽ có 1 cái __Console Link__
    - __Console Link__: dùng để đăng nhập zo cái AWS console dành cho cái acc đó __tất nhiên là không phải là console của root account__
    - Vì account admin được assign vào group admin cho nên nó tất cả các quyền. Nếu remove ra thì toang.

### IAM Roles là gì 
- Thằng Role này bao gồm 2 phần chính là:
    - Permission: cái này quyết định cái __Principle__ đó làm được gì khi mà nó được gắn cái role này
    - Trust Policy: cái này sẽ quyết định là cái __quyền hạn "Principle"__ mà cái role này đảm nhận.
- Role nó cũng giống như IAM users là nó sẽ cho phép người đăng nhập dược phép hoặc không dươc phép làm gì đó trong phiên đăng nhập đó.
- Đưa vào cáo role có thể cung cấp cho 1 phiên hoặc đại diện cho thằng user nào đó được phép làm gì trong phiên làm việc
    - chẳn hạn như được vào db, dược vào s3,...

## Day3 
### Học lại về permission
- Permisson sẽ được cấu thành từ các __policy__ và các __policy__ này thực chất là 1 JSON document
### IAM Policies là gì ?
- là 1 cái file JSON nhằm gắn vào 1 cái permission hoặc 1 account nào đó, khi đó account sẽ được cấp quyền tương ứng.
- Mình có thể custom 1 cái policy cho bản thân !!
## Ngày 3
### MFA- Multi factor Authentication
- thì cái này có 2 loại:
    - Virtual MFA device: là 1 cái ứng dụng được cài đặt trên thiết bị
    - Universal 2nd Factor Security Key 
### AWS CLI - Comman line interface 
- cái này giúp mình tương tác với service của aws thông qua comman line shell của mình.
### AWS SDK - Software development kit
- cái thằng này nó là 1 gói ngôn ngữ cụ rhe63, nếu muốn dùng thì nhúng nó zo cái app của mình. nó sẽ cho phép mình vào aws service và dev.
### Cách dùng AWS CLI
- Cài cái đã. Xogn thì m phải tạo 1 cái access key để được cấp quyền truy cập từ CLI-shell. Nhớ là cái key này tương tương với account nên không dược share.
- Sau đó thì phải configure lại cái aws theo access key vừa tạo. and bumm m có thể làm bất cứ thứ gì miễn là trong permission của m thông qua CLI.
- M có thể dùng Clound shell ở trên aws web lun, nhưng mà nó chỉ sup cho vài region thoai.
## AWS - IAM Role for AWS service
- thằng này giống như 1 phiên đăng nhập và có quyền sử dụng những gì mà nó đc cấp permission. Nhưng nó khác ở chổ đó là nó đc dùng cho các service của AWS. VD: tao có 1 cái EC2 instant và nó muốn dùng 1 service gì đó của aws. thì t phải có 1 cái role cho cái ec2 đó.

### IAM Sercurity: 
- chia ra làm 2 phần: 
    - IAM Credentials thì cái này n1o sẽ cho phép mình quản lý cái list user đang có.(account)
    - IAM advice access thì cái này nó giúp mình xem cái acc nào đó có những cái policy nào (user)
IAM Guildlines $ Best Practices


## Ngày 4
### AWS - EC2
- Thằng EC2 này hiện đang support tạo 3 hệ điều hành, Linux, Mac OS và Window.
- EC2 - User Data:
    - Tức là cái này nó sẽ chỉ khởi chạy 1 lần đoạn __script__  của User Data đó.
- EC2 Instant type:
    - cái này là mấy cái kiểu khi tạo 1 cái EC2:
        - Genaral Perpose: cái này tốt cho web server và code dự án
        - Compute Optimize: cái này tốt nếu m muốn 1 con máy xịn.
        - Memory Optimize: cái này tốt cho lưu data.
        - Storage Optimize: cái này tốt cho xử lý dữ liệu
        - Trong này thì nó đặt tên theo kiểu như sau: 
        - __m5.2xlarge__ trong đó __m__ là instant class, __5__ là generation và __2xlarge__ là size đi kèm với instant đó .
- Securiry Group & Classic port for EC2
    - mấy cái port cở bản phải biết:
        - 22: SSH (Secure Shell) - log in to a linux instant
        - 21: FTP (File Transfer Protocal) - upload file into a file share
        - 22: SFTP (Secure File Tranfer Protocal) - upload file dùng SSH
        - 80: HTTP - chấp thuận truy cập từ nguồn đăng nhập lạ
        - 443: HTTPS - truy cập an toàn
        - 3389: RDP (Remote desktop protocal) 
## Ngày 5 Learn about SSH
- Okei thì bây giờ muồn vào được cái máy ảo thì cần phải có 1 cái SSH (Đã được lưu từ trước.)
- __cd__ zo cái thư mục lưu cái đấy để chạy lệnh run instant "ssh -i <tên ssh file> ec2-user@<public IP của instant đó>". Nhưng mà phải set cái file ssh này làm default bằng lệnh __chmod 0400 <tên SSH key>__
### EC2 Instance Connect
- Cũng là connect zo cái instance nhưng mà là trên AWS console.
### EC2 Role
- để mà cho phép cái instance dùng các service của AWS thì mình configure nhưng diểu đó không nên !!! (vấn đề bào mật !!!) => Vì thế mình dùng __Role__ 

### EC2 purcharingh option

## Ngày 6 

### Learn About EBS (Elastic Block Store)
- Là 1 cái ổ đĩa onl được tạo ở aws và có thể gắn zo cái instance của mình (cùng 1 AZ - Availability Zone.)
- Khi mà tạo xong muốn copy nó để bảo lưu hoặc chép qua 1 cái AZ khác thì phải tạo Snapshot.
    - Snapshot giúp mình sao lưu lại cái drive đó. và ở đây mình có thể tạo 1 cái recycle bin rule để tránh xóa phát mất luôn.
    - Mình có thể copy cái snapshot này (túc là 1 cái drive có data trước đó) cho cái az khác hoặc clone nó.
### AMI - Amazon Machine Image
- Cái này same như iamge của docker. mình có thể tạo 1 cái instance trước với cái bộ Image yêu thích. sau đó chọn create AMI. từ cái AMI này mình có thể clone ra 1 cái instace khác với cái image có sẳn mà không cần phải setup lại từ đầu.
## Ngày 7.
###  EBS - Elastic Block Store và EFS Elastic File system:
 - 2 cái này đều là dùng để lưu trữ nhưng 1 cái là lưu dạng block và chỉ 1 AZ cái còn lại là nó có thể scale theo data và nhiều AZ cùng lúc dc lun
 ## Ngày 8
 ### So sánh EBS Elastic Block Store và EFS Elastic File System.
 ### exp - chương EBS EFS:
 - What is EBS Multi-Attach: Gán cùng 1 cái EBS volumn zo nhiều cái intance nhưng cùng 1 cái Availability Zone
 - You are running a high-performance database that requires an IOPS of 310,000 for its underlying storage. What do you recommend?: Dùng EC2 Intance store 
 __You can run a database on an EC2 instance that uses an Instance Store, but you'll have a problem that the data will be lost if the EC2 instance is stopped (it can be restarted without problems). One solution is that you can set up a replication mechanism on another EC2 instance with an Instance Store to have a standby copy. Another solution is to set up backup mechanisms for your data. It's all up to you how you want to set up your architecture to validate your requirements. In this use case, it's around IOPS, so we have to choose an EC2 Instance Store.__
- Which of the following EBS volume types can be used as boot volumes when you create EC2 instances?:
    - gp2, gp3, io1, io2 và and Magnetic (Standard). mới đc boot
- nếu mà database thì cứ Intance store mà vã là lụm hết :>>
## Ngày 9 
### Scalability - cái này là nói về độ thích nghi của hệ thống hoặc ứng dụng.
- Có 2 loại scalability: 
    - Vertical: là tăng theo chiều dọc. tức là nó sẽ tăng về kích thước kiểu như đang size bé thì up lên size.
    - Horizontal: là tăng chiều ngang. tức là nó sẽ tăng về số lượng. 1 người thì tăng9 lên 2 người.vv..
### High Availability:
-  Nó sẽ hoat4 động giống như 1 cái backup luôn chờ để được phục vụ. nhằm mục đích không bị gián đoạn khi sử dụng.
### Load balancing là gì ???
- là nó check cái intance xem có bị quá tải hay không. hoặc nó sẽ chia nhỏ người dùng ra để đều tải các intance
- hiện tại thì có 4 loại:
    - Classic Load Balancer - CLB
    - Application Load Balance - ALB
        - Thích ứng với: HTTP, HTTP, Web socket
    - Network load balancer - MLB
        - tương thích với: TCL, TLS, UDP
    - Gateway Load balancer - GLB
        - tương thích: 
### Ngày 10 - Cụ thể về ALB
- Application Load Balancer: Cái này muốn dùng thì đầu tiên phải trỏ nó zo 1 cái port mà mình muốn dùng:
 http hoặc https > Tạo 1 cái load balance loại ALB sau đó trỏ vô cái > Listeners and rules (cái này quy định port để triển khai cái load nè) >  target group > trong cái target group này mình sẽ quy định đc intance nào sẽ đc dùng....
 - Đặt biệt trong cái Listeners and rules nó sẽ có 1 cái để mình setup rule. Mình có thể tạo vô số cái rule cho nó > ví dụ t tạo 1 cái rule dùng path là __/error__ và khai báo điều kiện trong đó. Thì cái load balance nó sẽ check theo cái path và điều kiện redirect nếu m zo đúng cái part nó sẽ redirect m đi.

### Ngày 11 - Sticky Session - Cross zone load balancing - SSL
- Sticky Session : cái này thì kiểu như nó sẽ là 1 phiên hoạt động của người dùng khi vào bât1 cứ 1 cái laod balance nào. Nó sẽ có 1 cái cookie để lưu trữ lại cái phiên đó: VD tróng phiên cookie sẻ cầm data của user đó và quy định thời gian hết hạn để truy cập vào intance và sẽ switch sang intance khác.
- Cookie Names:  Thì cái này có 2 loại đó là Application based cookies và Duration base-cookies (Tạo cái này ở target thì gọi là custom Cookie name)
- Cross Zone Load Balancing: cái này thì mình custom cái tỉ lệ nó truy cập vào các intance: VD có 10 cái chia tỉ lệ 2 || 6 ở 2 AZ thì cái Cross zone này cho phép mình phân chia tỉ lệ sao cho hợp lý. ALB thì nó tự bật và mình có thể cuctom tắt ở  target group. NLB thì bật lên tính tiền ở mục attribute, tương tự cho Gateway Load Balancer
- SSL/TLS: Cái này nó sẽ cho phé cho phép mình truy cập từ client vào cái load balance được mã hóa. SSL là Secure Socket Layer và TLS là Transport Layer Security -> Server Name Indication cái này nó sẽ phân định cho mình là cái SSL đó muốn zo cái target nào và chỉ đùng đc cho ALB & NLB, CloudFront
- connection draining cái này giúp tạm ngưng request tới 1 cái intance khi nó ở trạng thái draining.
- Auto Scaling Group (ASG):
    - Tự thêm và xóa intance nếu chạm ngưỡng. kết hợp với ELB để dùng.

### Ngày 12 Auto Scalling Group - Dynamic Scalling Pilice
- Dể sài dể settup, tự động phát hiện CPU đang ở trạng thái > 70% ( add 2 units) và < 30% (remove đi 1 unit).

### ngày 14