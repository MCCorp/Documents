#Graph API

`Graph API for third party`

##API Define
* `Result`: JSON
* `Method`: POST
* `Params`: 
```javascript
{
    //Require params
    access_key: STRING timestamp: 1439190122831
    client_id: STRING ID APP
    access_code: STRING access_code = sha256 (secret key + access_key)
    c_location: STRING Country code eg: US, GB.... default "US"    
          
    //Option param        
    c_date: STRING datetime now with format Y-m-d H:i:s, Default value equal server datetime
    c_limit: INTEGER default API Config
    c_offset: INTEGER default API Config
}
```
* `Basic API URL`: URL_API/v{VERSION/{NAME_OF_METHOD}/ with {VERSION} = Integer, {NAME_OF_METHOD} = String. 

`Eg: https://www.api.xxx.com/v1/getTopCoupons/`

* `Result Structure`:
```javascript
{
    code: 0,
    msg: 'Main message',   
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
* `Define Result Structure`:
    * code: Code = 0: Success, Code <> 0: Error
    * msg: Message
    * data: Result data
    * data_error: Result for dev

##Oauth

##Users

##Stores

##Coupons

###Get top coupons

```
URL: http://localhost:3002/v1/coupons/getTopCoupons/
Params options:
    c_limit
    c_offset
```

**Example**
```
URL: http://mobileapp.mccorp.co.com/v1/coupons/getTopCoupons/
Params = {
    access_key: '1439190122831', 
    client_id: '55a2af2a-b380-451b-a585-612a61af48f5',
    access_code: '5f50d27d603a0c09e2c53c35864ddcb42ac735c6d4fa369157a6f95e6380c7e8', 
    c_limit: 10,
    c_offset: 0
}
```
