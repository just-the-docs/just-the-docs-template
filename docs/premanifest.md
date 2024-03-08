---
title: PRE-MANIFEST
layout: default
nav_oder: 1
parent: API GET DROP POINTS
---

# PRE-MANIFEST

## Description

- This Endpoint provides tools to be called by ITX with POST method. It has a simple header 
authorization. To use these endpoint, the IP’s of the caller must be on a White list. (Please provide the 
IP addresses ITX will use to call).
- This endpoint is responsible for returning the necessary labels to print based on your request. 
- The request must be in array format.
- The difference from the one already implemented is that INDITEX must include the drop point ID in the 
field named 'drop point'.

```bash
curl -X POST https://itxlabels.alas-courier.com:9091/api/itxpremanifest
```

##  Header 
- **APIKEY : APIKEY**

## Body example:

```json
{
    "id_bulk": "1000501001",
    "items": [
        {
            "box_reference": "43709877666000100037",
            "order_number": "431190381725",
            "itx_code": "MOCK",
            "shipping_type": "3",
            "weight_in_grams": "670",
            "height_in_cms": "8",
            "width_in_cms": "37",
            "depth_in_cms": "39",
            "departure_date_utc": "20230316150022",
            "customer_name": "maria",
            "customer_last_name": "perez",
            "customer_address1": "Avenida de los Arces 12",
            "customer_address2": " Portal A - 4º A",
            "customer_city": "ciudad",
            "customer_postal_code": "14257",
            "customer_province": "provincia",
            "customer_country_iso": "ES",
            "phone_number1": "+306981903691",
            "phone_number2": "",
            "email": "strat@gmail.com",
            "remarks": "",
            "courier_code": "967256",
            "courier_description": "courier",
            "payment_type": "",
            "total_value": "34.9",
            "amount_pending": "",
            "currency_iso_code": "EUR",
            "preferred_language_iso": "ES",
            "destinity_store": "",
            "drop_point": "65cb54e2c452662fc3bb0366",
            "drop_point_user": "",
            "defined_delivery_date": "",
            "defined_delivery_time": "00",
            "brand": "ZARA",
            "source_warehouse": "ZARAGRATE",
            "courier_service_code": "ND",
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
            "cnpj": "00746848927",
            "audit_cnpj": "02952485006341",
            "audit_ie": "407686198110",
            "fiscal_note_key": "35230402952485006341550060041763591958236401",
            "fiscal_note_serial_number": "6",
            "fiscal_note_number": "4176359",
            "fiscal_note_date": "26042023",
            "fiscal_note_value": "2281.0",
            "module": 1,
            "sender_address1": "Address1",
            "sender_address2": "Address2",
            "sender_address3": "Address3"
        },
        {
            "box_reference": "43709975387600100096",
            "order_number": "431190381726",
            "itx_code": "MOCK",
            "shipping_type": "3",
            "weight_in_grams": "670",
            "height_in_cms": "8",
            "width_in_cms": "37",
            "depth_in_cms": "39",
            "departure_date_utc": "20230316150022",
            "customer_name": "juan",
            "customer_last_name": "migues",
            "customer_address1": "Calle de Carmen Rico Godoy 72 ",
            "customer_address2": "apto 3",
            "customer_city": "ciudad",
            "customer_postal_code": "142 34",
            "customer_province": "provincia",
            "customer_country_iso": "ES",
            "phone_number1": "+306981903691",
            "phone_number2": "",
            "email": "strat@gmail.com",
            "remarks": "",
            "courier_code": "967256",
            "courier_description": "courier",
            "payment_type": "",
            "total_value": "34.9",
            "amount_pending": "",
            "currency_iso_code": "EUR",
            "preferred_language_iso": "ES",
            "destinity_store": "",
            "drop_point": "65cb54e2c452662fc3bb0366",
            "drop_point_user": "",
            "defined_delivery_date": "",
            "defined_delivery_time": "00",
            "brand": "ZARA",
            "source_warehouse": "ZARAGRATE",
            "courier_service_code": "ND",
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
            "cnpj": "00746848927",
            "audit_cnpj": "02952485006341",
            "audit_ie": "407686198110",
            "fiscal_note_key": "35230402952485006341550060041763591958236401",
            "fiscal_note_serial_number": "6",
            "fiscal_note_number": "4176359",
            "fiscal_note_date": "26042023",
            "fiscal_note_value": "2281.0",
            "module": 1,
            "sender_address1": "Address1",
            "sender_address2": "Address2",
            "sender_address3": "Address3"
        }
    ]
}
```

## Response Status

### Status 200:
- Message: “success”.
- **The answer of the label is in base64.**

### Response:
```json
[
    {
        "box_reference": "xxxxxxxxxxxxxx",
        "tracking_number": "xxxxxxxxxxxxxx",
        "labelBase64": "JVBERi0xLjQKJdPr6e..... zIKJSVFT0Y="
    },
    {
        "box_reference": "xxxxxxxxxxxxxx",
        "tracking_number": "xxxxxxxxxxxxxx",
        "labelBase64": "JVBERi0xLjQKJdPr6e..... zIKJSVFT0Y="
    }
]
 ```

### Status 400:
- This items were not processed correctly, please check the fields.

```json
 { 
    "box_reference": "xxxxxxxxxxxxxx", 
    "box_reference": "xxxxxxxxxxxxxx"
 }
 ```

### Status 401:
- Unauthorized.

### Status 403:
- Forbidden.

### Status 405:
- Internal Server Error, Check the fields structure.

## Body Format for PRE MANIFEST

| **Order** | **Parameter**             | **Type**  | **Length** | **Mandatory** | **Description**                               |
|:---------:|:-------------------------:|:---------:|:------:|:-----------------:|:-----------------------------------------:|
|           | box_reference             | String    | 33     | YES       | Inditex Box Reference                       |
| **1**     | order_number              | String    | 30     | YES       | Inditex Order Number                        |
| **2**     | itx_code                  | String    | 30     | YES       | Client code of the company that Courier    |
| **3**     | shipping_type             | String    | 5      | YES       | Shipping type. It comes from master        |
| **4**     | weight_in_grams           | String    | 10     | YES       | Box weight in grams                         |
| **5**     | depth_in_cms              | String    | 5      | NO        | Length of the package in Centimeters        |
| **6**     | width_in_cms              | String    | 5      | NO        | Width of the package in Centimeter          |
| **7**     | height_in_cms             | String    | 5      | NO        | Height of the package in Centimeter         |
| **8**     | departure_date_utc        | String    | 14     | YES       | UTC time: yyyyMMddHH24mmss                  |
| **9**     | customer_name             | String    | 60     | YES       | Delivery client’s name                      |
| **10**    | customer_last_name        | String    | 60     | YES       | Delivery client’s surname                   |
| **11**    | customer_address1         | String    | 150    | YES       | Delivery client’s address 1                |
| **12**    | customer_address2         | String    | 150    | YES       | Delivery client’s address 2                |
| **13**    | customer_city             | String    | 60     | YES       | Delivery client’s town                      |
| **14**    | customer_postal_code      | String    | 15     | YES       | Delivery client’s postal code               |
| **15**    | customer_province         | String    | 60     | YES       | Delivery client’s province                  |
| **16**    | customer_country_iso      | String    | 5      | YES       | ISO for delivery client’s country           |
| **17**    | phone_number1             | String    | 60     | YES       | Delivery client’s phone number 1            |
| **18**    | phone_number2             | String    | 60     | NO        | Delivery client’s phone number 2            |
| **19**    | email                     | String    | 60     | YES       | Delivery client’s e-mail                    |
| **20**    | remarks                   | String    | 150    | NO        | Additional information of the address      |
| **21**    | courier_code              | String    | 20     | YES       | Code for Courier identification in Inditex |
| **22**    | courier_description       | String    | 100    | NO        | String for Courier identification in Inditex |
| **23**    | payment_type              | String    | 5      | YES       | Payment method. It comes from master        |
| **24**    | total_value               | String    | 10     | YES       | Total Value                                 |
| **25**    | amount_pending            | String    | 10     | YES       | Amount to be charged in case of POD         |
| **26**    | currency_iso_code         | String    | 5      | YES       | ISO Code for currency                       |
| **27**    | preferred_language_iso    | String    | 5      | NO        | ISO Code for the customer language          |
| **28**    | destinity_store           | String    | 9      | NO        | ID for bundle´s destiny store               |
| **29**    | drop_point                | String    | 30     | NO        | Drop Point id provided by ALAS             |
| **30**    | drop_point_user           | String    | 60     | NO        | Drop point username                         |
| **31**    | defined_delivery_date     | String    | 14     | NO        | Preferred delivery date                     |
| **32**    | defined_delivery_time     | String    | 30     | NO        | Preferred delivery time range               |
| **33**    | brand                     | String    | 50     | YES       | Brand that the bundle belongs to            |
| **34**    | tracking_number           | String    | 50     | YES       | Courier Box Reference                       |
| **35**    | source_warehouse          | String    | 50     | YES       | Source warehouse code                        |
| **36**    | courier_service_code      | String    | 50     | NO        | Courier Service to ship the parcel          |
| **37**    | package_type              | String    | 5      | NO        | Package Type of the parcel                   |
| **38**    | customer_order_number     | String    | 50     | YES       | Order number given to customer in eCommerce  |
| **39**    | district                  | String    | 100    | NO        | Delivery client’s district                   |
| **40**    | external_seller           | String    | 50     | NO        | External seller code in case that the order has been sold by platform (TMALL) |
| **41**    | external_order_id         | String    | 50     | NO        | Order Number in the External Seller platform in case that the order has been sold by another platform |
| **42**    | dangerous_goods           | Boolean   | -      | NO        | Flag to indicate if the box has dangerous goods (For Example value: true, false, null) |
| **43**    | second_life               | Boolean   | -      | NO        | Flag to indicate if the order which belongs this box is requested to Second Life collection (For Example value: true, false, null) |
| **44**    | origin_location_id_numeric| Integer   | 50     | NO        | ID for the origin location of the parcel, it comes from an Inditex master that will be provided to the courier if it’s needed |
| **45**    | free_field1               | String    | 50     | NO        | Field available, currently unused          |
| **46**    | drop_point_user_phone     | String    | 60     | NO        | Drop Point User Phone number               |
| **47**    | drop_point_user_email     | String    | 50     | NO        | Drop Point User e-mail address             |
| **48**    | Billing_company_numeric   | Integer   | 10     | YES       | Billing reference for the company          |
| **49**    | municipality              | String    | 50     | YES       | Delivery client’s municipality             |
| **50**    | service_type_feature      | String    | 50     | NO        | N/A                                       |
| **51**    | free_field2               | String    | 50     | NO        | Field available, currently unused          |
| **52**    | free_field3               | String    | 50     | NO        | Field available, currently unused          |
| **53**    | free_field4               | String    | 50     | NO        | Field available, currently unused          |
| **54**    | free_field5               | String    | 50     | NO        | Field available, currently unused          |
| **55**    | free_field6               | String    | 50     | NO        | Field available, currently unused          |
| **56**    | module                    | Integer   | 1      | YES       | If module is 1 it is last mile, 2 is devo. if the field is empty it is taken as last mile |
| **57**    | id_bulk                   | Integer   | 10     | YES       | Bulk numeric indicator, this id must be unique for bulk |
| **58**    | cnpj                      | String    | 50     | YES       | CNPJ                                      |
| **59**    | audit_cnpj                | String    | 50     | YES       | AuditCNPJ                                 |
| **60**    | audit_ie                  | String    | 50     | YES       | AuditIE                                   |
| **61**    | fiscal_note_key           | String    | 50     | YES       | FiscalNoteKey                             |
| **62**    | fiscal_note_serial_number | String    | 50     | YES       | FiscalNoteSerialNumber                    |
| **63**    | fiscal_note_number        | String    | 50     | YES       | FiscalNoteNumber                          |
| **64**    | fiscal_note_date          | String    | 50     | YES       | FiscalNoteDate                            |
| **65**    | fiscal_note_value         | String    | 50     | YES       | FiscalNoteValue                           |
| **66**    | sender_address1           | String    | 30     | NO        | Sender address description                |
| **67**    | sender_address2           | String    | 30     | NO        | Sender address description                |
| **68**    | sender_address3           | String    | 30     | NO        | Sender address description                |
