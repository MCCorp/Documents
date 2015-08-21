#Graph API

`Graph API for third party`

##API Define
* `URL DEV` : http://mobileapp.mccorp.co.com/
* `URL PRO` : Send later when mobile app completed
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
 
Example: http://mobileapp.mccorp.co.com/v1/getTopCoupons/

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

**Example**
```
URL: http://mobileapp.mccorp.co.com/v1/users/login/
Params = {
    client_secret: 'CLIENT_SECRET', 
    client_id: 'CLIENT_ID',    
    email: 'demo@gmail.com',
    password: 'demo_password'    
}

Success Result:
{
    code: 0,
    data: {
        userId: "55156ec8-3f48-45c0-a503-6bb761af48f5",
        fullName: "Demo Full Name",
        email: "demo@gmail.com",
        avatar: "https://s3-us-west-2.amazonaws.com/dev.mostcoupon.com/55156ec8-3f48-45c0-a503-6bb761af48f5-avatar",                
        accessToken: "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJleHBpcmVzX2luIjoxNDQwMTQyNzA1MDE3LCJ1c2VySWQiOiI1NTE1NmVjOC0zZjQ4LTQ1YzAtYTUwMy02YmI3NjFhZjQ4ZjUiLCJlbWFpbCI6InB0bGV2YW5AZ21haWwuY29tIn0.5XZYqlVxLnfzSVPBqHy6opNtEAihQSjodLD9TZM1tI0Cfok9BP9f8ToeG5c0JoL-uMQzVNqNaucGdr4K4PZ7sg",
        expiresIn: 1440142705017
    }
}
```

##Stores

##Home APP

###Top coupons of best store

```
URL: http://mobileapp.mccorp.co.com/v1/coupons/getTopCoupons/
Params options:    
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
