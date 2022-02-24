# Tnumber Loyalty & Rewards


Get reward points from local stores or online stores every time you shop. For more info visit: 

Single app to track and manage all your reward points in one place.

`config.ru` is a minimal Rack configuration for unicorn.

`run-tests.sh` runs a simplistic test and generates the API
documentation below.

It uses `run-curl-tests.rb` which runs each command defined in
`commands.yml`.

## Endpoints

    https://stage-retail.tnumber.co

## Authentication(Headers)

    key:<YOUR-API-KEY>

## Health Check

    {{Base_URL}}/merchant/health

# REST API

The REST API to the example app is described below.

## Health Check

### Request

`GET /health`

    curl --location --request GET 'https://stage-retail.tnumber.co/merchant/health' \--header 'key: <your api key here>'

### Headers

    key: <api key>

### Response

    {
         "message":"Healthy",
         "status":true
    }

## User Profile

### Request

`GET /userProfile/<user_phone_number>`

    curl --location --request GET 'https://stage-retail.tnumber.co/merchant/userProfile/<user_phone_number>' --header 'key: <your api key here>'

### Headers

    key: <api key>

### Params

    /user_phone_number

### Response

    {
        "message": "Successfully fetched the details.",
        "status": true,
        "data": {
            "_id": "61a8774ec23888abe2e9d8eb",
            "is_active": true,
            "member_since": "2021-12-02T07:35:42.076Z",
            "phone_number": "9958808464",
            "dob": "1997-08-15T00:00:00.000Z",
            "gender": "m",
            "name": "Jogn G",
            "referral_code": "aOPXh72147",
            "image_initials": "JG"
    }
}

## Join Store Membership

### Request

`POST /joinMembership`

    curl --location --request POST 'https://stage-retail.tnumber.co/merchant/joinMembership' --header 'key: U2FsdGVkX18Fno4Ivsdl7XOmbjiDqTVBwTzVQU/qNd8xl2Fu4mBqvZWqwMLH/+n+' --header 'Content-Type: application/json' --data-raw '
    {
        "phone_number": "9962472113",
        "name": "John Dow",
        "dob": "2018-12-19"
    }'

### Headers

    key: <api key>

### Body

`Content-Type: application/json`
    
    {
        "phone_number": "9962472113",
        "name": "John Dow",
        "dob": "2018-12-19"
    }

### Response

    {
        "message": "Successfully Joined Membership.",
        "status": true
    }

## User Reward History

### Request

`GET /rewardHistory/<user_phone_number>`

    curl --location --request GET 'https://stage-retail.tnumber.co/merchant/rewardHistory/9958808464' --header 'key: U2FsdGVkX19cnVpnMAIgNuC0/zwA1wUj594t6DFQSG/GltYgQtSel2BaZW2VNTla'

### Headers

    key: <api key>

### Params

    /user_phone_number


### Response

    {
        "message": "Successfully Fetched Data",
        "status": true,
        "data": [
            {
                "_id": "61f517375ce3e11c3ab571a5",
                "phone_number": "9958808464",
                "total_visits": 5,
                "user_id": "61a8774ec23888abe2e9d8eb",
                "location": null,
                "store_id": "61f4ea015ce3e11c3ab56cc5",
                "added_by": null,
                "membership_id": "61f517375ce3e11c3ab571a5",
                "is_active": true,
                "member_since": "2022-01-29T10:30:15.901Z",
                "member_type": "new",
                "store": {
                    "city": "Hyderabad",
                    "name": "Meenakshi Store",
                    "logo_url": "https://tnumber-retail.s3.ap-south-1.amazonaws.com/undefined/1644814081000Minakshi.png",
                    "category_id": 13
                },
                "category": {
                    "_id": "61d52dcf4086f58fcd166e37",
                    "is_active": true,
                    "sub_category": [
                        {
                            "_id": "6216172f1b3254778d66b1fe",
                            "sub_category_id": 130,
                            "name": "Grocery",
                            "is_active": true
                        },
                        {
                            "_id": "6216172f1b3254778d66b1ff",
                            "sub_category_id": 131,
                            "name": "Household",
                            "is_active": true
                        },
                        {
                            "_id": "6216172f1b3254778d66b200",
                            "sub_category_id": 132,
                            "name": "Kitchen",
                            "is_active": true
                        },
                        {
                            "_id": "6216172f1b3254778d66b201",
                            "sub_category_id": 133,
                            "name": "Automobile",
                            "is_active": true
                        },
                        {
                            "_id": "6216172f1b3254778d66b202",
                            "sub_category_id": 134,
                            "name": "Pet & Garden",
                            "is_active": true
                        }
                    ],
                    "category_name": "Shopping",
                    "category_id": 13,
                    "__v": 258
                },
                "available": 310,
                "total": 360
            }
        ]
    }


