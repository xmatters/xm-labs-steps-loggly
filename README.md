# Loggly Steps

These steps allow you to send and retieve data from Loggly.


---------

<kbd>
<a href="https://support.xmatters.com/hc/en-us/community/topics">
   <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</a>
</kbd>

---------

# Files

* [LogglySteps.zip](LogglySteps.zip) - Workflow zip file with the step and example flow
* [solarwinds.png](/solarwinds.png) - Solarwinds logo

# How it works
These steps follow what is provided in the documentation for [sending](https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/api-sending-data.htm) and [retrieving](https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/api-retrieving-data.htm) data.


# Installation

## Loggly Setup
For retrieving data this only requires having a Loggly account.

For sending data you will need a customer token (not an API Token). Follow [these](https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/customer-token-authentication-token.htm) instructions provided by Solarwinds to find a token. Store this value in an xMatters constant and then provide the constant in the Token input of the **Loggly - Send Data** step.

## xMatters Setup
1. Download the [LogglySteps.zip](LogglySteps.zip) file onto your local computer
2. Navigate to the Workflows tab of your xMatters instance
3. Click Import, and select the zip file you just downloaded

For using the **Loggly - Retrieve Data** step:
1. Create an Endpoint with the Basic Authentication type that connects to loggly. The URL Should be formed like so: "https://\<account\>.loggly.com". This should be the start of the URL when using Loggly normally.

For using the **Loggly - Send Data** step:
1. Create an Endpoint with no authentication that has the base URL `https://logs-01.loggly.com`


## Usage
Make sure you've created the appropriate endpoint for the step you are using. Find the instructions above in the **xMatters Setup**.

Steps included:
- **Loggly - Retrieve Data**
- **Loggly - Send Data**

## Retrieve Data

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| query | Yes | 0 | 2000 | query string for searching. '\*' returns everything. look here for more information: https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/search-query-language.htm | | No |
| from | No | 0 | 2000 | Start time for the search. Defaults to “-24h”. For more information look here https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/search-query-language.htm#time | | No |
| until | No | 0 | 2000 | End time for the search. Defaults to “now”. More info: https://documentation.solarwinds.com/en/Success_Center/loggly/Content/admin/search-query-language.htm#time | | No |
| order | No | 0 | 4 | Direction of results returned, either “asc” or “desc”. Defaults to “desc”. | | No |
| size | No | 0 | 2000 | Number of events to retrieve when calling the events endpoint for a given RSID. Results will be limited to 20000 characters. | | No |


### Outputs

| Name | Description |
| ---- | ----------  |
| events | The events retrieved |


## Send Data

### Inputs
| Name  | Required? | Min | Max | Help Text | Default Value | Multiline |
| ----- | ----------| --- | --- | --------- | ------------- | --------- |
| Token | Yes | 0 | 2000 | Customer token from Loggly. | | No |
| Data | Yes | 0 | 20000 | Data to send to logs. | | No |


## Example
This is what the provided flow looks like.

<kbd>
	<img src="/media/ExampleFlow.png">
</kbd>

