--- 

title: API Reference 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

Sentry Public API 

**Version:** v0 

# /API/0/ORGANIZATION/{ORGANIZATION_SLUG}/MONITORS/{MONITOR_SLUG}/CHECKINS/
## ***GET*** 

**Description:** Retrieve a list of check-ins for a monitor

### HTTP Request 
`***GET*** /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |
| checkin_id | path | The id of the check-in | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Creates a new check-in for a monitor.

If `status` is not present, it will be assumed that the check-in is starting, and be marked as `in_progress`.

To achieve a ping-like behavior, you can simply define `status` and optionally `duration` and
this check-in will be automatically marked as finished.

Note: If a DSN is utilized for authentication, the response will be limited in details.

### HTTP Request 
`***POST*** /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 201 |  |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATION/{ORGANIZATION_SLUG}/MONITORS/{MONITOR_SLUG}/CHECKINS/{CHECKIN_ID}/
## ***PUT*** 

**Description:** Updates a check-in.

Once a check-in is finished (indicated via an `ok` or `error` status) it can no longer be changed.

If you simply wish to update that the task is still running, you can simply send an empty payload.

You may use `latest` for the `checkin_id` parameter in order to retrieve
the most recent (by creation date) check-in which is still mutable (not marked as finished).

### HTTP Request 
`***PUT*** /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/{checkin_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |
| checkin_id | path | The id of the check-in | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 208 | Already Reported |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/EVENTS/
## ***GET*** 

**Description:** Retrieves discover (also known as events) data for a given organization.

**Eventsv2 Deprecation Note**: Users who may be using the `eventsv2` endpoint should update their requests to the `events` endpoint outline in this document.
The `eventsv2` endpoint is not a public endpoint and has no guaranteed availability. If you are not making any API calls to `eventsv2`, you can safely ignore this.
Changes between `eventsv2` and `events` include:
- Field keys in the response now match the keys in the requested `field` param exactly.
- The `meta` object in the response now shows types in the nested `field` object.

Aside from the url change, there are no changes to the request payload itself.

**Note**: This endpoint is intended to get a table of results, and is not for doing a full export of data sent to
Sentry.

The `field` query parameter determines what fields will be selected in the `data` and `meta` keys of the endpoint response.
- The `data` key contains a list of results row by row that match the `query` made
- The `meta` key contains information about the response, including the unit or type of the fields requested

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/events/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| end | query | The end of the period of time for the query, expected in ISO-8601 format. For example `2001-12-14T12:34:56.7890` | No |  |
| environment | query | The name of environments to filter by. | No |  |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| project | query | The ids of projects to filter by. `-1` means all available projects. If this parameter is omitted, the request will default to using 'My Projects' | No |  |
| start | query | The start of the period of time for the query, expected in ISO-8601 format. For example `2001-12-14T12:34:56.7890` | No |  |
| statsPeriod | query | The period of time for the query, will override the start & end parameters, a number followed by one of: - `d` for days - `h` for hours - `m` for minutes - `s` for seconds - `w` for weeks  For example `24h`, to mean query data starting from 24 hours ago to now. | No |  |
| field | query | The fields, functions, or equations to request for the query. At most 20 fields can be selected per request. Each field can be one of the following types: - A built-in key field. See possible fields in the [properties table](/product/sentry-basics/search/searchable-properties/#properties-table), under any field that is an event property     - example: `field=transaction` - A tag. Tags should use the `tag[]` formatting to avoid ambiguity with any fields     - example: `field=tag[isEnterprise]` - A function which will be in the format of `function_name(parameters,...)`. See possible functions in the [query builder documentation](/product/discover-queries/query-builder/#stacking-functions)     - when a function is included, Discover will group by any tags or fields     - example: `field=count_if(transaction.duration,greater,300)` - An equation when prefixed with `equation|`. Read more about [equations here](https://docs.sentry.io/product/discover-queries/query-builder/query-equations/)     - example: `field=equation|count_if(transaction.duration,greater,300) / count() * 100`  | Yes |  |
| per_page | query | Limit the number of rows to return in the result. Default and maximum allowed is 100. | No |  |
| query | query | The search filter for your query, read more about query syntax [here](https://docs.sentry.io/product/sentry-basics/search/)  example: `query=(transaction:foo AND release:abc) OR (transaction:[bar,baz] AND release:def)`  | No |  |
| sort | query | What to order the results of the query by. Must be something in the `field` list, excluding equations. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 400 | Invalid Query |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/MEMBERS/{MEMBER_ID}/
## ***GET*** 

**Description:** Retrieve an organization member's details.

Will return a pending invite as long as it's already approved.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/members/{member_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| member_id | path | The member ID. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Remove an organization member.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/members/{member_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| member_id | path | The member ID. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | No Content |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/MONITORS/
## ***GET*** 

**Description:** Lists monitors, including nested monitor enviroments. May be filtered to a project or environment.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/monitors/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| project | query | The ids of projects to filter by. `-1` means all available projects. If this parameter is omitted, the request will default to using 'My Projects' | No |  |
| environment | query | The name of environments to filter by. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a new monitor.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/monitors/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/MONITORS/{MONITOR_SLUG}/
## ***GET*** 

**Description:** Retrieves details for a monitor.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |
| environment | query | The name of environments to filter by. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***PUT*** 

**Description:** Update a monitor.

### HTTP Request 
`***PUT*** /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete a monitor or monitor environments.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| monitor_slug | path | The slug of the monitor | Yes |  |
| environment | query | The name of environments to filter by. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 | Accepted |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/PROJECTS/
## ***GET*** 

**Description:** Return a list of projects bound to a organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/projects/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SCIM/V2/GROUPS
## ***GET*** 

**Description:** Returns a paginated list of teams bound to a organization with a SCIM Groups GET Request.
- Note that the members field will only contain up to 10000 members.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/scim/v2/Groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| startIndex | query | SCIM 1-offset based index for pagination. | No |  |
| filter | query | A SCIM filter expression. The only operator currently supported is `eq`. | No |  |
| count | query | The maximum number of results the query should return, maximum of 100. | No |  |
| excludedAttributes | query | Fields that should be left off of return values. Right now the only supported field for this query is `members`. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Permission Denied |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a new team bound to an organization via a SCIM Groups POST Request. Note that teams are always created with an empty member set. The endpoint will also do a normalization of uppercase / spaces to lowercase and dashes.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/scim/v2/Groups` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 400 | Bad input |
| 403 | Forbidden |
| 409 | Team slug already exists |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SCIM/V2/GROUPS/{TEAM_ID}
## ***GET*** 

**Description:** Query an individual team with a SCIM Group GET Request.
- Note that the members field will only contain up to 10000 members.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| team_id | path | The id of the team you'd like to query / update. | Yes |  |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***PATCH*** 

**Description:** Update a team's attributes with a SCIM Group PATCH Request. Valid operations are:

* Renaming a team:
```json
{
    "Operations": [{
        "op": "replace",
        "value": {
            "id": 23,
            "displayName": "newName"
        }
    }]
}
```
* Adding a member to a team:
```json
{
    "Operations": [{
        "op": "add",
        "path": "members",
        "value": [
            {
                "value": 23,
                "display": "testexample@example.com"
            }
        ]
    }]
}
```
* Removing a member from a team:
```json
{
    "Operations": [{
        "op": "remove",
        "path": "members[value eq "23"]"
    }]
}
```
* Replacing an entire member set of a team:
```json
{
    "Operations": [{
        "op": "replace",
        "path": "members",
        "value": [
            {
                "value": 23,
                "display": "testexample2@sentry.io"
            },
            {
                "value": 24,
                "display": "testexample3@sentry.io"
            }
        ]
    }]
}
```

### HTTP Request 
`***PATCH*** /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| team_id | path | The id of the team you'd like to query / update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete a team with a SCIM Group DELETE Request.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| team_id | path | The id of the team you'd like to query / update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SCIM/V2/USERS
## ***GET*** 

**Description:** Returns a paginated list of members bound to a organization with a SCIM Users GET Request.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/scim/v2/Users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| startIndex | query | SCIM 1-offset based index for pagination. | No |  |
| count | query | The maximum number of results the query should return, maximum of 100. | No |  |
| filter | query | A SCIM filter expression. The only operator currently supported is `eq`. | No |  |
| excludedAttributes | query | Fields that should be left off of return values. Right now the only supported field for this query is members. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a new Organization Member via a SCIM Users POST Request.
- `userName` should be set to the SAML field used for email, and active should be set to `true`.
- `sentryOrgRole` can only be `admin`, `manager`, `billing`, or `member`.
- Sentry's SCIM API doesn't currently support setting users to inactive,
and the member will be deleted if active is set to `false`.
- The API also does not support setting secondary emails.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/scim/v2/Users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SCIM/V2/USERS/{MEMBER_ID}
## ***GET*** 

**Description:** Query an individual organization member with a SCIM User GET Request.
- The `name` object will contain fields `firstName` and `lastName` with the values of `N/A`.
Sentry's SCIM API does not currently support these fields but returns them for compatibility purposes.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| member_id | path | The id of the member you'd like to query. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***PATCH*** 

**Description:** Update an organization member's attributes with a SCIM PATCH Request.
The only supported attribute is `active`. After setting `active` to false
Sentry will permanently delete the Organization Member.

### HTTP Request 
`***PATCH*** /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| member_id | path | The id of the member you'd like to query. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete an organization member with a SCIM User DELETE Request.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| member_id | path | The id of the member you'd like to query. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/STATS_V2/
## ***GET*** 

**Description:** Query event counts for your Organization.
Select a field, define a date range, and group or filter by columns.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/stats_v2/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| statsPeriod | query | This defines the range of the time series, relative to now. The range is given in a `<number><unit>` format. For example `1d` for a one day range. Possible units are `m` for minutes, `h` for hours, `d` for days and `w` for weeks.You must either provide a `statsPeriod`, or a `start` and `end`. | No |  |
| interval | query | This is the resolution of the time series, given in the same format as `statsPeriod`. The default resolution is `1h` and the minimum resolution is currently restricted to `1h` as well. Intervals larger than `1d` are not supported, and the interval has to cleanly divide one day. | No |  |
| start | query | This defines the start of the time series range as an explicit datetime, either in UTC ISO8601 or epoch seconds.Use along with `end` instead of `statsPeriod`. | No |  |
| end | query | This defines the inclusive end of the time series range as an explicit datetime, either in UTC ISO8601 or epoch seconds.Use along with `start` instead of `statsPeriod`. | No |  |
| groupBy | query | can pass multiple groupBy parameters to group by multiple, e.g. `groupBy=project&groupBy=outcome` to group by multiple dimensions. Note that grouping by project can cause missing rows if the number of projects / interval is large. If you have a large number of projects, we recommend filtering and querying by them individually.Also note that grouping by projects does not currently support timeseries interval responses and will instead be a sum of the projectover the entire period specified. | Yes |  |
| field | query | the `sum(quantity)` field is bytes for attachments, and all others the 'event' count for those types of events.  `sum(times_seen)` sums the number of times an event has been seen. For 'normal' event types, this will be equal to `sum(quantity)` for now. For sessions, quantity will sum the total number of events seen in a session, while `times_seen` will be the unique number of sessions. and for attachments, `times_seen` will be the total number of attachments, while quantity will be the total sum of attachment bytes. | Yes |  |
| project | query | The ID of the projects to filter by.  Use `-1` to include all accessible projects. | No |  |
| category | query | If filtering by attachments, you cannot filter by any other category due to quantity values becoming nonsensical (combining bytes and event counts).  If filtering by `error`, it will automatically add `default` and `security` as we currently roll those two categories into `error` for displaying. | No |  |
| outcome | query | See https://docs.sentry.io/product/stats/ for more information on outcome statuses. | No |  |
| reason | query | The reason field will contain why an event was filtered/dropped. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/TEAMS/
## ***GET*** 

**Description:** Returns a list of teams bound to a organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/teams/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| detailed | query | Specify "0" to return team details that do not include projects | No |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a new team bound to an organization.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/teams/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| name | query | The name of the team. | Yes |  |
| slug | query | Optional slug for the team. If not provided a slug is generated from the name. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| 400 | Bad Request |
| 403 | Forbidden |
| 404 | A team with this slug already exists. |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/EVENTS/{EVENT_ID}/SOURCE-MAP-DEBUG/
## ***GET*** 

**Description:** Retrieve information about source maps for a given event.
```````````````````````````````````````````
Return a list of source map errors for a given event.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/source-map-debug/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| project_slug | path | The slug of the project the resource belongs to. | Yes |  |
| event_id | path | The id of the event | Yes |  |
| frame_idx | query | Index of the frame that should be used for source map resolution. | Yes |  |
| exception_idx | query | Index of the exception that should be used for source map resolution. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/TEAMS/{ORGANIZATION_SLUG}/{TEAM_SLUG}/PROJECTS/
## ***GET*** 

**Description:** Return a list of projects bound to a team.

### HTTP Request 
`***GET*** /api/0/teams/{organization_slug}/{team_slug}/projects/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| team_slug | path | The slug of the team the resource belongs to. | Yes |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |
| 403 | Forbidden |
| 404 | Team not found. |

## ***POST*** 

**Description:** Create a new project bound to a team.

### HTTP Request 
`***POST*** /api/0/teams/{organization_slug}/{team_slug}/projects/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the resource belongs to. | Yes |  |
| team_slug | path | The slug of the team the resource belongs to. | Yes |  |
| name | query | The name of the project. | Yes |  |
| slug | query | Optional slug for the project. If not provided a slug is generated from the name. | No |  |
| platform | query | The platform for the project. | No |  |
| default_rules | query | Defaults to true where the behavior is to alert the user on every new issue. Setting this to false will turn this off and the user must create their own alerts to be notified of new issues. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |
| 400 | Bad Request |
| 403 | Forbidden |
| 404 | Team not found. |
| 409 | A project with this slug already exists. |

# /API/0/TEAMS/{ORGANIZATION_SLUG}/{TEAM_SLUG}/
## ***GET*** 

**Description:** Return details on an individual team.

### HTTP Request 
`***GET*** /api/0/teams/{organization_slug}/{team_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the team belongs to. | Yes |  |
| team_slug | path | The slug of the team to get. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Team not found |

## ***PUT*** 

**Description:** Update various attributes and configurable settings for the given team.

### HTTP Request 
`***PUT*** /api/0/teams/{organization_slug}/{team_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the team belongs to. | Yes |  |
| team_slug | path | The slug of the team to get. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | Team not found |

## ***DELETE*** 

**Description:** Schedules a team for deletion.

Note: Deletion happens asynchronously and therefore is not immediate. However once deletion has begun the state of a project changes and will be hidden from most public views.

### HTTP Request 
`***DELETE*** /api/0/teams/{organization_slug}/{team_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the team belongs to. | Yes |  |
| team_slug | path | The slug of the team to get. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Team not found |

# /API/0/TEAMS/{ORGANIZATION_SLUG}/{TEAM_SLUG}/STATS/
## ***GET*** 

**Summary:** Caution: this endpoint may change in the future without notice.

**Description:** Return a set of points representing a normalized timestamp and the number of events seen in the period.

Query ranges are limited to Sentry’s configured time-series resolutions.

### HTTP Request 
`***GET*** /api/0/teams/{organization_slug}/{team_slug}/stats/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the team belongs to. | Yes |  |
| team_slug | path | The slug of the team to get. | Yes |  |
| stat | query | The name of the stat to query `("received", "rejected")`. | No |  |
| since | query | A timestamp to set the start of the query in seconds since UNIX epoch. | No |  |
| until | query | A timestamp to set the end of the query in seconds since UNIX epoch. | No |  |
| resolution | query | An explicit resolution to search for (one of `10s`, `1h`, and `1d`). | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Team not found |

# /API/0/ORGANIZATIONS/
## ***GET*** 

**Description:** Return a list of organizations available to the authenticated session.  This is particularly useful for requests with an user bound context.  For API key based requests this will only return the organization that belongs to the key.

### HTTP Request 
`***GET*** /api/0/organizations/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| owner | query | Restrict results to organizations in which you are an organization owner. | No |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/EVENTIDS/{EVENT_ID}/
## ***GET*** 

**Description:** This resolves an event ID to the project slug and internal issue ID and internal event ID.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/eventids/{event_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the event ID should be looked up in. | Yes |  |
| event_id | path | The event ID to look up. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/
## ***GET*** 

**Description:** Return details on an individual organization including various details such as membership access, features, and teams.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization to look up. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***PUT*** 

**Description:** Update various attributes and configurable settings for the given organization.

### HTTP Request 
`***PUT*** /api/0/organizations/{organization_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization to update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/REPOS/
## ***GET*** 

**Description:** Return a list of version control repositories for a given organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/repos/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The organization short name. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/REPOS/{REPO_ID}/COMMITS/
## ***GET*** 

**Description:** Return a list of commits for a given repository.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/repos/{repo_id}/commits/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The organization short name. | Yes |  |
| repo_id | path | The repository ID. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/STATS/
## ***GET*** 

**Description:** This endpoint is deprecated in favor of [Organization Stats V2](/api/organizations/retrieve-event-counts-for-an-organization-v2/).

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/stats/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the event ID should be looked up in. | Yes |  |
| stat | query | The name of the stat to query `("received", "rejected", "blacklisted")`. | No |  |
| since | query | A timestamp to set the start of the query in seconds since UNIX epoch. | No |  |
| until | query | A timestamp to set the end of the query in seconds since UNIX epoch. | No |  |
| resolution | query | An explicit resolution to search for (one of `10s`, `1h`, and `1d`). | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SESSIONS/
## ***GET*** 

**Description:** Returns a time series of release health session statistics for projects bound to an organization.

The interval and date range are subject to certain restrictions and rounding rules.

The date range is rounded to align with the interval, and is rounded to at least one hour. The interval can at most be one day and at least one hour currently. It has to cleanly divide one day, for rounding reasons.

Apart from the query parameters listed below, this endpoint also supports the usual [pagination parameters](https://docs.sentry.io/api/pagination/).

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/sessions/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project | query | The ID of the projects to filter by.  Use `-1` to include all accessible projects. | Yes |  |
| field | query | The list of fields to query.  The available fields are   - `sum(session)`   - `count_unique(user)`   - `avg`, `p50`, `p75`, `p90`, `p95`, `p99`, `max` applied to `session.duration`. For example, `p99(session.duration)`. Session duration is [no longer being recorded](https://github.com/getsentry/sentry/discussions/42716) as of on Jan 12, 2023. Returned data may be incomplete.   - `crash_rate`, `crash_free_rate` applied to `user` or `session`. For example, `crash_free_rate(user)` | Yes |  |
| environment | query | The name of environments to filter by. | No |  |
| groupBy | query | The list of properties to group by.  The available groupBy conditions are `project`, `release`, `environment` and `session.status`.  Grouping by `session.status` does not work when `crash_rate` or `crash_free_rate` are queried. | No |  |
| orderBy | query | An optional field to order by, which must be one of the fields provided in `field`. Use `-` for descending order, for example `-sum(session)`.   This alters the order of the `groups` returned, so it only makes sense in combination with `groupBy`.   Ordering by more than one field is currently not supported. | No |  |
| query | query | A free-form query that is applied as a filter.  An example query could be `release:"1.1.0" or release:"1.2.0"`. | No |  |
| statsPeriod | query | This defines the range of the time series, relative to now.  The range is given in a `"<number><unit>"` format.  For example `1d` for a one day range. Possible units are `m` for minutes, `h` for hours, `d` for days and `w` for weeks.  It defaults to `90d`. | No |  |
| interval | query | This is the resolution of the time series, given in the same format as `statsPeriod`.  The default resolution is `1h` and the minimum resolution is currently restricted to `1h` as well.  Intervals larger than `1d` are not supported, and the interval has to cleanly divide one day. | No |  |
| statsPeriodStart | query | This defines the start of the time series range, in the same format as the `interval`, relative to now. | No |  |
| statsPeriodEnd | query | This defines the end of the time series range, in the same format as the `interval`, relative to now. | No |  |
| start | query | This defines the start of the time series range as an explicit datetime. | No |  |
| end | query | This defines the inclusive end of the time series range as an explicit datetime. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Time-series Session Statistics. |
| 400 | Wrong Parameters |
| 401 | Unauthorized |
| 403 | Forbidden |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/USERS/
## ***GET*** 

**Description:** Return a list of users that belong to a given organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/users/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the event ID should be looked up in. | Yes |  |
| project | query | Restrict results to users who have access to a given project ID | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SHORTIDS/{SHORT_ID}/
## ***GET*** 

**Description:** This resolves a short ID to the project slug and internal issue ID.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/shortids/{short_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the short ID should be looked up in. | Yes |  |
| short_id | path | The short ID to look up. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/PROJECTS/
## ***GET*** 

**Description:** Return a list of projects available to the authenticated session.

### HTTP Request 
`***GET*** /api/0/projects/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/
## ***GET*** 

**Description:** Return details on an individual project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the project belongs to. | Yes |  |
| project_slug | path | The slug of the project to retrieve. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Project not found |

## ***PUT*** 

**Description:** Update various attributes and configurable settings for the given project.  Only supplied values are updated.

### HTTP Request 
`***PUT*** /api/0/projects/{organization_slug}/{project_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the project belongs to. | Yes |  |
| project_slug | path | The slug of the project to update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | Project not found |

## ***DELETE*** 

**Description:** Schedules a project for deletion.

Deletion happens asynchronously and therefore is not immediate.
However once deletion has begun the state of a project changes and
will be hidden from most public views.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the project belongs to. | Yes |  |
| project_slug | path | The slug of the project to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Project not found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/FILES/DSYMS/
## ***GET*** 

**Description:** Retrieve a list of debug information files for a given project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the file belongs to. | Yes |  |
| project_slug | path | The slug of the project to list the DIFs of. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***POST*** 

**Description:** Upload a new debug information file for the given release.

Unlike other API requests, files must be uploaded using the
traditional multipart/form-data content-type.

The file uploaded is a zip archive of an Apple .dSYM folder which
contains the individual debug images.  Uploading through this endpoint
will create different files for the contained images.

### HTTP Request 
`***POST*** /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the project belongs to. | Yes |  |
| project_slug | path | The slug of the project to upload a file to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***DELETE*** 

**Description:** Delete a debug information file for a given project.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the file belongs to. | Yes |  |
| project_slug | path | The slug of the project to delete the DIF. | Yes |  |
| id | query | The ID of the DIF to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/USERS/
## ***GET*** 

**Description:** Return a list of users seen within this project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/users/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| query | query | Limit results to users matching the given query. Prefixes should be used to suggest the field to match on: `id`, `email`, `username`, `ip`. For example, `query=email:foo@example.com` | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/TAGS/{KEY}/VALUES/
## ***GET*** 

**Description:** Return a list of values associated with this key.  The `query`
parameter can be used to to perform a "contains" match on
values. 

When [paginated](/api/pagination) can return at most 1000 values.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/tags/{key}/values/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| key | path | The tag key to look up. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/STATS/
## ***GET*** 

**Summary:** Caution
This endpoint may change in the future without  notice.

**Description:** Return a set of points representing a normalized timestamp and the
number of events seen in the period.

Query ranges are limited to Sentry's configured time-series resolutions.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/stats/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| stat | query | The name of the stat to query `("received", "rejected", "blacklisted", "generated")`. | No |  |
| since | query | A timestamp to set the start of the query in seconds since UNIX epoch. | No |  |
| until | query | A timestamp to set the end of the query in seconds since UNIX epoch. | No |  |
| resolution | query | An explicit resolution to search for (one of `10s`, `1h`, and `1d`). | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/USER-FEEDBACK/
## ***GET*** 

**Description:** Return a list of user feedback items within this project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/user-feedback/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Submit and associate user feedback with an issue.

Feedback must be received by the server no more than 30 minutes after the event was saved.

Additionally, within 5 minutes of submitting feedback it may also be overwritten. This is useful in situations where you may need to retry sending a request due to network failures.

If feedback is rejected due to a mutability threshold, a 409 status code will be returned.

Note: Feedback may be submitted with DSN authentication (see auth documentation).

### HTTP Request 
`***POST*** /api/0/projects/{organization_slug}/{project_slug}/user-feedback/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | The requested resource does not exist |
| 409 | Conflict |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/KEYS/
## ***GET*** 

**Description:** Return a list of client keys bound to a project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/keys/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

## ***POST*** 

**Description:** Create a new client key bound to a project.  The key's secret and public key are generated by the server.

### HTTP Request 
`***POST*** /api/0/projects/{organization_slug}/{project_slug}/keys/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/KEYS/{KEY_ID}/
## ***PUT*** 

**Description:** Update a client key.  This can be used to rename a key.

### HTTP Request 
`***PUT*** /api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| key_id | path | The ID of the key to update. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | Project not found |

## ***DELETE*** 

**Description:** Delete a client key.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| key_id | path | The ID of the key to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Project not found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/HOOKS/
## ***GET*** 

**Description:** Return a list of service hooks bound to a project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/hooks/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | You do not have that feature enabled |

## ***POST*** 

**Description:** Register a new service hook on a project.

Events include:

- event.alert: An alert is generated for an event (via rules).
- event.created: A new event has been processed.

This endpoint requires the 'servicehooks' feature to be enabled for your project.

### HTTP Request 
`***POST*** /api/0/projects/{organization_slug}/{project_slug}/hooks/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 403 | You do not have that feature enabled |
| 404 | The requested resource does not exist |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/HOOKS/{HOOK_ID}/
## ***GET*** 

**Description:** Return a service hook bound to a project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| hook_id | path | The GUID of the service hook. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***PUT*** 

**Description:** Update a service hook.

### HTTP Request 
`***PUT*** /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| hook_id | path | The GUID of the service hook. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***DELETE*** 

**Description:** Remove a service hook.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the client keys belong to. | Yes |  |
| project_slug | path | The slug of the project the client keys belong to. | Yes |  |
| hook_id | path | The GUID of the service hook. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/EVENTS/{EVENT_ID}/
## ***GET*** 

**Description:** Return details on an individual event.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the event belongs to. | Yes |  |
| project_slug | path | The slug of the project the event belongs to. | Yes |  |
| event_id | path | The ID of the event to retrieve. It is the hexadecimal ID as reported by the client. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/EVENTS/
## ***GET*** 

**Description:** Return a list of events bound to a project.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/events/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the groups belong to. | Yes |  |
| project_slug | path | The slug of the project the groups belong to. | Yes |  |
| full | query | If this is set to true then the event payload will include the full event body, including the stacktrace.  Set to true to enable. | No |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/ISSUES/
## ***GET*** 

**Description:** Return a list of issues (groups) bound to a project.  All parameters are supplied as query string parameters. 

 A default query of ``is:unresolved`` is applied. To return results with other statuses send an new query value (i.e. ``?query=`` for all results).

The ``statsPeriod`` parameter can be used to select the timeline stats which should be present. Possible values are: ``""`` (disable),``"24h"``, ``"14d"``

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/issues/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the issues belong to. | Yes |  |
| project_slug | path | The slug of the project the issues belong to. | Yes |  |
| statsPeriod | query | An optional stat period (can be one of `"24h"`, `"14d"`, and `""`). | No |  |
| shortIdLookup | query | If this is set to true then short IDs are looked up by this function as well. This can cause the return value of the function to return an event issue of a different project which is why this is an opt-in. Set to 1 to enable. | No |  |
| query | query | An optional Sentry structured search query. If not provided an implied `"is:unresolved"` is assumed. | No |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

## ***PUT*** 

**Description:** Bulk mutate various attributes on issues.  The list of issues to modify is given through the `id` query parameter.  It is repeated for each issue that should be modified.

- For non-status updates, the `id` query parameter is required.
- For status updates, the `id` query parameter may be omitted
for a batch "update all" query.
- An optional `status` query parameter may be used to restrict
mutations to only events with the given status.

The following attributes can be modified and are supplied as JSON object in the body:

If any ids are out of scope this operation will succeed without any data mutation.

### HTTP Request 
`***PUT*** /api/0/projects/{organization_slug}/{project_slug}/issues/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the issues belong to. | Yes |  |
| project_slug | path | The slug of the project the issues belong to. | Yes |  |
| id | query | A list of IDs of the issues to be mutated. This parameter shall be repeated for each issue. It is optional only if a status is mutated in which case an implicit update all is assumed. | No |  |
| status | query | Optionally limits the query to issues of the specified status. Valid values are `"resolved"`, `"unresolved"`, and `"ignored"`. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 400 | Bad Input |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***DELETE*** 

**Description:** Permanently remove the given issues. The list of issues to modify is given through the `id` query parameter.  It is repeated for each issue that should be removed.

Only queries by 'id' are accepted.

If any ids are out of scope this operation will succeed without any data mutation.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/issues/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the issues belong to. | Yes |  |
| project_slug | path | The slug of the project the issues belong to. | Yes |  |
| id | query | A list of IDs of the issues to be removed. This parameter shall be repeated for each issue. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Project not found |

# /API/0/ISSUES/{ISSUE_ID}/TAGS/{KEY}/VALUES/
## ***GET*** 

**Description:** Returns details for given tag key related to an issue. 

When [paginated](/api/pagination) can return at most 1000 values.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/tags/{key}/values/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to retrieve. | Yes |  |
| key | path | The tag key to look the values up for. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/TAGS/{KEY}/
## ***GET*** 

**Description:** Returns details for given tag key related to an issue.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/tags/{key}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to retrieve. | Yes |  |
| key | path | The tag key to look the values up for. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/HASHES/
## ***GET*** 

**Description:** This endpoint lists an issue's hashes, which are the generated checksums used to aggregate individual events.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/hashes/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to retrieve. | Yes |  |
| cursor | query | A pointer to the last object fetched and its sort order; used to retrieve the next or previous results. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/EVENTS/OLDEST/
## ***GET*** 

**Description:** Retrieves the details of the oldest event for an issue.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/events/oldest/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/EVENTS/LATEST/
## ***GET*** 

**Description:** Retrieves the details of the latest event for an issue.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/events/latest/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/EVENTS/
## ***GET*** 

**Description:** This endpoint lists an issue's events.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/events/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to retrieve. | Yes |  |
| full | query | If this is set to true then the event payload will include the full event body, including the stacktrace.  Set to true to enable. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

# /API/0/ISSUES/{ISSUE_ID}/
## ***GET*** 

**Description:** Return details on an individual issue. This returns the basic stats for the issue (title, last seen, first seen), some overall numbers (number of comments, user reports) as well as the summarized event data.

### HTTP Request 
`***GET*** /api/0/issues/{issue_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to retrieve. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |

## ***PUT*** 

**Description:** Updates an individual issue's attributes.  Only the attributes submitted are modified.

### HTTP Request 
`***PUT*** /api/0/issues/{issue_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the group to retrieve. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

## ***DELETE*** 

**Description:** Removes an individual issue.

### HTTP Request 
`***DELETE*** /api/0/issues/{issue_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| issue_id | path | The ID of the issue to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 202 | Success |
| 403 | Forbidden |
| 404 | The requested resource does not exist |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/
## ***GET*** 

**Description:** Return a list of releases for a given organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| query | query | This parameter can be used to create a "starts with" filter for the version. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 401 | Permission Denied |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a new release for the given organization.  Releases are used by
Sentry to improve its error reporting abilities by correlating
first seen events with the release that might have introduced the
problem.
Releases are also necessary for source maps and other debug features
that require manual upload for functioning well.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/releases/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 400 | Bad Input |
| 403 | Forbidden |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/
## ***GET*** 

**Description:** Return a release for a given organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***PUT*** 

**Description:** Update a release for a given organization.

### HTTP Request 
`***PUT*** /api/0/organizations/{organization_slug}/releases/{version}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete a release for a given organization.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/releases/{version}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/FILES/
## ***GET*** 

**Description:** Return a list of files for a given release.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/files/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Upload a new organization release file.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/releases/{version}/files/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/RELEASES/{VERSION}/FILES/
## ***GET*** 

**Description:** Return a list of files for a given release.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Upload a new project release file.

### HTTP Request 
`***POST*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/FILES/{FILE_ID}/
## ***GET*** 

**Description:** Retrieve a file for a given release.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to retrieve. | Yes |  |
| download | query | If this is set to true, then the response payload will be the raw file contents. Otherwise, the response will be the file metadata as JSON. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***PUT*** 

**Description:** Update an organization release file.

### HTTP Request 
`***PUT*** /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to retrieve. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete a file for a given release.

### HTTP Request 
`***DELETE*** /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/RELEASES/{VERSION}/FILES/{FILE_ID}/
## ***GET*** 

**Description:** Retrieve a file for a given release.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to retrieve. | Yes |  |
| download | query | If this is set to true, then the response payload will be the raw file contents. Otherwise, the response will be the file metadata as JSON. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***PUT*** 

**Description:** Update a project release file.

### HTTP Request 
`***PUT*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to retrieve. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***DELETE*** 

**Description:** Delete a file for a given release.

### HTTP Request 
`***DELETE*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |
| file_id | path | The ID of the file to delete. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/COMMITS/
## ***GET*** 

**Description:** List an organization release's commits.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/commits/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/RELEASES/{VERSION}/COMMITS/
## ***GET*** 

**Description:** List a project release's commits.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/commits/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| project_slug | path | The slug of the project the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/COMMITFILES/
## ***GET*** 

**Description:** Retrieve files changed in a release's commits

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/commitfiles/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization the release belongs to. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/PROJECTS/{ORGANIZATION_SLUG}/{PROJECT_SLUG}/RELEASES/{VERSION}/RESOLVED/
## ***GET*** 

**Description:** List issues to be resolved in a particular release.

### HTTP Request 
`***GET*** /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/resolved/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| project_slug | path | The slug of the project. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/RELEASES/{VERSION}/DEPLOYS/
## ***GET*** 

**Description:** Return a list of deploys for a given release.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/releases/{version}/deploys/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

## ***POST*** 

**Description:** Create a deploy.

### HTTP Request 
`***POST*** /api/0/organizations/{organization_slug}/releases/{version}/deploys/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The slug of the organization. | Yes |  |
| version | path | The version identifier of the release. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Success |
| 208 | Already Reported |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/ORGANIZATIONS/{ORGANIZATION_SLUG}/SENTRY-APP-INSTALLATIONS/
## ***GET*** 

**Description:** Return a list of integration platform installations for a given organization.

### HTTP Request 
`***GET*** /api/0/organizations/{organization_slug}/sentry-app-installations/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| organization_slug | path | The organization short name. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/SENTRY-APP-INSTALLATIONS/{UUID}/EXTERNAL-ISSUES/
## ***POST*** 

**Description:** Create an external issue from an integration platform integration.

### HTTP Request 
`***POST*** /api/0/sentry-app-installations/{uuid}/external-issues/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| uuid | path | The uuid of the integration platform integration. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Success |
| 403 | Forbidden |
| 404 | Not Found |

# /API/0/SENTRY-APP-INSTALLATIONS/{UUID}/EXTERNAL-ISSUES/{EXTERNAL_ISSUE_ID}/
## ***DELETE*** 

**Description:** Delete an external issue.

### HTTP Request 
`***DELETE*** /api/0/sentry-app-installations/{uuid}/external-issues/{external_issue_id}/` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| uuid | path | The uuid of the integration platform integration. | Yes |  |
| external_issue_id | path | The id of the external issue. | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 204 | Success |
| 403 | Forbidden |
| 404 | External issue not found |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
