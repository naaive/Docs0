---
title: Get Activities by Accounts
---

## API Changes

GET `/platforms/notes/{platform}` -> GET `/decentralized/platform/{platform}`

Both endpoints serve the same purpose: to retrieve a list of activities from a specified decentralized platform. Previously, the request parameters were limited. The new version offers enhanced parameters and filtering options to improve usability and performance.

The updated endpoint includes more detailed filtering options such as timestamps, success status, and activity direction, ensuring more efficient and flexible retrieval of Open Information. This change reflects the need for more comprehensive data retrieval on the Open Web.

## Parameter Changes

### For Requests

| v0.4                                                               | v1.0                                                                                                                                                            |
| ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `platform` (required, string): The platform to query.              | **No change.** `platform` (required, string): Retrieve activities from the specified platform.                                                                  |
| `limit` (number, optional): Limits the number of records returned. | **Renamed.** `limit` (integer, optional): Specifies the number of activities to retrieve. By default, this is set to 100, and the maximum allowed value is 100. |
| `cursor` (string, optional): A string used for pagination.         | **No change.** `cursor` (string, optional): Specifies the cursor used for pagination.                                                                           |
|                                                                    | **New.** `action_limit` (integer, optional): Specifies the number of actions within the activity to retrieve.                                                   |
|                                                                    | **New.** `since_timestamp` (integer, optional): Retrieves activities starting from this timestamp. The timestamp is specified in Unix epoch time.               |
|                                                                    | **New.** `until_timestamp` (integer, optional): Retrieves activities up to this timestamp. The timestamp is specified in Unix epoch time.                       |
|                                                                    | **New.** `success` (boolean, optional): Retrieves activities based on success status.                                                                           |
|                                                                    | **New.** `direction` (string, optional): Retrieves activities based on direction. The direction specifies whether the activity is incoming or outgoing.         |
|                                                                    | **New.** `tag` (array of strings, optional): Retrieves activities for the specified tag(s).                                                                     |
|                                                                    | **New.** `type` (array of strings, optional): Retrieves activities for the specified type(s).                                                                   |
|                                                                    | **New.** `network` (array of strings, optional): Retrieves activities from the specified network(s).                                                            |

### For Responses

| v0.4                                                                                                                                                                                                                           | v1.0                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `address_status` (array of string): Contains the status of each queried address, reflecting the current state of the cache for that address. This helps users understand the timeliness and reliability of the data presented. | **Removed.** No longer needed as the Node version does not use caching for address indexing.                                                                      |
| `cursor` (string): A string used for pagination, indicating the position from which to continue fetching data in subsequent requests.                                                                                          | **Replaced.** `meta.cursor` (string): Contains metadata such as the pagination cursor for continuing the data fetch.                                              |
| `message` (string): A general message about the response, typically regarding the status of the request.                                                                                                                       | **Removed.** Due to low usage.                                                                                                                                    |
| `total` (number, nullable): The total number of items that match the query, which may be absent if not applicable.                                                                                                             | **Removed.** Providing a count is no longer meaningful and practical (adding unnecessary calculation time) due to the large amount of Open Information available. |
| `result` (array): An array of activities relevant to the queried platform.                                                                                                                                                     | **Replaced.** `data` (array): Lists the activities associated with the platform.                                                                                  |
| `result.actions` (array): Details of actions involved in the activity.                                                                                                                                                         | **Replaced.** `data.actions` (array): Upgraded protocol schema.                                                                                                   |
| `result.address_from` (string): The originating address of the activity.                                                                                                                                                       | **Replaced.** `data.from` (string): The originating account of the activity.                                                                                      |
| `result.address_to` (string): The destination address of the activity.                                                                                                                                                         | **Replaced.** `data.to` (string): The destination account of the activity.                                                                                        |
| `result.timestamp` (Time): Timestamps indicating the actual time of the activity.                                                                                                                                              | **Replaced.** `data.timestamp` (integer): Changed from a potentially more complex `Time` object to a simpler integer format.                                      |
| `result.fee` (nullable): The activity fee, which may be null.                                                                                                                                                                  | **Replaced.** `data.fee` (Fee): Detailed fee information for the activity.                                                                                        |
| `result.hash` (string): The hash of the activity.                                                                                                                                                                              | **Replaced.** `data.id` (string): A unique identifier for the activity.                                                                                           |
| `result.owner` (string): The owner of the address involved in the activity.                                                                                                                                                    | **No change.** `data.owner` (string)                                                                                                                              |
| `result.network` (string): The open information network on which the activity occurred.                                                                                                                                        | **Schema upgraded.** `data.network` (Network): The network on which the activity occurred.                                                                        |
| `result.platform` (string): The platform associated with the activity.                                                                                                                                                         | **Schema upgraded.** `data.platform` (Platform): The platform associated with the activity.                                                                       |
| `result.tag` (string): A tag related to the activity.                                                                                                                                                                          | **Schema upgraded.** `data.tag` (Tag): A tag related to the activity.                                                                                             |
| `result.type` (string): The type of the activity.                                                                                                                                                                              | **Schema upgraded.** `data.type` (string): The type of the activity.                                                                                              |
| `result.success` (boolean, nullable): Indicates whether the activity was successful.                                                                                                                                           | **No change.** `data.success` (boolean)                                                                                                                           |
|                                                                                                                                                                                                                                | **New.** `data.calldata` (Calldata): Details of the call made during the activity.                                                                                |
|                                                                                                                                                                                                                                | **New.** `data.direction` (Direction): The direction of the activity.                                                                                             |
|                                                                                                                                                                                                                                | **New.** `data.index` (integer): The index position of the activity in the list.                                                                                  |
|                                                                                                                                                                                                                                | **New.** `data.total_actions` (integer): The total number of actions within the activity.                                                                         |