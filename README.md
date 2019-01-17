**Welcome to Socar Tracking API for Vehicle market module.**

First things first, be sure you have 2 API Keys, one for testing and one for operations.
Those keys are provided via our support please contact marvin.ai@rgwit.be 

We strongly suggest to use programs like CURL or [POSTMAN](https://www.getpostman.com/) to test the API.

**Important:** *Each merchant has its own pair of keys, and a unique identifier*

Requirements: 

 1. The photos dimensions must be **1:1**
 2. The photos must be already published in a public URL where our servers can download the photos
 3. You need to prepare/add a field in your data base table to save the generated ID of the vehicle.

Set up the work environment:

 - Step 1: Install CURL or [POSTMAN](https://www.getpostman.com/) in your computer.
 - Step 2: Get your merchant Keys.
 - Step 3: Launch your first query.

Methods

|Method|Description  |
|--|--|
|insert|Create a new vehicle record in our database  |
|update|Update an existing vehicle in our database  |
|delete|Delete an existing vehicle in our database (this action can't be undone) |
|addphoto|Add a new photo from an existing URL  |

Method **insert**

    
|Parameter|Mandatory  |Type | Description|Max length
|--|--|--|--|--|
|key|YES  |string|Merchant API Key|128
|a|YES  |string|Action in this case : insert|12
|maker|YES  |string|Vehicle maker, no special characters|30
|model|YES  |string|Model|30
|model_type|YES|string|can be CAR,VAN,TRUCK,PARTS|10
|year|YES|integer|must be 4 digit length|4
|price|YES|integer|Between 0-999999999|11
|fuel|YES|string|Can be: DIESEL,PETROL,HYBRID,LGP,ELECTRIC|12
|kms|YES|integer|0-99999999|12

Example/Sample:

    https://socartest.rgwit.be/api/?key=facd4eek-f747-443e-99e0-d8fbc10fb1dd&a=insert&maker=MITSUBISHI&model=PAJERO 3.2 DID AUT FINAL EDITION N456BE&model_type=CAR&year=2019&price=34500&gear=MANUAL&fuel=DIESEL&kms=3

