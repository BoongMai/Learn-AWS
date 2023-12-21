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
