## Activities
> Example fetching activities for the current application:

```shell
curl -i -H "Authorization: Bearer $ACCESS_TOKEN" https://platform.pokitdok.com/api/v4/activities/
```

```python
#retrieve an index of activities
pd.activities()
```

```ruby
#retrieve an index of activities
pd.activities
```

```csharp
// retrieve an index of activities
client.activities();
```

```java
pd.activities();
```

> Example fetching information for a specific activity:

```shell
curl -i -H "Authorization: Bearer $ACCESS_TOKEN" https://platform.pokitdok.com/api/v4/activities/5317f51527a27620f2ec7533
```

```python
#check on a specific activity
pd.activities(activity_id='5362b5a064da150ef6f2526c')
```

```ruby
#check on a specific activity
pd.activities({activity_id: '5362b5a064da150ef6f2526c'})
```

```csharp
// check on a specific activity
client.activities("5362b5a064da150ef6f2526c");
```

```java
HashMap<String, String> params = new HashMap<String, String>();
params.add("activity_id", "5362b5a064da150ef6f2526c");
client.activities(params);

```

> Example to cancel an existing activity:

```shell
curl -XPUT -i -H "Content-Type: application/json"
-H "Authorization: Bearer $ACCESS_TOKEN"
-d '{"transition": "cancel"}' https://platform.pokitdok.com/api/v4/activities/5317f51527a27620f2ec7533
```

*Available modes of operation: real-time*

The Activities endpoint is used to track the life cycle of a transaction.  Results returned will follow the states through which an Activity flows in the PokitDok platform. Long-running operations are performed asynchronously. Upon initiating those operations via an API endpoint, activity tracking information is returned to the caller, which can be used to query the status of the activity later on.
Throughout processing, activities may transition through the following states:

State             | Description
------------------|--------------------------------------------------------------------------------------
init              | The activity is initializing.
queued            | The activity is in queue waiting to start/resume.
scheduled         | The activity is scheduled for the next available transmission to the trading partner.
generating        | The activity is generating X12 transactions.
processing        | The activity is processing X12 transactions that have been received.
fallback          | The activity is enacting fallback action.
transmitting      | The activity is transmitting X12 transactions to the trading partner.
waiting           | The activity is waiting on a trading partner response.
receiving         | The activity is receiving X12 transactions from a trading partner.
paused            | The activity is paused.
notifying         | The activity is notifying the client application about activity results if a callback url was defined in the request.
stored            | The activity has stored uploaded batch transactions for later processing.
completed         | The activity has received acknowledgement by the trading partner. Completed activities may receive additional         responses.
canceled          | The activity was canceled by the client application.
failed            | The activity was unable to process successfully.
rejected          | The activity has been rejected by the trading partner for reasons outlined in the response.
rejected_reviewed | The activity has been rejected by the trading partner and reviewed for errors by the PokitDok team.


Information concerning the activity’s progression through the system is available via the API Dashboard, as well as the endpoints listed below.

Available Activity Endpoints:


Endpoint | HTTP Method | Description
-------- | ----------- | -----------
/activities/ | GET | List current activities. A query string parameter ‘parent_id’ may also be used with this API to get information about sub-activities that were initiated from a batch file upload.
/activities/{id} | GET | Return detailed information about the specified activity. API applications will receive an activity ID in the API response for all operations that are asynchronous.
/activities/{id} | PUT | Used for canceling pending activities that a client application no longer wishes to execute.


The /activities/ response includes the following fields:

<a name="activities_response"></a>

Field | Type | Description
----- | ---- | -----------
callback_url | {string} | The URL that will be invoked to notify the client application that this Activity has completed. You must use https for callback URLs used by your application. For added security, a callback URL can be defined in the application.
history | {array} | Historical status of the progress of this Activity.
id | {string} | ID of this Activity.
name | {string} | Activity name.
trading_partner_id | {string} | Unique id for the intended trading partner, as specified by the Trading Partners endpoint.
parent_id | {string} | Id only present on sub-activities that were initiated via a batch file upload of activities.
parameters | {dict} | The parameters that were originally supplied to the activity.
remaining_transitions | {array} | The list of remaining state transitions that the activity has yet to go through.
result | {dict} | The result of the activity processing.  This will be populated with the latest response from a trading partner.
result_history | {array} | A list of result values that have been received from a trading partner.  This list will be present when a request results in more than one response from a trading partner.  The most recent response will always be available in the result field for convenience.
state | {dict} | Current state of this Activity.
transition_path | {array} | The list of state transitions that will be used for this Activity.
units_of_work | {int} | The number of 'units of work' that the activity is operating on. This will typically be 1 for real-time requests like /eligibility/. When uploading batch X12 files via the /files/ endpoint, this will be the number of ‘transactions’ within that file. For example, if a client application POSTs a file of 20 eligibility requests to the /files/ API, the units_of_work value for that activity will be 20 after the X12 file has been analyzed. If an activity does show a value greater than 1 for units_of_work, the client application can fetch detailed information about each one of the activities processing those units of work by using the /activities/?parent_id=<activity_id> API.

