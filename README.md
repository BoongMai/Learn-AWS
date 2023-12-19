# ***----*---------------- NGÀY 1: Mục: 3.Vid-1-----------------*----***
## 1.IAM quản lý 3 phần chính gồm: Compute, Storage và DataBase.
### 1.1: Compute bao gồm 6 phần:
- EC2 
- ECS
- Lambda
- Auto Scaling
- Elastic BeanStalk 
- ELB
### 1.2: Storage bao gồm 4 phần: 
- S3
- Glacier
- Storage Gateway
- EFS
### 1.3: DataBase bao gồm 5 phần:
- RDS
- DynamoDB
- RedShift
- ElasticCache
- DB Accelerator

***----*-----------------*-----------------*----***


# ***----*----------------NGÀY 2/ Mục 3: Vid-4 IAM Groups, User, Roles -----------------*----***

## IAM là gì ? 
- IAM cung cấp quyền cho người dùng đăng nhập vào hệ thống AWS 
- Trong đó IAM đc chia thành 2 nhánh:
-  Identities (danh tính của người đăng nhập). Identities có 3 loại identities đó là:
-    Users: have credentials (chỉ users và groups có thông tin xác thực)`
-    Groups: have credentials
-    Roles: not have credentials
-  Permissions (Quyền hạn của account); 
-    Ở phần quyền hạn thì sẽ được quản lý bằng "Policies" và những "Policies" này được tạo bằng những "Statement"

## Giải thích ý nghĩa Policies:
- Một cái IAM identity có thể có 1 hoặc nhiều cái "Policies" thì cái Policies này nó sẽ 
    quyết định thằng đó được làm gì ở trên 1 cái resource nào đó

## IAM Users:
- Tạo cho người dùng 1 quyền hạn (Bao gồn tài khoảng, mật khẩu và 2 access key) để tương tác với service AWS bằng APIs và CLI.
## IAM Groups:   
- là tập hợp mấy thằng IAM Users lại,và quản lý bởi cái policies base....


## THực hành hiểu IAM Users và IAM Group.
- Tạo 1 thằng user: và khi tạo nó phải được assigned zo 1 cái "group" hoặc 1 cái "permissions" hoặc attach nó zo 1 cái  policy có sẳn.
- Case ở bài tập là tạo 1 cái group và add user vừa tạo vào
- Tạo thành công account "admin":
-  Tài khoảng: admin/ mật khảu: 100820Za@
-  Click detail thằng  user 'admin' vừa tạo và vào phần security credential thì nó sẽ có 1 cái "Console Link"
-   "Console Link": dùng để đăng nhập zo cái AWS console dành cho cái acc đó ("tất nhiên là không phải là console của root account")
-   Vì account admin được assign vào group admin cho nên nó tất cả các quyền. Nếu remove ra thì toang.

## IAM Roles là gì 