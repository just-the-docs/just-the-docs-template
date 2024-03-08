---
title: API GET DROP POINTS
layout: default
has_children: yes
---

# API GET DROP POINTS

## Description

- This API provides the list of available drop points. 
- Base URL - APIKEY: Will be provided for different environments.

```bash
curl -X GET /api/v1/droppoints
```
##  Header 
- **APIKEY : APIKEY**

## Example query params:

```bash 
?Latitude=23.8469335&Longitude=37.9565762&MaxDistanceMeters=1000&CourierCode=979317&Page=1&PageSize=1
Latitude:23.8469335
Longitude:37.9565762
MaxDistanceMeters:1000
CourierCode:979317
Page:1
PageSize:1
```

## Example response

```json
{
  "totalItems": 23,
  "dropPoints": [
    {
      "id": "65cb54e2c452662fc3bb0366",
      "name": "Π. ΠΑΙΑΝΙΑΣ",
      "courierCode": "979317",
      "longitude": 37.9565762,
      "latitude": 23.8469335,
      "typeId": 1,
      "type": "Drop Point",
      "streetName": "ΑΓΙΑΣ ΤΡΙΑΔΑΣ 28Α Τ.Κ 19002",
      "city": "ΠΑΙΑΝΙΑ",
      "postalCode": "19002",
      "country": "ΑΤΤΙΚΗΣ",
      "active": true,
      "allowReturns": true,
      "workingHours": [
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Monday"
        },
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Tuesday"
          },
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Wednesday"
        },
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Thursday"
        },
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Friday"
           },
        {
            "from": "08:00",
            "to": "14:00",
            "day": "Saturday"
        }
      ]
    }
  ]
}
```

## Query params format

| **Order**        | **Parameter**       | **Type**    | **Mandatory** | **DefaultValue**                     | **Description**                                              |
|:---------------:|:-------------------:|:-----------:|:-------------:|:-----------------------------------:|:------------------------------------------------------------:|
| **1**            | Latitude            | Double      | NO            | N/A                                 | Latitude (-90 <= latitude <= 90 )                            |
| **2**            | Longitude           | Double      | NO            | N/A                                 | Longitude (-180 <= longitude <= 180 )                        |
| **3**            | MaxDistanceMeters   | Number      | NO            | 1000 (if the location are sended)   | Specifies the maximum distance, in meters, from the given location to display the available drop points             |
| **4**            | CourierCode         | String      | NO            | N/A                                 | Courier code                                                 |
| **5**            | Page                | Number      | YES           | 1                                   | Number of result pages                                       |
| **6**            | PageSize            | Number      | YES           | 500                                 | Maximum number of results per page                           |


## Response format

| **Parameter**   | **Type**   | **Description**                                 |
|:---------------:|:----------:|:---------------------------------------------:|
| totalItems      | Number     | Number of total items obtained by filters      |
| id              | String     | Drop Point id                                   |
| name            | String     | Drop Point name                                 |
| courierCode     | String     | Courier code                                    |
| longitude       | Double     | Longitude (-180 <= longitude <= 180 )          |
| latitude        | Double     | Latitude (-90 <= latitude <= 90 )              |
| typeId          | Number     | Drop Point type (1 = Drop Point, 2 = Locker)   |
| type            | String     | Drop Point type description (Drop Point, Locker)|
| streetName      | String     | Drop Point Street name                          |
| city            | String     | Drop Point city                                 |
| postalCode      | String     | Drop Point postal code                          |
| country         | String     | Drop Point country                              |
| active          | Boolean    | Available Drop Point                           |
| allowReturns    | Boolean    | Enabled for the return module                   |
| workingHours    | Array      | Available Drop Point working hours             |



