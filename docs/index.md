#Graph API

`Graph API for third party`

##API Define
* `Định dạng kết quả trả về`: JSON
* `Phương thức`: POST
* `Tham số`: 
```javascript
{
    //Tham số bắt buộc với các hàm lấy dữ liệu
    access_key: STRING thời gian hiện tại dạng số: "1439190122831"
    client_id: STRING ID của ứng dụng
    access_code: STRING được tính theo công thức access_code = sha256 (secret key + access_key)
      
    //Tham số tùy chọn
    c_location: STRING US, GB, VN.... mặc định "US"
    c_date: STRING thời gian hiện tại với định dạng Y-m-d H:i:s
    c_limit: INTEGER mặc định config.limit của Server
    c_offset: INTEGER mặc định 0
}
```
* `Basic API URL`: URL_API/v{VERSION/{NAME_OF_METHOD}/ with {VERSION} = Integer, {NAME_OF_METHOD} = String. Eg: https://www.api.xxx.com/v1/getTopCoupons/
* `Cấu trúc`:
```javascript
{
    code: 0,
    msg: 'Main message',
    messages : {
        message_1 : '....',
        message_2 : '....',
        message_3 : '....',
        
        message_n : '....',
    },
    data: {
        key_1 : 'value 1',
        key_2 : {
            //Object
        },
        key_3 : [
            //Array
        ],      
        key_n : 'value n',
    },
    data_error : ....
}
```
* `Định nghĩa kết quả trả về`:
    * code: Code != 0 tức là có lỗi trả về
    * msg: Thông báo trả về nếu có lỗi, tức là code != 0 ở trên
    * messages: Thông báo phụ nếu có nhiều lỗi
    * data: cấu trúc linh động tùy theo mỗi {NAME_OF_METHOD} mà định dạng khác nhau
    * data_error: Dữ liệu phục vụ debug cho API khi có lỗi trong TRY CATCH (Exception) xảy ra

##Oauth

##Users

##Stores

##Coupons

###Get top coupons

```
URL: http://localhost:3002/v1/coupons/getTopCoupons/
Tham số tùy chọn:
    c_limit
    c_offset
```
