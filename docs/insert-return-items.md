---
title: INSERT RETURN ITEMS
layout: default
nav_oder: 3
parent: API GET DROP POINTS
---

# INSERT RETURN ITEMS

## Description

- This API provides tools to be called by the sender with the POST method. It has a simple header 
authorization. The purpose of this tool is to manifest the return packages (DEVOS) for a pre-designated 
courier, which must be picked up by the same Courier from the customer's Address defined in the 
mentioned information. **This endpoint only receives requesters in array format.**
- The difference from the one already implemented is that INDITEX must include the drop point ID in the 
field named 'drop point'.

```bash
curl -X POST https://itx-returns.alas-courier.com:9091/api/itxitems
```

##  Header 
- **APIKEY : APIKEY**

## Body example:
```json
[
    {
        "order_number": "8657143709877666000100037",
        "customer_order_number": "431190381725620",
        "return_identifier": "43119038112312333075",
        "return_box_identifier": "571431190381725",
        "return_request_date": "20230727124520",
        "pickup_day": "20230727",
        "pickup_time": "1745",
        "customer_return_request_type": "type1",
        "comments": "comment",
        "brand": "brand",
        "customer_account_code": "15687",
        "pre_printed": "true",
        "customer_name": "sandra",
        "customer_surname": "pedroza",
        "customer_address1": "direccion calle 1",
        "customer_address2": "direccion calle 2",
        "customer_city": "ciudad",
        "customer_zip_code": "49870",
        "customer_province": "provincia",
        "customer_country": "ES",
        "customer_district": "distrito",
        "customer_municipality": "municipalidad",
        "customer_phone_number1": "+985647515687",
        "customer_phone_number2": "+985647515687",
        "customer_email": "mail@mail.com",
        "customer_pickup_location": "tower",
        "customer_pickup_location_identifier": "tower25",
        "delivery_name": "miguel",
        "delivery_surname": "cruz",
        "delivery_address1": "direccion calle 1",
        "delivery_address2": "direccion calle 2",
        "delivery_city": "city",
        "delivery_zip_code": "658412",
        "delivery_province": "provinica",
        "delivery_country": "ES",
        "delivery_district": "distrito",
        "delivery_municipality": "municipalidad",
        "delivery_phone_number1": "+8985647515756",
        "delivery_phone_number2": "+885647515756",
        "delivery_email": "mail@mail.com",
        "delivery_store_id_delivery": "warehouse",
        "courier_code": "12585",
        "tracking_number": "12341456252246",
        "courier_service_code": 3,
        "billing_company": 7,
        "drop_point": "",
        "free_field2": "",
        "free_field3": "",
        "free_field4": "",
        "free_field5": "",
        "free_field6": "",
        "free_field7": "",
        "free_field8": "",
        "free_field9": "",
        "free_field10": ""
    },
    {
        "order_number": "8657143709877666000100038",
        "customer_order_number": "431190381725621",
        "return_identifier": "43119038112312333077",
        "return_box_identifier": "571431190381745",
        "return_request_date": "20230727124520",
        "pickup_day": "20230727",
        "pickup_time": "1745",
        "customer_return_request_type": "type1",
        "comments": "comment",
        "brand": "brand",
        "customer_account_code": "15687",
        "pre_printed": "true",
        "customer_name": "sandra",
        "customer_surname": "pedroza",
        "customer_address1": "direccion calle 1",
        "customer_address2": "direccion calle 2",
        "customer_city": "ciudad",
        "customer_zip_code": "49870",
        "customer_province": "provincia",
        "customer_country": "ES",
        "customer_district": "distrito",
        "customer_municipality": "municipalidad",
        "customer_phone_number1": "+985647515687",
        "customer_phone_number2": "+985647515687",
        "customer_email": "mail@mail.com",
        "customer_pickup_location": "tower",
        "customer_pickup_location_identifier": "tower25",
        "delivery_name": "miguel",
        "delivery_surname": "cruz",
        "delivery_address1": "direccion calle 1",
        "delivery_address2": "direccion calle 2",
        "delivery_city": "city",
        "delivery_zip_code": "658412",
        "delivery_province": "provinica",
        "delivery_country": "ES",
        "delivery_district": "distrito",
        "delivery_municipality": "municipalidad",
        "delivery_phone_number1": "+8985647515756",
        "delivery_phone_number2": "+885647515756",
        "delivery_email": "mail@mail.com",
        "delivery_store_id_delivery": "warehouse",
        "courier_code": "12585",
        "courier_description": "desc",
        "tracking_number": "1234125755224",
        "courier_service_code": 3,
        "billing_company": 7,
        "drop_point": "",
        "free_field2": "",
        "free_field3": "",
        "free_field4": "",
        "free_field5": "",
        "free_field6": "",
        "free_field7": "",
        "free_field8": "",
        "free_field9": "",
        "free_field10": ""
    }
]
```

# Response Status


### Status 200:
- **Message:** “Total Items Received: “X”. At the end of the insertion, a manifest email will be sent.”.

### Status 400:
- This items were not processed correctly, please check the fields.

### Status 401:
- Unauthorized.

### Status 403:
- forbidden

### Status 500
- Internal Server Error, Check the fields structure.

# Body Format for INSERT ITEM'S

| **Order** | **Parameter**                | **Type**   | **Length** | **Mandatory** | **Description**                                          |
|:---------:|:----------------------------:|:----------:|:----------:|:-------------:|:--------------------------------------------------------:|
| **1**     | order_number                 | String     | 25         | YES           | Inditex Order Number                                     |
| **2**     | customer_order_number        | String     | 15         | NO            | Order number given to customer in eCommerce. It could be different than field Order Number |
| **3**     | return_identifier            | String     | 20         | YES           | Inditex internal identifier for the return               |
| **4**     | return_box_identifier        | String     | 15         | YES           | Inditex internal box identifier. This code is unique for each box or label manifested and it must be used to return tracking Information by the courier. |
| **5**     | return_request_date           | String     | 16         | YES           | Date when the return was requested to Inditex. The format will be YYYYMMDDhh24mmss |
| **6**     | pickup_day                    | String     | 16         | NO            | Pick-up hour requested by the customer in case of home pick-up |
| **7**     | pickup_time                   | String     | 20         | NO            | Pick-up hour requested by the customer in case of home pick-up |
| **8**     | customer_return_request_type  | String     | 20         | YES           | Type of return chosen by the customer. It comes from a master table |
| **9**     | comments                      | String     | 20         | NO            | Customer comments regarding this return                  |
| **10**    | brand                         | String     | 20         | YES           | Brand identifier for this return                           |
| **11**    | customer_account_code         | String     | 20         | YES           | Client code of the company that Courier with be invoicing  |
| **12**    | pre_printed                   | Boolean    | -          | YES           | Flag to indicate if this label is a pre-printed label so it could be sent or not |
| **13**    | customer_name                 | String     | 60         | YES           | Customer name for return’s consignee                       |
| **14**    | customer_surname              | String     | 60         | NO            | Customer surname for return’s consignee                    |
| **15**    | customer_address1             | String     | 150        | YES           | Pick-up address line 1                                     |
| **16**    | customer_address2             | String     | 150        | NO            | Pick-up address line 2                                     |
| **17**    | customer_city                 | String     | 5          | YES           | Pick-up city                                              |
| **18**    | customer_zip_code             | String     | 60         | YES           | Pick-up zip code                                          |
| **19**    | customer_province             | String     | 60         | YES           | Pick-up province/state                                    |
| **20**    | customer_country              | String     | 60         | YES           | ISO code for the pick-up country                           |
| **21**    | customer_district              | String     | 150        | NO            | Pick-up address district (only MX)                         |
| **22**    | customer_municipality          | String     | 20         | NO            | Pick-up address municipality                               |
| **23**    | customer_phone_number1         | String     | 100        | YES           | Customer’s phone number 1                                  |
| **24**    | customer_phone_number2         | String     | 5          | NO            | Customer’s phone number 2                                  |
| **25**    | customer_email                 | String     | 10         | YES           | Customer’s email address                                   |
| **26**    | customer_pickup_location       | String     | 10         | NO            | Identifier for the location where the return request should be picked-up (e.g. packstation, drop-off point…) |
| **27**    | customer_pickup_location_identifier | String  | 5          | NO            | Code given by the customer for delivery location identification (e.g. packstation, drop-off point…) |
| **28**    | delivery_name                  | String     | 60         | YES           | Delivery destination name                                  |
| **29**    | delivery_surname               | String     | 60         | YES           | Delivery destination surname                               |
| **30**    | delivery_address1              | String     | 150        | YES           | Pick-up address line 1                                     |
| **31**    | delivery_address2              | String     | 150        | NO            | Pick-up address line 2                                     |
| **32**    | delivery_city                  | String     | 60         | NO            | Delivery city                                             |
| **33**    | delivery_zip_code              | String     | 15         | YES           | Delivery zip code                                         |
| **34**    | delivery_province              | String     | 60         | YES           | Delivery province/state                                   |
| **35**    | delivery_country               | String     | 5          | YES           | ISO code for the delivery country                           |
| **36**    | delivery_district              | String     | 80         | NO            | Delivery address district (only MX)                        |
| **37**    | delivery_municipality          | String     | 80         | NO            | Delivery address municipality                              |
| **38**    | delivery_phone_number1         | String     | 60         | YES           | Delivery phone number 1                                    |
| **39**    | delivery_phone_number2         | String     | 60         | NO            | Delivery phone number 2                                    |
| **40**    | delivery_email                 | String     | 60         | YES           | Delivery email address                                     |
| **41**    | delivery_store_id_delivery     | Integer    | 10         | NO            | Inditex Internal store ID for delivery the return parcel if the return would be delivered to a store |
| **42**    | courier_code                   | String     | 20         | YES           | Code for Courier identification in Inditex               |
| **43**    | courier_description            | String     | 100        | NO            | String for Courier identification in Inditex              |
| **44**    | tracking_number                | String     | 50         | NO            | Courier Box Reference                                    |
| **45**    | courier_service_code           | String     | 50         | YES           | Courier Service to ship the parcel                         |
| **46**    | billing_company                | Integer    | 10         | NO            | Billing company to which invoices should be directed      |
| **47**    | drop_point                     | String     | 30         | NO            | Drop Point id provided by ALAS                             |
| **48**    | free_field2                    | String     | 50         | NO            | Spare Field 2                                            |
| **49**    | free_field3                    | String     | 50         | NO            | Spare Field 3                                            |
| **50**    | free_field4                    | String     | 50         | NO            | Spare Field 4                                            |
| **51**    | free_field5                    | String     | 50         | NO            | Spare Field 5                                            |
| **52**    | free_field6                    | String     | 50         | NO            | Spare Field 6                                            |
| **53**    | free_field7                    | String     | 50         | NO            | Spare Field 7                                            |
| **54**    | free_field8                    | String     | 50         | NO            | Spare Field 8                                            |
| **55**    | free_field9                    | String     | 50         | NO            | Spare Field 9                                            |
| **56**    | free_field10                   | String     | 50         | NO            | Spare Field 10                                           |
