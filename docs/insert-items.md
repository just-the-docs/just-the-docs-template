---
title: INSERT ITEMS
layout: default
nav_oder: 2
parent: API GET DROP POINTS
---

# INSERT ITEMS

## Description

- This API provides tools to be called by the Sender with the POST method. It has a simple header 
authorization. Added a new module field, detailing items that are for Last Mile or Devos. Once all the 
items have been manifested, those labels that correspond to this order which were sent in the 
pre-manifest and do not exist in this call, will be removed and deleted.
- The difference from the one already implemented is that INDITEX must include the drop point ID in the 
field named 'drop point'.

```bash
curl -X POST https://itx.alas-courier.com:9091/api/itxitems
```

##  Header 
- **APIKEY : APIKEY**

## Body example:
```json
[
    {
        "order_number": "431190381716",
        "box_reference": "43119038171600100036",
        "itx_code": "MOCK",
        "shipping_type": "3",
        "weight_in_grams": "670",
        "height_in_cms": "8",
        "width_in_cms": "37",
        "depth_in_cms": "39",
        "departure_date_utc": "20230316150022",
        "customer_name": "Emma",
        "customer_last_name": "Pedroza",
        "customer_address1": "C. Gran Vía 58",
        "customer_address2": "xx customer address 2 xx",
        "customer_city": "West palm",
        "customer_postal_code": "10443",
        "customer_province": "Attiki",
        "customer_country_iso": "GR",
        "phone_number1": "+306949566174",
        "phone_number2": "+306978689141",
        "email": "stratakirania@gmail.com",
        "remarks": "",
        "courier_code": "967256",
        "courier_description": "PACKMAN",
        "payment_type": "",
        "total_value": "34.9",
        "amount_pending": "",
        "currency_iso_code": "EUR",
        "preferred_language_iso": "el",
        "destinity_store": "",
        "drop_point": "65cb54e2c452662fc3bb0366",
        "drop_point_user": "",
        "defined_delivery_date": "",
        "defined_delivery_time": "00",
        "brand": "ZARA",
        "tracking_number": "",
        "source_warehouse": "ZARAGRATE",
        "courier_servicevcode": "ND",
        "package_type": "177",
        "customer_order_number": "52771027429",
        "district": "",
        "external_seller": "",
        "external_order_id": "",
        "dangerous_goods": false,
        "second_life": false,
        "origin_location_id_numeric": 9713,
        "free_field1": "",
        "drop_point_user_phone": "",
        "drop_point_user_email": "",
        "billing_company_numeric": 39,
        "municipality": "",
        "service_type_feature": "",
        "free_field2": "",
        "free_field3": "",
        "free_field4": "",
        "free_field5": "",
        "free_field6": "",
        "cnpj": "",
        "audit_cnpj": "",
        "audit_ie": "",
        "fiscal_note_key": "",
        "fiscal_note_serial_number": "",
        "fiscal_note_number": "",
        "fiscal_note_date": "",
        "fiscal_note_value": "",
        "module": 1
    }
]
```

## Body Format for INSERT ITEM'S

| **Order** | **Parameter**               | **Type**| **Length** | **Mandatory** |**Description**                                           |
|:---------:|:---------------------------:|:-------:|:------:|:---------:|:-----------------------------------------------------:|
| **1**     | order_number                | String  | 30     | YES       | Inditex Order Number                                  |
| **2**     | box_reference               | String  | 33     | YES       | Inditex Box Reference                                 |
| **3**     | itx _code                   | String  | 30     | YES       | Client code of the company that Courier               |
| **4**     | shipping_type               | String  | 5      | YES       | Shipping type. It comes from master                   |
| **5**     | weight_in_grams             | String  | 10     | YES       | Box weight in grams                                    |
| **6**     | depth_in_cms                | String  | 5      | NO        | Length of the package in Centimeters                   |
| **7**     | width_in_cms                | String  | 5      | NO        | Width of the package in Centimeter                     |
| **8**     | height_in_cms               | String  | 5      | NO        | Height of the package in Centimeter                    |
| **9**     | departure_date_utc          | String  | 14     | YES       | UTC time: yyyyMMddHH24mmss                             |
| **10**    | customer_name               | String  | 60     | YES       | Delivery client’s name                                 |
| **11**    | customer_last_name          | String  | 60     | YES       | Delivery client’s surname                              |
| **12**    | customer_address1           | String  | 150    | YES       | Delivery client’s address 1                            |
| **13**    | customer_address2           | String  | 150    | YES       | Delivery client’s address 2                            |
| **14**    | customer_city               | String  | 60     | YES       | Delivery client’s town                                 |
| **15**    | customer_postal_code        | String  | 15     | YES       | Delivery client’s postal code                          |
| **16**    | customer_province           | String  | 60     | YES       | Delivery client’s province                             |
| **17**    | customer_country_iso        | String  | 5      | YES       | ISO for delivery client’s country                      |
| **18**    | phone_number1               | String  | 60     | YES       | Delivery client’s phone number 1                       |
| **19**    | phone_number2               | String  | 60     | NO        | Delivery client’s phone number 2                       |
| **20**    | email                       | String  | 60     | YES       | Delivery client’s e-mail                               |
| **21**    | remarks                     | String  | 150    | NO        | Additional information of the address                 |
| **22**    | courier_code                | String  | 20     | YES       | Code for Courier identification in Inditex            |
| **23**    | courier_description         | String  | 100    | NO        | String for Courier identification in Inditex         |
| **24**    | payment_type                | String  | 5      | NO        | Payment method. It comes from master                   |
| **25**    | total_value                 | String  | 10     | NO        | Total Value                                           |
| **26**    | amount_pending              | String  | 10     | NO        | Amount to be charged in case of POD                    |
| **27**    | currency_iso_code           | String  | 5      | NO        | ISO Code for currency                                  |
| **28**    | preferred_language_iso      | String  | 5      | NO        | ISO Code for the customer language                     |
| **29**    | destinity_store             | String  | 20     | NO        | ID for bundle´s destiny store                          |
| **30**    | drop_point                  | String  | 30     | NO        | Drop Point id provided by ALAS                        |
| **31**    | drop_point_user             | String  | 60     | NO        | Drop point username                                    |
| **32**    | defined_delivery_date       | String  | 14     | NO        | Preferred delivery date                                |
| **33**    | defined_delivery_time            | String     | 30         | NO            | Preferred delivery time range                                   |
| **34**    | brand                           | String     | 50         | YES           | Brand that the bundle belongs to                                |
| **35**    | tracking_number                 | String     | 50         | YES           | Not applicable for labelling process                            |
| **36**    | source_warehouse                | String     | 50         | YES           | Source warehouse code                                          |
| **37**    | courier_service_code             | String     | 50         | NO            | Courier Service to ship the parcel                              |
| **38**    | package_type                    | String     | 5          | NO            | Package Type of the parcel                                      |
| **39**    | customer_order_number           | String     | 50         | YES           | Order number given to customer in eCommerce                    |
| **40**    | district                        | String     | 100        | NO            | Delivery client’s district                                      |
| **41**    | external_seller                 | String     | 50         | NO            | External seller code in case that the order has been sold by platform (TMALL) |
| **42**    | external_order_id               | String     | 50         | NO            | Order Number in the External Seller platform in case that the order has been sold by another platform |
| **43**    | dangerous_goods                 | Boolean    | -          | NO            | Flag to indicate if the box has dangerous goods (For Example value: true, false, null) |
| **44**    | second_life                     | Boolean    | -          | NO            | Flag to indicate if the order which belongs this box is requested to Second Life collection (For Example value: true, false, null) |
| **45**    | origin_location_id_numeric      | Integer    | 50         | NO            | ID for the origin location of the parcel, it comes from an Inditex master that will be provided to the courier if it’s needed |
| **46**    | free_field1                     | String     | 50         | NO            | Field available, currently unused                              |
| **47**    | drop_point_user_phone            | String     | 60         | NO            | Drop Point User Phone number                                   |
| **48**    | drop_point_user_email            | String     | 50         | NO            | Drop Point User e-mail address                                 |
| **49**    | Billing_company_numeric          | Integer    | 10         | NO            | Billing reference for the company                              |
| **50**    | municipality                    | String     | 50         | NO            | Delivery client’s municipality                                  |
| **51**    | service_type_feature            | String     | 50         | NO            | N/A                                                            |
| **52**    | free_field2                     | String     | 50         | NO            | Field available, currently unused                              |
| **53**    | free_field3                     | String     | 50         | NO            | Field available, currently unused                              |
| **54**    | free_field4                     | String     | 50         | NO            | Field available, currently unused                              |
| **55**    | free_field5                     | String     | 50         | NO            | Field available, currently unused                              |
| **56**    | free_field6                     | String     | 50         | NO            | Field available, currently unused                              |
| **57**    | cnpj                            | String     | 50         | NO            | CNPJ                                                           |
| **58**    | audit_cnpj                      | String     | 50         | NO            | AuditCNPJ                                                       |
| **59**    | audit_ie                    | String     | 50         | NO            | AuditIE                                               |
| **60**    | fiscal_note_key             | String     | 50         | NO            | FiscalNoteKey                                         |
| **61**    | fiscal_note_serial_number   | String     | 50         | NO            | FiscalNoteSerialNumber                                |
| **62**    | fiscal_note_number          | String     | 50         | NO            | FiscalNoteNumber                                      |
| **63**    | fiscal_note_date            | String     | 50         | NO            | FiscalNoteDate                                        |
| **64**    | Fiscal_note_value           | String     | 50         | NO            | FiscalNoteValue                                       |
| **65**    | module                      | Integer    | 1          | NO            | If module is 1 it is last mile, 2 is devo. If the field is empty, it is taken as last mile |
