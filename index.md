### Request a gateway
{:toc #markdown-toc}
* The request gateway for external APIs is:[https://api.sellersprite.com/](https://api.sellersprite.com/)

### DEMO address
{:toc #markdown-toc2}
* DEMO code cloud address for external API access:[https://gitee.com/cdyunya/sellersprite-api-demo](https://gitee.com/cdyunya/sellersprite-api-demo)

### Public header description
{:toc #markdown-toc3}
* The access interface needs to apply for an access key. After obtaining the access key, you need to put the key into the header and pass it to the background, and the parameter type and return parameter type of the request interface are json. Request header examples:

| Header       | Value                            |
| -------------- | ---------------------------------- |
| secret-key   | 8957c4cd9rdc4a0eaa3c257e68bu767p |
| Content-Type | application/json;charset=utf-8   |

### Provider public return parameters

| Name    | Type   | Introduction | Example         |
| --------- | -------- | -------------- | ----------------- |
| code    | String | status code  | see table below |
| message | String | description  |                 |
| data    | Object | json         |                 |

### Code descriptions

| Code                     | Introduction          | Description                                                             |
| -------------------------- | ----------------------- | ------------------------------------------------------------------------- |
| OK                       | success               |                                                                         |
| ERROR_URL_NOT_FOUND      | url not found         |                                                                         |
| ERROR_SERVER_INTERNAL    | server internal error |                                                                         |
| ERROR_PARAM              | parameter error       | passed parameter is wrong, which parameter to check the content of data |
| ERROR_SECRET_KEY         | secret key error      |                                                                         |
| ERROR_SECRET_KEY_OVERDUE | secret key expired    |                                                                         |
| ERROR_VISIT_MAX          | visits exceeded       | interface access has reached the daily access or monthly access limit   |
| ERROR_SECRET_KEY_INVALID | secret key invalid    |                                                                         |

### Product research

* Request URI：POST /v1/product/research

#### Request parameter

| Name            | Type    | Introduction                                                                                | Example                                                      | Required |
| ----------------- | --------- | --------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | ---------- |
| marketplace     | String  | marketplace code                                                                            | see table 1.2                                                | ✓       |
| month           | String  | The filter date is the last 30 days by default, and the earliest query time is January 2020 | see table 1.1                                                |          |
| keyword         | String  |                                                                                             | N95                                                          |          |
| excludeKeywords | String  | Keywords that need to be excluded                                                           | portable                                                     |          |
| minPrice        | Float   |                                                                                             | 10                                                           |          |
| maxPrice        | Float   |                                                                                             | 30                                                           |          |
| minRating       | Float   |                                                                                             | 1.0                                                          |          |
| maxRating       | Float   |                                                                                             | 5.0                                                          |          |
| minRatings      | Integer |                                                                                             | 1                                                            |          |
| maxRatings      | Integer |                                                                                             | 90                                                           |          |
| minRatingsCv    | Integer | Minimum number of new ratings per month                                                     | 1                                                            |          |
| maxRatingsCv    | Integer | Maximum number of new ratings per month                                                     | 5                                                            |          |
| minSellers      | Integer |                                                                                             | 3                                                            |          |
| maxSellers      | Integer |                                                                                             | 10                                                           |          |
| minBsr          | Integer |                                                                                             | 50                                                           |          |
| maxBsr          | Integer |                                                                                             | 1                                                            |          |
| minBsrCv        | Integer | BSR minimum increase                                                                        | 3                                                            |          |
| maxBsrCv        | Integer | BSR Maximum increase                                                                        | 5                                                            |          |
| minBsrCr        | Float   | BSR minimum growth rate                                                                     | 30                                                           |          |
| maxBsrCr        | Float   | BSR Maximum growth rate                                                                     | 60                                                           |          |
| minUnits        | Integer |                                                                                             | 20                                                           |          |
| maxUnits        | Integer |                                                                                             | 50                                                           |          |
| minRevenue      | Float   |                                                                                             | 60                                                           |          |
| maxRevenue      | Float   |                                                                                             | 200                                                          |          |
| minRevenueCr    | Float   | Minimum monthly revenue growth rate                                                         | 20                                                           |          |
| maxRevenueCr    | Float   | Maximum monthly revenue growth rate                                                         | 30                                                           |          |
| minUnitsCr      | Float   | Minimum monthly sales growth rate                                                           | 20                                                           |          |
| maxUnitsCr      | Float   | Maximum monthly sales growth rate                                                           | 30                                                           |          |
| nodeIdPath      | String  | complete node id paths, separated by colon                                                  | see product node interface                                   |          |
| availableMonth  | Integer |                                                                                             | see table 1.3，unlimited by default                          |          |
| dimensionType   | String  | A collection of size types, separated by commas, unlimited by default                       | see table 1.4                                                |          |
| minFba          | Float   |                                                                                             | 10                                                           |          |
| maxFba          | Float   |                                                                                             | 20                                                           |          |
| minLqs          | Float   |                                                                                             | 0                                                            |          |
| maxLqs          | Float   |                                                                                             | 10                                                           |          |
| sellerNation    | String  | The seller's place of origin is not restricted by default                                   | see table 1.5                                                |          |
| badgeBS         | String  | whether to include best seller                                                              | If true, the result returns those containing Best-Seller     |          |
| badgeAC         | String  | whether to include Amazon's Choice                                                          | If true, the result returns those containing Amazon's Choice |          |
| fulfillment     | String  | shipping method                                                                             | AMZ or FBA or FBM，The default is empty and unlimited        |          |
| variation       | String  | whether to query variations                                                                 | if true,query variations                                     |          |
| page            | Integer | default 1                                                                                   |                                                              |          |
| size            | Integer | default 50                                                                                  |                                                              |          |
| order           | Object  |                                                                                             |                                                              |          |
| └field         | String  |                                                                                             | see table1.6                                                 |          |
| └desc          | boolean | default descending                                                                          |                                                              |          |

#### Response parameter

| Name           | Type    | Description                                | Example                                                                                                                                 |
| ---------------- | --------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| asin           | String  | asin                                       | B078J8VPVW                                                                                                                              |
| brand          | String  |                                            | Pampers                                                                                                                                 |
| brandUrl       | String  |                                            | [https://www.amazon.com/s?k=HP](https://www.amazon.com/s?k=HP)                                                                             |
| imageUrl       | String  |                                            | [https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL .AC_US200.jpg](https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL) |
| title          | String  |                                            | Diapers Size 2, 186 Count - Pampers Swaddlers Disposable Baby Diapers, ONE MONTH SUPPLY                                                 |
| parent         | String  |                                            | B081RGNL17                                                                                                                              |
| nodeId         | Long    |                                            | 3741281                                                                                                                                 |
| nodeIdPath     | String  | complete node id paths, separated by colon | 2619525011:3741271:3741281                                                                                                              |
| nodeLabelPath  | String  |                                            | Baby Products:Diapering:Disposable Diapers                                                                                              |
| bsrId          | String  |                                            | office-products                                                                                                                         |
| bsr            | Integer | bsr rank                                   | 1                                                                                                                                       |
| units          | Integer | monthly sales                              | 26289                                                                                                                                   |
| unitsGr        | Float   | Monthly sales growth rate                  | -46.3                                                                                                                                   |
| revenue        | Float   |                                            | 1693537.4                                                                                                                               |
| price          | Float   |                                            | 64.42                                                                                                                                   |
| profit         | Float   |                                            | 63.92                                                                                                                                   |
| fba            | Float   |                                            | 13.58                                                                                                                                   |
| ratings        | Integer |                                            | 32004                                                                                                                                   |
| ratingsRate    | Float   |                                            | 40.57                                                                                                                                   |
| rating         | Float   |                                            | 4.8                                                                                                                                     |
| ratingsCv      | Integer | ratings of monthly growths                 | 10666                                                                                                                                   |
| ratingDelta    | Integer | the number of rating in the last 30 days   | 0                                                                                                                                       |
| availableDate  | Long    |                                            | 1454083200000                                                                                                                           |
| fulfillment    | String  |                                            | AMZ or FBA or FBM                                                                                                                       |
| variations     | Integer |                                            | 7                                                                                                                                       |
| sellers        | Integer |                                            | 7                                                                                                                                       |
| sellerId       | String  |                                            | A1Y8BVAASXO4R7                                                                                                                          |
| sellerName     | String  |                                            | Amazon                                                                                                                                  |
| sellerNation   | String  |                                            | see table 1.5                                                                                                                           |
| badge          | Badge   | badge object                               |                                                                                                                                         |
| └bestSeller   | String  | whether to contains best-seller            | Y/N                                                                                                                                     |
| └amazonChoice | String  | whether to contains Amazon's choice        | Y/N                                                                                                                                     |
| └newRelease   | String  | whether to contains newRelease             | Y/N                                                                                                                                     |
| └ebc          | String  | whether to contains A+                     | Y/N                                                                                                                                     |
| └video        | String  | whether to contains video                  | Y/N                                                                                                                                     |
| weight         | String  |                                            | 8.88 pounds                                                                                                                             |
| dimension      | String  |                                            | 13.3 x 15.8 x 10.6 inches                                                                                                               |
| dimensionsType | String  |                                            | ST,0V                                                                                                                                   |
| sku            | String  |                                            | ["Color: Beige","Size: 47 inches"]                                                                                                      |

#### Request example

```
curl 'https://api.sellersprite.com/v1/product/research' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace": "US",\n "excludeKeywords":"HP",\n "maxPrice":432}' \
--compressed
```

### Competitor lookup

* Request URI：POST /v1/product/competitor-lookup

#### Request parameter

| Name        | Type    | Introduction                                                                                | Example                    | Required |
| ------------- | --------- | --------------------------------------------------------------------------------------------- | ---------------------------- | ---------- |
| marketplace | String  | marketplace id                                                                              | see table 1.2              | ✓       |
| month       | String  | The filter date is the last 30 days by default, and the earliest query time is January 2020 | see table 1.1              |          |
| brand       | String  |                                                                                             | WWDOLL                     |          |
| sellerName  | String  |                                                                                             | Chengde Technology Co.     |          |
| asins       | List    | asin collection,the maximum is 50                                                           | ["B08MT3JR3F"]             |          |
| nodeIdPath  | String  | complete node id paths, separated by colon                                                  | see product node interface |          |
| keyword     | String  |                                                                                             | N95                        |          |
| variation   | String  | whether to query variations                                                                 | Y/N,default N              |          |
| page        | Integer | one-based page index                                                                        | default 1                  |          |
| size        | Integer | the size of the page to be returned.                                                        | default 50                 |          |
| order       | Object  |                                                                                             |                            |          |
| └field     | String  | sort field                                                                                  | See table 1.6              |          |
| └desc      | boolean | sort direction                                                                              | true/false,default false   |          |

#### Response parameter

| Name           | Type    | Description                                               | Example                                                                                                                                 |
| ---------------- | --------- | ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| asin           | String  | asin                                                      | B078J8VPVW                                                                                                                              |
| brand          | String  |                                                           | Pampers                                                                                                                                 |
| brandUrl       | String  |                                                           | [https://www.amazon.com/s?k=HP](https://www.amazon.com/s?k=HP)                                                                             |
| imageUrl       | String  |                                                           | [https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL .AC_US200.jpg](https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL) |
| title          | String  |                                                           | Diapers Size 2, 186 Count - Pampers Swaddlers Disposable Baby Diapers, ONE MONTH SUPPLY                                                 |
| parent         | String  |                                                           | B081RGNL17                                                                                                                              |
| nodeId         | Long    |                                                           | 3741281                                                                                                                                 |
| nodeIdPath     | String  | complete node id paths, separated by colon                | 2619525011:3741271:3741281                                                                                                              |
| nodeLabelPath  | String  |                                                           | Baby Products:Diapering:Disposable Diapers                                                                                              |
| bsrId          | String  |                                                           | office-products                                                                                                                         |
| bsr            | Integer |                                                           | 1                                                                                                                                       |
| units          | Integer | monthly sales                                             | 26289                                                                                                                                   |
| unitsGr        | Float   | monthly sales growth rate                                 | -46.3                                                                                                                                   |
| revenue        | Float   |                                                           | 1693537.4                                                                                                                               |
| price          | Float   |                                                           | 64.42                                                                                                                                   |
| profit         | Float   |                                                           | 63.92                                                                                                                                   |
| fba            | Float   |                                                           | 13.58                                                                                                                                   |
| ratings        | Integer |                                                           | 32004                                                                                                                                   |
| ratingsRate    | Float   |                                                           | 40.57                                                                                                                                   |
| rating         | Float   |                                                           | 4.8                                                                                                                                     |
| ratingsCv      | Integer | ratings increase                                          | 10666                                                                                                                                   |
| ratingDelta    | Integer | the number of rating in the last 30 days                  | 0                                                                                                                                       |
| availableDate  | Long    |                                                           | 1454083200000                                                                                                                           |
| fulfillment    | String  | shipping method                                           | AMZ or FBA or FBM，The default is empty and unlimited                                                                                   |
| variations     | Integer |                                                           | 7                                                                                                                                       |
| sellers        | Integer |                                                           | 7                                                                                                                                       |
| sellerId       | String  |                                                           | A1Y8BVAASXO4R7                                                                                                                          |
| sellerName     | String  |                                                           | Amazon                                                                                                                                  |
| sellerNation   | String  | the seller's place of origin is not restricted by default | see table 1.5                                                                                                                           |
| badge          | Badge   | badge object                                              |                                                                                                                                         |
| └bestSeller   | String  | whether to contains best-seller                           | Y/N                                                                                                                                     |
| └amazonChoice | String  | whether to contains Amazon's choice                       | Y/N                                                                                                                                     |
| └newRelease   | String  | whether to contains newRelease                            | Y/N                                                                                                                                     |
| └ebc          | String  | whether to contains A+                                    | Y/N                                                                                                                                     |
| └video        | String  | whether to contains video                                 | Y/N                                                                                                                                     |
| weight         | String  |                                                           | 8.88 pounds                                                                                                                             |
| dimension      | String  |                                                           | 13.3 x 15.8 x 10.6 inches                                                                                                               |
| dimensionsType | String  |                                                           | ST,0V                                                                                                                                   |
| sku            | String  |                                                           | ["Color: Beige","Size: 47 inches"]                                                                                                      |
| subcategories  | List    |                                                           |                                                                                                                                         |
| └code         | String  |                                                           | 1063242                                                                                                                                 |
| └rank         | Integer |                                                           | 1                                                                                                                                       |
| └label        | String  |                                                           | Bath Rugs                                                                                                                               |

#### Request example

```
curl 'https://api.sellersprite.com/v1/product/competitor-lookup' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace": "US",\n "brand":"Gorilla Grip"\n }' \
--compressed
```

### Product node

* Request URI：**GET** /v1/product/node

#### Request parameter

| Name        | Type   | description                                | Example                    | Required |
| ------------- | -------- | -------------------------------------------- | ---------------------------- | ---------- |
| marketplace | String | marketplace code                           | see table 1.2              | ✓       |
| nodeIdPath  | String | complete node id paths, separated by colon | 2619525011:3741271:3741281 |          |
| keyword     | String | keywords or node id                        | Books or 4053              |          |

#### Response parameter

| Name                | Type    | Description                                | Example                |
| --------------------- | --------- | -------------------------------------------- | ------------------------ |
| nodeIdPath          | String  | complete node id paths, separated by colon | 2619525011:3741271     |
| nodeLabelPath       | String  | node name                                  | Appliances:Dishwashers |
| products            | Integer | the number of product                      | 42                     |
| nodeLabelLocale     | String  | chinese translation of node names          | 洗碗机                 |
| nodeLabelPathLocale | String  | chinese translation of full node names     | 大家电:洗碗机          |

#### Request example

```
curl 'https://api.sellersprite.com/v1/product/node?marketplace=US&nodeIdPath=2619525011' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=utf-8' \
--compressed
```

### Keyword mining

* Request URI：**GET** /v1/keyword/miner

#### Request parameter

| Name                 | Type    | Description                                          | Example         | Required |
| ---------------------- | --------- | ------------------------------------------------------ | ----------------- | ---------- |
| marketplace          | String  | marketplace code                                     | see table 1.2   | ✓       |
| historyDate          | String  | Historical date, yyyyMM format, default last 30 days | 202201          |          |
| keyword              | String  |                                                      |                 | ✓       |
| keywordList          | List    | keyword collection                                   | ["phone stand"] |          |
| minSearch            | Integer |                                                      | 543             |          |
| maxSearch            | Integer |                                                      | 23453           |          |
| minPurchases         | Integer |                                                      | 6               |          |
| maxPurchases         | Integer |                                                      | 34              |          |
| minPurchasesRate     | Float   |                                                      | 3               |          |
| maxPurchasesRate     | Float   |                                                      | 43              |          |
| minSPR               | Integer | minimum SellerSprite product rank                    | 2               |          |
| maxSPR               | Integer | maximum SellerSprite product rank                    | 16              |          |
| minTitleDensity      | Integer | minimum title density                                | 2               |          |
| maxTitleDensity      | Integer | maximum title density                                | 23              |          |
| minRelevancy         | Float   | minimum 0                                            | 23              |          |
| maxRelevancy         | Float   | maximum 100                                          | 90              |          |
| minSearchRank        | Integer |                                                      | 33              |          |
| maxSearchRank        | Integer |                                                      | 3223            |          |
| minProducts          | Integer |                                                      | 54              |          |
| maxProducts          | Integer |                                                      | 324             |          |
| minSupplyDemandRatio | Float   |                                                      | 11.2            |          |
| maxSupplyDemandRatio | Float   |                                                      | 45.2            |          |
| minAdProducts        | Integer |                                                      | 123             |          |
| maxAdProducts        | Integer |                                                      | 345             |          |
| minWordCount         | Integer |                                                      | 2               |          |
| maxWordCount         | Integer |                                                      | 4               |          |
| minMonopolyClickRate | Float   |                                                      | 23.4            |          |
| maxMonopolyClickRate | Float   |                                                      | 53.1            |          |
| minBid               | Float   |                                                      | 10.2            |          |
| maxBid               | Float   |                                                      | 23.1            |          |
| minPrice             | Float   |                                                      | 43.3            |          |
| maxPrice             | Float   |                                                      | 234.2           |          |
| minRatings           | Integer |                                                      | 100             |          |
| maxRatings           | Integer |                                                      | 399             |          |
| minRating            | Float   |                                                      | 3.0             |          |
| maxRating            | Float   |                                                      | 4.9             |          |
| amazonChoice         | Boolean | whether amazonChoice                                 | true            |          |
| filterRootWord       | Integer | Filter root 0 contains all 1 contains only roots     | 0               |          |
| includeKeywords      | List    | collection of included keywords                      | ["phone stand"] |          |
| excludeKeywords      | List    | collection of excluded keywords                      | ["phone stand"] |          |
| page                 | Integer | one-based page index                                 | default 1       |          |
| size                 | Integer | the size of the page to be returned                  | default 50      |          |
| order                | Object  |                                                      |                 |          |
| └field              | String  | sort field                                           | see table 2.4   |          |
| └desc               | boolean | sort direction                                       | default true    |          |

#### Response parameter

| Name              | Type    | Description                                                                   | Example                   |
| ------------------- | --------- | ------------------------------------------------------------------------------- | --------------------------- |
| marketplace       | String  | marketplace code，see table 1.2                                               | US                        |
| keyword           | String  |                                                                               | phone stand for recording |
| keywordCn         | String  | chinese translation of node names                                             | 用于录音的电话支架        |
| keywordJp         | String  | japanese translation of node names                                            | 録音用電話スタンド        |
| departments       | List    |                                                                               |                           |
| └code            | String  |                                                                               | electronics               |
| └label           | String  |                                                                               | Electronics               |
| month             | String  | historical date, yyyyMM format, default last 30 days                          | 202201                    |
| supplement        | String  | whether it is a supplementary keyword (current monthly search volume is null) | Y/N                       |
| searches          | Integer |                                                                               | 21582                     |
| purchases         | Integer |                                                                               | 1996                      |
| purchaseRate      | Float   |                                                                               | 0.0925                    |
| monopolyClickRate | Float   |                                                                               | 0.3                       |
| products          | Integer |                                                                               | 1645                      |
| adProducts        | Integer |                                                                               | 34                        |
| supplyDemandRatio | Float   | supply and demand ratio                                                       | 13.12                     |
| avgPrice          | Float   |                                                                               | 36.14                     |
| avgRatings        | Integer |                                                                               | 12223                     |
| avgRating         | Float   |                                                                               | 4.5                       |
| bidMin            | Float   | maximum ppc price                                                             | 1.34                      |
| bidMax            | Float   | minimumppc price                                                              | 3.21                      |
| bid               | Float   | ppc price                                                                     | 1.6                       |
| cvsShareRate      | Float   | conversion sharing rate                                                       | 0.3084                    |
| wordCount         | Integer | the number of words                                                           | 4                         |
| titleDensity      | Integer |                                                                               | 42.9                      |
| spr               | Integer | SellerSprite product rank                                                     | 6                         |
| relevancy         | Double  |                                                                               | 28.6                      |
| amazonChoice      | Boolean |                                                                               | false                     |
| searchRank        | Integer |                                                                               | 17910                     |

#### Request example

```
curl 'https://api.sellersprite.com/v1/keyword/miner' \
--H 'Content-Type: application/json' \
--H 'secret-key: your secret key' \
--data-raw '{"desc": true,"keyword":"phone stand","marketplace": "US","amazonChoice":false,"pageNum": 1,"pageSize":100,"order":{ "field":"searches", "desc":false}}'
--compressed
```

### Reverse ASIN

* Request URI：**POST** /v1/traffic/keyword

#### Request parameter

| Name                   | Type    | Description                                              | Example                                                         | Required |
| ------------------------ | --------- | ---------------------------------------------------------- | ----------------------------------------------------------------- | ---------- |
| marketplace            | String  |                                                          | US                                                              | ✓       |
| asin                   | String  |                                                          | B07Z82895W                                                      | ✓       |
| keyword                | String  |                                                          | phone stand                                                     |          |
| month                  | String  | yyyyMM,If null, the default is to query the last 30 days | 202308                                                          |          |
| badges                 | List    |                                                          | see table 1.10                                                  |          |
| trafficKeywordTypes    | List    |                                                          | see table 2.0                                                   |          |
| conversionKeywordTypes | List    |                                                          | see table 2.1                                                   |          |
| page                   | Integer |                                                          | default 1                                                       |          |
| size                   | Integer |                                                          | default 200，Maximum 200,The maximum number of queries is 2,000 |          |
| order                  | Object  |                                                          |                                                                 |         |
| └field                | String  |                                                          | see table 2.3                                                   |         |
| └desc                 | Boolean |                                                          | false                                                           |         |

#### Response parameter

| Name                       | Type         | Description                                          | Example       |
| ---------------------------- | -------------- | ------------------------------------------------------ | --------------- |
| marketplace                | String       |                                                      | US            |
| asin                       | String       | asin                                                 | B07Z82895W    |
| total                      | Integer      |                                                      | 2685          |
| items                      | List         |                                                      | 1848          |
| └keywords                 | String       |                                                      | phone stand   |
| └keywordCn                | String       |                                                      | 手机支架      |
| └searches                 | Integer      |                                                      | 10            |
| └products                 | Integer      |                                                      | 10            |
| └purchases                | Integer      |                                                      | 10000         |
| └purchaseRate             | Float        |                                                      | 0.5           |
| └bid                      | Float        |                                                      | 2.9           |
| └bidMax                   | Float        |                                                      |               |
| └bidMin                   | Float        |                                                      |               |
| └badges                   | List         |                                                      | see table 1.9 |
| └rankPosition             | RankPosition |                                                      |               |
| └└page                   | Integer      |                                                      | 3             |
| └└pageSize               | Integer      |                                                      | 60            |
| └└index                  | Integer      |                                                      | 10            |
| └└position               | Integer      |                                                      | 106           |
| └└updatedTime            | long         |                                                      |               |
| └adPosition               | AdPosition   |                                                      |               |
| └└page                   | Integer      |                                                      | 2             |
| └└pageSize               | Integer      |                                                      | 63            |
| └└index                  | Integer      |                                                      | 37            |
| └└position               | Integer      |                                                      | 85            |
| └└updatedTime            | long         |                                                      |               |
| └searchesRank             | Integer      |                                                      | 25            |
| └searchesRankTimeFrom     | Long         |                                                      |               |
| └searchesRankTimeTo       | Long         |                                                      |               |
| └latest1daysAds           | Integer      | Number of advertised competitors in the last 1 days  | 70            |
| └latest7daysAds           | Integer      | Number of advertised competitors in the last 7 days  | 100           |
| └latest30daysAds          | Integer      | Number of advertised competitors in the last 30 days | 280           |
| └supplyDemandRatio        | Float        |                                                      | 3.8           |
| └trafficPercentage        | Float        | percentage of traffic flow                           | 0.015         |
| └trafficKeywordType       | String       |                                                      | see table 2.0 |
| └conversionKeywordType    | String       |                                                      | see table 2.1 |
| └calculatedWeeklySearches | Float        | Estimated weekly search volume                       | 40            |
| └updatedTime              | Long         |                                                      |               |
| stats                      | List         | High-frequency word statistics                       |               |
| └keywords                 | String       | keyword term                                         | phone         |
| └total                    | Integer      | number of keyword term                               | 90            |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffic/keyword' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","asin":"B07Z82895W"}' \
--compressed
```
### Reverse Multiple ASINs

* Request URI：**POST** /v1/traffic/extend

#### Request parameter

| **Name**             | **Type**    | **Description**                                       | **Example**               | **Required** |
| -------------------------- | ----------------- | ---------------------------------------------------- | ------------------------ | -------------- |
| marketplace          | String      | marketplace code,see table 1.2                                   | US                 | ✓       |
| historyDate      | String      | Historical month, default to the last 30 days if not passed | 202201             |              |
| asinList             | List        | asin list                                       | ["B07Z82895W"] | ✓       |
| queryType            | Integer     | Query Method 0 All Variants 1 Bestseller Variant 2 Current Variant, Default 2 | 2                  |              |
| minSearches          | Integer     |                                  | 100                |              |
| maxSearches          | Integer     |                                    | 300                |              |
| minSearchRank        | Integer     |                                    | 33                 |              |
| maxSearchRank        | Integer     |                                    | 3223               |              |
| minPurchases         | Integer     |                                   | 6                  |              |
| maxPurchases         | Integer     |                                     | 34                 |              |
| minPurchasesRate | Float       |                                      | 3                  |              |
| maxPurchasesRate | Float       |                                      | 43                 |              |
| minProducts          | Integer     |                                      | 10                 |              |
| maxProducts          | Integer     |                                      | 90                 |              |
| minSupplyDemandRatio | Float       |                                    | 11.2               |              |
| maxSupplyDemandRatio | Float       |                                      | 45.2               |              |
| minBid               | Float       | Minimum PPC bidding                                    | 10.2               |              |
| maxBid               | Float       | Maximum PPC bidding                                    | 23.1               |              |
| minAdProducts    | Integer     | Minimum number of advertising competitors                                 | 123                |              |
| maxAdProducts    | Integer     | Maximum number of advertising competitors                                 | 345                |              |
| minAvgPrice          | Float       |                                        | 20.0               |              |
| maxAvgPrice          | Float       |                                        | 30.3               |              |
| minWordCount     | Integer     |                                        | 2                  |              |
| maxWordCount     | Integer     |                                        | 4                  |              |
| includeKeywords      | List        |                                 | ["phone stand"]    |              |
| excludeKeywords      | List        |                                       | ["phone stand"]    |              |
| minSPR               | Integer     |                                     | 2                  |              |
| maxSPR               | Integer     |                                       | 16                 |              |
| minTitleDensity      | Integer     |                                  | 2                  |              |
| maxTitleDensity      | Integer     |                                    | 23                 |              |
| minMonopolyClickRate | Float       | Minimum Click Concentration                                 | 23.4               |              |
| maxMonopolyClickRate | Float       | Maximum Click Concentration                                 | 53.1               |              |
| minTrafficPercentage | Float       | Minimum traffic proportion                                   | 45                 |              |
| maxTrafficPercentage | Float       | Maximum traffic proportion                                   | 23                 |              |
| minConversionRate    | Float       | Minimum Conversion Share                                     | 0.23               |              |
| maxConversionRate    | Float       | Maximum Conversion Share                                     | 1.4                |              |
| minCompetitors       | Integer     | Minimum Related ASINs                                     | 4                  |              |
| maxCompetitors       | Integer     | Maximum Related ASINs                                     | 23                 |              |
| amazonChoice         | Boolean     |                                  | true               |              |
| page                 | Integer     |                                 | default 1            |              |
| size                 | Integer |                                        | default 50           |              |
| order                | Object  |                                            |                        |              |
| └field              | String      |                                        | set table 2.5            |              |
| └desc               | boolean     | True is in descending order,False is in ascending order                         | default true           |           

#### Response parameter

| **Name**                 | **Type** | **Description**             | **Example**               |
| ------------------------------ | -------------- | -------------------------- | ------------------------ |
| keyword                  | String   |               | N95                |
| keywordCn                | String   |      | 用于录音的电话支架 |
| searches                 | Integer  |                | 21582              |
| purchases            | Integer  |              | 1996               |
| purchaseRate             | Float    |              | 0.0925             |
| products                 | Integer  |                | 1645               |
| bidMin                   | Float    |           | 1.34               |
| bidMax                   | Float    |           | 3.21               |
| bid                      | Float    |               | 1.6                |
| badges                   | List     |            | see table 1.10           |
| rankPosition             | Object   | Natural ranking             |                        |
| └page                   | Integer  |                | 3                  |
| └pageSize               | Integer  |                | 60                 |
| └index                  | Integer  |          | 10                 |
| └position               | Integer  |        | 106                |
| └updatedTime            | long     | Ranking time             |                        |
| adPosition               | Object   | Advertising ranking             |                        |
| └page                   | Integer  |                | 2                  |
| └pageSize               | Integer  |        | 63                 |
| └index                  | Integer  |          | 37                 |
| └position               | Integer  |        | 85                 |
| └updatedTime            | long     | Ranking time             |                        |
| updatedTime              | long     | update time             |                        |
| searchesRank             | Integer  | Weekly search volume ranking         | 25                 |
| searchesRankTimeFrom     | Long     | Weekly search volume ranking time range |                        |
| searchesRankTimeTo       | Long     | Weekly search volume ranking time range                         |                        |
| latest1daysAds           | Integer  | Number of advertising competitors in the past day    | 70                 |
| latest7daysAds           | Integer  | Number of advertising competitors in the past 7 days    | 100                |
| latest30daysAds          | Integer  | Number of advertising competitors in the past 30 days   | 280                |
| supplyDemandRatio        | Float    |                | 3.8                |
| trafficPercentage        | Float    |              | 0.015              |
| trafficKeywordType       | List     |          | see table 2.0            |
| conversionKeywordType    | List     |          | see table 2.1            |
| calculatedWeeklySearches | Float    | Estimated weekly search volume         | 40                 |
| avgPrice                 | Float    |              | 36.14              |
| avgRatings           | Integer  |            | 12223              |
| avgRating                | Float    |            | 4.5                |
| titleDensity             | Integer  |              | 42.9               |
| spr                      | Integer  |                   | 6                  |
| monopolyClickRate        | Float    |            | 0.3                |
| top3ClickingRate         | Float    | First three clicks             | 0.0813             |
| top3ConversionRate       | Float    | Top three conversions             | 0.2011             |
| relationVariationsItems  | List     | From which variants       |                        |
| └marketplace            | String   |                  | US                  |
| └asin                   | String   |                          | B08P6SC34B         |
| └imageUrl               | String   |              | 10                 |
| └trafficPercentage      | Float    |              | 54.6               |
| └title                  | String   |                  |                        |
| └price                  | Float    |                  | 60                 |
| └reviews                | Float    |                | 10                 |
| └rating                 | Float    |                  | 4.5                |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffice/extend' \
  -H 'secret-key: Your Key' \
  -H 'content-type: application/json;charset=UTF-8' \
  --data-raw $'{"marketplace": "US","asinList":["B07Z82895W"] }' \
  --compressed
```

### ASIN Detail

* Request URI：**GET** /v1/asin/{marketplace}/{asin}
  
#### Request parameter

| Name              | Type           | Description                       | Example          | Required       |
| ----------------- | -------------- | --------------------------------- | ---------------- | -------------- |
| marketplace       | String         | marketplace code,see table 1.2    | US               | ✓              |
| asin              | String         | asin                              | B08GHW4TBS       | ✓              |
| month             | String         | Historical month, default to the last 30 days if not passed | 202308     |              |

#### Response parameter

| Name        | Type    | Description                      | Example    |
| ------------------------- | -------------- | -------------------------- | --------------------------------- |
| asin                | String   | asin                 | B08GHW4TBS     |
| asinUrl             | String   | asin url             | [https://www.amazon.com/dp/B08GHW4TBS](https://www.amazon.com/dp/B08GHW4TBS)    |
| availableDate       | Long     | Date of listing             | 1609059137000   |
| badge               | Badge    | characteristic    | Including the following 5 signs  |
| └bestSeller        | String   | Best Seller      | Y or N       |
| └amazonChoice      | String   | amazon choice    | Y or N       |
| └newRelease        | String   | release          | Y or N     |
| └ebc               | String   | A+ Pages               | Y or N      |
| └video             | String   | Video Introduction     | Y or N      |
| brand               | String   | brand                 | mermaker    |
| brandUrl            | String   | brand URL             | /stores/Mermaker/page/984A6448-1C68-4CCA-AD5A-D574EA2D65D5?ref_=ast_bln    |
| bsrId               | String   | bsr id               | home-garden      |
| bsrLabel            | String   | BSR label             | Home & Kitchen       |
| bsrRank             | Integer  | bsr rank             | 1006         |
| createdTime         | Long     | Creation time             | 1606467137000     |
| dimensions          | String   | dimensions                 | 7 x 6 x 0.6 inches      |
| firstRatingDate     | Long     | First comment time       | 1609059137000      |
| imageUrl            | String   | pictures linking             | [https://images-na.ssl-images-amazon.com/images/I/412616zl5YL .AC_US200.jpg](https://images-na.ssl-images-amazon.com/images/I/412616zl5YL)     |
| lqs                 | Integer  | Listing Page Quality Score | 97       |
| nodeId              | String   | node id              | 1063280       |
| nodeIdPath          | String   | node id path           | 1055398:1063252:1063280     |
| nodeLabelPath       | String   | Category name string           | Home & Kitchen:Bedding:Blankets & Throws  |
| nodeLabelPathLocale | String   | Category name string in Chinese       | 家居厨房用品:床上用品:毯子、盖毯       |
| parent              | String   | parent asin              | B07V5GB9B5      |
| price               | Float    | price                 | 21.99               |
| questions           | Integer  | Number of issues             | 5                  |
| rating              | Float    | score                 | 4.8           |
| ratings             | Integer  | Score evaluation               | 29229        |
| sellerId            | String   | seller id              | A13AJ1GXFINAZ    |
| sellerName          | String   | seller name             | Mermaker         |
| fulfillment         | String   | Delivery method             | FBA           |
| sellers             | Integer  | Number of sellers               | 1        |
| skuList             | List     | sku                  | ["Color: Beige","Size: 47 inches"]    |
| marketplace         | String   | marketplace               | table 1.2    |
| title               | String   | title                 | mermaker Burritos Tortilla Blanket 2.0 Double Sided 47 inches for Adult and Kids,Giant Funny Realistic Food Throw Blanket,285 GSM Novelty Soft Flannel Taco Blanket (Yellow Blanket-Double Sided) |
| updatedTime         | Long     | update time             | 1609059137000  |
| variationList       | List     | variant                 | [{"asin":"B07V5GB9B5","attribute":"Beige"},{"asin":"B08H86SSSF","attribute":"Cookie"}]  |
| variations          | Integer  | Number of variants             | 14      |
| weight              | String   | weight                 | 15.2 ounces         |
| zoomImageUrl        | String   | Large image URL            | [https://images-na.ssl-images-amazon.com/images/I/412616zl5YL .AC_US600.jpg](https://images-na.ssl-images-amazon.com/images/I/412616zl5YL)    |
| subcategories       | Object   | Subcategory information           |                   |
| └rank              | Integer  | Ranking of subcategories           | 1              |
| └code              | String   | Subcategory code           | 17874234011            |
| └label             | String   | Subclass Target Label           | Kids' Throw Blankets |

#### Request example

```
curl 'https://api.sellersprite.com/v1/asin/US/B07V34QQ3C' \
  -H 'secret-key: Your Key' \
  -H 'content-type: application/json;charset=utf-8' \
  --compressed
```

### Reverse ASIN Stat

* Request URI：**GET** /v1/traffic/keyword/stat/{marketplace}/{asin}

#### Request parameter

| Name        | Type   | Description                    | Example    | Required |
| ------------- | -------- | -------------------------------- | ------------ | ---------- |
| marketplace | String | marketplace code,see table 1.2 | US         | ✓       |
| asin        | String | asin                           | B07Z82895W | ✓       |

#### Response parameter

| Name        | Type    | Description                      | Example    |
| ------------- | --------- | ---------------------------------- | ------------ |
| marketplace | String  | marketplace code                 | US         |
| asin        | String  | asin                             | B07Z82895W |
| keywords    | Integer | number of all keywords           | 2685       |
| ranks       | Integer | number of keywords without ads   | 1848       |
| ads         | Integer | number of keywords with ads only | 1414       |
| calcTime    | Long    | last calculated time             |            |
| badgeCount  | Object  | keyword type statistics          |            |
| └ns        | Integer | natural search terms             | 1070       |
| └ac        | Integer | amazon'choice terms              | 0          |
| └er        | Integer | edition recommendation terms     | 42         |
| └fs        | Integer | four stars terms                 | 0          |
| └hr        | Integer | highly recommendation terms      | 117        |
| └sb        | Integer | sponsor brand terms              | 334        |
| └sv        | Integer | sponsor video terms              | 208        |
| └ad        | Integer | sponsor terms                    | 764        |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffic/keyword/stat/US/B07Z82895W' \
-H 'secret-key: your key' \
-H 'content-type: application/json;charset=UTF-8' \
--compressed
```

### Google trends

* Request URI：**GET** /v1/google/trends

#### Request parameter

| Name        | Type    | Description                                             | Example          | Required |
| ------------- | --------- | --------------------------------------------------------- | ------------------ | ---------- |
| marketplace | String  | marketplace code                                        | see table 1.2    | ✓       |
| keyword     | String  |                                                         | iphone stand     | ✓       |
| googleProp  | String  | search type                                             | web/shoppingCart |          |
| monthly     | boolean | Whether the statistics are based on monthly granularity | false            |          |

#### Response parameter

| Name        | Type    | Description                     | Example       |
| ------------- | --------- | --------------------------------- | --------------- |
| marketplace | String  | marketplace code，see table 1.2 | US            |
| keyword     |         |                                 | phone stand   |
| link        | String  | google trend link               |               |
| items       | List    |                                 |               |
| └time      | Long    |                                 | 1555804800000 |
| └value     | Integer |                                 | 2             |

#### Request example

```
curl 'https://api.sellersprite.com/v1/google/trends?googleProp=web&keyword=iphone%20stand&marketplace=US&monthly=true' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=utf-8' \
--compressed
```

### Keyword Research

* Request URI：**POST** /v1/keyword-research

#### Request parameter

| dName                | Type    | Description                                                          | Example                        | Required |
| ---------------------- | --------- | ---------------------------------------------------------------------- | -------------------------------- | ---------- |
| marketplace          | String  | marketplace code                                                     | see table 1.2                  | ✓       |
| month                | String  | Historical date, yyyyMM format, default last 30 days                 | 202203                         |          |
| departments          | List    | see **Keyword Research Category** interface,pass the code            | ["automotive","baby-products"] |          |
| keywords             | String  |                                                                      | N95                            |          |
| excludeKeywords      | String  |                                                                      | portable                       |          |
| minSearches          | Integer |                                                                      | 100                            |          |
| maxSearches          | Integer |                                                                      | 300                            |          |
| minSearchesCr        | Float   | minimum searches growth rate                                         | 10.0                           |          |
| maxSearchesCr        | Float   | maximum searches growth rate                                         | 50.8                           |          |
| minProducts          | Integer |                                                                      | 10                             |          |
| maxProducts          | Integer |                                                                      | 90                             |          |
| minPurchases         | Integer |                                                                      | 100                            |          |
| maxPurchases         | Integer |                                                                      | 500                            |          |
| minPurchaseRate      | Float   |                                                                      | 3.2                            |          |
| maxPurchaseRate      | Float   |                                                                      | 10.5                           |          |
| withYearlyGrowth     | Boolean | new market segments                                                  | false                          |          |
| minSearchMonthCv     | Integer | minimum searches increase                                            | 1000                           |          |
| maxSearchMonthCv     | Integer | maximum searches increase                                            | 3000                           |          |
| minSearchMonthCr     | Float   | Year-over-year growth rate of minimum monthly searches               | 5.3                            |          |
| maxSearchMonthCr     | Float   | Year-over-year growth rate of maximum monthly searches               | 30.1                           |          |
| minSearchNearlyCv    | Integer | The minimum monthly searches has increased in the last 3 months      | 6000                           |          |
| maxSearchNearlyCv    | Integer | The maximum monthly searches has increased in the last 3 months      | 20000                          |          |
| minSearchNearlyCr    | Float   | The growth rate of the minimum monthly searches in the past 3 months | 10.3                           |          |
| maxSearchNearlyCr    | Float   | The growth rate of the maximum monthly searches in the past 3 months | 20.4                           |          |
| marketPeriod         | String  | marketplace cycls                                                    | see table1.7                   |          |
| minAvgPrice          | Float   |                                                                      | 20.0                           |          |
| maxAvgPrice          | Float   |                                                                      | 30.3                           |          |
| minRatings           | Integer |                                                                      | 2000                           |          |
| maxRatings           | Integer |                                                                      | 3000                           |          |
| minRating            | Float   |                                                                      | 3.2                            |          |
| maxRating            | Float   |                                                                      | 4.1                            |          |
| minBid               | Float   |                                                                      | 6.2                            |          |
| maxBid               | Float   |                                                                      | 10.6                           |          |
| minAraClickRate      | Float   | minimum click concentration                                          | 20.1                           |          |
| maxAraClickRate      | Float   | maximum click concentration                                          | 56.4                           |          |
| minGoodsValue        | Float   | minimum flow value                                                   | 10.1                           |          |
| maxGoodsValue        | Float   | maximum flow value                                                   | 41.1                           |          |
| minSupplyDemandRatio | Float   |                                                                      | 5.6                            |          |
| maxSupplyDemandRatio | Float   |                                                                      | 10.4                           |          |
| minWordCount         | Integer |                                                                      | 1                              |          |
| maxWordCount         | Integer |                                                                      | 3                              |          |
| page                 | Integer | one-based page index                                                 | default 1                      |          |
| size                 | Integer |                                                                      | default 50                     |          |
| order                | Object  | sort object                                                          |                                |          |
| └field              | String  | sort field                                                           | see table1.8                   |          |
| └desc               | boolean | sort direction                                                       | default true                   |          |

#### Response parameter

| Name                  | Type    | Description                                                                   | Example                                                                                                                       |
| ----------------------- | --------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| marketplace           | String  | marketplace code                                                              | US                                                                                                                            |
| keywords              | String  |                                                                               | polaroid cameras                                                                                                              |
| searches              | Integer |                                                                               | 141356                                                                                                                        |
| purchases             | Integer |                                                                               | 4029                                                                                                                          |
| growth                | Float   |                                                                               | -25.482092                                                                                                                    |
| purchaseRate          | Float   |                                                                               | 0.0285                                                                                                                        |
| products              | Integer |                                                                               | 173                                                                                                                           |
| supplyDemandRatio     | Float   |                                                                               | 817.09                                                                                                                        |
| searchDepartments     | List    | product node object                                                           |                                                                                                                               |
| └code                | String  |                                                                               | electronics                                                                                                                   |
| └label               | String  |                                                                               | Electronics                                                                                                                   |
| └total               | Integer |                                                                               | 141356                                                                                                                        |
| └ratio               | Float   |                                                                               | 1.0                                                                                                                           |
| month                 | String  | query month, yyyyMM format, default last 30 days                              | 202201                                                                                                                        |
| supplement            | String  | whether it is a supplementary keyword (current monthly search volume is null) | N                                                                                                                             |
| searchMonthlyCv       | Integer | searches increase                                                             | 139749                                                                                                                        |
| searchMonthlyCr       | Float   | year-over-year growth rate of minimum monthly searches                        | 8696.27                                                                                                                       |
| searchNearlyCv        | Integer | monthly searches has increased in the last 3 months                           | -48338                                                                                                                        |
| searchNearlyCr        | Float   | the growth rate of the monthly searches in the past 3 months                  | -25.48                                                                                                                        |
| currency              | String  | currency unit                                                                 | $                                                                                                                             |
| avgPrice              | Float   |                                                                               | 116.24                                                                                                                        |
| avgRatings            | Integer |                                                                               | 2584                                                                                                                          |
| avgRating             | Float   |                                                                               | 4.5                                                                                                                           |
| relationAsinList      | List    | collection of related asin                                                    | 4.8                                                                                                                           |
| └asin                | String  |                                                                               | B06WW64YM6                                                                                                                    |
| └imageUrl            | String  |                                                                               | [https://m.media-amazon.com/images/I/817aVWYpblL._AC_UY218_.jpg](https://m.media-amazon.com/images/I/817aVWYpblL._AC_UY218_.jpg) |
| └price               | Float   |                                                                               | 59.95                                                                                                                         |
| └ratings             | Integer |                                                                               | 20115                                                                                                                         |
| └rating              | Float   |                                                                               | 4.7                                                                                                                           |
| bidMin                | Float   |                                                                               | 0.987                                                                                                                         |
| bidMax                | Float   |                                                                               | 2.54                                                                                                                          |
| bid                   | Float   |                                                                               | 1.26                                                                                                                          |
| araClickRate          | Float   | click concentration                                                           | 0.2633                                                                                                                        |
| araAsinList           | List    | click on the first three ASINs                                                |                                                                                                                               |
| └asin                | String  |                                                                               | B099VDRGG1                                                                                                                    |
| └title               | String  |                                                                               | Fujifilm Instax Mini 9                                                                                                        |
| └imageUrl            | String  |                                                                               | [https://m.media-amazon.com/images/I/51aZiZaicYL._AC_US200_.jpg](https://m.media-amazon.com/images/I/51aZiZaicYL._AC_US200_.jpg) |
| └clickRate           | Double  |                                                                               | 0.116                                                                                                                         |
| └conversionShareRate | Double  |                                                                               | 0.1217                                                                                                                        |
| goodsValue            | Float   | flow value                                                                    | 0.0108                                                                                                                        |
| marketPeriod          | String  | marketplace cycles                                                            | S11,S12                                                                                                                       |
| brand                 | String  |                                                                               | Fujifilm                                                                                                                      |
| hasBrandWord          | Boolean |                                                                               | false                                                                                                                         |
| keywordCn             | String  | chinese translation of keyword                                                | 宝丽来相机                                                                                                                    |

#### Request example

```
curl 'https://api.sellersprite.com/v1/keyword-research' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","month":"202203"}' \
--compressed
```

### Keyword Research Category

* Request URI：**GET** /v1/keyword-research/department

#### Request parameter

| Name        | Type   | Description      | Example       | Required |
| ------------- | -------- | ------------------ | --------------- | ---------- |
| marketplace | String | marketplace code | see table 1.2 | ✓       |

#### Response parameter

| Name  | Type   | Description      | Example                        |
| ------- | -------- | ------------------ | -------------------------------- |
| code  | String | department name  | automotive                     |
| label | String | department label | Automotive Parts & Accessories |

#### Request example

```
curl 'https://api.sellersprite.com/v1/keyword-research/department?marketplace=US' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--compressed
```

### ABA Search Terms

* Request URI：**POST** /v1/aba/research

#### Request parameter

| Name                  | Type     | Description                                                                                                            | Example                                                        | Required |
| ----------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- | ---------- |
| marketplace           | String   |                                                                                                                       | See table 1.2                                                  | ✓       |
| reverseType           | String   | [W,M]W:weekM:monthDefault M                                                                                            |                                                                | #       |
| date                  | String   | Works with reverseTypeWhen reverseType=W or empty, query the latest week.When reverseType=M, query the last 30 days. | Weekly queries are limited to Saturday's date, e.g., 20230610. |          |
| departments           | List     | Department collection                                                                                                  | ["automotive","baby-products"]                                 |          |
| keywordList           | List     |                                                                                                                       | ["phone","stand"]                                              |          |
| asins                 | List     |                                                                                                                       |                                                                |          |
| excludeKeywords       | String   |                                                                                                                       | portable                                                       |          |
| includeKeywords       | String   |                                                                                                                       |                                                                |          |
| exactFlag             | Boolean  | Whether to use exact queries                                                                                           | true                                                           |          |
| rankGrowthValue       | Integer  |                                                                                                                       |                                                                |          |
| rankGrowthRate        | Double   |                                                                                                                       |                                                                |          |
| minRankGrowthRate     | Double   |                                                                                                                       |                                                                |          |
| maxRankGrowthRate     | Double   |                                                                                                                       |                                                                |          |
| rankGrowthType        | String   | Type of growth timeW1:last weekW2:last 2 weeksW3:last 3 weeksW4:last 4 weeks                                           | W1                                                             |          |
| minSearchRank         | Integer  |                                                                                                                       |                                                                |          |
| maxSearchRank         | Integer  |                                                                                                                       |                                                                |         |
| minSearches           | Integer  |                                                                                                                       |                                                                |         |
| maxSearches           | Integer  |                                                                                                                       |                                                                |         |
| minMonopolyClickRate  | Double   |                                                                                                                       |                                                                |         |
| maxMonopolyClickRate  | Double   |                                                                                                                       |                                                                |         |
| minConversionRate     | Double   |                                                                                                                       |                                                                |         |
| maxConversionRate     | Double   |                                                                                                                       |                                                                |         |
| minWordCount          | Integer  |                                                                                                                       |                                                                |         |
| maxWordCount          | Integer  |                                                                                                                       |                                                                |         |
| minSPR                | Integer  |                                                                                                                       |                                                                |         |
| maxSPR                | Integer  |                                                                                                                       |                                                                |         |
| minTitleDensity       | Integer  |                                                                                                                       |                                                                |         |
| maxTitleDensity       | Integer  |                                                                                                                       |                                                                |         |
| searchModel           | Integer  | Search Mode：1：hot2：abnormal3：growth4：rapidly soaring5：potential6：long tail                                      | 1                                                              |         |
| page                  | Integer  | Base on 1                                                                                                              | Default 1                                                      |         |
| size                  | Integer  |                                                                                                                       | Default 50                                                     |          |
| order                 | Object   |                                                                                                                       |                                                                |          |
| └field               | String   |                                                                                                                       | See table 1.9                                                  |          |
| └desc                | boolean  |                                                                                                                       | Default true                                                   |         |

#### Response parameter

| Name                   | Type    | Description                    | Example                       |
| ------------------------ | --------- | -------------------------------- | ------------------------------- |
| marketplace            | String  |                               | US                            |
| keyword                | String  |                               | portable charger              |
| keywordCn              | Integer | Keyword Chinese translation    | 便携式充电器                  |
| keywordJp              | String  | Keyword Japanese translation   |                               |
| departments            | List    |                               | ["Cell Phones & Accessories"] |
| searchRank             | Integer |                               | 62                            |
| searchRankCv           | Integer |                               | 19                            |
| searchRankCr           | Double  |                               | 0.2346                        |
| searches               | Integer |                               |                               |
| purchases              | Integer |Purchase quantity              | 2492                          |
| purchaseRate           | Double  |Purchase rate                  | 0.0054                        |
| searchRankGrowthValue  | Integer |                               |                               |
| searchRankGrowthRate   | Double  |                               |                               |
| cvsShareRate           | Double  |                               |                               |
| titleDensityExact      | Integer |                               |                               |
| cprExact               | Integer |                               |                               |
| w1SearchRank           | Integer | Last week search rank          |                               |
| w1RankGrowthValue      | Integer | Last week rank growth          |                               |
| w1RankGrowthRate       | Double  | Last week rank growth rate     |                               |
| w4SearchRank           | Integer | Last 4 weeks search rank       |                               |
| w4RankGrowthValue      | Integer | Last 4 weeks rank growth       |                               |
| w4RankGrowthRate       | Double  | Last 4 weeks rank growth rate  |                               |
| w12SearchRank          | Integer | Last 12 weeks search rank      |                               |
| w12RankGrowthValue     | Integer | Last 12 weeks rank growth      |                               |
| w12RankGrowthRate      | Double  | Last 12 weeks rank growth rate |                               |
| top3Brands             | List    |                               |                               |
| bid                    | Float   |                               |                               |
| bidMax                 | Float   |                               |                               |
| bidMin                 | Float   |                               |                               |
| top3AsinDtoList        | List    | First three clicks asin        |                               |
| -asin                  | String  | asin                           |                               |
| -imageUrl              | String  |                               |                               |
| -clickRate             | Double  |                               |                               |
| -conversionRate        | Double  |                               |                               |
| sumClickRate           | Double  | Percentage of top three hits   | 54.2                          |
| sumConversionRate      | Double  | Total share of conversions     | 43.5                          |

#### Request example

````
curl 'https://api.sellersprite.com/v1/aba/research' \
-H 'secret-key:  your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","rankGrowthType":"W1","date":"20220129"}' \
--compressed
````

### Related Products Stat

* Request URI：**GET**  /v1/traffic/listing/stat

#### Request parameter

| Name        | Type   | Description                    | Example | Required |
| ------------- | -------- | -------------------------------- | --------- | ---------- |
| marketplace | String | marketplace code,see table 1.2 | US      | ✓       |
| asinList    | List   | Collection of query ASINs      |        |         |

#### Response parameter

| Name          | Type    | Description                             | Example    |
| --------------- | --------- | ----------------------------------------- | ------------ |
| marketplace   | String  | marketplace code                        | US         |
| asin          | String  | asin                                    | B07Z82895W |
| relations     | Integer | the number of related asin              | 1848       |
| freeRelations | Integer | associated traffic without sponsored    | 1414       |
| paidRelations | Integer | associated traffic with sponsored       | 286        |
| calcTime      | Long    | last calculated time                    |            |
| items         | List    | result set                              |            |
| └relation    | String  | relation type，see table2.2,ignore case | vav        |
| └count       | Integer | the number of relation                  | 3          |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffic/listing/stat \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","asinList":["B07Z82895W"]}' \
--compressed
```

### Related Products

* Request URI：**POST**  /v1/traffic/listing/page

#### Request parameter

| Name        | Type    | Description                                             | Example       | Required |
| ------------- | --------- | --------------------------------------------------------- | --------------- | ---------- |
| marketplace | String  | marketplace code,see table 1.2                          | US            | ✓       |
| asinList    | List    | Collection of asin                                      | [B07Z82895W]  | ✓       |
| relations   | List    | Collection of relation type，see table 2.2，default vav | [vav,bab]     |         |
| variations  | Boolean | Whether to query variation ASINs                        |              |         |
| page        | Integer | Base on 1                                               | Default 1     |         |
| size        | Integer |                                                        | Default 50    |         |
| order       | Object  |                                                        |               |         |
| └field     | String  |                                                        | See table 2.2 |         |
| └desc      | boolean |                                                        | Default true  |         |

#### Response parameter

| Name           | Type    | Description                                | Example                                                                                                                                 |
| ---------------- | --------- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| asin           | String  | asin                                       | B078J8VPVW                                                                                                                              |
| brand          | String  |                                            | Pampers                                                                                                                                 |
| brandUrl       | String  |                                            | [https://www.amazon.com/s?k=HP](https://www.amazon.com/s?k=HP)                                                                             |
| imageUrl       | String  |                                            | [https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL .AC_US200.jpg](https://images-na.ssl-images-amazon.com/images/I/51axlzme6aL) |
| title          | String  |                                            | Diapers Size 2, 186 Count - Pampers Swaddlers Disposable Baby Diapers, ONE MONTH SUPPLY                                                 |
| parent         | String  | parent asin                                | B081RGNL17                                                                                                                              |
| nodeId         | Long    | product node id                            | 3741281                                                                                                                                 |
| nodeIdPath     | String  | complete node id paths, separated by colon | 2619525011:3741271:3741281                                                                                                              |
| nodeLabelPath  | String  |                                            | Baby Products:Diapering:Disposable Diapers                                                                                              |
| bsrId          | String  | bsr id                                     | office-products                                                                                                                         |
| bsr            | Integer | bsr rank                                   | 1                                                                                                                                       |
| units          | Integer | monthly sales volume                       | 26289                                                                                                                                   |
| unitsCr        | Float   | monthly sales volume growth rate           | -46.3                                                                                                                                   |
| revenue        | Float   | monthly sales amount                       | 1693537.4                                                                                                                               |
| price          | Float   |                                            | 64.42                                                                                                                                   |
| profit         | Float   |                                            | 63.92                                                                                                                                   |
| fba            | Float   |                                            | 13.58                                                                                                                                   |
| ratings        | Integer |                                            | 32004                                                                                                                                   |
| ratingsRate    | Float   | retention rate                             | 40.57                                                                                                                                   |
| rating         | Float   |                                            | 4.8                                                                                                                                     |
| ratingsCv      | Integer | number of monthly growth in ratings        | 10666                                                                                                                                   |
| ratingDelta    | Integer | number of new comments in the last 30 days | 0                                                                                                                                       |
| availableDate  | Long    | shelf time,millisecond format              | 1454083200000                                                                                                                           |
| fulfillment    | String  |                                            | AMZ or FBA or FBM                                                                                                                       |
| variations     | Integer |                                            | 7                                                                                                                                       |
| sellers        | Integer |                                            | 7                                                                                                                                       |
| sellerId       | String  |                                            | A1Y8BVAASXO4R7                                                                                                                          |
| sellerName     | String  |                                            | Amazon                                                                                                                                  |
| sellerNation   | String  |                                            | see table 1.5                                                                                                                           |
| badge          | Badge   | badge object                               |                                                                                                                                         |
| └bestSeller   | String  | whether to contains best-seller            | Y/N                                                                                                                                     |
| └amazonChoice | String  | whether to contains Amazon's choice        | Y/N                                                                                                                                     |
| └newRelease   | String  | whether to contains newRelease             | Y/N                                                                                                                                     |
| └ebc          | String  | whether to contains A+                     | Y/N                                                                                                                                     |
| └video        | String  | whether to contains video                  | Y/N                                                                                                                                     |
| weight         | String  |                                            | 8.88 pounds                                                                                                                             |
| dimension      | String  |                                            | 13.3 x 15.8 x 10.6 inches                                                                                                               |
| dimensionType  | String  |                                            | ST,0V                                                                                                                                   |
| sku            | String  |                                            | ["Color: Beige","Size: 47 inches"]                                                                                                      |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffic/listing' \
-H 'secret-key: your secret key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","asinList":["B07Z82895W"]}' \
--compressed
```

### Keyword Distribution

* Request URI：**POST** /v1/traffic/source

#### Request parameter

| Name        | Type    | Description                                                                                                                 | Example       | Required |
| ------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------- |
| marketplace | String  | marketplace code,see table 1.2                                                                                              | US            | ✓       |
| q           | String  | The query asin,or keywords                                                                                                  | B07Z82895W    | ✓       |
| month       | String  | query month, yyyyMM format, default last 30 days                                                                            | 202210        | ✓       |
| page        | Integer |                                                                                         | 1            | ✓       |
| size        | Integer |                                                                                            |  20   | ✓       |
| order       | Object  |                                                                            |         | ✓       |
| -field      | String  | sort field | See table 2.4 |         |
| -desc       | Boolean | True or false                                                                                                               |              |         |

#### Response parameter

| Name              | Type             | Description              | Example                                                                                                                       |
| ------------------- | ------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| keywords          | Integer          | All traffic terms | 1423                                                                                                                    |
| searchKeywords    | Integer          | Natural search terms      |        23                                                                                                                      |
| acKeywords        | Integer          | AC Recommendation     |        43                                                                                                                      |
| editorialKeywords | Integer          | ER Recommendation      |     234                                                                                                                         |
| fourStarsKeywords | Integer          | 4-star recommendation        |    234                                                                                                                 |
| hrKeywords        | Integer          | HR Recommendation   |                    234                                                                                                          |
| adKeywords        | Integer          | SP advertising slogan       |             214                                                                                                                |
| videoKeywords     | Integer          | Video advertising slogans   |              453                                                                                                                |
| brandKeywords     | Integer          | Brand advertising slogan |                 223                                                                                                             |
| badgeLabels       | List             | Overview of traffic sources   | ["SEARCH", "OFFICIAL", "AD"]                                                                                                  |
| badgeDetails      | Map |         Traffic source details   | {"SEARCH": ["NATURAL_SEARCHING"],"OFFICIAL": ["AMAZON_CHOICE"]} |
| asinInfo          | Object           |  Asin related information    |                                                                                                                              |
| -asin             | String            |  asin                   |            B078J8VPVW                                                                                                  |
| -asinUrl          | String            |  asin url                   |           https://www.amazon.com/dp/B08GHW4TBS                                                       |
| -currency         | String            |  Currency code               |      $                                                                                                                        |
| -price            | Float            |    price                |         23                                                                                                                     |
| -rating           | Float            |   score                   |        32                                                                                                                      |
| -reviews          | Integer          |  Score evaluation        |          354                                                                                                                    |
| -sku              | String            |     SKU                    |    ["Color: Beige","Size: 47 inches"]                   |
| -title            | String            |      title                    |                       |
| -variations       | Integer          | Number of variants |                    2                                                                                                          |

#### Request example

```
curl 'https://api.sellersprite.com/v1/traffic/source \
-H 'secret-key: Your Key' \
-H 'content-type: application/json;charset=UTF-8' \
--data-raw $'{"marketplace":"US","q":"B07Z82895W","month":"202210"}' \
--compressed
```

### BSR Sales Estimator

* Request URI：**GET** /v1/sales/prediction/bsr

#### Request parameter

| Name            | Type         | Description                       | Example       | Required |
| ----------------- | -------------- | ---------------------------------- | ----------------- | -------------- |
| marketplace | String   | marketplace,see table 1.2                 | US          | ✓       |
| bsr                 | Integer  | Ranking of major categories | 1024        | ✓       |
| categoryId  | String   | First level category node, **Product node** interface return | 11260432011 | ✓     |

#### Response parameter

| Name              | Type             | Description              | Example                                                                                |
| ------------------- | ------------------ | -------------------------- | --------------------------------------------------------------------------------- |
| marketplace     | String  | marketplace         | US         |
| --------------------- | ------------- | ------------------ | ---------------- |
| bsr             | Integer | 1            | B07Z82895W |
| categoryLabel   | String  | Category name | 2685       |
| estDailySales   | Integer | Forecast daily sales| 99         |
| estMonthSales   | Integer | Forecast 30 day sales | 2965       |
| itemList        | List    | detail         |                |
| └bsr           | Integer | bsr          | 1          |
| └estDailySales | Integer | Forecast daily sales   | 99         |
| └estMonthSales | Integer |Forecast 30 day sales | 2965       |

#### Request example

```
curl 'https://api.sellersprite.com/v1/sales/prediction/bsr?
bsr=2&categoryId=11260432011&marketplace=US' \
  -H 'secret-key: Your Key' \
  -H 'content-type: application/json;charset=UTF-8' \
  --compressed
```
### ASIN Sales Estimator

* Request URI：**GET** /v1/sales/prediction/asin

#### Request parameter

| Name            | Type         | Description                       | Example       | Required |
| ----------------- | -------------- | ---------------------------------- | ----------------- | -------------- |
| marketplace | String   | marketplace,see table 1.2                 | US          | ✓       |
| asin          | String  | asin                                    | B07Z82895W | ✓       |

#### Response parameter

| Name              | Type             | Description              | Example                                                                                |
| ------------------- | ------------------ | -------------------------- | --------------------------------------------------------------------------------- |
| asinDetail      | Object  | asin detail       |                                                                                                                                                                               |
| --------------------- | ------------- | -------------------- | ------------------------------------------------------------------------------------- |
| └asin          | String  | asin           | B00CFM8DI2                                                                                                                                                                |
| └title         | String  | title           | Boot Bananas Original Shoe Deodorizer  | 
| └brand         | String  | brand           | Boot Bananas                                                                                                                                                              |
| └availableDate | Long    | Listing time       | 1397001600000                                                                                                                                                             |
| └category      | String  | Category name      | Clothing, Shoes & Jewelry                                                                                                                                                 |
| └categoryId    | String  | Category  Id| 7141123011                                                                                                                                                                |
| └imageUrl      | String  | image url        | https://images-na.ssl-images-amazon.com/images/I/41AGxmiW-vL._AC_US600_.jpg                                                                                               |
| └ratings       | Integer | Score evaluation         | 32004                                                                                                                                                                     |
| └rating        | Float   | rating value        | 4.6                                                                                                                                                                       |
| dailyItemList   | List    | Daily sales forecast details |                                                                                                                                                                               |
| └date          | String  | date           | 2023-04-19                                                                                                                                                                |
| └bsr           | Integer | bsr            | 48614                                                                                                                                                                     |
| └sales         | Integer | sales           | 14                                                                                                                                                                        |
| └amount        | Float   | sales volume          | 200                                                                                                                                                                       |
| └price         | Float   | price           | 20                                                                                                                                                                        |
| monthItemList   | List    | Monthly Sales Forecast Details |                                                                                                                                                                               |
| └date          | String  | date           | 2023-04                                                                                                                                                                   |
| └sales         | Integer | sales           | 14                                                                                                                                                                        |
| └amount        | Float   | sales volume | 200                                                                                                                                                                       |
| └price         | Float   | price           | 20                                                                                                                                                                        |

#### Request example

```
curl 'https://api.sellersprite.com/v1/sales/prediction/asin?
asin=B08C7HDF1F&marketplace=US' \
  -H 'secret-key: You Key' \
  -H 'content-type: application/json;charset=UTF-8' \
  --compressed
```

### OCR

* Request URI：**GET** /v1/ocr/identify
* Request Content-Type:multipart/form-data

#### Request parameter

| Name            | Type         | Description                       | Example       | Required |
| ----------------- | -------------- | ---------------------------------- | ----------------- | -------------- |
| type     | Integer  | 0：Remote Pictures；1：Base64 string；2：Picture files   | 2                                                                                                                                                   | ✓       |
| fn       | String   | Language types to be recognized: CHINESE Or LATIN| CHINESE                                                                                                                                             | ✓       |
| url      | String   | remote url                                     | |              |
| base64   | String   | Base64 string                                |                                                                                                                                                         |              |
| image    | File     | Uploaded files                                 | C:\fakepath\photo.jpeg

#### Response parameter

| Name              | Type             | Description              | Example                                                                                   |
| ------------------- | ------------------ | -------------------------- | ------------------------------------------------------------------- |
| data          | String          | Recognized text | sellersprite                                                                                                                    |
| code    | String          |      status code                    |      OK                                                                                                                        |
| message        | String          |                          |                                                                                                                              |

#### Request example

```
curl 'https://api.sellersprite.com/v1/ocr/identify' \
  -H 'secret-key:  Your Key' \
  -H 'content-type: multipart/form-data' \
  -F 'image=@/home/image/photo.jpeg' -F 'base64=' -F 'fn=CHINESE' -F 'type=2' -F 'url=' \
  --compressed
```

### Appendix

#### Table 1.1 Query month

| Value              | description           |
| -------------------- | ----------------------- |
| nearly             | last 30 days          |
| formated as yyyyMM | example:202202202213  |

#### Table 1.2 Marketplace code

| Value | Description    |
| ------- | ---------------- |
| US    | United States  |
| UK    | United Kingdom |
| DE    | Germany        |
| FR    | France         |
| JP    | Japan          |
| CA    | Canada         |
| IT    | Italy          |
| ES    | Spain          |

#### Table 1.3 Release date

| Value | Description   |
| ------- | --------------- |
| null  | no limitation |
| 1     | last 30 days  |
| 3     | last 3 months |
| 6     | last 6 months |
| 12    | last 1 year   |
| 24    | last 2 years  |

#### Table 1.4 Product size

* U.S. Market

| Value | Description          |
| ------- | ---------------------- |
| ST    | Small standard size  |
| LS    | Large standard size  |
| SO    | Small oversize       |
| MO    | Medium oversize      |
| LO    | Large oversize       |
| SP    | Special large pieces |
| O     | Other                |

* Japanese Market

| Value | Description      |
| ------- | ------------------ |
| SM    | small            |
| ST    | standard         |
| OV    | oversize         |
| SS    | Extra large size |
| O     | Other            |

* UK, France, Germany, Italy, Spain markets

| Value | Description       |
| ------- | ------------------- |
| SL    | Small envelope    |
| NL    | Standard envelope |
| LL    | Large envelope    |
| SD    | Standard package  |
| SB    | Small oversize    |
| NB    | Standard oversize |
| LB    | Large oversize    |
| O     | Other             |

* Canada Market

| Value | Description |
| ------- | ------------- |
| EN    | Envelope    |
| ST    | Standard    |
| OS    | Oversize    |
| O     | Other       |

#### Table 1.5 Seller's Nationality

| Value | Description     |
| ------- | ----------------- |
| CN    | China           |
| HK    | Hong Kong,China |
| US    | United States   |
| JP    | Japan           |
| DE    | Germany         |
| FR    | France          |

See link for 2-character codes for other countries：[http://www.mamicode.com/info-detail-1583748.html](http://www.mamicode.com/info-detail-1583748.html)

#### Table 1.6 Product research and competitor lookup sorting fields

| Value                | Description                             |
| ---------------------- | ----------------------------------------- |
| total_units          | monthly sales volume                    |
| total_amount         | monthly sales amount                    |
| bsr_rank             | bsr rank                                |
| price                |                                         |
| rating               |                                         |
| reviews              |                                         |
| profit               |                                         |
| reviews_rate         |                                         |
| available_date       |                                         |
| questions            | Q & A                                   |
| total_units_growth   | monthly sales volume growth rate        |
| total_amount_growth  | monthly sales amount growth rate        |
| reviews_increasement |                                         |
| bsr_rank_cv          | number of BSR growth in the last 7 days |
| bsr_rank_cr          | last 7 days BSR growth rate             |

#### Table 1.7 Marketplace Granularity

| Value       | Description                  |
| ------------- | ------------------------------ |
| N           | normal                       |
| S1,S2,S3    | January to March peak season |
| S4,S5,S6    | April to June peak season    |
| S7,S8,S9    | July-September peak season   |
| S10,S11,S12 | October-December peak season |
| I           | Continuous Growth Markets    |
| D           | Continued recession market   |

#### Table 1.8 Keyword research sorting fields

| Value                 | Description |
| ----------------------- | ------------- |
| searches              |             |
| keywordsIsHide        |             |
| searches_growth       |             |
| yearly_growth_rate    |             |
| growth_rate_trend_min |             |
| monopoly_click_rate   |             |
| goods_value           |             |

#### Table 1.9 Keyword research trends sorting fields

| Value               | Description |
| --------------------- | ------------- |
| searchfrequencyrank |             |
| n1RankGrowthValue   |             |
| n1RankGrowthRate    |             |
| monopolyClickRate   |             |

#### Table 1.10 Reverse ASIN exposure position

| Value                    | Description |
| -------------------------- | ------------- |
| naturalSearching         |             |
| amazonChoice             |             |
| editorialRecommendations |             |
| fourStar                 |             |
| highlyRated              |             |
| sponsorBrand             |             |
| sponsorVideo             |             |
| ads                      |             |

#### Table 2.0 Reverse ASIN share type

| Value           | Description                        |
| ----------------- | ------------------------------------ |
| primary         | primary traffic share type         |
| precise         | precise traffic share type         |
| preciseLongTail | preciseLongTail traffic share type |

#### Table 2.1 Reverse ASIN conversion type

| Value     | Description                       |
| ----------- | ----------------------------------- |
| excellent | excellent traffic conversion type |
| stable    | stable traffic conversion type    |
| lost      | lost traffic conversion type      |
| invalid   | invalid traffic conversion type   |

#### Table 2.2 Related Products association type

| Value | Description               |
| ------- | --------------------------- |
| mib   | Make it bundle            |
| fbt   | frequency bought together |
| csi   | compare similar items     |
| cob   | consider our brands       |
| mie   | more items explore        |
| bab   | bought also bought        |
| vav   | viewd also viewd          |
| avp   | also viewd product        |
| bav   | buy after viewing         |
| asf   | also shoped for           |
| cpf   | climate pledge friendly   |
| bca   | brands category amazon    |
| fsa   | four star above           |
| sp    | sponsored products        |

#### Table 2.3 Reverse ASIN list sorting field

| Value             | Description |
| ------------------- | ------------- |
| rankPosition      |             |
| adPosition        |             |
| createdTime       |             |
| searchesRank      |             |
| searches          |             |
| purchases         |             |
| purchaseRate      |             |
| products          |             |
| supplyDemandRatio |             |
| latest1daysAds    |             |
| bid               |             |
| trafficPercentage |             |

#### Table 2.4 Keyword Distribution list sorting field

| Value       | Description |
| ------------- | ------------- |
| keyword     |             |
| nk          |             |
| ac          |             |
| er          |             |
| fs          |             |
| hr          |             |
| spb         |             |
| spv         |             |
| ads         |             |
| updatedTime |             |

#### Table 2.5 Reverse Multiple ASINs sorting field

| **Value**            | **Description**       |
| ----------------------- | ---------------- |
| trafficPercentage |   Related ASINs |
| relationAsin      | Related ASINs   |
| searchesRank      | ABA Rank/W  |
| searches          |    M. Searches|
| purchases         |  M. Purchase  |
| purchaseRate      | Purchase Rate     |
| spr               | spr        |
| titleDensity      | Title Density   |
| products          | Products     |
| supplyDemandRatio | DSR     |
| adProduct         | Sponsored ASINs |
| monopolyClickRate | Click Concentration |
| bid               | PPC Bid    |
