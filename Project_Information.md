# Thông tin du lịch #
## I.Yêu cầu chung: ##
- Chương trình phải bao gồm những tính năng chính sau:
> + Danh sách các nhóm dịch vụ chính. Trong các nhóm dịch vụ chính có thể có các nhóm dịch vụ con. Vd: Nhóm dịch vụ chính “Restaurant” có nhóm dịch vụ con là “Sit down”, “Take away”, “Café”…
> + Danh sách các địa điểm, được phân loại theo các nhóm dịch vụ. Các địa điểm phải có các thông tin, hình ảnh, số lượng bình luận.
> + Google map cho phép người dùng xem và tìm kiếm địa điểm theo yêu cầu.
> + “Hot style” cập nhật những địa điểm có chương trình đặc biệt hoặc trào lưu mới.
> + Bình luận và chấm điểm của người dùng về địa điểm nào đó.
> + Đánh dấu các địa điểm yêu thích.
> + Tính năng bổ sung: liên kết mạng xã hội, chụp ảnh.
## II.Mô tả chức năng cụ thể: ##
1.Danh sách các nhóm chính và nhóm con:
> - Dùng để phân chia các địa điểm theo từng nhóm nhỏ, đem lại sự tiện lợi cho việc tìm kiếm của người dùng và sắp xếp chương trình.
> - Cho phép người dùng tìm kiếm dựa trên nhóm địa điểm.
Rest place	Nhóm các địa điểm về nơi ở
+ Hotel	Nhóm địa điểm là khách sạn
+ Motel	Nhóm địa điểm là nhà nghỉ
+ Apartment	Nhóm địa điểm là nhà riêng

Restaurant	Nhom các địa điểm về ăn uống
+ Sit down	Nhóm địa điểm là nhà hàng
+ Take away	Nhóm địa điểm là ăn nhanh/mang đi
+ Café	Nhóm địa điểm là quán nước

ShouldGo	Nhóm các địa điểm về vui chơi
+ Tourist attractions	Nhóm địa điểm du lịch thu hút
+ Nightlife	Nhóm địa điểm vui chơi
+ Shopping	Nhóm địa điểm mua sắm


2.Danh sách địa điểm và thông tin liên quan
> - Cung cấp thông tin chi tiết về địa điểm mà người dùng quan tâm.
Name	Tên địa điểm
Address	Địa chỉ
Phone	Điện thoại liên lạc
Description	Mô tả
Website/Fb	Trang thông tin (option)
Image	Hình ảnh
Price	Giá cả (option)
Location	Tọa độ (dùng trong google map)

3.Google map
> - Cung cấp 2 chức năng là hiển thị và tìm kiếm. Chức năng hiển thị cho phép hiển thị vị trí (kèm hướng dẫn xem chi tiết) của địa điểm. Tìm kiếm cho phép người dùng lọc những địa điểm m quan tâm.
4. “Hot Style”
> - Cập nhật những địa điểm có tổ chức sự kiện hoặc những trào lưu mới đang diễn ra. Chức năng này kết hợp vs kết nối internet. Nếu không có internet, chương trình sẽ có default 1 số điểm “Hot style”. Nếu khi có internet, chương trình sẽ cập nhật cho người dùng thông tin mới. “Hot Style” sẽ được lưu trữ theo ngày, mỗi ngày chương trình sẽ load “Hot style” cho người dùng (nếu có) và tối đa 5 địa điểm hoặc chương trình trong 1 “hot style”.
5. Bình luận và chấm điểm:
> - Chức năng ghi lại bình luận của người dùng về 1 địa điểm. Người dùng có thể chấm điểm về địa điểm theo các mức thang: “Good”, “Normal” ,”Bad”.
6. Đánh dấu địa điểm yêu thích:
> - Lưu lại những địa điểm người dùng quan tâm, tạo nên 1 danh sách địa điểm yêu thích. Người dùng có thể thêm, sửa, xóa địa điểm trong danh sách hoặc xóa toàn bộ danh sách.
7. Tính năng bổ sung:
> - Liên kết mạng xã hội như fb, twister thông qua internet.
> - Chụp ảnh: ảnh được lưu vào thư mục Galary của người dùng.


## III.Cơ sở dữ liệu ##
1.Mô tả

Tên bảng:	tblMainTypes
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã nhóm	Int 	Primary
Name	Tên nhóm	Varchar(50)
mainID	Mã nhóm cha	Int	Foreign	True_

Tên bảng:	tblPlace
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã địa điểm	Int 	Primary
Name	Tên địa điểm	Varchar(50)
Address	Địa chỉ	Varchar(100)
Phone	Số điện thoại	Int
Website	Địa chỉ web	Char(100)		True
Image	Ảnh 	Char(100)
Description	Mô tả về địa điểm	Text(100)
Price	Giá	Double		True
Location	Địa điểm	Char(20)
Saved	Yêu thích	Bit_

Tên bảng:	tblComment
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã  comment	Int 	Primary
placeID	Mã địa điểm	Int	Foreign
Username	Tên người đăng	Varchar(50)
Comment	Nội dung comment	Text(100)
Date	Ngày đăng	Char(15)_

Tên bảng:	tblRate
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã loại bình chọn	Int 	Primary
Name	Tên loại bình chọn	Varchar(10)_

Tên bảng:	tblRatingDetail
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã nhóm	Int 	Primary
placeID	Mã địa điệm	Int	Foreign
rateID	Mã bình chọn	Int	Foreign
Count	Điểm bình chọn	Int_

Tên bảng:	tblHotStyle
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã loại	Int 	Primary
Date	Ngày đăng	Char(20)_

Tên bảng:	tblHotStyleDetail
Mã	Diễn giải	Kiểu	Khóa	Null
_id	Mã 	Int 	Primary
styleID	Mã loại	Int	Foreign
placeID	Mã địa điểm	Int	Foreign
Info	Thông tin nổi bật	Text(100)
Time	Thời gian diễn ra	Char(10)_

2. Quan hệ
