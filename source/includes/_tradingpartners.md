## Trading Partners
> Example fetching trading partner information:

```shell
curl -i -H "Authorization: Bearer $ACCESS_TOKEN" https://platform.pokitdok.com/api/v4/tradingpartners/
```

```python
client.trading_partners()
```

```csharp
client.tradingPartners();
```

```ruby
client.trading_partners
```

```java
client.tradingPartners();
```

>Example response (for a more complete response please use the test application):

```json
[
  {
    "enrollment_required": [],
    "id": "aetna",
    "is_enabled": true,
    "name": "Aetna",
    "supported_transactions": [
      "276",
      "270",
      "278",
      "837"
    ]
  },
  {
    "enrollment_required": [],
    "id": "aetna_affordable_health_src",
    "is_enabled": true,
    "name": "Aetna Affordable Health Choices SM SRC",
    "supported_transactions": [
      "837"
    ]
  },
  {
    "enrollment_required": [],
    "id": "aetna_better_health",
    "is_enabled": true,
    "name": "Aetna Better Health",
    "supported_transactions": [
      "276",
      "837",
      "270"
    ]
  }
]
```

> Example fetching information for a specific trading partner:

```shell
curl -i -H "Authorization: Bearer $ACCESS_TOKEN" https://platform.pokitdok.com/api/v4/tradingpartners/aetna
```

```python
client.trading_partners('aetna')
```

```csharp
client.tradingPartners("MOCKPAYER");
```

```ruby
client.trading_partners('aetna')
```

```java
client.tradingPartners("aetna");
```

> Example response:

```json
{
  "enrollment_required": [],
  "id": "aetna",
  "is_enabled": true,
  "metrics": {
    "real_time_response_average": 3003.6001872586876,
    "real_time_response_percentiles": {
      "50": 2003.67335,
      "75": 2966.8265625,
      "95": 8257.593599999927
    }
  },
  "monitoring": {
    "eligibility": {
      "last_updated": "2016-06-25T11:42:30.546000",
      "status": "available"
    }
  },
  "name": "Aetna",
  "supported_search_options": [
    "no_id_search",
    "no_first_name_search",
    "no_birth_date_search",
    "no_name_search",
    "primary_search"
  ],
  "supported_transactions": [
    "270",
    "837",
    "276",
    "278"
  ]
}
```

*Available modes of operation: real-time*

The Trading Partners endpoint provides access to the collection of PokitDok's trading
partners.

Available Trading Partner endpoints:

| Endpoint              | HTTP Method | Description                                                                                   |
|:----------------------|:------------|:----------------------------------------------------------------------------------------------|
| /tradingpartners/     | GET         | Get a list of trading partners.                                                               |
| /tradingpartners/{id} | GET         | Retreive the data for a specified trading partner; the ID is the PokitDok trading partner id. |


The /tradingpartners/ response contains the following fields:

| Field                                  | Type      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         															|
|:---------------------------------------|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                                     | {string}  | The "trading_partner_id" used in requests to identify this trading partner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               																	|
| is_enabled                             | {boolean} | Indicates if the connection to the trading partner is enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     															|
| name                                   | {string}  | Full name for the trading partner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  															|
| supported_transactions                 | {array}   | Identifies the X12 transaction sets (270, 276, 278, 837, etc.) available for a trading partner. The list of supported transactions indicates the API Endpoints that are enabled for the trading partner.                                                                                                                                                                                                                                                                                                                                                                                      																																																																																												|
| enrollment_required                    | {array}   | Identifies the X12 transaction sets (270, 276, 278, 837, etc.) that require additional set up before transacting.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       																																																						|
| metrics                                | {object}  | When a specific trading partner id is requested and metrics are available, they will be included in the response. Timings are in milliseconds unless otherwise specified. Field returned only for /tradingpartners/{id} request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          	|
| metrics.real_time_response_average     | {float}   | The average response time (milliseconds) for requests to this trading partner. Field returned only for /tradingpartners/{id} request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      	|
| metrics.real_time_response_percentiles | {float}   | Provides a percentile rank of the trading partner's response times, with the following groupings: 50%, 75%, and 95%. Field returned only for /tradingpartners/{id} request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                	|
| monitoring                             | {object}  | When a specific trading partner id is requested and monitoring data is available, monitoring information will be included in the response. Each key in the monitoring section corresponds to the name of an API where connectivity is enabled (e.g. authorizations, claim_status, eligibility, etc). Each API name will be associated with a monitoring status value and a timestamp to indicate when the status was last updated. Field returned only for /tradingpartners/{id} request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 	|
| monitoring.{api_name}.status           | {string}  | The most recent status for the trading partner/API combination as returned by our monitoring system. Possible values include: available, unavailable, delayed, and unknown. A status of "available" indicates that the trading partner is operating normally based successful transactions executing within their average response time range. A status of "unavailable" indicates that the trading partner is unable to respond normally at that time. This may be due to scheduled or unplanned downtime. A status of "delayed" indicates that the trading partner is able to respond successfully to requests but that response times are higher than their average response time. A status of "unknown" will be returned for new trading partners that have just been added to the system and also for cases where the monitoring system encounters an exception and is unable to determine the current status. Field returned only for /tradingpartners/{id} request. 	|
| monitoring.{api_name}.last_updated     | {datetime}| The date the monitoring status was last updated. Field returned only for /tradingpartners/{id} request. In ISO8601 format (YYYY-MM-DDThh:mm:ss.ssssss).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| restricted_transactions                | {array}   | Identifies the X12 transaction sets (270, 278, 837) that require NPI submission in the client dashboard prior to use. Field returned only for /tradingpartners/{id} request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           						|
| supported_search_options               | {array}   | A list of member search options that are supported by the trading partner for eligibility requests.  A complete listing of possible [search options](#search-options) is included below.																																																																																																																																																																																														|


<a name="search-options"></a>
Full list of possible search options that may be available for use with a trading partner on eligibility requests.
These constants align with Section 1.4.8 (Search Options) of the X12 270/271 specification around the use of available
member information to locate the member in the trading partner's system.


| Search Option                               | Description
|:--------------------------------------------|:----------------|
| primary_search                              | first_name, last_name, id, and birth_date are provided to locate a member.  This is the search option supported by most trading partners. |
| primary_search_gender                       | first_name, last_name, id, birth_date, and gender are provided to locate a member.                |
| no_first_name_search                        | last_name, id, and birth_date are provided to locate a member.                |
| no_birth_date_search                        | first_name, last_name, and id are provided to locate a member.               |
| no_name_search                              | id and birth_date are provided to locate a member.               |
| no_id_search                                | first_name, last_name and birth_date are provided to locate a member.               |
