---
title: Api GetDropPoints
layout: default
has_children: yes
---

# API GET DROP POINTS

## Description

* This API provides the list of available drop points. 
* Base URL - APIKEY: Will be provided for different environments.

```bash
curl -X GET /api/v1/droppoints
```
###  Header 
* APIKEY : APIKEY

## Example query params:

```json
?Latitude=23.8469335&Longitude=37.9565762&MaxDistanceMeters=1000&CourierCode=979317&Page=1&PageSize=1
Latitude:23.8469335
Longitude:37.9565762
MaxDistanceMeters:1000
CourierCode:979317
Page:1
PageSize:1
```

### Example response

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

| Order        | Parameter    | Type         | Mandatory    | DefaultValue | Description  |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 1   | Latitude    | Celda 1,3    | Celda 1,4    | Celda 1,5    | Celda 1,6    |
| 2    | Longitude    | Celda 2,3    | Celda 2,4    | Celda 2,5    | Celda 2,6    |
| 3    | Celda 3,2    | Celda 3,3    | Celda 3,4    | Celda 3,5    | Celda 3,6    |

