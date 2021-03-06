# API LOYALTY CLIENT - CMC

This is API DOCUMENT LOYALTY CLIENT

**Version:** 1.0.2

**x-scope:** client

**base-url:** http://183.91.11.56:5000/

Table of contents

1. [Tips](#tips)
1. [User](#user)
1. [Category](#category)
1. [Article](#article)
1. [Offer](#offer)
1. [Asset](#asset)
1. [Exchange](#exchange)
1. [Wishlist](#wishlist)
1. [Order](#order)
1. [Location](#location)
1. [Ranking](#ranking)
1. [Partner](#partner)
1. [Service](#service) 
1. [Navigation](#navigation)
1. [Brand](#brand)

# Tips
## STATUS CODE
| Code | Description |
| ---- | ----------- |
| 200 | oke |
| 201 | oke |
| 204 | oke |
| 401 |  Unauthorized   |
| 400 |  Bad request   |
| 403 | Forbidden |
| 404 |  Not found   |
| 500 |  Server error   |
| 502 |  Database Error   |
| 503 | Unavailable |

## FILTER

=: Equals

_ne: Not equals

_lt: Lower than

_gt: Greater than

_lte: Lower than or equal to

_gte: Greater than or equal to

_in: Include in array

_contains: Contains

_containss: Contains case sensitive

_in: Matches any value in the array of values

_nin: Doesn't match any value in the array of values

*Examples*

Find users having John as first name.

GET /users?firstname=Tuan

Find products having a price equal or greater than 3.

GET /products?price_gte=3

Find multiple news with id 3, 6, 8 GET /article/find?id_in=3&id_in=6&id_in=8

or data

GET /article/find?id_or=3&id_or=6


## Sort

Sort according to a specific field.

*Example*

Sort user by email.

ASC: GET /user?_sort=email:ASC

DESC: GET /user?_sort=email:DESC

## Limit

Limit the size of the returned results.

*Example*

Limit the result length to 30.

GET /users?_limit=30

## Start

Skip a specific number of entries (especially useful for pagination).

*Example*

Get the second page of results.

GET /users?_start=10&_limit=10 

## Like

*Example*

GET /users?email_like=%hoangnn% 

## Or

*Example*

GET /category/find?or_title=Category&or_status=0

## contains (include search array)

*Example*

GET /config/find?brands_contains=[13]

## Filter Json Object

GET /product/find?image.imageThumb=link

... 

# USER

## /USER/OTP

**Method:** POST

**Summary:** {{url}}/api/user/otp

**Description:** API otp

**HTTP Request**
`***POST*** /user/otp` 

**Parameters**

*otp Actived User*

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| name | body |  | Yes |  |
| phone | body |  | Yes |  |
| email | body |  | Yes |  |

*otp Forgot Password*

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| type | body | otpUserForgot | Yes |  |
| phone | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/LOGIN

**Method:** POST

**Summary:** {{url}}/api/user/login

**Description:** API login

**HTTP Request**
`***POST*** /user/login` 

**Parameters**

| Name | Located in | Description | Required | Type | Default |
| ---- | ---------- | ----------- | -------- | ---- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string | client |
| account | body |  | Yes |  | 1234567899 |
| password | body |  | Yes |  |123456 |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/SIGHUP

**Method:** POST

**Summary:** {{url}}/api/user/sighup

**Description:** API Sighup

**HTTP Request**
`***POST*** /user/sighup` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| firstname | body |  | Yes | string |
| lastname | body |  | No | string |
| phone | body |  | Yes | string |
| email | body |  | No | string |
| password | body |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/LOGOUT

**Method:** POST

**Summary:** {{url}}/api/user/logout

**Description:** API logout

**HTTP Request**
`***POST*** /user/logout` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/PROFILE

**Method:** GET

**Summary:** {{url}}/api/user/profile

**Description:** API profile

**HTTP Request**
`***GET*** /user/profile` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/MODIFY

**Method:** PUT

**Summary:** {{url}}/api/user/modify

**Description:** API modify

**HTTP Request**
`***PUT*** /user/modify` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| id | body |  | Yes |  |
| firstname | body |  | Yes | string |
| password | body |  | No | string |
| phone | body |  | Yes | string |
| confirm | body |  | No | string |
| new_password | body |  | No | string |
| email | body |  | Yes | string |
| lastname | body |  | No | string |
| gender | body | Giới tính người dùng với 0 là nữ và 1 là nam | No | number |
| birthday | body | Ngày sinh của người dùng: 16/4/1991 | No | string |
| avatar | body | Ảnh đại diện người dùng lấy từ API upload | No | object |
| info | body | Thông tin location, address... | No | object |
| type | body | Kiểu người dùng enum(1,2,3,4,5) | No | enum |
| brand_id | body |  | No | number |
| rank_id | body |  | No | number |
| category_id | body |  | No | number |
| group_id | body |  | No | number |
| role_id | body |  | No | number |
| rules | body | Luật ... Kiểu dữ liệu: [1,2,3,4] | No | array |
| rights | body | Quyền Kiểu dữ liệu: [1,2,3,4] | No | array |
 
**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/RESET

**Method:** POST 

**Summary:** {{url}}/api/user/reset

**Description:** API reset Password

**HTTP Request**
`***POST*** /user/reset` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| password | body |  | Yes |  |
| confirm | body |  | Yes |  |
| reset_password_token | body |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/CHANGEPASSWORD

**Method:** POST 

**Summary:** {{url}}/api/user/changePassword

**Description:** API change password

**HTTP Request**
`***POST*** /user/changePassword` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| password | body | Mật khẩu hiện tại | Yes | string |
| new_password | body | Mật khẩu mới | Yes | string |
| confirm | body | Mật khẩu giống mất khẩu mới | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |


## /USER/EXTEND

**Method:** POST 

**Summary:** {{url}}/api/user/extend

**Description:** API extend token

**HTTP Request**
`***POST*** /user/extend` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/QRCODE

**Method:** GET

**Summary:** {{url}}/api/user/qrcode

**Description:** API qrcode

**HTTP Request**
`***GET*** /user/qrcode` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /USER/SCANNER

**Method:** GET

**Summary:** {{url}}/api/user/scanner

**Description:** API user scanner

Với type = null sẽ trả ra cả barcode và qrcode

**HTTP Request**
`***GET*** /user/scanner` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| type | query | Ex: type=barcode or type=qrcode | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# CATEGORY
## /CATEGORY/COUNT
**Method:** GET

**Summary:** {{url}}/api/category/count

**Description:** API count

**HTTP Request**
`***GET*** /category/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /CATEGORY/FIND
**Method:** GET

**Summary:** {{url}}/api/category/find

**Description:** API get list category

**HTTP Request**
`***GET*** /category/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /CATEGORY/FINDONE/1
**Method:** GET

**Summary:** {{url}}/api/category/findOne/1

**Description:** API detail category

**HTTP Request**
`***GET*** /category/findOne/2` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# ARTICLE
## /ARTICLE/COUNT
**Method:** GET

**Summary:** {{url}}/api/article/count

**Description:** API count

**HTTP Request**
`***GET*** /article/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ARTICLE/FIND
**Method:** GET

**Summary:** {{url}}/api/article/find

**Description:** API get list article

**HTTP Request**
`***GET*** /article/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ARTICLE/FINDONE/1
**Method:** GET

**Summary:** {{url}}/api/article/findOne/1

**Description:** API detail article

**HTTP Request**
`***GET*** /article/findOne/2` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# OFFER

( VOUCHER - COUPON - GIFT )

## /OFFER/COUNT
**Method:** GET

**Summary:** {{url}}/api/offer/count

**Description:** API count

**HTTP Request**
`***GET*** /offer/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/LIST
**Method:** GET

**Summary:** {{url}}/api/offer/list?_limit=2&_start=0

**Description:** API get list offer

**HTTP Request**
`***GET*** /offer/list` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| _limit | query |  | No | integer |
| _start | query |  | No | integer |
| x-scope | header |  | yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/DETAIL/1
**Method:** GET

**Summary:** {{url}}/api/offer/detail/1

**Description:** API detail offer

**HTTP Request**
`***GET*** /offer/detail/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/USE
**Method:** POST

**Summary:** {{url}}/api/offer/use

**Description:** API use offer

**HTTP Request**
`***POST*** /offer/use`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| program_id | body |  | Yes | string |
| reward_id | body |  | Yes | string |
| type | body | default: pos | No | string |
| code | body |  | No | string |
| partner_id | body |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/USEPOS
**Method:** POST

**Summary:** {{url}}/api/offer/usePos

**Description:** API usePos offer

**HTTP Request**
`***POST*** /offer/usePos`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code | body | REJF6LS2M2900191 (là code_sys của voucher) | Yes | string |
| partner_code | body | BBQ (là code của partner) | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/CHECKUSE
**Method:** POST

**Summary:** {{url}}/api/offer/checkUse

**Description:** API checkUse offer

**HTTP Request**
`***POST*** /offer/checkUse`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| program_id | body |  | Yes | string |
| reward_id | body |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/TOPUP
**Method:** POST

**Summary:** {{url}}/api/offer/topup

**Description:** API topup offer (nạp điểm)

Dùng mã code: E4824S3T9861239 để demo

**HTTP Request**
`***POST*** /offer/topup`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code_sys | body | ex: E4824S3T9861239 | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/SCANNER
**Method:** POST

**Summary:** {{url}}/api/offer/scanner

**Description:** API scanner offer

Dùng mã code: của reward

**HTTP Request**
`***POST*** /offer/scanner`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code | query | Là code_sys của reward | Yes | string |
| type | query | type=barcode or type=qrcode | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /OFFER/TRANSFER
**Method:** POST

**Summary:** {{url}}/api/offer/transfer

**Description:** API transfer offer

**HTTP Request**
`***POST*** /offer/transfer`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| point | body |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# ASSET
## /ASSET/COUNT
**Method:** GET

**Summary:** {{url}}/api/asset/count

**Description:** API count

**HTTP Request**
`***GET*** /asset/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ASSET/LIST
**Method:** GET

**Summary:** {{url}}/api/asset/list

**Description:** API get list asset

**HTTP Request**
`***GET*** /asset/list` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ASSET/CREATE
**Method:** POST

**Summary:** {{url}}/api/asset/create

**Description:** API create asset

**HTTP Request**
`***POST*** /asset/create` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| program_id | header |  | Yes | number |
| reward_id | header |  | Yes | number |
| brand_id | header |  | No | number |
| comment | header |  | No | string |
| note | header |  | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ASSET/USE/1
**Method:** PUT

**Summary:** {{url}}/api/asset/use/1

**Description:** API use asset

**HTTP Request**
`***PUT*** /asset/use/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# CAMPAIGN
## /CAMPAIGN/COUNT
**Method:** GET

**Summary:** {{url}}/api/campaign/count

**Description:** API count

**HTTP Request**
`***GET*** /campaign/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /CAMPAIGN/FIND
**Method:** GET

**Summary:** {{url}}/api/campaign/find

**Description:** API get list campaign

**HTTP Request**
`***GET*** /campaign/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /CAMPAIGN/FINDONE/1
**Method:** GET

**Summary:** {{url}}/api/campaign/findOne/1

**Description:** API detail campaign

**HTTP Request**
`***GET*** /campaign/findOne/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# EXCHANGE

## /EXCHANGE/COUNT
**Method:** GET

**Summary:** {{url}}/api/exchange/count

**Description:** API count

**HTTP Request**
`***GET*** /exchange/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /EXCHANGE/FIND
**Method:** GET

**Summary:** {{url}}/api/exchange/find

**Description:** API get list exchange

Type (Kiểu tương tác giao dịch)

Có các type:

0 - Hoạt động không ảnh hưởng tới điểm

1 - Nạp điểm

2 - Tiêu điểm

**HTTP Request**
`***GET*** /exchange/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /EXCHANGE/FINDONE/1
**Method:** GET

**Summary:** {{url}}/api/exchange/findOne/1

**Description:** API detail exchange

**HTTP Request**
`***GET*** /exchange/findOne/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /EXCHANGE/CREATE

**Method:** POST 

**Summary:** {{url}}/api/exchange/create

**Description:** Create exchange

**HTTP Request**
`***POST*** /exchange/create` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| Content-Type | header |  | Yes | string |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| title | header | Tiêu đề sự kiện tương tác, giao dịch | Yes | string |
| type | header | Kiểu tương tác giao dịch với: 0 - Hoạt động không ảnh hưởng tới điểm, 1 - Nạp điểm, 2 - Tiêu điểm | Yes | string |
| source | header | Nguồn phát sinh tương tác, giao dịch | Yes | string |
| amount | header | Giá trị giao dịch | No | string |
| point | header | Số điểm quy đổi | No | string |
| product | header | Thông tin sản phẩm có liên quan tới tương tác, giao dịch | No | string |
| campaign | header | Thông tin chiến dịch có liên quan tới tương tác, giao dịch | No | string |
| program | header | Thông tin chương trình có liên quan tới tương tác, giao dịch | No | string |
| data | header | Thông tin nội dung voucher, coupon có liên quan tới tương tác, giao dịch | No | string |
| description | header | Thông tin mô tả về sự kiện tương tác, giao dịch | No | string |
| note | header | Thông tin ghi chú về sự kiện tương tác, giao dịch | No | string |
| brand_id | header | Mã ID sở hữu giao dịch với mặc định 0 là của bất kỳ doanh nghiệp nào | Yes | string |
| status | header | Trạng thái của sự kiện, giao dịch với: 0 - Không có hiệu lực, 1 - Đang được kích hoạt, 2 - Đang chờ được phê duyệt, 3 - Đã được phê duyệt chấp thuận, 4 - Đã bị phê duyệt từ chối | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /EXCHANGE/findByPartner
**Method:** GET

**Summary:** {{url}}/api/exchange/findByPartner

**Description:** API get list exchange findByPartner

Type (Kiểu tương tác giao dịch)

Có các type:

0 - Hoạt động không ảnh hưởng tới điểm

1 - Nạp điểm

2 - Tiêu điểm

**HTTP Request**
`***GET*** /exchange/findByPartner` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| partner_code | query | Yes | string |
**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# WISHLIST
## /WISHLIST/COUNT
**Method:** GET

**Summary:** {{url}}/api/wishlist/count

**Description:** API count

**HTTP Request**
`***GET*** /wishlist/count` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /WISHLIST/FIND
**Method:** GET

**Summary:** {{url}}/api/wishlist/find

**Description:** API get list wishlist

**HTTP Request**
`***GET*** /wishlist/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /WISHLIST/FINDONE/1
**Method:** GET

**Summary:** {{url}}/api/wishlist/findOne/1

**Description:** API detail wishlist

**HTTP Request**
`***GET*** /wishlist/findOne/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# /TASK
## /TASK/FIND
**Method:** GET

**Summary:** {{url}}/api/task/find

**Description:** API get list task

**HTTP Request**
`***GET*** /task/find` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# ORDER
## /ORDER/QRCODE
**Method:** GET

**Summary:** {{url}}/api/order/qrcode?code=I2932FUOPFW&partner_id=1

**Description:** API get qrcode order

**HTTP Request**
`***GET*** /order/qrcode?code=I2932FUOPFW&partner_id=1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code | query | Ex: I2932FUOPFW | Yes | string |
| partner_id | query | Ex: 1 | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ORDER/DETAIL
**Method:** GET

**Summary:** {{url}}/api/order/detail?code=I2932FUOPFW&partner_id=1

**Description:** API get order detail

**HTTP Request**
`***GET*** /order/detail?code=I2932FUOPFW&partner_id=1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code | query | Ex: I2932FUOPFW | Yes | string |
| partner_id | query | Ex: 1 | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /ORDER/PRODUCT
**Method:** POST

**Summary:** {{url}}/api/order/product

**Description:** API sử dụng dịch vụ sẽ được tích điểm

**HTTP Request**
`***POST*** /order/product` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |
| code | body | Ex: Mã sản phẩm, hoặc mã đơn hàng | Yes | string |
| partner_code | body | Ex: Mã đối tác, có thể không có trên hệ thống | Yes | string |
| base_point | body | Ex: Điểm thưởng | Yes | string |
| total | body | Ex: Giá trị sản phẩm or đơn hàng | Yes | string |
| data | body | Ex: Dữ liệu sản phẩm or đơn hàng | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# LOCATION
## /LOCATION/LISTPROVINCE
**Method:** GET

**Summary:** {{url}}/api/location/listProvince

**Description:** API get listProvince

**HTTP Request**
`***GET*** /location/listProvince` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /LOCATION/LISTDISTRICT/01
**Method:** GET

**Summary:** {{url}}/api/location/listDistrict/01

**Description:** API get listDistrict

**HTTP Request**
`***GET*** /location/listDistrict/01` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

## /LOCATION/LISTWARD/001
**Method:** GET

**Summary:** {{url}}/api/location/listWard/001

**Description:** API get listWard

**HTTP Request**
`***GET*** /location/listWard/001` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# RANKING
## /RANKING/LIST
**Method:** GET

**Summary:** {{url}}/api/ranking/list

**Description:** API get ranking

**HTTP Request**
`***GET*** /ranking/list` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# Partner
## /PARTNER/DETAIL/1
**Method:** GET

**Summary:** {{url}}/api/partner/detail/1

**Description:** API get partner detail

**HTTP Request**
`***GET*** /api/partner/detail/1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# Service
## /SERVICE/CHECK
**Method:** GET

**Summary:** {{url}}/api/service/check

**Description:** API check service

**HTTP Request**
`***GET*** /api/service/check` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header | system | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# NAVIGATION
## /NAVIGATION/LIST
**Method:** GET

**Summary:** {{url}}/api/navigation/list?type=menu_portal

**Description:** API get navigation

type=menu_portal

**HTTP Request**
`***GET*** /navigation/list?type=menu_portal` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header |  | Yes | string |
| Authorization | header |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |

# BRAND
## /BRAND/DETAIL
**Method:** GET

**Summary:** {{url}}/api/brand/detail?alias=microsoft

**Description:** API get brand

**HTTP Request**
`***GET*** /brand/detail` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| x-scope | header | client | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | oke |
