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

Working Example/Sample (replace the MERCHANT_KEY by your test key):

    https://socartest.rgwit.be/api/?key=MERCHANT_KEY&a=insert&maker=MITSUBISHI&model=PAJERO 3.2 DID AUT FINAL EDITION N456BE&model_type=CAR&year=2019&price=34500&gear=MANUAL&fuel=DIESEL&kms=3

jSON Answer: 

    {"ans":39,"data":[],"data2":[],"data3":[]}
The value ans gives you the generated vehicle ID this ID can now be use to specify the vehicle photos, update or delete the announcement in the mobile APP.

Method **addphoto**

|Parameter|Mandatory  |Type | Description|Max length
|--|--|--|--|--|
|key|YES  |string|Merchant API Key|128
|a|YES  |string|Action in this case : addphoto|12
|id|YES  |integer|Vehicle Generated ID|11
|model|YES  |string|Model|30
|url|YES|string|valid URL with a .jpg file format at then end|512

Example/Sample:

    https://socartest.rgwit.be/api/?key=MERCHANT_KEY&a=addphoto&id=39&url=https://autosgaite.com/images/465/3899_50.jpg

jSON Answer: 

    {"ans":320,"data":[],"data2":[],"data3":[]}
If the ans value is greater than zero then your photo has been download it to our servers and the vehicle is already visible in Socar Tracking app.
