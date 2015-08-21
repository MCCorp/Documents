#Graph API

`Graph API for third party`

##API Define
* `Result`: JSON
* `Method`: POST
* `Version`: v1
* `Params`: 
```javascript
{
    //Require params for all request
    client_id: {STRING} Id app
    client_secret: {STRING} Secret key
    c_location: {STRING} Country code eg: US, GB.... default "US". US: MostCoupon, GB: DiscountVoucher
    c_date: {STRING} datetime now with format Y-m-d H:i:s, Default value equal server datetime    
              
    //Option params
    c_domain: {STRING} VALUE in ['http://www.mostcoupon.com', 'http://www.discountsvoucher.co.uk']. Use this info for send email when user register, lost password...
    c_limit: {INTEGER} default API Config. - SQL Limit
    c_offset: {INTEGER} default API Config - SQL Offset
}
```
* `Basic API URL`: URL_API/v{VERSION/{NAME_OF_METHOD}/ with {VERSION} = Integer, {NAME_OF_METHOD} = String. 

**For DEV:** Eg: http://mobileapp.mccorp.co.com/v1/getTopCoupons/

**For PRO:** Send later

* `Result Structure`:
```javascript
{
    code: 0,
    msg: 'Result message',   
    data: {Array|Object}
    data_error : ....
}
```
* `Define Result Structure`:
    * code: Code = 0: Success, Code <> 0: Error
    * msg: Message
    * data: Result data
    * data_error: Result for dev

##Users

###Login

```
URL: http://mobileapp.mccorp.co.com/v1/users/login/
Params:
    email: {STRING}
    password: {STRING}
    
Success result:    
{
    code : 0,
    data: {OBJECT} //Object user info
}
```

##Stores

##Home APP

###Top coupons of best store

```
URL: http://mobileapp.mccorp.co.com/v1/coupons/getTopCoupons/
Params options:
    c_location
    c_date
    c_limit
    c_offset
```

**Example**
```
URL: http://mobileapp.mccorp.co.com/v1/coupons/getTopCoupons/
Params = {
    client_secret: 'CLIENT_SECRET', 
    client_id: 'CLIENT_ID',    
    c_location: 'US',
    c_date: '2015-08-15 00:00:00'
    c_limit: 10,
    c_offset: 0
}

Success Result:
{
    code: 0,
    data: {Array}
}
```

###The shop/Daily deals

```
URL: http://mobileapp.mccorp.co.com/v1/coupons/getTopCoupons/
Params options:
    c_location
    c_date
    c_limit
    c_offset
```

**Example**
```
URL: http://mobileapp.mccorp.co.com/v1/deals/dailyDeals/
Params = {
    client_secret: 'CLIENT_SECRET', 
    client_id: 'CLIENT_ID',    
    c_location: 'US'
    c_date: '2015-08-15 00:00:00'
    c_limit: 10,
    c_offset: 0
}

Success Result:
{
    code: 0,
    data: {
        deals: {Array},
        totals: {Integer}
    }
}
```
