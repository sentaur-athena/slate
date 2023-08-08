---
title: API Reference v0
language_tabs:
  - ruby: Ruby
  - python: Python
  - javascript: JavaScript
language_clients:
  - ruby: ""
  - python: ""
  - javascript: ""
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 3

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="api-reference">API Reference v0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Sentry Public API

Base URLs:

* <a href="https://sentry.io">https://sentry.io</a>

<a href="http://sentry.io/terms/">Terms of service</a>
Email: <a href="mailto:partners@sentry.io">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Authentication

- HTTP Authentication, scheme: bearer 

- HTTP Authentication, scheme: DSN 

<h1 id="api-reference-organizations">Organizations</h1>

Endpoints for organizations

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/organizations/&template=api_error_template.md">Found an error? Let us know.</a>

## Retrieve an Organization Member

<a id="opIdRetrieve an Organization Member"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/members/{member_id}/`

Retrieve an organization member's details.

Will return a pending invite as long as it's already approved.

<h3 id="retrieve-an-organization-member-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|member_id|path|string|true|The member ID.|

> Example responses

> 200 Response

```json
{
  "externalUsers": [
    {
      "externalId": "string",
      "userId": "string",
      "teamId": "string",
      "id": "string",
      "provider": "string",
      "externalName": "string",
      "integrationId": "string"
    }
  ],
  "id": "string",
  "email": "string",
  "name": "string",
  "user": {
    "identities": [
      {
        "id": "string",
        "name": "string",
        "organization": {
          "slug": "string",
          "name": "string"
        },
        "provider": {
          "id": "string",
          "name": "string"
        },
        "dateVerified": "2019-08-24T14:15:22Z",
        "dateSynced": "2019-08-24T14:15:22Z"
      }
    ],
    "avatar": {
      "avatarType": "string",
      "avatarUuid": "string"
    },
    "id": "string",
    "name": "string",
    "username": "string",
    "email": "string",
    "avatarUrl": "string",
    "isActive": true,
    "hasPasswordAuth": true,
    "isManaged": true,
    "dateJoined": "2019-08-24T14:15:22Z",
    "lastLogin": "2019-08-24T14:15:22Z",
    "has2fa": true,
    "lastActive": "2019-08-24T14:15:22Z",
    "isSuperuser": true,
    "isStaff": true,
    "experiments": {
      "property1": null,
      "property2": null
    },
    "emails": [
      {
        "id": "string",
        "email": "string",
        "is_verified": true
      }
    ]
  },
  "role": "string",
  "roleName": "string",
  "orgRole": "string",
  "groupOrgRoles": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "pending": true,
  "expired": "string",
  "flags": {
    "idp:provisioned": true,
    "idp:role-restricted": true,
    "sso:linked": true,
    "sso:invalid": true,
    "member-limit:restricted": true
  },
  "dateCreated": "2019-08-24T14:15:22Z",
  "inviteStatus": "string",
  "inviterName": "string",
  "teams": [
    "string"
  ],
  "teamRoles": [
    {
      "teamSlug": "string",
      "role": "string"
    }
  ],
  "invite_link": "string",
  "isOnlyOwner": true,
  "roles": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "orgRoleList": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "teamRoleList": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ]
}
```

<h3 id="retrieve-an-organization-member-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-an-organization-member-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» externalUsers|[object]|false|none|none|
|»» externalId|string|false|none|none|
|»» userId|string|false|none|none|
|»» teamId|string|false|none|none|
|»» id|string|true|none|none|
|»» provider|string|true|none|none|
|»» externalName|string|true|none|none|
|»» integrationId|string|true|none|none|
|» id|string|true|none|none|
|» email|string|true|none|none|
|» name|string|true|none|none|
|» user|object|true|none|none|
|»» identities|[object]|false|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» organization|object|true|none|none|
|»»»» slug|string|true|none|none|
|»»»» name|string|true|none|none|
|»»» provider|object|true|none|none|
|»»»» id|string|true|none|none|
|»»»» name|string|true|none|none|
|»»» dateVerified|string(date-time)|true|none|none|
|»»» dateSynced|string(date-time)|true|none|none|
|»» avatar|object|false|none|none|
|»»» avatarType|string|true|none|none|
|»»» avatarUuid|string¦null|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» username|string|true|none|none|
|»» email|string|true|none|none|
|»» avatarUrl|string|true|none|none|
|»» isActive|boolean|true|none|none|
|»» hasPasswordAuth|boolean|true|none|none|
|»» isManaged|boolean|true|none|none|
|»» dateJoined|string(date-time)|true|none|none|
|»» lastLogin|string(date-time)|true|none|none|
|»» has2fa|boolean|true|none|none|
|»» lastActive|string(date-time)|true|none|none|
|»» isSuperuser|boolean|true|none|none|
|»» isStaff|boolean|true|none|none|
|»» experiments|object|true|none|none|
|»»» **additionalProperties**|any|false|none|none|
|»» emails|[object]|true|none|none|
|»»» id|string|true|none|none|
|»»» email|string|true|none|none|
|»»» is_verified|boolean|true|none|none|
|» role|string|true|none|none|
|» roleName|string|true|none|none|
|» orgRole|string|true|none|none|
|» groupOrgRoles|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» desc|string|true|none|none|
|»» scopes|[string]|true|none|none|
|»» is_global|boolean|true|none|none|
|»» allowed|boolean|true|none|none|
|» pending|boolean|true|none|none|
|» expired|string|true|none|none|
|» flags|object|true|none|none|
|»» idp:provisioned|boolean|true|none|none|
|»» idp:role-restricted|boolean|true|none|none|
|»» sso:linked|boolean|true|none|none|
|»» sso:invalid|boolean|true|none|none|
|»» member-limit:restricted|boolean|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» inviteStatus|string|true|none|none|
|» inviterName|string¦null|true|none|none|
|» teams|[string]|true|none|none|
|» teamRoles|[object]|true|none|none|
|»» teamSlug|string|true|none|none|
|»» role|string|true|none|none|
|» invite_link|string¦null|true|none|none|
|» isOnlyOwner|boolean|true|none|none|
|» roles|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» desc|string|true|none|none|
|»» scopes|[string]|true|none|none|
|»» is_global|boolean|true|none|none|
|»» allowed|boolean|true|none|none|
|» orgRoleList|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» desc|string|true|none|none|
|»» scopes|[string]|true|none|none|
|»» is_global|boolean|true|none|none|
|»» allowed|boolean|true|none|none|
|» teamRoleList|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» desc|string|true|none|none|
|»» scopes|[string]|true|none|none|
|»» is_global|boolean|true|none|none|
|»» allowed|boolean|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:read member:write )
</aside>

## Delete an Organization Member

<a id="opIdDelete an Organization Member"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/members/{member_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/members/{member_id}/`

Remove an organization member.

<h3 id="delete-an-organization-member-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|member_id|path|string|true|The member ID.|

<h3 id="delete-an-organization-member-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:read member:write )
</aside>

## List an Organization's Projects

<a id="opIdList an Organization's Projects"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/projects/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/projects/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/projects/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/projects/`

Return a list of projects bound to a organization.

<h3 id="list-an-organization's-projects-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

```json
[
  {
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "firstEvent": null,
    "access": [],
    "hasAccess": true,
    "id": "3",
    "isBookmarked": false,
    "isMember": true,
    "name": "Prime Mover",
    "platform": "",
    "platforms": [],
    "slug": "prime-mover",
    "team": {
      "id": "2",
      "name": "Powerful Abolitionist",
      "slug": "powerful-abolitionist"
    },
    "teams": [
      {
        "id": "2",
        "name": "Powerful Abolitionist",
        "slug": "powerful-abolitionist"
      }
    ],
    "environments": [
      "local"
    ],
    "eventProcessing": {
      "symbolicationDegraded": false
    },
    "features": [
      "releases"
    ],
    "firstTransactionEvent": true,
    "hasSessions": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasMinifiedStackTrace": false,
    "hasMonitors": true,
    "hasUserReports": false,
    "latestRelease": null
  }
]
```

<h3 id="list-an-organization's-projects-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-projects-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» latestDeploys|object¦null|false|none|none|
|»» **additionalProperties**|object|false|none|none|
|»»» **additionalProperties**|string|false|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» team|object¦null|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» teams|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» eventProcessing|object|true|none|none|
|»» symbolicationDegraded|boolean|true|none|none|
|» platforms|[string]|true|none|none|
|» hasUserReports|boolean|true|none|none|
|» environments|[string]|true|none|none|
|» latestRelease|object¦null|true|none|none|
|»» version|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

## Retrieve Event Counts for an Organization (v2)

<a id="opIdRetrieve Event Counts for an Organization (v2)"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/stats_v2/',
  params: {
  'groupBy' => 'array[string]',
'field' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/stats_v2/', params={
  'groupBy': [
  "outcome"
],  'field': 'sum(quantity)'
}, headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/stats_v2/?groupBy=outcome&field=sum%28quantity%29',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/stats_v2/`

Query event counts for your Organization.
Select a field, define a date range, and group or filter by columns.

<h3 id="retrieve-event-counts-for-an-organization-(v2)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|statsPeriod|query|string|false|This defines the range of the time series, relative to now. The range is given in a `<number><unit>` format. For example `1d` for a one day range. Possible units are `m` for minutes, `h` for hours, `d` for days and `w` for weeks.You must either provide a `statsPeriod`, or a `start` and `end`.|
|interval|query|string|false|This is the resolution of the time series, given in the same format as `statsPeriod`. The default resolution is `1h` and the minimum resolution is currently restricted to `1h` as well. Intervals larger than `1d` are not supported, and the interval has to cleanly divide one day.|
|start|query|string(date-time)|false|This defines the start of the time series range as an explicit datetime, either in UTC ISO8601 or epoch seconds.Use along with `end` instead of `statsPeriod`.|
|end|query|string(date-time)|false|This defines the inclusive end of the time series range as an explicit datetime, either in UTC ISO8601 or epoch seconds.Use along with `start` instead of `statsPeriod`.|
|groupBy|query|array[string]|true|can pass multiple groupBy parameters to group by multiple, e.g. `groupBy=project&groupBy=outcome` to group by multiple dimensions. Note that grouping by project can cause missing rows if the number of projects / interval is large. If you have a large number of projects, we recommend filtering and querying by them individually.Also note that grouping by projects does not currently support timeseries interval responses and will instead be a sum of the projectover the entire period specified.|
|field|query|string|true|the `sum(quantity)` field is bytes for attachments, and all others the 'event' count for those types of events.|
|project|query|array[any]|false|The ID of the projects to filter by.|
|category|query|string|false|If filtering by attachments, you cannot filter by any other category due to quantity values becoming nonsensical (combining bytes and event counts).|
|outcome|query|string|false|See https://docs.sentry.io/product/stats/ for more information on outcome statuses.|
|reason|query|string|false|The reason field will contain why an event was filtered/dropped.|

#### Detailed descriptions

**field**: the `sum(quantity)` field is bytes for attachments, and all others the 'event' count for those types of events.

`sum(times_seen)` sums the number of times an event has been seen. For 'normal' event types, this will be equal to `sum(quantity)` for now. For sessions, quantity will sum the total number of events seen in a session, while `times_seen` will be the unique number of sessions. and for attachments, `times_seen` will be the total number of attachments, while quantity will be the total sum of attachment bytes.

**project**: The ID of the projects to filter by.

Use `-1` to include all accessible projects.

**category**: If filtering by attachments, you cannot filter by any other category due to quantity values becoming nonsensical (combining bytes and event counts).

If filtering by `error`, it will automatically add `default` and `security` as we currently roll those two categories into `error` for displaying.

#### Enumerated Values

|Parameter|Value|
|---|---|
|groupBy|outcome|
|groupBy|category|
|groupBy|reason|
|groupBy|project|
|field|sum(quantity)|
|field|sum(times_seen)|
|category|error|
|category|transaction|
|category|attachment|
|outcome|accepted|
|outcome|filtered|
|outcome|rate_limited|
|outcome|invalid|
|outcome|abuse|
|outcome|client_discard|

> Example responses

```json
{
  "start": "2022-02-14T19:00:00Z",
  "end": "2022-02-28T18:03:00Z",
  "intervals": [
    "2022-02-28T00:00:00Z"
  ],
  "groups": [
    {
      "by": {
        "outcome": "invalid"
      },
      "totals": {
        "sum(quantity)": 165665
      },
      "series": {
        "sum(quantity)": [
          165665
        ]
      }
    }
  ]
}
```

<h3 id="retrieve-event-counts-for-an-organization-(v2)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-event-counts-for-an-organization-(v2)-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» start|string|true|none|none|
|» end|string|true|none|none|
|» intervals|[string]|true|none|none|
|» groups|[object]|true|none|none|
|»» by|object|true|none|none|
|»»» **additionalProperties**|any|false|none|none|
|»» totals|object|true|none|none|
|»»» **additionalProperties**|any|false|none|none|
|»» series|object|true|none|none|
|»»» **additionalProperties**|any|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

## List Your Organizations

<a id="opIdList Your Organizations"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/`

Return a list of organizations available to the authenticated session.  This is particularly useful for requests with an user bound context.  For API key based requests this will only return the organization that belongs to the key.

<h3 id="list-your-organizations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|owner|query|boolean|false|Restrict results to organizations in which you are an organization owner.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "dateCreated": "2018-11-06T21:19:55.101Z",
    "id": "2",
    "isEarlyAdopter": false,
    "name": "The Interstellar Jurisdiction",
    "require2FA": false,
    "slug": "the-interstellar-jurisdiction",
    "status": {
      "id": "active",
      "name": "active"
    }
  }
]
```

<h3 id="list-your-organizations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-your-organizations-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» id|string|true|none|none|
|» isEarlyAdopter|boolean|true|none|none|
|» name|string|true|none|none|
|» require2FA|boolean|true|none|none|
|» slug|string|true|none|none|
|» status|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## Resolve an Event ID

<a id="opIdResolve an Event ID"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/eventids/{event_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/eventids/{event_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/eventids/{event_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/eventids/{event_id}/`

This resolves an event ID to the project slug and internal issue ID and internal event ID.

<h3 id="resolve-an-event-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the event ID should be looked up in.|
|event_id|path|string|true|The event ID to look up.|

> Example responses

> 200 Response

```json
{
  "event": {
    "_meta": {
      "context": null,
      "contexts": null,
      "entries": {},
      "message": null,
      "packages": null,
      "sdk": null,
      "tags": {},
      "user": null
    },
    "context": {
      "length": 10837790,
      "results": [
        1,
        2,
        3,
        4,
        5
      ],
      "session": {
        "foo": "bar"
      },
      "unauthorized": false,
      "url": "http://example.org/foo/bar/"
    },
    "contexts": {},
    "dateCreated": "2018-11-06T21:19:55Z",
    "dateReceived": "2018-11-06T21:19:55Z",
    "dist": null,
    "entries": [
      {
        "type": "request",
        "data": {
          "fragment": null,
          "cookies": [],
          "inferredContentType": null,
          "env": null,
          "headers": [
            [
              "User-Agent",
              "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36"
            ]
          ],
          "url": "http://example.com/foo",
          "query": [],
          "data": null,
          "method": null
        }
      }
    ],
    "errors": [],
    "eventID": "9fac2ceed9344f2bbfdd1fdacb0ed9b1",
    "fingerprints": [
      "c4a4d06bc314205bb3b6bdb612dde7f1"
    ],
    "groupID": "1",
    "id": "1",
    "message": "",
    "title": "This is an example Python exception",
    "metadata": {
      "title": "This is an example Python exception"
    },
    "packages": {
      "my.package": "1.0.0"
    },
    "platform": "python",
    "sdk": null,
    "size": 7055,
    "tags": [
      {
        "_meta": null,
        "key": "browser",
        "value": "Chrome 28.0"
      },
      {
        "_meta": null,
        "key": "device",
        "value": "Other"
      },
      {
        "_meta": null,
        "key": "level",
        "value": "error"
      },
      {
        "_meta": null,
        "key": "os",
        "value": "Windows 8"
      },
      {
        "_meta": null,
        "key": "release",
        "value": "17642328ead24b51867165985996d04b29310337"
      },
      {
        "_meta": null,
        "key": "url",
        "value": "http://example.com/foo"
      },
      {
        "_meta": null,
        "key": "user",
        "value": "id:1"
      }
    ],
    "type": "default",
    "user": {
      "data": {},
      "email": "sentry@example.com",
      "id": "1",
      "ip_address": "127.0.0.1",
      "name": "Sentry",
      "username": "sentry"
    }
  },
  "eventId": "1",
  "groupId": "1",
  "organizationSlug": "the-interstellar-jurisdiction",
  "projectSlug": "pump-station"
}
```

<h3 id="resolve-an-event-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="resolve-an-event-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» event|object|true|none|none|
|»» _meta|object|true|none|none|
|»»» context|string¦null|false|none|none|
|»»» contexts|object¦null|false|none|none|
|»»» entries|object|false|none|none|
|»»» message|string¦null|false|none|none|
|»»» packages|string¦null|false|none|none|
|»»» sdk|string¦null|false|none|none|
|»»» tags|object|false|none|none|
|»»» user|string¦null|false|none|none|
|»» context|object|true|none|none|
|»»» length|integer|false|none|none|
|»»» results|[integer]|false|none|none|
|»»» session|object|false|none|none|
|»»»» foo|string|false|none|none|
|»»» unauthorized|boolean|false|none|none|
|»»» url|string|false|none|none|
|»» contexts|object|true|none|none|
|»»» ForbiddenError|object|false|none|none|
|»»»» status|integer|false|none|none|
|»»»» statusText|string|false|none|none|
|»»»» responseJSON|object|false|none|none|
|»»»»» detail|string|false|none|none|
|»»»» type|string|false|none|none|
|»»» browser|object|false|none|none|
|»»»» version|string|false|none|none|
|»»»» type|string|false|none|none|
|»»»» name|string|false|none|none|
|»»» os|object|false|none|none|
|»»»» version|string|false|none|none|
|»»»» type|string|false|none|none|
|»»»» name|string|false|none|none|
|»»» trace|object|false|none|none|
|»»»» span_id|string|false|none|none|
|»»»» type|string|false|none|none|
|»»»» trace_id|string|false|none|none|
|»»»» op|string|false|none|none|
|»»» organization|object|false|none|none|
|»»»» type|string|false|none|none|
|»»»» id|string|false|none|none|
|»»»» slug|string|false|none|none|
|»» dateCreated|string|true|none|none|
|»» dateReceived|string|true|none|none|
|»» dist|string¦null|true|none|none|
|»» entries|[anyOf]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» values|[object]|true|none|none|
|»»»»»» category|string|true|none|none|
|»»»»»» level|string|true|none|none|
|»»»»»» event_id|string¦null|true|none|none|
|»»»»»» timestamp|string(date-time)|true|none|none|
|»»»»»» data|object¦null|true|none|none|
|»»»»»» message|string¦null|true|none|none|
|»»»»»» type|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» fragment|string¦null|true|none|none|
|»»»»» cookies|[array]¦null|true|none|none|
|»»»»» inferredContentType|string¦null|true|none|none|
|»»»»» env|object¦null|true|none|none|
|»»»»»» ENV|string|false|none|none|
|»»»»» headers|[array]|true|none|none|
|»»»»» url|string|true|none|none|
|»»»»» query|[array]|true|none|none|
|»»»»» data|object¦null|true|none|none|
|»»»»» method|string¦null|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» formatted|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» excOmitted|[integer]¦null|true|none|none|
|»»»»» hasSystemFrames|boolean|true|none|none|
|»»»»» values|[object]|true|none|none|
|»»»»»» stacktrace|object¦null|true|none|none|
|»»»»»»» frames|[object]|true|none|none|
|»»»»»»»» function|string|true|none|none|
|»»»»»»»» errors|string¦null|true|none|none|
|»»»»»»»» colNo|integer¦null|true|none|none|
|»»»»»»»» vars|object¦null|true|none|none|
|»»»»»»»» package|string¦null|true|none|none|
|»»»»»»»» absPath|string¦null|true|none|none|
|»»»»»»»» inApp|boolean|true|none|none|
|»»»»»»»» lineNo|integer|true|none|none|
|»»»»»»»» module|string|true|none|none|
|»»»»»»»» filename|string|true|none|none|
|»»»»»»»» platform|string¦null|true|none|none|
|»»»»»»»» instructionAddr|string¦null|true|none|none|
|»»»»»»»» context|[array]|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»»» *anonymous*|string|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»» symbolAddr|string¦null|true|none|none|
|»»»»»» trust|string¦null|true|none|none|
|»»»»»» symbol|string¦null|true|none|none|
|»»»»» framesOmitted|string¦null|true|none|none|
|»»»»» registers|string¦null|true|none|none|
|»»»»» hasSystemFrames|boolean|true|none|none|
|»»»» module|string¦null|true|none|none|
|»»»» rawStacktrace|object¦null|true|none|none|
|»»»» mechanism|object¦null|true|none|none|
|»»»»» type|string|false|none|none|
|»»»»» handled|boolean|false|none|none|
|»»»» threadId|string¦null|true|none|none|
|»»»» value|string|true|none|none|
|»»»» type|string|true|none|none|
|errors|[object]|true|none|none|
|» message|string|false|none|none|
|» type|string|false|none|none|
|» data|object|false|none|none|
|eventID|string|true|none|none|
|fingerprints|[string]|true|none|none|
|groupID|string|true|none|none|
|id|string|true|none|none|
|message|string|true|none|none|
|metadata|object|true|none|none|
|» title|string|false|none|none|
|packages|object|true|none|none|
|» my.package|string|false|none|none|
|platform|string|true|none|none|
|sdk|object¦null|true|none|none|
|size|integer|true|none|none|
|tags|[object]|true|none|none|
|» _meta|string¦null|false|none|none|
|» key|string|false|none|none|
|» value|string|false|none|none|
|type|string|true|none|none|
|user|object¦null|true|none|none|
|» username|string¦null|true|none|none|
|» name|string¦null|true|none|none|
|» ip_address|string¦null|true|none|none|
|» email|string¦null|true|none|none|
|» data|object¦null|true|none|none|
|»» isStaff|boolean|false|none|none|
|» id|string|true|none|none|
|title|string|true|none|none|
|eventId|string|true|none|none|
|groupId|string|true|none|none|
|organizationSlug|string|true|none|none|
|projectSlug|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## Retrieve an Organization

<a id="opIdRetrieve an Organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/`

Return details on an individual organization including various details such as membership access, features, and teams.

<h3 id="retrieve-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization to look up.|

> Example responses

> 200 Response

```json
{
  "access": [],
  "allowSharedIssues": true,
  "availableRoles": [
    {
      "id": "member",
      "name": "Member"
    },
    {
      "id": "admin",
      "name": "Admin"
    },
    {
      "id": "manager",
      "name": "Manager"
    },
    {
      "id": "owner",
      "name": "Owner"
    }
  ],
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "dataScrubber": false,
  "dataScrubberDefaults": false,
  "dateCreated": "2018-11-06T21:19:55.101Z",
  "defaultRole": "member",
  "enhancedPrivacy": false,
  "experiments": {},
  "features": [
    "new-teams",
    "shared-issues",
    "new-issue-ui",
    "repos",
    "open-membership",
    "invite-members",
    "sso-saml2",
    "sso-basic",
    "suggested-commits"
  ],
  "id": "2",
  "isDefault": false,
  "isEarlyAdopter": false,
  "name": "The Interstellar Jurisdiction",
  "onboardingTasks": [
    {
      "data": {},
      "dateCompleted": "2018-11-06T21:20:08.089Z",
      "status": "complete",
      "task": 1,
      "user": ""
    }
  ],
  "openMembership": true,
  "pendingAccessRequests": 0,
  "projects": [
    {
      "dateCreated": "2018-11-06T21:19:58.536Z",
      "firstEvent": null,
      "hasAccess": true,
      "id": "3",
      "isBookmarked": false,
      "isMember": true,
      "latestDeploys": null,
      "name": "Prime Mover",
      "platform": null,
      "platforms": [],
      "slug": "prime-mover",
      "team": {
        "id": "2",
        "name": "Powerful Abolitionist",
        "slug": "powerful-abolitionist"
      },
      "teams": [
        {
          "id": "2",
          "name": "Powerful Abolitionist",
          "slug": "powerful-abolitionist"
        }
      ]
    },
    {
      "dateCreated": "2018-11-06T21:19:55.121Z",
      "firstEvent": null,
      "hasAccess": true,
      "id": "2",
      "isBookmarked": false,
      "isMember": true,
      "latestDeploys": null,
      "name": "Pump Station",
      "platform": null,
      "platforms": [],
      "slug": "pump-station",
      "team": {
        "id": "2",
        "name": "Powerful Abolitionist",
        "slug": "powerful-abolitionist"
      },
      "teams": [
        {
          "id": "2",
          "name": "Powerful Abolitionist",
          "slug": "powerful-abolitionist"
        }
      ]
    },
    {
      "dateCreated": "2018-11-06T21:20:08.064Z",
      "firstEvent": null,
      "hasAccess": true,
      "id": "4",
      "isBookmarked": false,
      "isMember": true,
      "latestDeploys": null,
      "name": "The Spoiled Yoghurt",
      "platform": null,
      "platforms": [],
      "slug": "the-spoiled-yoghurt",
      "team": {
        "id": "2",
        "name": "Powerful Abolitionist",
        "slug": "powerful-abolitionist"
      },
      "teams": [
        {
          "id": "2",
          "name": "Powerful Abolitionist",
          "slug": "powerful-abolitionist"
        }
      ]
    }
  ],
  "quota": {
    "accountLimit": 0,
    "maxRate": 0,
    "maxRateInterval": 60,
    "projectLimit": 100
  },
  "require2FA": false,
  "safeFields": [],
  "scrapeJavaScript": true,
  "scrubIPAddresses": false,
  "sensitiveFields": [],
  "slug": "the-interstellar-jurisdiction",
  "status": {
    "id": "active",
    "name": "active"
  },
  "storeCrashReports": 0,
  "teams": [
    {
      "avatar": {
        "avatarType": "letter_avatar",
        "avatarUuid": null
      },
      "dateCreated": "2018-11-06T21:20:08.115Z",
      "hasAccess": true,
      "id": "3",
      "isMember": true,
      "isPending": false,
      "memberCount": 1,
      "name": "Ancient Gabelers",
      "slug": "ancient-gabelers"
    },
    {
      "avatar": {
        "avatarType": "letter_avatar",
        "avatarUuid": null
      },
      "dateCreated": "2018-11-06T21:19:55.114Z",
      "hasAccess": true,
      "id": "2",
      "isMember": true,
      "isPending": false,
      "memberCount": 1,
      "name": "Powerful Abolitionist",
      "slug": "powerful-abolitionist"
    }
  ],
  "trustedRelays": []
}
```

<h3 id="retrieve-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="retrieve-an-organization-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» access|[string]|true|none|none|
|» allowSharedIssues|boolean|true|none|none|
|» availableRoles|[object]|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» dataScrubber|boolean|true|none|none|
|» dataScrubberDefaults|boolean|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» defaultRole|string|true|none|none|
|» enhancedPrivacy|boolean|true|none|none|
|» experiments|object|true|none|none|
|» features|[string]|true|none|none|
|» id|string|true|none|none|
|» isDefault|boolean|true|none|none|
|» isEarlyAdopter|boolean|true|none|none|
|» name|string|true|none|none|
|» onboardingTasks|[object]|true|none|none|
|»» data|object¦null|false|none|none|
|»» dateCompleted|string(date-time)|false|none|none|
|»» status|string|false|none|none|
|»» task|integer|false|none|none|
|»» user|string¦null|false|none|none|
|» openMembership|boolean|true|none|none|
|» pendingAccessRequests|integer(int64)|true|none|none|
|» projects|[object]|true|none|none|
|»» dateCreated|string|true|none|none|
|»» firstEvent|string¦null|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» latestDeploys|string¦null|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» platforms|[string]|true|none|none|
|»» slug|string|true|none|none|
|»» team|object¦null|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» slug|string|true|none|none|
|»» teams|[object]|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» slug|string|true|none|none|
|» quota|object|true|none|none|
|»» accountLimit|integer(int64)|false|none|none|
|»» maxRate|integer(int64)¦null|false|none|none|
|»» maxRateInterval|integer(int64)|false|none|none|
|»» projectLimit|integer(int64)|false|none|none|
|» require2FA|boolean|true|none|none|
|» safeFields|[string]|true|none|none|
|» scrapeJavaScript|boolean|true|none|none|
|» scrubIPAddresses|boolean|true|none|none|
|» sensitiveFields|[string]|true|none|none|
|» slug|string|true|none|none|
|» status|object|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|» storeCrashReports|integer(int64)|true|none|none|
|» teams|[object]|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isMember|boolean|true|none|none|
|»» isPending|boolean|true|none|none|
|»» memberCount|integer(int64)|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» trustedRelays|[string]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## Update an Organization

<a id="opIdUpdate an Organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/organizations/{organization_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/organizations/{organization_slug}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "slug": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/organizations/{organization_slug}/`

Update various attributes and configurable settings for the given organization.

> Body parameter

```json
{
  "name": "string",
  "slug": "string"
}
```

<h3 id="update-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization to update.|
|body|body|object|false|none|
|» name|body|string|true|An optional new name for the organization.|
|» slug|body|string|false|An optional new slug for the organization. Needs to be available and unique.|

> Example responses

> 200 Response

```json
{
  "access": [],
  "allowSharedIssues": true,
  "availableRoles": [
    {
      "id": "member",
      "name": "Member"
    },
    {
      "id": "admin",
      "name": "Admin"
    },
    {
      "id": "manager",
      "name": "Manager"
    },
    {
      "id": "owner",
      "name": "Owner"
    }
  ],
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "dataScrubber": false,
  "dataScrubberDefaults": false,
  "dateCreated": "2018-11-06T21:20:19.548Z",
  "defaultRole": "member",
  "enhancedPrivacy": false,
  "experiments": {},
  "features": [
    "new-teams",
    "shared-issues",
    "new-issue-ui",
    "repos",
    "open-membership",
    "invite-members",
    "sso-saml2",
    "sso-basic",
    "suggested-commits"
  ],
  "id": "3",
  "isDefault": false,
  "isEarlyAdopter": false,
  "name": "Impeccably Designated",
  "onboardingTasks": [],
  "openMembership": true,
  "pendingAccessRequests": 0,
  "projects": [],
  "quota": {
    "accountLimit": 0,
    "maxRate": 0,
    "maxRateInterval": 60,
    "projectLimit": 100
  },
  "require2FA": false,
  "safeFields": [],
  "scrapeJavaScript": true,
  "scrubIPAddresses": false,
  "sensitiveFields": [],
  "slug": "impeccably-designated",
  "status": {
    "id": "active",
    "name": "active"
  },
  "storeCrashReports": 0,
  "teams": [],
  "trustedRelays": []
}
```

<h3 id="update-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-an-organization-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» access|[string]|true|none|none|
|» allowSharedIssues|boolean|true|none|none|
|» availableRoles|[object]|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» dataScrubber|boolean|true|none|none|
|» dataScrubberDefaults|boolean|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» defaultRole|string|true|none|none|
|» enhancedPrivacy|boolean|true|none|none|
|» experiments|object|true|none|none|
|» features|[string]|true|none|none|
|» id|string|true|none|none|
|» isDefault|boolean|true|none|none|
|» isEarlyAdopter|boolean|true|none|none|
|» name|string|true|none|none|
|» onboardingTasks|[object]|true|none|none|
|»» data|object¦null|false|none|none|
|»» dateCompleted|string(date-time)|false|none|none|
|»» status|string|false|none|none|
|»» task|integer|false|none|none|
|»» user|string¦null|false|none|none|
|» openMembership|boolean|true|none|none|
|» pendingAccessRequests|integer(int64)|true|none|none|
|» projects|[object]|true|none|none|
|»» dateCreated|string|true|none|none|
|»» firstEvent|string¦null|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» latestDeploys|string¦null|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» platforms|[string]|true|none|none|
|»» slug|string|true|none|none|
|»» team|object¦null|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» slug|string|true|none|none|
|»» teams|[object]|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»»» slug|string|true|none|none|
|» quota|object|true|none|none|
|»» accountLimit|integer(int64)|false|none|none|
|»» maxRate|integer(int64)¦null|false|none|none|
|»» maxRateInterval|integer(int64)|false|none|none|
|»» projectLimit|integer(int64)|false|none|none|
|» require2FA|boolean|true|none|none|
|» safeFields|[string]|true|none|none|
|» scrapeJavaScript|boolean|true|none|none|
|» scrubIPAddresses|boolean|true|none|none|
|» sensitiveFields|[string]|true|none|none|
|» slug|string|true|none|none|
|» status|object|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|» storeCrashReports|integer(int64)|true|none|none|
|» teams|[object]|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isMember|boolean|true|none|none|
|»» isPending|boolean|true|none|none|
|»» memberCount|integer(int64)|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» trustedRelays|[string]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:write )
</aside>

## List an Organization's Repositories

<a id="opIdList an Organization's Repositories"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/repos/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/repos/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/repos/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/repos/`

Return a list of version control repositories for a given organization.

<h3 id="list-an-organization's-repositories-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The organization short name.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "id": "3",
    "name": "sentry/sentry"
  }
]
```

<h3 id="list-an-organization's-repositories-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-repositories-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## List a Repository's Commits

<a id="opIdList a Repository's Commits"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/repos/{repo_id}/commits/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/repos/{repo_id}/commits/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/repos/{repo_id}/commits/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/repos/{repo_id}/commits/`

Return a list of commits for a given repository.

<h3 id="list-a-repository's-commits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The organization short name.|
|repo_id|path|string|true|The repository ID.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "id": "acbafc639127fd89d10f474520104517ff1d709e",
    "message": "Initial commit from Create Next App"
  }
]
```

<h3 id="list-a-repository's-commits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-a-repository's-commits-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string(date-time)|true|none|none|
|» id|string|true|none|none|
|» message|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## Retrieve Event Counts for an Organization

<a id="opIdRetrieve Event Counts for an Organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/stats/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/stats/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/stats/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/stats/`

This endpoint is deprecated in favor of [Organization Stats V2](/api/organizations/retrieve-event-counts-for-an-organization-v2/).

<h3 id="retrieve-event-counts-for-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the event ID should be looked up in.|
|stat|query|string|false|The name of the stat to query `("received", "rejected", "blacklisted")`.|
|since|query|string(date-time)|false|A timestamp to set the start of the query in seconds since UNIX epoch.|
|until|query|string(date-time)|false|A timestamp to set the end of the query in seconds since UNIX epoch.|
|resolution|query|string|false|An explicit resolution to search for (one of `10s`, `1h`, and `1d`).|

#### Enumerated Values

|Parameter|Value|
|---|---|
|stat|received|
|stat|rejected|
|stat|blacklisted|
|resolution|10s|
|resolution|1h|
|resolution|1d|

> Example responses

> 200 Response

```json
[
  [
    1541455200,
    8264
  ],
  [
    1541458800,
    6564
  ],
  [
    1541462400,
    8652
  ],
  [
    1541466000,
    7436
  ],
  [
    1541469600,
    8127
  ],
  [
    1541473200,
    7643
  ],
  [
    1541476800,
    6518
  ],
  [
    1541480400,
    6752
  ],
  [
    1541484000,
    6559
  ],
  [
    1541487600,
    7039
  ],
  [
    1541491200,
    7384
  ],
  [
    1541494800,
    6265
  ],
  [
    1541498400,
    8390
  ],
  [
    1541502000,
    6393
  ],
  [
    1541505600,
    7298
  ],
  [
    1541509200,
    7422
  ],
  [
    1541512800,
    5603
  ],
  [
    1541516400,
    6846
  ],
  [
    1541520000,
    8886
  ],
  [
    1541523600,
    6544
  ],
  [
    1541527200,
    8812
  ],
  [
    1541530800,
    8172
  ],
  [
    1541534400,
    5733
  ],
  [
    1541538000,
    9435
  ]
]
```

<h3 id="retrieve-event-counts-for-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-event-counts-for-an-organization-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## List an Organization's Users

<a id="opIdList an Organization's Users"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/users/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/users/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/users/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/users/`

Return a list of users that belong to a given organization.

<h3 id="list-an-organization's-users-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the event ID should be looked up in.|
|project|query|string|false|Restrict results to users who have access to a given project ID|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2019-05-09T18:06:01.728Z",
    "user": {
      "username": "testEmail@test.com",
      "lastLogin": "2019-09-16T02:56:06.806Z",
      "isSuperuser": false,
      "isManaged": false,
      "lastActive": "2019-10-08T15:05:38.715Z",
      "isStaff": false,
      "id": "433307",
      "isActive": true,
      "has2fa": false,
      "name": "OtherTest McTestuser",
      "avatarUrl": "https:  //secure.gravatar.com/avatar/1eb103c0e899f372a85eb0a44f0a0f42?s=32&d=mm",
      "dateJoined": "2019-05-09T18:06:01.443Z",
      "emails": [
        {
          "is_verified": true,
          "id": "468229",
          "email": "testEmail@test.com"
        }
      ],
      "avatar": {
        "avatarUuid": null,
        "avatarType": "letter_avatar"
      },
      "hasPasswordAuth": false,
      "email": "testEmail@test.com"
    },
    "roleName": "Organization Owner",
    "expired": false,
    "id": "9376061",
    "projects": [
      "buggy-sentry-project"
    ],
    "name": "OtherTest McTestuser",
    "role": "owner",
    "flags": {
      "sso: linked": false,
      "sso: invalid": false
    },
    "email": "testEmail@test.com",
    "pending": false
  }
]
```

<h3 id="list-an-organization's-users-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-users-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» user|object|true|none|none|
|»» username|string|true|none|none|
|»» lastLogin|string¦null|true|none|none|
|»» isSuperuser|boolean|true|none|none|
|»» isManaged|boolean|true|none|none|
|»» lastActive|string|true|none|none|
|»» isStaff|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isActive|boolean|true|none|none|
|»» has2fa|boolean|true|none|none|
|»» name|string|true|none|none|
|»» avatarUrl|string|true|none|none|
|»» dateJoined|string|true|none|none|
|»» emails|[object]|true|none|none|
|»»» is_verified|boolean|false|none|none|
|»»» id|string|false|none|none|
|»»» email|string|false|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» hasPasswordAuth|boolean|true|none|none|
|»» email|string|true|none|none|
|» roleName|string|true|none|none|
|» expired|boolean|true|none|none|
|» id|string|true|none|none|
|» projects|[string]|true|none|none|
|» name|string|true|none|none|
|» role|string|true|none|none|
|» flags|object|true|none|none|
|»» sso: linked|boolean|false|none|none|
|»» sso: invalid|boolean|false|none|none|
|» email|string|true|none|none|
|» pending|boolean|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|role|owner|
|role|manager|
|role|admin|
|role|member|
|role|billing|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## Resolve a Short ID

<a id="opIdResolve a Short ID"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/shortids/{short_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/shortids/{short_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/shortids/{short_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/shortids/{short_id}/`

This resolves a short ID to the project slug and internal issue ID.

<h3 id="resolve-a-short-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the short ID should be looked up in.|
|short_id|path|string|true|The short ID to look up.|

> Example responses

> 200 Response

```json
{
  "group": {
    "annotations": [],
    "assignedTo": null,
    "count": "1",
    "culprit": "raven.scripts.runner in main",
    "firstSeen": "2018-11-06T21:19:55Z",
    "hasSeen": false,
    "id": "1",
    "isBookmarked": false,
    "isPublic": false,
    "isSubscribed": true,
    "lastSeen": "2018-11-06T21:19:55Z",
    "level": "error",
    "logger": null,
    "metadata": {
      "title": "This is an example Python exception"
    },
    "numComments": 0,
    "permalink": "https://sentry.io/the-interstellar-jurisdiction/pump-station/issues/1/",
    "project": {
      "id": "2",
      "name": "Pump Station",
      "slug": "pump-station"
    },
    "shareId": null,
    "shortId": "PUMP-STATION-1",
    "status": "unresolved",
    "statusDetails": {},
    "subscriptionDetails": null,
    "title": "This is an example Python exception",
    "type": "default",
    "userCount": 0
  },
  "groupId": "1",
  "organizationSlug": "the-interstellar-jurisdiction",
  "projectSlug": "pump-station",
  "shortId": "PUMP-STATION-1"
}
```

<h3 id="resolve-a-short-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="resolve-a-short-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» organizationSlug|string|true|none|none|
|» projectSlug|string|true|none|none|
|» shortId|string|true|none|none|
|» group|object|true|none|none|
|»» lastSeen|string|true|none|none|
|»» numComments|integer|true|none|none|
|»» userCount|integer|true|none|none|
|»» culprit|string¦null|true|none|none|
|»» title|string|true|none|none|
|»» id|string|true|none|none|
|»» assignedTo|object¦null|true|none|none|
|»»» type|string|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»» logger|string¦null|true|none|none|
|»» type|string|true|none|none|
|»» annotations|[string]|true|none|none|
|»» metadata|object|true|none|none|
|»»» function|string|false|none|none|
|»»» title|string|false|none|none|
|»»» type|string|false|none|none|
|»»» value|string|false|none|none|
|»»» filename|string|false|none|none|
|»» status|string|true|none|none|
|»» subscriptionDetails|object¦null|true|none|none|
|»»» reason|string|false|none|none|
|»» isPublic|boolean|true|none|none|
|»» hasSeen|boolean|true|none|none|
|»» shortId|string|true|none|none|
|»» shareId|string¦null|true|none|none|
|»» firstSeen|string|true|none|none|
|»» count|string|true|none|none|
|»» permalink|string|true|none|none|
|»» level|string|true|none|none|
|»» isSubscribed|boolean|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» project|object|true|none|none|
|»»» slug|string|false|none|none|
|»»» id|string|false|none|none|
|»»» name|string|false|none|none|
|»» statusDetails|object|true|none|none|
|» groupId|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|resolved|
|status|unresolved|
|status|ignored|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

<h1 id="api-reference-teams">Teams</h1>

Endpoints for teams

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/teams/&template=api_error_template.md">Found an error? Let us know.</a>

## List an Organization's Teams

<a id="opIdList an Organization's Teams"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/teams/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/teams/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/teams/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/teams/`

Returns a list of teams bound to a organization.

<h3 id="list-an-organization's-teams-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|detailed|query|string|false|Specify "0" to return team details that do not include projects|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

```json
[
  {
    "id": "48531",
    "slug": "ancient-gabelers",
    "name": "Ancient Gabelers",
    "dateCreated": "2018-11-06T21:20:08.115Z",
    "isMember": false,
    "teamRole": null,
    "flags": {
      "idp:provisioned": false
    },
    "access": [
      "member:read",
      "alerts:read",
      "org:read",
      "event:read",
      "project:read",
      "project:releases",
      "event:write",
      "team:read"
    ],
    "hasAccess": true,
    "isPending": false,
    "memberCount": 2,
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "orgRole": null
  },
  {
    "id": "100253",
    "slug": "powerful-abolitionist",
    "name": "Powerful Abolitionist",
    "dateCreated": "2018-10-03T17:47:50.745447Z",
    "isMember": false,
    "teamRole": null,
    "flags": {
      "idp:provisioned": false
    },
    "access": [
      "member:read",
      "alerts:read",
      "org:read",
      "event:read",
      "project:read",
      "project:releases",
      "event:write",
      "team:read"
    ],
    "hasAccess": true,
    "isPending": false,
    "memberCount": 5,
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "orgRole": null,
    "projects": [
      {
        "id": "6403534",
        "slug": "prime-mover",
        "name": "Prime Mover",
        "platform": null,
        "dateCreated": "2019-04-06T00:02:40.468175Z",
        "isBookmarked": false,
        "isMember": false,
        "features": [
          "alert-filters",
          "custom-inbound-filters",
          "data-forwarding",
          "discard-groups",
          "minidump",
          "race-free-group-creation",
          "rate-limits",
          "servicehooks",
          "similarity-indexing",
          "similarity-indexing-v2",
          "similarity-view",
          "similarity-view-v2",
          "releases"
        ],
        "firstEvent": "2019-04-06T02:00:21Z",
        "firstTransactionEvent": true,
        "access": [
          "alerts:read",
          "event:write",
          "org:read",
          "project:read",
          "member:read",
          "team:read",
          "event:read",
          "project:releases"
        ],
        "hasAccess": true,
        "hasMinifiedStackTrace": false,
        "hasMonitors": true,
        "hasProfiles": false,
        "hasReplays": false,
        "hasSessions": true,
        "isInternal": false,
        "isPublic": false,
        "avatar": {
          "avatarType": "letter_avatar",
          "avatarUuid": null
        },
        "color": "#6d3fbf",
        "status": "active"
      },
      {
        "id": "6403599",
        "slug": "the-spoiled-yoghurt",
        "name": "The Spoiled Yoghurt",
        "platform": "",
        "dateCreated": "2022-06-24T17:55:27.304367Z",
        "isBookmarked": false,
        "isMember": false,
        "features": [
          "alert-filters",
          "custom-inbound-filters",
          "data-forwarding",
          "discard-groups",
          "minidump",
          "race-free-group-creation",
          "rate-limits",
          "servicehooks",
          "similarity-indexing",
          "similarity-indexing-v2",
          "similarity-view",
          "similarity-view-v2"
        ],
        "firstEvent": "2022-07-13T18:17:56.197351Z",
        "firstTransactionEvent": false,
        "access": [
          "alerts:read",
          "event:write",
          "org:read",
          "project:read",
          "member:read",
          "team:read",
          "event:read",
          "project:releases"
        ],
        "hasAccess": true,
        "hasMinifiedStackTrace": false,
        "hasMonitors": true,
        "hasProfiles": false,
        "hasReplays": false,
        "hasSessions": false,
        "isInternal": false,
        "isPublic": false,
        "avatar": {
          "avatarType": "letter_avatar",
          "avatarUuid": null
        },
        "color": "#6e3fbf",
        "status": "active"
      }
    ]
  }
]
```

<h3 id="list-an-organization's-teams-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-teams-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» externalTeams|[object]|false|none|none|
|»» externalId|string|false|none|none|
|»» userId|string|false|none|none|
|»» teamId|string|false|none|none|
|»» id|string|true|none|none|
|»» provider|string|true|none|none|
|»» externalName|string|true|none|none|
|»» integrationId|string|true|none|none|
|» organization|object|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»» name|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» requireEmailVerification|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» features|any|true|none|none|
|»» links|object|true|none|none|
|»»» organizationUrl|string|true|none|none|
|»»» regionUrl|string|true|none|none|
|»» hasAuthProvider|boolean|true|none|none|
|» projects|[object]|false|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isMember|boolean|true|none|none|
|» teamRole|string¦null|true|none|none|
|» flags|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» isPending|boolean|true|none|none|
|» memberCount|integer|true|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|true|none|none|
|»» avatarUuid|string¦null|true|none|none|
|» orgRole|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

## Create a New Team

<a id="opIdCreate a New Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/teams/',
  params: {
  'name' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/teams/', params={
  'name': 'string'
}, headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "slug": "string",
  "idp_provisioned": false
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/teams/?name=string',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/teams/`

Create a new team bound to an organization.

> Body parameter

```json
{
  "name": "string",
  "slug": "string",
  "idp_provisioned": false
}
```

<h3 id="create-a-new-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|name|query|string|true|The name of the team.|
|slug|query|string|false|Optional slug for the team. If not provided a slug is generated from the name.|
|body|body|object|false|none|
|» name|body|string¦null|false|none|
|» slug|body|string¦null|false|none|
|» idp_provisioned|body|boolean|false|none|

> Example responses

```json
{
  "id": "5151492858",
  "slug": "ancient-gabelers",
  "name": "Ancient Gabelers",
  "dateCreated": "2021-06-12T23:38:54.168307Z",
  "isMember": true,
  "teamRole": "admin",
  "flags": {
    "idp:provisioned": false
  },
  "access": [
    "project:write",
    "member:read",
    "event:write",
    "team:admin",
    "alerts:read",
    "project:releases",
    "alerts:write",
    "org:read",
    "team:read",
    "project:admin",
    "project:read",
    "org:integrations",
    "event:read",
    "event:admin",
    "team:write"
  ],
  "hasAccess": true,
  "isPending": false,
  "memberCount": 1,
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "orgRole": null
}
```

<h3 id="create-a-new-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|A team with this slug already exists.|None|

<h3 id="create-a-new-team-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» externalTeams|[object]|false|none|none|
|»» externalId|string|false|none|none|
|»» userId|string|false|none|none|
|»» teamId|string|false|none|none|
|»» id|string|true|none|none|
|»» provider|string|true|none|none|
|»» externalName|string|true|none|none|
|»» integrationId|string|true|none|none|
|» organization|object|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»» name|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» requireEmailVerification|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» features|any|true|none|none|
|»» links|object|true|none|none|
|»»» organizationUrl|string|true|none|none|
|»»» regionUrl|string|true|none|none|
|»» hasAuthProvider|boolean|true|none|none|
|» projects|[object]|false|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isMember|boolean|true|none|none|
|» teamRole|string¦null|true|none|none|
|» flags|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» isPending|boolean|true|none|none|
|» memberCount|integer|true|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|true|none|none|
|»» avatarUuid|string¦null|true|none|none|
|» orgRole|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:write team:write )
</aside>

## List a Team's Projects

<a id="opIdList a Team's Projects"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/teams/{organization_slug}/{team_slug}/projects/`

Return a list of projects bound to a team.

<h3 id="list-a-team's-projects-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|team_slug|path|string|true|The slug of the team the resource belongs to.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

```json
[
  {
    "team": {
      "id": "2349234102",
      "name": "Prime Mover",
      "slug": "prime-mover"
    },
    "teams": [
      {
        "id": "2349234102",
        "name": "Prime Mover",
        "slug": "prime-mover"
      },
      {
        "id": "47584447",
        "name": "Powerful Abolitionist",
        "slug": "powerful-abolitionist"
      }
    ],
    "id": "6758470122493650",
    "name": "the-spoiled-yoghurt",
    "slug": "The Spoiled Yoghurt",
    "isBookmarked": false,
    "isMember": true,
    "access": [
      "project:read",
      "event:read",
      "team:read",
      "alerts:read",
      "org:read",
      "event:write",
      "project:releases",
      "member:read"
    ],
    "hasAccess": true,
    "dateCreated": "2023-03-29T15:25:21.344565Z",
    "environments": [
      "production"
    ],
    "eventProcessing": {
      "symbolicationDegraded": false
    },
    "features": [
      "alert-filters",
      "custom-inbound-filters",
      "data-forwarding",
      "discard-groups",
      "minidump",
      "race-free-group-creation",
      "rate-limits",
      "servicehooks",
      "similarity-indexing",
      "similarity-indexing-v2",
      "similarity-view",
      "similarity-view-v2"
    ],
    "firstEvent": null,
    "firstTransactionEvent": true,
    "hasSessions": false,
    "hasProfiles": false,
    "hasReplays": false,
    "hasMonitors": false,
    "hasMinifiedStackTrace": false,
    "platform": "node-express",
    "platforms": [],
    "latestRelease": null,
    "hasUserReports": false,
    "latestDeploys": null
  },
  {
    "team": {
      "id": "2349234102",
      "name": "Prime Mover",
      "slug": "prime-mover"
    },
    "teams": [
      {
        "id": "2349234102",
        "name": "Prime Mover",
        "slug": "prime-mover"
      }
    ],
    "id": "1829334501859481",
    "name": "Pump Station",
    "slug": "pump-station",
    "isBookmarked": false,
    "isMember": true,
    "access": [
      "project:read",
      "event:read",
      "team:read",
      "alerts:read",
      "org:read",
      "event:write",
      "project:releases",
      "member:read"
    ],
    "hasAccess": true,
    "dateCreated": "2023-03-29T15:21:49.943746Z",
    "environments": [
      "production"
    ],
    "eventProcessing": {
      "symbolicationDegraded": false
    },
    "features": [
      "alert-filters",
      "custom-inbound-filters",
      "data-forwarding",
      "discard-groups",
      "minidump",
      "race-free-group-creation",
      "rate-limits",
      "servicehooks",
      "similarity-indexing",
      "similarity-indexing-v2",
      "similarity-view",
      "similarity-view-v2"
    ],
    "firstEvent": "2023-04-05T21:02:08.054000Z",
    "firstTransactionEvent": false,
    "hasSessions": false,
    "hasProfiles": false,
    "hasReplays": false,
    "hasMonitors": false,
    "hasMinifiedStackTrace": true,
    "platform": "javascript",
    "platforms": [
      "javascript"
    ],
    "latestRelease": null,
    "hasUserReports": false,
    "latestDeploys": null
  }
]
```

<h3 id="list-a-team's-projects-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found.|None|

<h3 id="list-a-team's-projects-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» latestDeploys|object¦null|false|none|none|
|»» **additionalProperties**|object|false|none|none|
|»»» **additionalProperties**|string|false|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» team|object¦null|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» teams|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» eventProcessing|object|true|none|none|
|»» symbolicationDegraded|boolean|true|none|none|
|» platforms|[string]|true|none|none|
|» hasUserReports|boolean|true|none|none|
|» environments|[string]|true|none|none|
|» latestRelease|object¦null|true|none|none|
|»» version|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Retrieve a Team

<a id="opIdRetrieve a Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/teams/{organization_slug}/{team_slug}/`

Return details on an individual team.

<h3 id="retrieve-a-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the team belongs to.|
|team_slug|path|string|true|The slug of the team to get.|

> Example responses

> 200 Response

```json
{
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "dateCreated": "2018-11-06T21:19:55.114Z",
  "hasAccess": true,
  "id": "2",
  "isMember": true,
  "isPending": false,
  "memberCount": 1,
  "name": "Powerful Abolitionist",
  "organization": {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "dateCreated": "2018-11-06T21:19:55.101Z",
    "id": "2",
    "isEarlyAdopter": false,
    "name": "The Interstellar Jurisdiction",
    "require2FA": false,
    "slug": "the-interstellar-jurisdiction",
    "status": {
      "id": "active",
      "name": "active"
    }
  },
  "slug": "powerful-abolitionist"
}
```

<h3 id="retrieve-a-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found|None|

<h3 id="retrieve-a-team-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» hasAccess|boolean|true|none|none|
|» id|string|true|none|none|
|» isMember|boolean|true|none|none|
|» isPending|boolean|true|none|none|
|» memberCount|integer(int64)|true|none|none|
|» organization|object|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» id|string|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» name|string|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:read )
</aside>

## Update a Team

<a id="opIdUpdate a Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "slug": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/teams/{organization_slug}/{team_slug}/`

Update various attributes and configurable settings for the given team.

> Body parameter

```json
{
  "name": "string",
  "slug": "string"
}
```

<h3 id="update-a-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the team belongs to.|
|team_slug|path|string|true|The slug of the team to get.|
|body|body|object|true|none|
|» name|body|string|true|The new name for the team.|
|» slug|body|string|false|A new slug for the team. It has to be unique and available.|

> Example responses

> 200 Response

```json
{
  "avatar": {
    "avatarType": "letter_avatar"
  },
  "dateCreated": "2018-11-06T21:20:08.115Z",
  "hasAccess": true,
  "id": "3",
  "isMember": false,
  "isPending": false,
  "memberCount": 1,
  "name": "The Inflated Philosophers",
  "slug": "the-inflated-philosophers"
}
```

<h3 id="update-a-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found|None|

<h3 id="update-a-team-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» hasAccess|boolean|true|none|none|
|» id|string|true|none|none|
|» isMember|boolean|true|none|none|
|» isPending|boolean|true|none|none|
|» memberCount|integer(int64)|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:write )
</aside>

## Delete a Team

<a id="opIdDelete a Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/teams/{organization_slug}/{team_slug}/`

Schedules a team for deletion.

Note: Deletion happens asynchronously and therefore is not immediate. However once deletion has begun the state of a project changes and will be hidden from most public views.

<h3 id="delete-a-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the team belongs to.|
|team_slug|path|string|true|The slug of the team to get.|

<h3 id="delete-a-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:admin )
</aside>

## Caution: this endpoint may change in the future without notice.

<a id="opIdRetrieve Event Counts for a Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/stats/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/stats/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/stats/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/teams/{organization_slug}/{team_slug}/stats/`

Return a set of points representing a normalized timestamp and the number of events seen in the period.

Query ranges are limited to Sentry’s configured time-series resolutions.

<h3 id="caution:-this-endpoint-may-change-in-the-future-without-notice.-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the team belongs to.|
|team_slug|path|string|true|The slug of the team to get.|
|stat|query|string|false|The name of the stat to query `("received", "rejected")`.|
|since|query|string(date-time)|false|A timestamp to set the start of the query in seconds since UNIX epoch.|
|until|query|string(date-time)|false|A timestamp to set the end of the query in seconds since UNIX epoch.|
|resolution|query|string|false|An explicit resolution to search for (one of `10s`, `1h`, and `1d`).|

#### Enumerated Values

|Parameter|Value|
|---|---|
|stat|received|
|stat|rejected|
|resolution|10s|
|resolution|1h|
|resolution|1d|

> Example responses

> 200 Response

```json
[
  [
    1541455200,
    3302
  ],
  [
    1541458800,
    3832
  ],
  [
    1541462400,
    3669
  ],
  [
    1541466000,
    3533
  ],
  [
    1541469600,
    3499
  ],
  [
    1541473200,
    3201
  ],
  [
    1541476800,
    3769
  ],
  [
    1541480400,
    2706
  ],
  [
    1541484000,
    2698
  ],
  [
    1541487600,
    3747
  ],
  [
    1541491200,
    3261
  ],
  [
    1541494800,
    2860
  ],
  [
    1541498400,
    4350
  ],
  [
    1541502000,
    2924
  ],
  [
    1541505600,
    3389
  ],
  [
    1541509200,
    2931
  ],
  [
    1541512800,
    3132
  ],
  [
    1541516400,
    3213
  ],
  [
    1541520000,
    3650
  ],
  [
    1541523600,
    3096
  ],
  [
    1541527200,
    3845
  ],
  [
    1541530800,
    3545
  ],
  [
    1541534400,
    2880
  ],
  [
    1541538000,
    4057
  ]
]
```

<h3 id="caution:-this-endpoint-may-change-in-the-future-without-notice.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found|None|

<h3 id="caution:-this-endpoint-may-change-in-the-future-without-notice.-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:read )
</aside>

<h1 id="api-reference-projects">Projects</h1>

Endpoints for projects

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/projects/&template=api_error_template.md">Found an error? Let us know.</a>

## Create a New Project

<a id="opIdCreate a New Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/',
  params: {
  'name' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/', params={
  'name': 'string'
}, headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "slug": "string",
  "platform": "string",
  "default_rules": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/teams/{organization_slug}/{team_slug}/projects/?name=string',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/teams/{organization_slug}/{team_slug}/projects/`

Create a new project bound to a team.

> Body parameter

```json
{
  "name": "string",
  "slug": "string",
  "platform": "string",
  "default_rules": true
}
```

<h3 id="create-a-new-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|team_slug|path|string|true|The slug of the team the resource belongs to.|
|name|query|string|true|The name of the project.|
|slug|query|string|false|Optional slug for the project. If not provided a slug is generated from the name.|
|platform|query|string|false|The platform for the project.|
|default_rules|query|boolean|false|Defaults to true where the behavior is to alert the user on every new issue. Setting this to false will turn this off and the user must create their own alerts to be notified of new issues.|
|body|body|object|true|none|
|» name|body|string|true|none|
|» slug|body|string¦null|false|none|
|» platform|body|string¦null|false|none|
|» default_rules|body|boolean|false|none|

> Example responses

```json
{
  "id": "4505321021243392",
  "slug": "the-spoiled-yoghurt",
  "name": "The Spoiled Yoghurt",
  "platform": "python",
  "dateCreated": "2023-06-08T00:13:06.004534Z",
  "isBookmarked": false,
  "isMember": true,
  "features": [
    "alert-filters",
    "custom-inbound-filters",
    "data-forwarding",
    "discard-groups",
    "minidump",
    "race-free-group-creation",
    "rate-limits",
    "servicehooks",
    "similarity-indexing",
    "similarity-indexing-v2",
    "similarity-view",
    "similarity-view-v2"
  ],
  "firstEvent": null,
  "firstTransactionEvent": false,
  "access": [
    "member:read",
    "event:read",
    "project:admin",
    "team:write",
    "project:write",
    "team:admin",
    "project:read",
    "org:integrations",
    "org:read",
    "project:releases",
    "team:read",
    "alerts:write",
    "event:admin",
    "event:write",
    "alerts:read"
  ],
  "hasAccess": true,
  "hasMinifiedStackTrace": false,
  "hasMonitors": false,
  "hasProfiles": false,
  "hasReplays": false,
  "hasSessions": false,
  "isInternal": false,
  "isPublic": false,
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "color": "#3f70bf",
  "status": "active"
}
```

<h3 id="create-a-new-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Team not found.|None|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|A project with this slug already exists.|None|

<h3 id="create-a-new-project-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» avatar|any|true|none|none|
|» color|string|true|none|none|
|» status|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:write )
</aside>

## List Your Projects

<a id="opIdList Your Projects"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/`

Return a list of projects available to the authenticated session.

<h3 id="list-your-projects-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "color": "#bf6e3f",
    "dateCreated": "2018-11-06T21:20:08.064Z",
    "features": [
      "servicehooks",
      "sample-events",
      "data-forwarding",
      "rate-limits",
      "minidump"
    ],
    "firstEvent": null,
    "hasAccess": true,
    "id": "4",
    "isBookmarked": false,
    "isInternal": false,
    "isMember": true,
    "isPublic": false,
    "name": "The Spoiled Yoghurt",
    "organization": {
      "avatar": {
        "avatarType": "letter_avatar",
        "avatarUuid": null
      },
      "dateCreated": "2018-11-06T21:19:55.101Z",
      "id": "2",
      "isEarlyAdopter": false,
      "name": "The Interstellar Jurisdiction",
      "require2FA": false,
      "slug": "the-interstellar-jurisdiction",
      "status": {
        "id": "active",
        "name": "active"
      }
    },
    "platform": null,
    "slug": "the-spoiled-yoghurt",
    "status": "active"
  },
  {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "color": "#bf5b3f",
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "features": [
      "releases",
      "sample-events",
      "minidump",
      "servicehooks",
      "rate-limits",
      "data-forwarding"
    ],
    "firstEvent": null,
    "hasAccess": true,
    "id": "3",
    "isBookmarked": false,
    "isInternal": false,
    "isMember": true,
    "isPublic": false,
    "name": "Prime Mover",
    "organization": {
      "avatar": {
        "avatarType": "letter_avatar",
        "avatarUuid": null
      },
      "dateCreated": "2018-11-06T21:19:55.101Z",
      "id": "2",
      "isEarlyAdopter": false,
      "name": "The Interstellar Jurisdiction",
      "require2FA": false,
      "slug": "the-interstellar-jurisdiction",
      "status": {
        "id": "active",
        "name": "active"
      }
    },
    "platform": null,
    "slug": "prime-mover",
    "status": "active"
  },
  {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "color": "#3fbf7f",
    "dateCreated": "2018-11-06T21:19:55.121Z",
    "features": [
      "releases",
      "sample-events",
      "minidump",
      "servicehooks",
      "rate-limits",
      "data-forwarding"
    ],
    "firstEvent": null,
    "hasAccess": true,
    "id": "2",
    "isBookmarked": false,
    "isInternal": false,
    "isMember": true,
    "isPublic": false,
    "name": "Pump Station",
    "organization": {
      "avatar": {
        "avatarType": "letter_avatar",
        "avatarUuid": null
      },
      "dateCreated": "2018-11-06T21:19:55.101Z",
      "id": "2",
      "isEarlyAdopter": false,
      "name": "The Interstellar Jurisdiction",
      "require2FA": false,
      "slug": "the-interstellar-jurisdiction",
      "status": {
        "id": "active",
        "name": "active"
      }
    },
    "platform": null,
    "slug": "pump-station",
    "status": "active"
  }
]
```

<h3 id="list-your-projects-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-your-projects-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» color|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string¦null|true|none|none|
|» hasAccess|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» name|string|true|none|none|
|» organization|object|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» id|string|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» name|string|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|active|
|status|disabled|
|status|pending_deletion|
|status|deletion_in_progress|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Retrieve a Project

<a id="opIdRetrieve a Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/`

Return details on an individual project.

<h3 id="retrieve-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the project belongs to.|
|project_slug|path|string|true|The slug of the project to retrieve.|

> Example responses

> 200 Response

```json
{
  "allowedDomains": [
    "*"
  ],
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "color": "#3fbf7f",
  "dataScrubber": true,
  "dataScrubberDefaults": true,
  "dateCreated": "2018-11-06T21:19:55.121Z",
  "defaultEnvironment": null,
  "digestsMaxDelay": 1800,
  "digestsMinDelay": 300,
  "features": [
    "releases",
    "sample-events",
    "minidump",
    "servicehooks",
    "rate-limits",
    "data-forwarding"
  ],
  "firstEvent": null,
  "hasAccess": true,
  "id": "2",
  "isBookmarked": false,
  "isInternal": false,
  "isMember": true,
  "isPublic": false,
  "latestRelease": {
    "authors": [],
    "commitCount": 0,
    "data": {},
    "dateCreated": "2018-11-06T21:20:08.033Z",
    "dateReleased": null,
    "deployCount": 0,
    "firstEvent": null,
    "lastCommit": null,
    "lastDeploy": null,
    "lastEvent": null,
    "newGroups": 0,
    "owner": null,
    "projects": [
      {
        "name": "Pump Station",
        "slug": "pump-station"
      }
    ],
    "ref": "6ba09a7c53235ee8a8fa5ee4c1ca8ca886e7fdbb",
    "shortVersion": "2.0rc2",
    "url": null,
    "version": "2.0rc2"
  },
  "name": "Pump Station",
  "options": {
    "feedback:branding": true,
    "filters:blacklisted_ips": "",
    "filters:error_messages": "",
    "filters:releases": "",
    "sentry:csp_ignored_sources": "",
    "sentry:csp_ignored_sources_defaults": true,
    "sentry:reprocessing_active": false
  },
  "organization": {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "dateCreated": "2018-11-06T21:19:55.101Z",
    "id": "2",
    "isEarlyAdopter": false,
    "name": "The Interstellar Jurisdiction",
    "require2FA": false,
    "slug": "the-interstellar-jurisdiction",
    "status": {
      "id": "active",
      "name": "active"
    }
  },
  "platform": null,
  "platforms": [],
  "plugins": [
    {
      "assets": [],
      "author": {
        "name": "Sentry Team",
        "url": "https://github.com/getsentry/sentry"
      },
      "canDisable": true,
      "contexts": [],
      "description": "Integrates web hooks.",
      "doc": "",
      "enabled": false,
      "hasConfiguration": true,
      "id": "webhooks",
      "isTestable": true,
      "metadata": {},
      "name": "WebHooks",
      "resourceLinks": [
        {
          "title": "Bug Tracker",
          "url": "https://github.com/getsentry/sentry/issues"
        },
        {
          "title": "Source",
          "url": "https://github.com/getsentry/sentry"
        }
      ],
      "shortName": "WebHooks",
      "slug": "webhooks",
      "status": "unknown",
      "type": "notification",
      "version": "9.1.0.dev0"
    }
  ],
  "processingIssues": 0,
  "relayPiiConfig": null,
  "resolveAge": 0,
  "safeFields": [],
  "scrapeJavaScript": true,
  "scrubIPAddresses": false,
  "securityToken": "c3072787e20911e8a37988e9fe5cab71",
  "securityTokenHeader": null,
  "sensitiveFields": [],
  "slug": "pump-station",
  "status": "active",
  "storeCrashReports": false,
  "subjectPrefix": "[Sentry]",
  "subjectTemplate": "$shortID - $title",
  "team": {
    "id": "2",
    "name": "Powerful Abolitionist",
    "slug": "powerful-abolitionist"
  },
  "teams": [
    {
      "id": "2",
      "name": "Powerful Abolitionist",
      "slug": "powerful-abolitionist"
    }
  ],
  "verifySSL": false
}
```

<h3 id="retrieve-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<h3 id="retrieve-a-project-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» allowedDomains|[string]|true|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» color|string|true|none|none|
|» dataScrubber|boolean|true|none|none|
|» dataScrubberDefaults|boolean|true|none|none|
|» dateCreated|string|true|none|none|
|» defaultEnvironment|string¦null|true|none|none|
|» digestsMaxDelay|integer|true|none|none|
|» digestsMinDelay|integer|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string¦null|true|none|none|
|» hasAccess|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» latestRelease|object¦null|true|none|none|
|»» authors|[object]|true|none|none|
|»»» name|string|false|none|none|
|»»» email|string|false|none|none|
|»» commitCount|integer|true|none|none|
|»» data|object|true|none|none|
|»» dateCreated|string|true|none|none|
|»» dateReleased|string¦null|true|none|none|
|»» deployCount|integer|true|none|none|
|»» firstEvent|string¦null|true|none|none|
|»» lastCommit|object¦null|true|none|none|
|»» lastDeploy|object¦null|true|none|none|
|»» lastEvent|string¦null|true|none|none|
|»» newGroups|integer|true|none|none|
|»» owner|string¦null|true|none|none|
|»» projects|[object]|true|none|none|
|»»» name|string|false|none|none|
|»»» slug|string|false|none|none|
|»» ref|string¦null|true|none|none|
|»» shortVersion|string|true|none|none|
|»» url|string¦null|true|none|none|
|»» version|string|true|none|none|
|» name|string|true|none|none|
|» options|object|true|none|none|
|»» feedback:branding|boolean|false|none|none|
|»» filters:blacklisted_ips|string|false|none|none|
|»» filters:error_messages|string|false|none|none|
|»» filters:releases|string|false|none|none|
|»» sentry:csp_ignored_sources|string|false|none|none|
|»» sentry:csp_ignored_sources_defaults|boolean|false|none|none|
|»» sentry:reprocessing_active|boolean|false|none|none|
|» organization|object|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» id|string|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» name|string|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» platforms|[string]|true|none|none|
|» plugins|[object]|false|none|none|
|»» assets|[string]|true|none|none|
|»» author|object¦null|false|none|none|
|»»» name|string|false|none|none|
|»»» url|string|false|none|none|
|»» canDisable|boolean|true|none|none|
|»» contexts|[string]|true|none|none|
|»» description|string|false|none|none|
|»» doc|string|true|none|none|
|»» enabled|boolean|true|none|none|
|»» hasConfiguration|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isTestable|boolean|true|none|none|
|»» metadata|object|true|none|none|
|»» name|string|true|none|none|
|»» resourceLinks|[object]¦null|false|none|none|
|»»» title|string|false|none|none|
|»»» url|string|false|none|none|
|»» shortName|string|true|none|none|
|»» slug|string|true|none|none|
|»» status|string|true|none|none|
|»» type|string|true|none|none|
|»» version|string¦null|false|none|none|
|» processingIssues|integer|true|none|none|
|» relayPiiConfig|string¦null|true|none|none|
|» resolveAge|integer|true|none|none|
|» safeFields|[string]|true|none|none|
|» scrapeJavaScript|boolean|true|none|none|
|» scrubIPAddresses|boolean|true|none|none|
|» securityToken|string|true|none|none|
|» securityTokenHeader|string¦null|true|none|none|
|» sensitiveFields|[string]|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» storeCrashReports|boolean¦null|true|none|none|
|» subjectPrefix|string|true|none|none|
|» subjectTemplate|string|true|none|none|
|» team|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» teams|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» verifySSL|boolean|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Update a Project

<a id="opIdUpdate a Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "slug": "string",
  "platform": "string",
  "isBookmarked": true,
  "digestsMinDelay": 0,
  "digestsMaxDelay": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/projects/{organization_slug}/{project_slug}/`

Update various attributes and configurable settings for the given project.  Only supplied values are updated.

> Body parameter

```json
{
  "name": "string",
  "slug": "string",
  "platform": "string",
  "isBookmarked": true,
  "digestsMinDelay": 0,
  "digestsMaxDelay": 0
}
```

<h3 id="update-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the project belongs to.|
|project_slug|path|string|true|The slug of the project to update.|
|body|body|object|false|none|
|» name|body|string|false|The new name for the project.|
|» slug|body|string|false|The new slug for the project.|
|» platform|body|string|false|The new platform for the project.|
|» isBookmarked|body|boolean|false|In case this API call is invoked with a user context this allows changing of the bookmark flag.|
|» digestsMinDelay|body|integer|false|none|
|» digestsMaxDelay|body|integer|false|none|

> Example responses

> 200 Response

```json
{
  "allowedDomains": [
    "http://example.com",
    "http://example.invalid"
  ],
  "avatar": {
    "avatarType": "letter_avatar",
    "avatarUuid": null
  },
  "color": "#bf803f",
  "dataScrubber": true,
  "dataScrubberDefaults": true,
  "dateCreated": "2018-11-06T21:20:19.624Z",
  "defaultEnvironment": null,
  "digestsMaxDelay": 1800,
  "digestsMinDelay": 300,
  "features": [
    "releases",
    "sample-events",
    "minidump",
    "servicehooks",
    "rate-limits",
    "data-forwarding"
  ],
  "firstEvent": null,
  "hasAccess": true,
  "id": "5",
  "isBookmarked": false,
  "isInternal": false,
  "isMember": true,
  "isPublic": false,
  "latestRelease": {
    "authors": [],
    "commitCount": 0,
    "data": {},
    "dateCreated": "2018-11-06T21:20:19.645Z",
    "dateReleased": null,
    "deployCount": 0,
    "firstEvent": "2018-11-06T21:20:19.718Z",
    "lastCommit": null,
    "lastDeploy": null,
    "lastEvent": "2018-11-06T21:20:19.718Z",
    "newGroups": 0,
    "owner": null,
    "projects": [
      {
        "name": "Plane Proxy",
        "slug": "plane-proxy"
      }
    ],
    "ref": null,
    "shortVersion": "21c04bd",
    "url": null,
    "version": "21c04bd8fa23cfd85f5f5867f18efd2cf13247bc"
  },
  "name": "Plane Proxy",
  "options": {
    "feedback:branding": true,
    "filters:blacklisted_ips": "",
    "filters:error_messages": "",
    "filters:releases": "",
    "sentry:csp_ignored_sources": "",
    "sentry:csp_ignored_sources_defaults": true,
    "sentry:reprocessing_active": false
  },
  "organization": {
    "avatar": {
      "avatarType": "letter_avatar",
      "avatarUuid": null
    },
    "dateCreated": "2018-11-06T21:19:55.101Z",
    "id": "2",
    "isEarlyAdopter": false,
    "name": "The Interstellar Jurisdiction",
    "require2FA": false,
    "slug": "the-interstellar-jurisdiction",
    "status": {
      "id": "active",
      "name": "active"
    }
  },
  "platform": "javascript",
  "platforms": [],
  "plugins": [
    {
      "assets": [],
      "author": {
        "name": "Sentry Team",
        "url": "https://github.com/getsentry/sentry"
      },
      "canDisable": true,
      "contexts": [],
      "description": "Integrates web hooks.",
      "doc": "",
      "enabled": false,
      "hasConfiguration": true,
      "id": "webhooks",
      "isTestable": true,
      "metadata": {},
      "name": "WebHooks",
      "resourceLinks": [
        {
          "title": "Bug Tracker",
          "url": "https://github.com/getsentry/sentry/issues"
        },
        {
          "title": "Source",
          "url": "https://github.com/getsentry/sentry"
        }
      ],
      "shortName": "WebHooks",
      "slug": "webhooks",
      "status": "unknown",
      "type": "notification",
      "version": "9.1.0.dev0"
    }
  ],
  "processingIssues": 0,
  "relayPiiConfig": null,
  "resolveAge": 0,
  "safeFields": [],
  "scrapeJavaScript": true,
  "scrubIPAddresses": false,
  "securityToken": "c55a4bdce20911e88eed88e9fe5cab71",
  "securityTokenHeader": null,
  "sensitiveFields": [],
  "slug": "plane-proxy",
  "status": "active",
  "storeCrashReports": false,
  "subjectPrefix": "[Sentry]",
  "subjectTemplate": "$shortID - $title",
  "team": {
    "id": "2",
    "name": "Powerful Abolitionist",
    "slug": "powerful-abolitionist"
  },
  "teams": [
    {
      "id": "2",
      "name": "Powerful Abolitionist",
      "slug": "powerful-abolitionist"
    }
  ],
  "verifySSL": false
}
```

<h3 id="update-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<h3 id="update-a-project-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» allowedDomains|[string]|true|none|none|
|» avatar|object|true|none|none|
|»» avatarType|string|false|none|none|
|»» avatarUuid|string¦null|false|none|none|
|» color|string|true|none|none|
|» dataScrubber|boolean|true|none|none|
|» dataScrubberDefaults|boolean|true|none|none|
|» dateCreated|string|true|none|none|
|» defaultEnvironment|string¦null|true|none|none|
|» digestsMaxDelay|integer|true|none|none|
|» digestsMinDelay|integer|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string¦null|true|none|none|
|» hasAccess|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» latestRelease|object¦null|true|none|none|
|»» authors|[object]|true|none|none|
|»»» name|string|false|none|none|
|»»» email|string|false|none|none|
|»» commitCount|integer|true|none|none|
|»» data|object|true|none|none|
|»» dateCreated|string|true|none|none|
|»» dateReleased|string¦null|true|none|none|
|»» deployCount|integer|true|none|none|
|»» firstEvent|string¦null|true|none|none|
|»» lastCommit|object¦null|true|none|none|
|»» lastDeploy|object¦null|true|none|none|
|»» lastEvent|string¦null|true|none|none|
|»» newGroups|integer|true|none|none|
|»» owner|string¦null|true|none|none|
|»» projects|[object]|true|none|none|
|»»» name|string|false|none|none|
|»»» slug|string|false|none|none|
|»» ref|string¦null|true|none|none|
|»» shortVersion|string|true|none|none|
|»» url|string¦null|true|none|none|
|»» version|string|true|none|none|
|» name|string|true|none|none|
|» options|object|true|none|none|
|»» feedback:branding|boolean|false|none|none|
|»» filters:blacklisted_ips|string|false|none|none|
|»» filters:error_messages|string|false|none|none|
|»» filters:releases|string|false|none|none|
|»» sentry:csp_ignored_sources|string|false|none|none|
|»» sentry:csp_ignored_sources_defaults|boolean|false|none|none|
|»» sentry:reprocessing_active|boolean|false|none|none|
|» organization|object|true|none|none|
|»» avatar|object|true|none|none|
|»»» avatarType|string|false|none|none|
|»»» avatarUuid|string¦null|false|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» id|string|true|none|none|
|»» isEarlyAdopter|boolean|true|none|none|
|»» name|string|true|none|none|
|»» require2FA|boolean|true|none|none|
|»» slug|string|true|none|none|
|»» status|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» platforms|[string]|true|none|none|
|» plugins|[object]|false|none|none|
|»» assets|[string]|true|none|none|
|»» author|object¦null|false|none|none|
|»»» name|string|false|none|none|
|»»» url|string|false|none|none|
|»» canDisable|boolean|true|none|none|
|»» contexts|[string]|true|none|none|
|»» description|string|false|none|none|
|»» doc|string|true|none|none|
|»» enabled|boolean|true|none|none|
|»» hasConfiguration|boolean|true|none|none|
|»» id|string|true|none|none|
|»» isTestable|boolean|true|none|none|
|»» metadata|object|true|none|none|
|»» name|string|true|none|none|
|»» resourceLinks|[object]¦null|false|none|none|
|»»» title|string|false|none|none|
|»»» url|string|false|none|none|
|»» shortName|string|true|none|none|
|»» slug|string|true|none|none|
|»» status|string|true|none|none|
|»» type|string|true|none|none|
|»» version|string¦null|false|none|none|
|» processingIssues|integer|true|none|none|
|» relayPiiConfig|string¦null|true|none|none|
|» resolveAge|integer|true|none|none|
|» safeFields|[string]|true|none|none|
|» scrapeJavaScript|boolean|true|none|none|
|» scrubIPAddresses|boolean|true|none|none|
|» securityToken|string|true|none|none|
|» securityTokenHeader|string¦null|true|none|none|
|» sensitiveFields|[string]|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» storeCrashReports|boolean¦null|true|none|none|
|» subjectPrefix|string|true|none|none|
|» subjectTemplate|string|true|none|none|
|» team|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» teams|[object]|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» slug|string|true|none|none|
|» verifySSL|boolean|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Delete a Project

<a id="opIdDelete a Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/`

Schedules a project for deletion.

Deletion happens asynchronously and therefore is not immediate.
However once deletion has begun the state of a project changes and
will be hidden from most public views.

<h3 id="delete-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the project belongs to.|
|project_slug|path|string|true|The slug of the project to delete.|

<h3 id="delete-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin )
</aside>

## Upload a New File

<a id="opIdUpload a New File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "file": "string"
}';
const headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/`

Upload a new debug information file for the given release.

Unlike other API requests, files must be uploaded using the
traditional multipart/form-data content-type.

The file uploaded is a zip archive of an Apple .dSYM folder which
contains the individual debug images.  Uploading through this endpoint
will create different files for the contained images.

> Body parameter

```yaml
file: string

```

<h3 id="upload-a-new-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the project belongs to.|
|project_slug|path|string|true|The slug of the project to upload a file to.|
|body|body|object|true|none|
|» file|body|string(binary)|true|The multipart encoded file.|

> Example responses

<h3 id="upload-a-new-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="upload-a-new-file-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Delete a Specific Project's Debug Information File

<a id="opIdDelete a Specific Project's Debug Information File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/',
  params: {
  'id' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/', params={
  'id': 'string'
}, headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/?id=string',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/`

Delete a debug information file for a given project.

<h3 id="delete-a-specific-project's-debug-information-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the file belongs to.|
|project_slug|path|string|true|The slug of the project to delete the DIF.|
|id|query|string|true|The ID of the DIF to delete.|

<h3 id="delete-a-specific-project's-debug-information-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## List a Project's Users

<a id="opIdList a Project's Users"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/users/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/users/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/users/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/users/`

Return a list of users seen within this project.

<h3 id="list-a-project's-users-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|query|query|string|false|Limit results to users matching the given query. Prefixes should be used to suggest the field to match on: `id`, `email`, `username`, `ip`. For example, `query=email:foo@example.com`|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2020-07-16T00:50:40.342174Z",
    "id": "21077833046",
    "username": "sentry",
    "email": "sentry@example.com"
  }
]
```

<h3 id="list-a-project's-users-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-project's-users-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» id|string|true|none|none|
|» username|string¦null|true|none|none|
|» email|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## List a Tag's Values

<a id="opIdList a Tag's Values"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/tags/{key}/values/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/tags/{key}/values/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/tags/{key}/values/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/tags/{key}/values/`

Return a list of values associated with this key.  The `query`
parameter can be used to to perform a "contains" match on
values. 

When [paginated](/api/pagination) can return at most 1000 values.

<h3 id="list-a-tag's-values-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|key|path|string|true|The tag key to look up.|

> Example responses

> 200 Response

```json
[
  {
    "name": "mint_choco"
  }
]
```

<h3 id="list-a-tag's-values-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-tag's-values-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» name|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Caution
This endpoint may change in the future without  notice.

<a id="opIdRetrieve Event Counts for a Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/stats/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/stats/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/stats/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/stats/`

Return a set of points representing a normalized timestamp and the
number of events seen in the period.

Query ranges are limited to Sentry's configured time-series resolutions.

<h3 id="caution
this-endpoint-may-change-in-the-future-without--notice.-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|stat|query|string|false|The name of the stat to query `("received", "rejected", "blacklisted", "generated")`.|
|since|query|string(date-time)|false|A timestamp to set the start of the query in seconds since UNIX epoch.|
|until|query|string(date-time)|false|A timestamp to set the end of the query in seconds since UNIX epoch.|
|resolution|query|string|false|An explicit resolution to search for (one of `10s`, `1h`, and `1d`).|

#### Enumerated Values

|Parameter|Value|
|---|---|
|stat|received|
|stat|rejected|
|stat|blacklisted|
|stat|generated|
|resolution|10s|
|resolution|1h|
|resolution|1d|

> Example responses

> 200 Response

```json
[
  [
    1541455200,
    1184
  ],
  [
    1541458800,
    1410
  ],
  [
    1541462400,
    1440
  ],
  [
    1541466000,
    1682
  ],
  [
    1541469600,
    1203
  ],
  [
    1541473200,
    497
  ],
  [
    1541476800,
    661
  ],
  [
    1541480400,
    1481
  ],
  [
    1541484000,
    678
  ],
  [
    1541487600,
    1857
  ],
  [
    1541491200,
    819
  ],
  [
    1541494800,
    1013
  ],
  [
    1541498400,
    1883
  ],
  [
    1541502000,
    1450
  ],
  [
    1541505600,
    1102
  ],
  [
    1541509200,
    1317
  ],
  [
    1541512800,
    1017
  ],
  [
    1541516400,
    813
  ],
  [
    1541520000,
    1189
  ],
  [
    1541523600,
    496
  ],
  [
    1541527200,
    1936
  ],
  [
    1541530800,
    1405
  ],
  [
    1541534400,
    617
  ],
  [
    1541538000,
    1533
  ]
]
```

<h3 id="caution
this-endpoint-may-change-in-the-future-without--notice.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="caution
this-endpoint-may-change-in-the-future-without--notice.-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## List a Project's User Feedback

<a id="opIdList a Project's User Feedback"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/user-feedback/`

Return a list of user feedback items within this project.

<h3 id="list-a-project's-user-feedback-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|

> Example responses

> 200 Response

```json
[
  {
    "comments": "It broke!",
    "dateCreated": "2018-11-06T21:20:11.468Z",
    "email": "jane@example.com",
    "event": {
      "eventID": "14bad9a2e3774046977a21440ddb39b2",
      "id": null
    },
    "eventID": "14bad9a2e3774046977a21440ddb39b2",
    "id": "1",
    "issue": null,
    "name": "Jane Smith",
    "user": null
  }
]
```

<h3 id="list-a-project's-user-feedback-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-a-project's-user-feedback-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» comments|string|true|none|none|
|» dateCreated|string|true|none|none|
|» email|string|true|none|none|
|» event|object|true|none|none|
|»» eventID|string|false|none|none|
|»» id|string¦null|false|none|none|
|» eventID|string|true|none|none|
|» id|string|true|none|none|
|» issue|object¦null|true|none|none|
|» name|string|true|none|none|
|» user|object¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Submit User Feedback

<a id="opIdSubmit User Feedback"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "event_id": "string",
  "name": "string",
  "email": "string",
  "comments": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/user-feedback/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/projects/{organization_slug}/{project_slug}/user-feedback/`

Submit and associate user feedback with an issue.

Feedback must be received by the server no more than 30 minutes after the event was saved.

Additionally, within 5 minutes of submitting feedback it may also be overwritten. This is useful in situations where you may need to retry sending a request due to network failures.

If feedback is rejected due to a mutability threshold, a 409 status code will be returned.

Note: Feedback may be submitted with DSN authentication (see auth documentation).

> Body parameter

```json
{
  "event_id": "string",
  "name": "string",
  "email": "string",
  "comments": "string"
}
```

<h3 id="submit-user-feedback-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|body|body|object|false|none|
|» event_id|body|string|true|The event ID. This can be retrieved from the [beforeSend callback](https://docs.sentry.io/platforms/javascript/configuration/filtering/#using-beforesend).|
|» name|body|string|true|User's name.|
|» email|body|string|true|User's email address.|
|» comments|body|string|true|Comments supplied by user.|

> Example responses

> 200 Response

```json
{
  "comments": "It broke!",
  "dateCreated": "2018-11-06T21:20:11.468Z",
  "email": "jane@example.com",
  "event": {
    "eventID": "14bad9a2e3774046977a21440ddb39b2",
    "id": null
  },
  "eventID": "14bad9a2e3774046977a21440ddb39b2",
  "id": "1",
  "issue": null,
  "name": "Jane Smith",
  "user": null
}
```

<h3 id="submit-user-feedback-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|None|

<h3 id="submit-user-feedback-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» comments|string|true|none|none|
|» dateCreated|string|true|none|none|
|» email|string|true|none|none|
|» event|object|true|none|none|
|»» eventID|string|false|none|none|
|»» id|string¦null|false|none|none|
|» eventID|string|true|none|none|
|» id|string|true|none|none|
|» issue|object¦null|true|none|none|
|» name|string|true|none|none|
|» user|object¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write ), dsn
</aside>

## Create a New Client Key

<a id="opIdCreate a New Client Key"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/projects/{organization_slug}/{project_slug}/keys/`

Create a new client key bound to a project.  The key's secret and public key are generated by the server.

> Body parameter

```json
{
  "name": "string"
}
```

<h3 id="create-a-new-client-key-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|body|body|object|true|none|
|» name|body|string|true|The name for the new key.|

> Example responses

> 201 Response

```json
{
  "browserSdk": {
    "choices": [
      [
        "latest",
        "latest"
      ],
      [
        "4.x",
        "4.x"
      ]
    ]
  },
  "browserSdkVersion": "4.x",
  "dateCreated": "2018-11-06T21:20:07.941Z",
  "dsn": {
    "cdn": "https://sentry.io/js-sdk-loader/cec9dfceb0b74c1c9a5e3c135585f364.min.js",
    "csp": "https://sentry.io/api/2/csp-report/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
    "minidump": "https://sentry.io/api/2/minidump/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
    "public": "https://cec9dfceb0b74c1c9a5e3c135585f364@sentry.io/2",
    "secret": "https://cec9dfceb0b74c1c9a5e3c135585f364:4f6a592349e249c5906918393766718d@sentry.io/2",
    "security": "https://sentry.io/api/2/security/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364"
  },
  "id": "cec9dfceb0b74c1c9a5e3c135585f364",
  "isActive": true,
  "label": "Fabulous Key",
  "name": "Fabulous Key",
  "projectId": 2,
  "public": "cec9dfceb0b74c1c9a5e3c135585f364",
  "rateLimit": null,
  "secret": "4f6a592349e249c5906918393766718d"
}
```

<h3 id="create-a-new-client-key-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="create-a-new-client-key-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» browserSdk|object|true|none|none|
|»» choices|[array]|false|none|none|
|» browserSdkVersion|string|true|none|none|
|» dateCreated|string|true|none|none|
|» dsn|object|true|none|none|
|»» cdn|string|true|none|none|
|»» csp|string|true|none|none|
|»» minidump|string|true|none|none|
|»» public|string|true|none|none|
|»» secret|string|true|none|none|
|»» security|string|true|none|none|
|» id|string|true|none|none|
|» isActive|boolean|true|none|none|
|» label|string|true|none|none|
|» name|string|true|none|none|
|» projectId|integer|true|none|none|
|» public|string|true|none|none|
|» rateLimit|string¦null|true|none|none|
|» secret|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Delete a Client Key

<a id="opIdDelete a Client Key"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/`

Delete a client key.

<h3 id="delete-a-client-key-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|key_id|path|string|true|The ID of the key to delete.|

<h3 id="delete-a-client-key-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin )
</aside>

## Register a New Service Hook

<a id="opIdRegister a New Service Hook"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "url": "string",
  "events": [
    "string"
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/projects/{organization_slug}/{project_slug}/hooks/`

Register a new service hook on a project.

Events include:

- event.alert: An alert is generated for an event (via rules).
- event.created: A new event has been processed.

This endpoint requires the 'servicehooks' feature to be enabled for your project.

> Body parameter

```json
{
  "url": "string",
  "events": [
    "string"
  ]
}
```

<h3 id="register-a-new-service-hook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|body|body|object|true|none|
|» url|body|string|true|The URL for the webhook.|
|» events|body|[string]|true|The events to subscribe to.|

> Example responses

> 201 Response

```json
{
  "dateCreated": "2018-11-06T21:20:08.143Z",
  "events": [
    "event.alert",
    "event.created"
  ],
  "id": "4f9d73e63b7144ecb8944c41620a090b",
  "secret": "8fcac28aaa4c4f5fa572b61d40a8e084364db25fd37449c299e5a41c0504cbc2",
  "status": "active",
  "url": "https://empowerplant.io/sentry-hook"
}
```

<h3 id="register-a-new-service-hook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|You do not have that feature enabled|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="register-a-new-service-hook-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» events|[string]|true|none|none|
|» id|string|true|none|none|
|» secret|string|true|none|none|
|» status|string|true|none|none|
|» url|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Update a Service Hook

<a id="opIdUpdate a Service Hook"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "url": "string",
  "events": [
    "string"
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/`

Update a service hook.

> Body parameter

```json
{
  "url": "string",
  "events": [
    "string"
  ]
}
```

<h3 id="update-a-service-hook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|hook_id|path|string|true|The GUID of the service hook.|
|body|body|object|false|none|
|» url|body|string|true|The URL for the webhook.|
|» events|body|[string]|true|The events to subscribe to.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:08.143Z",
  "events": [
    "event.alert",
    "event.created"
  ],
  "id": "4f9d73e63b7144ecb8944c41620a090b",
  "secret": "8fcac28aaa4c4f5fa572b61d40a8e084364db25fd37449c299e5a41c0504cbc2",
  "status": "active",
  "url": "https://empowerplant.io/sentry-hook"
}
```

<h3 id="update-a-service-hook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="update-a-service-hook-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» events|[string]|true|none|none|
|» id|string|true|none|none|
|» secret|string|true|none|none|
|» status|string|true|none|none|
|» url|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Remove a Service Hook

<a id="opIdRemove a Service Hook"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/`

Remove a service hook.

<h3 id="remove-a-service-hook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|hook_id|path|string|true|The GUID of the service hook.|

<h3 id="remove-a-service-hook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin )
</aside>

<h1 id="api-reference-client-keys">Client Keys</h1>

Endpoints for projects

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/projects/&template=api_error_template.md">Found an error? Let us know.</a>

## List a Project's Client Keys

<a id="opIdList a Project's Client Keys"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/keys/`

Return a list of client keys bound to a project.

<h3 id="list-a-project's-client-keys-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "browserSdk": {
      "choices": [
        [
          "latest",
          "latest"
        ],
        [
          "4.x",
          "4.x"
        ]
      ]
    },
    "browserSdkVersion": "4.x",
    "dateCreated": "2018-11-06T21:20:07.941Z",
    "dsn": {
      "cdn": "https://sentry.io/js-sdk-loader/cec9dfceb0b74c1c9a5e3c135585f364.min.js",
      "csp": "https://sentry.io/api/2/csp-report/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
      "minidump": "https://sentry.io/api/2/minidump/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
      "public": "https://cec9dfceb0b74c1c9a5e3c135585f364@sentry.io/2",
      "secret": "https://cec9dfceb0b74c1c9a5e3c135585f364:4f6a592349e249c5906918393766718d@sentry.io/2",
      "security": "https://sentry.io/api/2/security/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364"
    },
    "id": "cec9dfceb0b74c1c9a5e3c135585f364",
    "isActive": true,
    "label": "Fabulous Key",
    "name": "Fabulous Key",
    "projectId": 2,
    "public": "cec9dfceb0b74c1c9a5e3c135585f364",
    "rateLimit": null,
    "secret": "4f6a592349e249c5906918393766718d"
  }
]
```

<h3 id="list-a-project's-client-keys-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-project's-client-keys-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» browserSdk|object|true|none|none|
|»» choices|[array]|false|none|none|
|» browserSdkVersion|string|true|none|none|
|» dateCreated|string|true|none|none|
|» dsn|object|true|none|none|
|»» cdn|string|true|none|none|
|»» csp|string|true|none|none|
|»» minidump|string|true|none|none|
|»» public|string|true|none|none|
|»» secret|string|true|none|none|
|»» security|string|true|none|none|
|» id|string|true|none|none|
|» isActive|boolean|true|none|none|
|» label|string|true|none|none|
|» name|string|true|none|none|
|» projectId|integer|true|none|none|
|» public|string|true|none|none|
|» rateLimit|string¦null|true|none|none|
|» secret|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Update a Client Key

<a id="opIdUpdate a Client Key"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/projects/{organization_slug}/{project_slug}/keys/{key_id}/`

Update a client key.  This can be used to rename a key.

> Body parameter

```json
{
  "name": "string"
}
```

<h3 id="update-a-client-key-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|key_id|path|string|true|The ID of the key to update.|
|body|body|object|true|none|
|» name|body|string|false|The new name for the client key.|

> Example responses

> 200 Response

```json
{
  "browserSdk": {
    "choices": [
      [
        "latest",
        "latest"
      ],
      [
        "4.x",
        "4.x"
      ]
    ]
  },
  "browserSdkVersion": "4.x",
  "dateCreated": "2018-11-06T21:20:07.941Z",
  "dsn": {
    "cdn": "https://sentry.io/js-sdk-loader/cec9dfceb0b74c1c9a5e3c135585f364.min.js",
    "csp": "https://sentry.io/api/2/csp-report/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
    "minidump": "https://sentry.io/api/2/minidump/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364",
    "public": "https://cec9dfceb0b74c1c9a5e3c135585f364@sentry.io/2",
    "secret": "https://cec9dfceb0b74c1c9a5e3c135585f364:4f6a592349e249c5906918393766718d@sentry.io/2",
    "security": "https://sentry.io/api/2/security/?sentry_key=cec9dfceb0b74c1c9a5e3c135585f364"
  },
  "id": "cec9dfceb0b74c1c9a5e3c135585f364",
  "isActive": true,
  "label": "Fluffy Key",
  "name": "Fluffy Key",
  "projectId": 2,
  "public": "cec9dfceb0b74c1c9a5e3c135585f364",
  "rateLimit": null,
  "secret": "4f6a592349e249c5906918393766718d"
}
```

<h3 id="update-a-client-key-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<h3 id="update-a-client-key-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» browserSdk|object|true|none|none|
|»» choices|[array]|false|none|none|
|» browserSdkVersion|string|true|none|none|
|» dateCreated|string|true|none|none|
|» dsn|object|true|none|none|
|»» cdn|string|true|none|none|
|»» csp|string|true|none|none|
|»» minidump|string|true|none|none|
|»» public|string|true|none|none|
|»» secret|string|true|none|none|
|»» security|string|true|none|none|
|» id|string|true|none|none|
|» isActive|boolean|true|none|none|
|» label|string|true|none|none|
|» name|string|true|none|none|
|» projectId|integer|true|none|none|
|» public|string|true|none|none|
|» rateLimit|string¦null|true|none|none|
|» secret|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

<h1 id="api-reference-debug-files">Debug Files</h1>

Endpoints for projects

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/projects/&template=api_error_template.md">Found an error? Let us know.</a>

## List a Project's Debug Information Files

<a id="opIdList a Project's Debug Information Files"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/files/dsyms/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/files/dsyms/`

Retrieve a list of debug information files for a given project.

<h3 id="list-a-project's-debug-information-files-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the file belongs to.|
|project_slug|path|string|true|The slug of the project to list the DIFs of.|

> Example responses

<h3 id="list-a-project's-debug-information-files-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="list-a-project's-debug-information-files-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

<h1 id="api-reference-service-hooks">Service Hooks</h1>

Endpoints for projects

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/projects/&template=api_error_template.md">Found an error? Let us know.</a>

## List a Project's Service Hooks

<a id="opIdList a Project's Service Hooks"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/hooks/`

Return a list of service hooks bound to a project.

<h3 id="list-a-project's-service-hooks-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:20:08.143Z",
    "events": [
      "event.alert",
      "event.created"
    ],
    "id": "4f9d73e63b7144ecb8944c41620a090b",
    "secret": "8fcac28aaa4c4f5fa572b61d40a8e084364db25fd37449c299e5a41c0504cbc2",
    "status": "active",
    "url": "https://empowerplant.io/sentry-hook"
  }
]
```

<h3 id="list-a-project's-service-hooks-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|You do not have that feature enabled|None|

<h3 id="list-a-project's-service-hooks-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» events|[string]|true|none|none|
|» id|string|true|none|none|
|» secret|string|true|none|none|
|» status|string|true|none|none|
|» url|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## Retrieve a Service Hook

<a id="opIdRetrieve a Service Hook"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/hooks/{hook_id}/`

Return a service hook bound to a project.

<h3 id="retrieve-a-service-hook-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the client keys belong to.|
|project_slug|path|string|true|The slug of the project the client keys belong to.|
|hook_id|path|string|true|The GUID of the service hook.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:08.143Z",
  "events": [
    "event.alert",
    "event.created"
  ],
  "id": "4f9d73e63b7144ecb8944c41620a090b",
  "secret": "8fcac28aaa4c4f5fa572b61d40a8e084364db25fd37449c299e5a41c0504cbc2",
  "status": "active",
  "url": "https://empowerplant.io/sentry-hook"
}
```

<h3 id="retrieve-a-service-hook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="retrieve-a-service-hook-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string|true|none|none|
|» events|[string]|true|none|none|
|» id|string|true|none|none|
|» secret|string|true|none|none|
|» status|string|true|none|none|
|» url|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

<h1 id="api-reference-events">Events</h1>

Endpoints for events and issues

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/events/&template=api_error_template.md">Found an error? Let us know.</a>

## Debug issues related to source maps for a given event

<a id="opIdDebug issues related to source maps for a given event"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/source-map-debug/',
  params: {
  'frame_idx' => 'integer',
'exception_idx' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/source-map-debug/', params={
  'frame_idx': '0',  'exception_idx': '0'
}, headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/source-map-debug/?frame_idx=0&exception_idx=0',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/source-map-debug/`

Retrieve information about source maps for a given event.
```````````````````````````````````````````
Return a list of source map errors for a given event.

<h3 id="debug-issues-related-to-source-maps-for-a-given-event-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|project_slug|path|string|true|The slug of the project the resource belongs to.|
|event_id|path|string(uuid)|true|The id of the event|
|frame_idx|query|integer|true|Index of the frame that should be used for source map resolution.|
|exception_idx|query|integer|true|Index of the exception that should be used for source map resolution.|

> Example responses

> 200 Response

```json
{
  "errors": [
    {
      "type": "string",
      "message": "string",
      "data": {
        "property1": null,
        "property2": null
      }
    }
  ]
}
```

<h3 id="debug-issues-related-to-source-maps-for-a-given-event-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="debug-issues-related-to-source-maps-for-a-given-event-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» errors|[object]|true|none|none|
|»» type|string|true|none|none|
|»» message|string|true|none|none|
|»» data|object¦null|true|none|none|
|»»» **additionalProperties**|any|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Retrieve an Event for a Project

<a id="opIdRetrieve an Event for a Project"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/events/{event_id}/`

Return details on an individual event.

<h3 id="retrieve-an-event-for-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the event belongs to.|
|project_slug|path|string|true|The slug of the project the event belongs to.|
|event_id|path|string|true|The ID of the event to retrieve. It is the hexadecimal ID as reported by the client.|

> Example responses

> 200 Response

```json
{
  "eventID": "9999aaaaca8b46d797c23c6077c6ff01",
  "dist": null,
  "userReport": null,
  "previousEventID": null,
  "message": "",
  "title": "This is an example Python exception",
  "id": "9999aaafcc8b46d797c23c6077c6ff01",
  "size": 107762,
  "errors": [
    {
      "data": {
        "column": 8,
        "source": "https://s1.sentry-cdn.com/_static/bloopbloop/sentry/dist/app.js.map",
        "row": 15
      },
      "message": "Invalid location in sourcemap",
      "type": "js_invalid_sourcemap_location"
    }
  ],
  "platform": "javascript",
  "nextEventID": "99f9e199e9a74a14bfef6196ad741619",
  "type": "error",
  "metadata": {
    "type": "ForbiddenError",
    "value": "GET /organizations/hellboy-meowmeow/users/ 403"
  },
  "tags": [
    {
      "value": "Chrome 83.0.4103",
      "key": "browser",
      "_meta": null
    },
    {
      "value": "Chrome",
      "key": "browser.name",
      "_meta": null
    },
    {
      "value": "prod",
      "key": "environment",
      "_meta": null
    },
    {
      "value": "yes",
      "key": "handled",
      "_meta": null
    },
    {
      "value": "error",
      "key": "level",
      "_meta": null
    },
    {
      "value": "generic",
      "key": "mechanism",
      "_meta": null
    }
  ],
  "dateCreated": "2020-06-17T22:26:56.098086Z",
  "dateReceived": "2020-06-17T22:26:56.428721Z",
  "user": {
    "username": null,
    "name": "Hell Boy",
    "ip_address": "192.168.1.1",
    "email": "hell@boy.cat",
    "data": {
      "isStaff": false
    },
    "id": "550747"
  },
  "entries": [
    {
      "type": "exception",
      "data": {
        "values": [
          {
            "stacktrace": {
              "frames": [
                {
                  "function": "ignoreOnError",
                  "errors": null,
                  "colNo": 23,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "inApp": false,
                  "lineNo": 71,
                  "module": "usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      66,
                      "            }"
                    ],
                    [
                      67,
                      "            // Attempt to invoke user-land function"
                    ],
                    [
                      68,
                      "            // NOTE: If you are a Sentry user, and you are seeing this stack frame, it"
                    ],
                    [
                      69,
                      "            //       means the sentry.javascript SDK caught an error invoking your application code. This"
                    ],
                    [
                      70,
                      "            //       is expected behavior and NOT indicative of a bug with sentry.javascript."
                    ],
                    [
                      71,
                      "            return fn.apply(this, wrappedArguments);"
                    ],
                    [
                      72,
                      "            // tslint:enable:no-unsafe-any"
                    ],
                    [
                      73,
                      "        }"
                    ],
                    [
                      74,
                      "        catch (ex) {"
                    ],
                    [
                      75,
                      "            ignoreNextOnError();"
                    ],
                    [
                      76,
                      "            withScope(function (scope) {"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": "apply",
                  "errors": null,
                  "colNo": 24,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "inApp": false,
                  "lineNo": 74,
                  "module": "usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      69,
                      "     */"
                    ],
                    [
                      70,
                      "    triggerAsync: function triggerAsync() {"
                    ],
                    [
                      71,
                      "        var args = arguments,"
                    ],
                    [
                      72,
                      "            me = this;"
                    ],
                    [
                      73,
                      "        _.nextTick(function () {"
                    ],
                    [
                      74,
                      "            me.trigger.apply(me, args);"
                    ],
                    [
                      75,
                      "        });"
                    ],
                    [
                      76,
                      "    },"
                    ],
                    [
                      77,
                      ""
                    ],
                    [
                      78,
                      "    /**"
                    ],
                    [
                      79,
                      "     * Wraps the trigger mechanism with a deferral function."
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "module": null,
            "rawStacktrace": {
              "frames": [
                {
                  "function": "a",
                  "errors": null,
                  "colNo": 88800,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 81,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      76,
                      "/*!"
                    ],
                    [
                      77,
                      "  Copyright (c) 2018 Jed Watson."
                    ],
                    [
                      78,
                      "  Licensed under the MIT License (MIT), see"
                    ],
                    [
                      79,
                      "  http://jedwatson.github.io/react-select"
                    ],
                    [
                      80,
                      "*/"
                    ],
                    [
                      81,
                      "{snip} e,t)}));return e.handleEvent?e.handleEvent.apply(this,s):e.apply(this,s)}catch(e){throw c(),Object(o.m)((function(n){n.addEventProcessor((fu {snip}"
                    ],
                    [
                      82,
                      "/*!"
                    ],
                    [
                      83,
                      " * JavaScript Cookie v2.2.1"
                    ],
                    [
                      84,
                      " * https://github.com/js-cookie/js-cookie"
                    ],
                    [
                      85,
                      " *"
                    ],
                    [
                      86,
                      " * Copyright 2006, 2015 Klaus Hartl & Fagner Brack"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": null,
                  "errors": null,
                  "colNo": 149484,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 119,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      114,
                      "/* @license"
                    ],
                    [
                      115,
                      "Papa Parse"
                    ],
                    [
                      116,
                      "v5.2.0"
                    ],
                    [
                      117,
                      "https://github.com/mholt/PapaParse"
                    ],
                    [
                      118,
                      "License: MIT"
                    ],
                    [
                      119,
                      "{snip} (){var e=arguments,t=this;r.nextTick((function(){t.trigger.apply(t,e)}))},deferWith:function(e){var t=this.trigger,n=this,r=function(){t.app {snip}"
                    ],
                    [
                      120,
                      "/**!"
                    ],
                    [
                      121,
                      " * @fileOverview Kickass library to create and place poppers near their reference elements."
                    ],
                    [
                      122,
                      " * @version 1.16.1"
                    ],
                    [
                      123,
                      " * @license"
                    ],
                    [
                      124,
                      " * Copyright (c) 2016 Federico Zivolo and contributors"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "mechanism": {
              "type": "generic",
              "handled": true
            },
            "threadId": null,
            "value": "GET /organizations/hellboy-meowmeow/users/ 403",
            "type": "ForbiddenError"
          }
        ],
        "excOmitted": null,
        "hasSystemFrames": true
      }
    },
    {
      "type": "breadcrumbs",
      "data": {
        "values": [
          {
            "category": "tracing",
            "level": "debug",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.266586Z",
            "data": null,
            "message": "[Tracing] pushActivity: idleTransactionStarted#1",
            "type": "debug"
          },
          {
            "category": "xhr",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.619446Z",
            "data": {
              "url": "/api/0/internal/health/",
              "status_code": 200,
              "method": "GET"
            },
            "message": null,
            "type": "http"
          },
          {
            "category": "sentry.transaction",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.945016Z",
            "data": null,
            "message": "7787a027f3fb46c985aaa2287b3f4d09",
            "type": "default"
          }
        ]
      }
    },
    {
      "type": "request",
      "data": {
        "fragment": null,
        "cookies": [],
        "inferredContentType": null,
        "env": null,
        "headers": [
          [
            "User-Agent",
            "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.97 Safari/537.36"
          ]
        ],
        "url": "https://sentry.io/organizations/hellboy-meowmeow/issues/",
        "query": [
          [
            "project",
            "5236886"
          ]
        ],
        "data": null,
        "method": null
      }
    }
  ],
  "packages": {},
  "sdk": {
    "version": "5.17.0",
    "name": "sentry.javascript.browser"
  },
  "_meta": {
    "user": null,
    "context": null,
    "entries": {},
    "contexts": null,
    "message": null,
    "packages": null,
    "tags": {},
    "sdk": null
  },
  "contexts": {
    "ForbiddenError": {
      "status": 403,
      "statusText": "Forbidden",
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "type": "default"
    },
    "browser": {
      "version": "83.0.4103",
      "type": "browser",
      "name": "Chrome"
    },
    "os": {
      "version": "10",
      "type": "os",
      "name": "Windows"
    },
    "trace": {
      "span_id": "83db1ad17e67dfe7",
      "type": "trace",
      "trace_id": "da6caabcd90e45fdb81f6655824a5f88",
      "op": "navigation"
    },
    "organization": {
      "type": "default",
      "id": "323938",
      "slug": "hellboy-meowmeow"
    }
  },
  "fingerprints": [
    "fbe908cc63d63ea9763fd84cb6bad177"
  ],
  "context": {
    "resp": {
      "status": 403,
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "name": "ForbiddenError",
      "statusText": "Forbidden",
      "message": "GET /organizations/hellboy-meowmeow/users/ 403",
      "stack": "Error\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480441\n    at u (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51006)\n    at Generator._invoke (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:50794)\n    at Generator.A.forEach.e.<computed> [as next] (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51429)\n    at n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68684)\n    at s (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68895)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68954\n    at new Promise (<anonymous>)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68835\n    at v (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480924)\n    at m (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480152)\n    at t.fetchMemberList (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:902983)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:900527)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:15597)\n    at Pc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:101023)\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Rc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:97371)\n    at Oc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:87690)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45820\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Zo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45765)\n    at Jo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45700)\n    at gc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:84256)\n    at Object.enqueueSetState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:50481)\n    at t.M.setState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:173:1439)\n    at t.onUpdate (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:543076)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at p.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at p.onInitializeUrlState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:541711)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at Function.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149484\n    at a (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:81:88800)"
    }
  },
  "release": {
    "dateReleased": "2020-06-17T19:21:02.186004Z",
    "newGroups": 4,
    "commitCount": 11,
    "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
    "data": {},
    "lastDeploy": {
      "name": "b65bc521378269d3eaefdc964f8ef56621414943 to prod",
      "url": null,
      "environment": "prod",
      "dateStarted": null,
      "dateFinished": "2020-06-17T19:20:55.641748Z",
      "id": "6883490"
    },
    "deployCount": 1,
    "dateCreated": "2020-06-17T18:45:31.042157Z",
    "lastEvent": "2020-07-08T21:21:21Z",
    "version": "b65bc521378269d3eaefdc964f8ef56621414943",
    "firstEvent": "2020-06-17T22:25:14Z",
    "lastCommit": {
      "repository": {
        "status": "active",
        "integrationId": "2933",
        "externalSlug": "getsentry/getsentry",
        "name": "getsentry/getsentry",
        "provider": {
          "id": "integrations:github",
          "name": "GitHub"
        },
        "url": "https://github.com/getsentry/getsentry",
        "id": "2",
        "dateCreated": "2016-10-10T21:36:45.373994Z"
      },
      "releases": [
        {
          "dateReleased": "2020-06-23T13:26:18.427090Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/staging/2077/",
          "dateCreated": "2020-06-23T13:22:50.420265Z",
          "version": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "shortVersion": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "ref": "perf/source-maps-test"
        },
        {
          "dateReleased": "2020-06-17T19:21:02.186004Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
          "dateCreated": "2020-06-17T18:45:31.042157Z",
          "version": "b65bc521378269d3eaefdc964f8ef56621414943",
          "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
          "ref": "master"
        }
      ],
      "dateCreated": "2020-06-17T18:43:37Z",
      "message": "feat(billing): Get a lot of money",
      "id": "b65bc521378269d3eaefdc964f8ef56621414943"
    },
    "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
    "authors": [
      {
        "username": "a37a1b4520ce46cea147ae2885a4e7e7",
        "lastLogin": "2020-09-14T22:34:55.550640Z",
        "isSuperuser": false,
        "isManaged": false,
        "experiments": {},
        "lastActive": "2020-09-15T22:13:20.503880Z",
        "isStaff": false,
        "id": "655784",
        "isActive": true,
        "has2fa": false,
        "name": "hell.boy@sentry.io",
        "avatarUrl": "https://secure.gravatar.com/avatar/eaa22e25b3a984659420831a77e4874e?s=32&d=mm",
        "dateJoined": "2020-04-20T16:21:25.365772Z",
        "emails": [
          {
            "is_verified": false,
            "id": "784574",
            "email": "hellboy@gmail.com"
          },
          {
            "is_verified": true,
            "id": "749185",
            "email": "hell.boy@sentry.io"
          }
        ],
        "avatar": {
          "avatarUuid": null,
          "avatarType": "letter_avatar"
        },
        "hasPasswordAuth": false,
        "email": "hell.boy@sentry.io"
      }
    ],
    "owner": null,
    "ref": "master",
    "projects": [
      {
        "name": "Sentry CSP",
        "slug": "sentry-csp"
      },
      {
        "name": "Backend",
        "slug": "sentry"
      },
      {
        "name": "Frontend",
        "slug": "javascript"
      }
    ]
  },
  "groupID": "1341191803"
}
```

<h3 id="retrieve-an-event-for-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-an-event-for-a-project-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» eventID|string|true|none|none|
|» dist|string¦null|true|none|none|
|» userReport|object¦null|true|none|none|
|» previousEventID|string¦null|true|none|none|
|» message|string|true|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|
|» errors|[object]|true|none|none|
|»» message|string|false|none|none|
|»» type|string|false|none|none|
|»» data|object|false|none|none|
|»»» column|integer|false|none|none|
|»»» source|string|false|none|none|
|»»» row|integer|false|none|none|
|» platform|string|true|none|none|
|» nextEventID|string¦null|true|none|none|
|» type|string|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» tags|[object]|true|none|none|
|»» value|string|false|none|none|
|»» key|string|false|none|none|
|»» _meta|string¦null|false|none|none|
|» dateCreated|string|true|none|none|
|» dateReceived|string|true|none|none|
|» user|object¦null|true|none|none|
|»» username|string¦null|true|none|none|
|»» name|string¦null|true|none|none|
|»» ip_address|string¦null|true|none|none|
|»» email|string¦null|true|none|none|
|»» data|object¦null|true|none|none|
|»»» isStaff|boolean|false|none|none|
|»» id|string|true|none|none|
|» entries|[anyOf]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» category|string|true|none|none|
|»»»»» level|string|true|none|none|
|»»»»» event_id|string¦null|true|none|none|
|»»»»» timestamp|string(date-time)|true|none|none|
|»»»»» data|object¦null|true|none|none|
|»»»»» message|string¦null|true|none|none|
|»»»»» type|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» fragment|string¦null|true|none|none|
|»»»» cookies|[array]¦null|true|none|none|
|»»»» inferredContentType|string¦null|true|none|none|
|»»»» env|object¦null|true|none|none|
|»»»»» ENV|string|false|none|none|
|»»»» headers|[array]|true|none|none|
|»»»» url|string|true|none|none|
|»»»» query|[array]|true|none|none|
|»»»» data|object¦null|true|none|none|
|»»»» method|string¦null|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» formatted|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» excOmitted|[integer]¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» stacktrace|object¦null|true|none|none|
|»»»»»» frames|[object]|true|none|none|
|»»»»»»» function|string|true|none|none|
|»»»»»»» errors|string¦null|true|none|none|
|»»»»»»» colNo|integer¦null|true|none|none|
|»»»»»»» vars|object¦null|true|none|none|
|»»»»»»» package|string¦null|true|none|none|
|»»»»»»» absPath|string¦null|true|none|none|
|»»»»»»» inApp|boolean|true|none|none|
|»»»»»»» lineNo|integer|true|none|none|
|»»»»»»» module|string|true|none|none|
|»»»»»»» filename|string|true|none|none|
|»»»»»»» platform|string¦null|true|none|none|
|»»»»»»» instructionAddr|string¦null|true|none|none|
|»»»»»»» context|[array]|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|string|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» symbolAddr|string¦null|true|none|none|
|»»»»» trust|string¦null|true|none|none|
|»»»»» symbol|string¦null|true|none|none|
|»»»» framesOmitted|string¦null|true|none|none|
|»»»» registers|string¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»» module|string¦null|true|none|none|
|»»» rawStacktrace|object¦null|true|none|none|
|»»» mechanism|object¦null|true|none|none|
|»»»» type|string|false|none|none|
|»»»» handled|boolean|false|none|none|
|»»» threadId|string¦null|true|none|none|
|»»» value|string|true|none|none|
|»»» type|string|true|none|none|
|packages|object|true|none|none|
|sdk|object|true|none|none|
|» version|string|false|none|none|
|» name|string|false|none|none|
|_meta|object|true|none|none|
|» user|string¦null|false|none|none|
|» context|string¦null|false|none|none|
|» entries|object|false|none|none|
|» contexts|string¦null|false|none|none|
|» message|string¦null|false|none|none|
|» packages|string¦null|false|none|none|
|» tags|object|false|none|none|
|» sdk|string¦null|false|none|none|
|contexts|object|true|none|none|
|» ForbiddenError|object|false|none|none|
|»» status|integer|false|none|none|
|»» statusText|string|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» type|string|false|none|none|
|» browser|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» os|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» trace|object|false|none|none|
|»» span_id|string|false|none|none|
|»» type|string|false|none|none|
|»» trace_id|string|false|none|none|
|»» op|string|false|none|none|
|» organization|object|false|none|none|
|»» type|string|false|none|none|
|»» id|string|false|none|none|
|»» slug|string|false|none|none|
|fingerprints|[string]|true|none|none|
|context|object|true|none|none|
|» resp|object|false|none|none|
|»» status|integer|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» name|string|false|none|none|
|»» statusText|string|false|none|none|
|»» message|string|false|none|none|
|»» stack|string|false|none|none|
|» session|object|false|none|none|
|»» foo|string|false|none|none|
|» unauthorized|boolean|false|none|none|
|» url|string|false|none|none|
|release|object¦null|true|none|none|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|
|groupID|string|true|none|none|
|title|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## List a Project's Events

<a id="opIdList a Project's Events"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/events/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/events/`

Return a list of events bound to a project.

<h3 id="list-a-project's-events-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the groups belong to.|
|project_slug|path|string|true|The slug of the project the groups belong to.|
|full|query|boolean|false|If this is set to true then the event payload will include the full event body, including the stacktrace. |
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

#### Detailed descriptions

**full**: If this is set to true then the event payload will include the full event body, including the stacktrace. 
Set to true to enable.

> Example responses

> 200 Response

```json
[
  {
    "eventID": "9fac2ceed9344f2bbfdd1fdacb0ed9b1",
    "tags": [
      {
        "key": "browser",
        "value": "Chrome 60.0"
      },
      {
        "key": "device",
        "value": "Other"
      },
      {
        "key": "environment",
        "value": "production"
      },
      {
        "value": "fatal",
        "key": "level"
      },
      {
        "key": "os",
        "value": "Mac OS X 10.12.6"
      },
      {
        "value": "CPython 2.7.16",
        "key": "runtime"
      },
      {
        "key": "release",
        "value": "17642328ead24b51867165985996d04b29310337"
      },
      {
        "key": "server_name",
        "value": "web1.example.com"
      }
    ],
    "dateCreated": "2020-09-11T17:46:36Z",
    "user": null,
    "message": "",
    "title": "This is an example Python exception",
    "id": "dfb1a2d057194e76a4186cc8a5271553",
    "platform": "python",
    "event.type": "error",
    "groupID": "1889724436"
  }
]
```

<h3 id="list-a-project's-events-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-project's-events-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» eventID|string|true|none|none|
|» tags|[object]|true|none|none|
|»» value|string|false|none|none|
|»» key|string|false|none|none|
|» dateCreated|string|true|none|none|
|» user|object¦null|true|none|none|
|»» username|string¦null|true|none|none|
|»» name|string¦null|true|none|none|
|»» ip_address|string¦null|true|none|none|
|»» email|string¦null|true|none|none|
|»» data|object¦null|true|none|none|
|»»» isStaff|boolean|false|none|none|
|»» id|string|true|none|none|
|» message|string|true|none|none|
|» id|string|true|none|none|
|» platform|string|true|none|none|
|» event.type|string|true|none|none|
|» groupID|string|true|none|none|
|» title|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:read )
</aside>

## List a Project's Issues

<a id="opIdList a Project's Issues"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/issues/`

Return a list of issues (groups) bound to a project.  All parameters are supplied as query string parameters. 

 A default query of ``is:unresolved`` is applied. To return results with other statuses send an new query value (i.e. ``?query=`` for all results).

The ``statsPeriod`` parameter can be used to select the timeline stats which should be present. Possible values are: ``""`` (disable),``"24h"``, ``"14d"``

<h3 id="list-a-project's-issues-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the issues belong to.|
|project_slug|path|string|true|The slug of the project the issues belong to.|
|statsPeriod|query|string|false|An optional stat period (can be one of `"24h"`, `"14d"`, and `""`).|
|shortIdLookup|query|boolean|false|If this is set to true then short IDs are looked up by this function as well. This can cause the return value of the function to return an event issue of a different project which is why this is an opt-in. Set to 1 to enable.|
|query|query|string|false|An optional Sentry structured search query. If not provided an implied `"is:unresolved"` is assumed.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "annotations": [],
    "assignedTo": null,
    "count": "1",
    "culprit": "raven.scripts.runner in main",
    "firstSeen": "2018-11-06T21:19:55Z",
    "hasSeen": false,
    "id": "1",
    "isBookmarked": false,
    "isPublic": false,
    "isSubscribed": true,
    "lastSeen": "2018-11-06T21:19:55Z",
    "level": "error",
    "logger": null,
    "metadata": {
      "title": "This is an example Python exception"
    },
    "numComments": 0,
    "permalink": "https://sentry.io/the-interstellar-jurisdiction/pump-station/issues/1/",
    "project": {
      "id": "2",
      "name": "Pump Station",
      "slug": "pump-station"
    },
    "shareId": null,
    "shortId": "PUMP-STATION-1",
    "stats": {
      "24h": [
        [
          1541455200,
          473
        ],
        [
          1541458800,
          914
        ],
        [
          1541462400,
          991
        ],
        [
          1541466000,
          925
        ],
        [
          1541469600,
          881
        ],
        [
          1541473200,
          182
        ],
        [
          1541476800,
          490
        ],
        [
          1541480400,
          820
        ],
        [
          1541484000,
          322
        ],
        [
          1541487600,
          836
        ],
        [
          1541491200,
          565
        ],
        [
          1541494800,
          758
        ],
        [
          1541498400,
          880
        ],
        [
          1541502000,
          677
        ],
        [
          1541505600,
          381
        ],
        [
          1541509200,
          814
        ],
        [
          1541512800,
          329
        ],
        [
          1541516400,
          446
        ],
        [
          1541520000,
          731
        ],
        [
          1541523600,
          111
        ],
        [
          1541527200,
          926
        ],
        [
          1541530800,
          772
        ],
        [
          1541534400,
          400
        ],
        [
          1541538000,
          943
        ]
      ]
    },
    "status": "unresolved",
    "statusDetails": {},
    "subscriptionDetails": null,
    "title": "This is an example Python exception",
    "type": "default",
    "userCount": 0
  }
]
```

<h3 id="list-a-project's-issues-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-project's-issues-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» annotations|[string]|true|none|none|
|» assignedTo|object¦null|true|none|none|
|» count|string|true|none|none|
|» culprit|string|true|none|none|
|» firstSeen|string|true|none|none|
|» hasSeen|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» isSubscribed|boolean|true|none|none|
|» lastSeen|string|true|none|none|
|» level|string|true|none|none|
|» logger|string¦null|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» filename|string|true|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» numComments|integer|true|none|none|
|» permalink|string|true|none|none|
|» project|object|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» shareId|string¦null|true|none|none|
|» shortId|string|true|none|none|
|» stats|object|true|none|none|
|»» 24h|[array]|false|none|none|
|» status|string|true|none|none|
|» statusDetails|object|true|none|none|
|» subscriptionDetails|object¦null|true|none|none|
|» title|string|true|none|none|
|» type|string|true|none|none|
|» userCount|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|resolved|
|status|unresolved|
|status|ignored|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Bulk Mutate a List of Issues

<a id="opIdBulk Mutate a List of Issues"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "status": "string",
  "statusDetails": {
    "inRelease": "string",
    "inNextRelease": true,
    "inCommit": "string",
    "ignoreDuration": 0,
    "ignoreCount": 0,
    "ignoreWindow": 0,
    "ignoreUserCount": 0,
    "ignoreUserWindow": 0
  },
  "ignoreDuration": 0,
  "isPublic": true,
  "merge": true,
  "assignedTo": "string",
  "hasSeen": true,
  "isBookmarked": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/projects/{organization_slug}/{project_slug}/issues/`

Bulk mutate various attributes on issues.  The list of issues to modify is given through the `id` query parameter.  It is repeated for each issue that should be modified.

- For non-status updates, the `id` query parameter is required.
- For status updates, the `id` query parameter may be omitted
for a batch "update all" query.
- An optional `status` query parameter may be used to restrict
mutations to only events with the given status.

The following attributes can be modified and are supplied as JSON object in the body:

If any ids are out of scope this operation will succeed without any data mutation.

> Body parameter

```json
{
  "status": "string",
  "statusDetails": {
    "inRelease": "string",
    "inNextRelease": true,
    "inCommit": "string",
    "ignoreDuration": 0,
    "ignoreCount": 0,
    "ignoreWindow": 0,
    "ignoreUserCount": 0,
    "ignoreUserWindow": 0
  },
  "ignoreDuration": 0,
  "isPublic": true,
  "merge": true,
  "assignedTo": "string",
  "hasSeen": true,
  "isBookmarked": true
}
```

<h3 id="bulk-mutate-a-list-of-issues-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the issues belong to.|
|project_slug|path|string|true|The slug of the project the issues belong to.|
|id|query|integer|false|A list of IDs of the issues to be mutated. This parameter shall be repeated for each issue. It is optional only if a status is mutated in which case an implicit update all is assumed.|
|status|query|string|false|Optionally limits the query to issues of the specified status. Valid values are `"resolved"`, `"unresolved"`, and `"ignored"`.|
|body|body|object|true|none|
|» status|body|string|false|The new status for the issues. Valid values are `"resolved"`, `"resolvedInNextRelease"`, `"unresolved"`, and `"ignored"`.|
|» statusDetails|body|object|false|Additional details about the resolution. Valid values are `"inRelease"`, `"inNextRelease"`, `"inCommit"`, `"ignoreDuration"`, `"ignoreCount"`, `"ignoreWindow"`, `"ignoreUserCount"`, and `"ignoreUserWindow"`.|
|»» inRelease|body|string|false|none|
|»» inNextRelease|body|boolean|false|none|
|»» inCommit|body|string|false|none|
|»» ignoreDuration|body|integer|false|none|
|»» ignoreCount|body|integer|false|none|
|»» ignoreWindow|body|integer|false|none|
|»» ignoreUserCount|body|integer|false|none|
|»» ignoreUserWindow|body|integer|false|none|
|» ignoreDuration|body|integer|false|The number of minutes to ignore this issue.|
|» isPublic|body|boolean|false|Sets the issue to public or private.|
|» merge|body|boolean|false|Allows to merge or unmerge different issues.|
|» assignedTo|body|string|false|The actor id (or username) of the user or team that should be assigned to this issue.|
|» hasSeen|body|boolean|false|In case this API call is invoked with a user context this allows changing of the flag that indicates if the user has seen the event.|
|» isBookmarked|body|boolean|false|In case this API call is invoked with a user context this allows changing of the bookmark flag.|

> Example responses

> 200 Response

```json
{
  "isPublic": false,
  "status": "unresolved",
  "statusDetails": {}
}
```

<h3 id="bulk-mutate-a-list-of-issues-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="bulk-mutate-a-list-of-issues-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» isPublic|boolean|true|none|none|
|» status|string|true|none|none|
|» statusDetails|object|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|resolved|
|status|unresolved|
|status|ignored|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:write )
</aside>

## Bulk Remove a List of Issues

<a id="opIdBulk Remove a List of Issues"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/issues/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/issues/`

Permanently remove the given issues. The list of issues to modify is given through the `id` query parameter.  It is repeated for each issue that should be removed.

Only queries by 'id' are accepted.

If any ids are out of scope this operation will succeed without any data mutation.

<h3 id="bulk-remove-a-list-of-issues-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the issues belong to.|
|project_slug|path|string|true|The slug of the project the issues belong to.|
|id|query|integer|false|A list of IDs of the issues to be removed. This parameter shall be repeated for each issue.|

<h3 id="bulk-remove-a-list-of-issues-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin )
</aside>

## List a Tag's Values Related to an Issue

<a id="opIdList a Tag's Values Related to an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/tags/{key}/values/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/tags/{key}/values/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/tags/{key}/values/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/tags/{key}/values/`

Returns details for given tag key related to an issue. 

When [paginated](/api/pagination) can return at most 1000 values.

<h3 id="list-a-tag's-values-related-to-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to retrieve.|
|key|path|string|true|The tag key to look the values up for.|

> Example responses

> 200 Response

```json
[
  {
    "key": "ice_cream",
    "value": "mint_choco"
  }
]
```

<h3 id="list-a-tag's-values-related-to-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-a-tag's-values-related-to-an-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» key|string|true|none|none|
|» value|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Retrieve Tag Details

<a id="opIdRetrieve Tag Details"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/tags/{key}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/tags/{key}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/tags/{key}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/tags/{key}/`

Returns details for given tag key related to an issue.

<h3 id="retrieve-tag-details-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to retrieve.|
|key|path|string|true|The tag key to look the values up for.|

> Example responses

> 200 Response

```json
{
  "key": "ice_cream",
  "totalValues": 6
}
```

<h3 id="retrieve-tag-details-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-tag-details-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» key|string|true|none|none|
|» totalValues|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## List an Issue's Hashes

<a id="opIdList an Issue's Hashes"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/hashes/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/hashes/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/hashes/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/hashes/`

This endpoint lists an issue's hashes, which are the generated checksums used to aggregate individual events.

<h3 id="list-an-issue's-hashes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to retrieve.|
|cursor|query|string|false|A pointer to the last object fetched and its sort order; used to retrieve the next or previous results.|

> Example responses

> 200 Response

```json
[
  {
    "id": "9999aaaaca8b46d797c23c6077c6ff01",
    "latestEvent": {
      "eventID": "9999aaaaca8b46d797c23c6077c6ff01",
      "dist": null,
      "message": "",
      "title": "This is an example Python exception",
      "id": "9999aaafcc8b46d797c23c6077c6ff01",
      "size": 107762,
      "errors": [
        {
          "data": {
            "column": 8,
            "source": "https://s1.sentry-cdn.com/_static/bloopbloop/sentry/dist/app.js.map",
            "row": 15
          },
          "message": "Invalid location in sourcemap",
          "type": "js_invalid_sourcemap_location"
        }
      ],
      "platform": "javascript",
      "type": "error",
      "metadata": {
        "type": "ForbiddenError",
        "value": "GET /organizations/hellboy-meowmeow/users/ 403"
      },
      "tags": [
        {
          "value": "Chrome 83.0.4103",
          "key": "browser",
          "_meta": null
        },
        {
          "value": "Chrome",
          "key": "browser.name",
          "_meta": null
        },
        {
          "value": "prod",
          "key": "environment",
          "_meta": null
        },
        {
          "value": "yes",
          "key": "handled",
          "_meta": null
        },
        {
          "value": "error",
          "key": "level",
          "_meta": null
        },
        {
          "value": "generic",
          "key": "mechanism",
          "_meta": null
        }
      ],
      "dateCreated": "2020-06-17T22:26:56.098086Z",
      "dateReceived": "2020-06-17T22:26:56.428721Z",
      "user": {
        "username": null,
        "name": "Hell Boy",
        "ip_address": "192.168.1.1",
        "email": "hell@boy.cat",
        "data": {
          "isStaff": false
        },
        "id": "550747"
      },
      "entries": [
        {
          "type": "exception",
          "data": {
            "values": [
              {
                "stacktrace": {
                  "frames": [
                    {
                      "function": "ignoreOnError",
                      "errors": null,
                      "colNo": 23,
                      "vars": null,
                      "package": null,
                      "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                      "inApp": false,
                      "lineNo": 71,
                      "module": "usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers",
                      "filename": "/usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                      "platform": null,
                      "instructionAddr": null,
                      "context": [
                        [
                          66,
                          "            }"
                        ],
                        [
                          67,
                          "            // Attempt to invoke user-land function"
                        ],
                        [
                          68,
                          "            // NOTE: If you are a Sentry user, and you are seeing this stack frame, it"
                        ],
                        [
                          69,
                          "            //       means the sentry.javascript SDK caught an error invoking your application code. This"
                        ],
                        [
                          70,
                          "            //       is expected behavior and NOT indicative of a bug with sentry.javascript."
                        ],
                        [
                          71,
                          "            return fn.apply(this, wrappedArguments);"
                        ],
                        [
                          72,
                          "            // tslint:enable:no-unsafe-any"
                        ],
                        [
                          73,
                          "        }"
                        ],
                        [
                          74,
                          "        catch (ex) {"
                        ],
                        [
                          75,
                          "            ignoreNextOnError();"
                        ],
                        [
                          76,
                          "            withScope(function (scope) {"
                        ]
                      ],
                      "symbolAddr": null,
                      "trust": null,
                      "symbol": null
                    },
                    {
                      "function": "apply",
                      "errors": null,
                      "colNo": 24,
                      "vars": null,
                      "package": null,
                      "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                      "inApp": false,
                      "lineNo": 74,
                      "module": "usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods",
                      "filename": "/usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                      "platform": null,
                      "instructionAddr": null,
                      "context": [
                        [
                          69,
                          "     */"
                        ],
                        [
                          70,
                          "    triggerAsync: function triggerAsync() {"
                        ],
                        [
                          71,
                          "        var args = arguments,"
                        ],
                        [
                          72,
                          "            me = this;"
                        ],
                        [
                          73,
                          "        _.nextTick(function () {"
                        ],
                        [
                          74,
                          "            me.trigger.apply(me, args);"
                        ],
                        [
                          75,
                          "        });"
                        ],
                        [
                          76,
                          "    },"
                        ],
                        [
                          77,
                          ""
                        ],
                        [
                          78,
                          "    /**"
                        ],
                        [
                          79,
                          "     * Wraps the trigger mechanism with a deferral function."
                        ]
                      ],
                      "symbolAddr": null,
                      "trust": null,
                      "symbol": null
                    }
                  ],
                  "framesOmitted": null,
                  "registers": null,
                  "hasSystemFrames": true
                },
                "module": null,
                "rawStacktrace": {
                  "frames": [
                    {
                      "function": "a",
                      "errors": null,
                      "colNo": 88800,
                      "vars": null,
                      "package": null,
                      "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                      "inApp": false,
                      "lineNo": 81,
                      "module": null,
                      "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                      "platform": null,
                      "instructionAddr": null,
                      "context": [
                        [
                          76,
                          "/*!"
                        ],
                        [
                          77,
                          "  Copyright (c) 2018 Jed Watson."
                        ],
                        [
                          78,
                          "  Licensed under the MIT License (MIT), see"
                        ],
                        [
                          79,
                          "  http://jedwatson.github.io/react-select"
                        ],
                        [
                          80,
                          "*/"
                        ],
                        [
                          81,
                          "{snip} e,t)}));return e.handleEvent?e.handleEvent.apply(this,s):e.apply(this,s)}catch(e){throw c(),Object(o.m)((function(n){n.addEventProcessor((fu {snip}"
                        ],
                        [
                          82,
                          "/*!"
                        ],
                        [
                          83,
                          " * JavaScript Cookie v2.2.1"
                        ],
                        [
                          84,
                          " * https://github.com/js-cookie/js-cookie"
                        ],
                        [
                          85,
                          " *"
                        ],
                        [
                          86,
                          " * Copyright 2006, 2015 Klaus Hartl & Fagner Brack"
                        ]
                      ],
                      "symbolAddr": null,
                      "trust": null,
                      "symbol": null
                    },
                    {
                      "function": null,
                      "errors": null,
                      "colNo": 149484,
                      "vars": null,
                      "package": null,
                      "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                      "inApp": false,
                      "lineNo": 119,
                      "module": null,
                      "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                      "platform": null,
                      "instructionAddr": null,
                      "context": [
                        [
                          114,
                          "/* @license"
                        ],
                        [
                          115,
                          "Papa Parse"
                        ],
                        [
                          116,
                          "v5.2.0"
                        ],
                        [
                          117,
                          "https://github.com/mholt/PapaParse"
                        ],
                        [
                          118,
                          "License: MIT"
                        ],
                        [
                          119,
                          "{snip} (){var e=arguments,t=this;r.nextTick((function(){t.trigger.apply(t,e)}))},deferWith:function(e){var t=this.trigger,n=this,r=function(){t.app {snip}"
                        ],
                        [
                          120,
                          "/**!"
                        ],
                        [
                          121,
                          " * @fileOverview Kickass library to create and place poppers near their reference elements."
                        ],
                        [
                          122,
                          " * @version 1.16.1"
                        ],
                        [
                          123,
                          " * @license"
                        ],
                        [
                          124,
                          " * Copyright (c) 2016 Federico Zivolo and contributors"
                        ]
                      ],
                      "symbolAddr": null,
                      "trust": null,
                      "symbol": null
                    }
                  ],
                  "framesOmitted": null,
                  "registers": null,
                  "hasSystemFrames": true
                },
                "mechanism": {
                  "type": "generic",
                  "handled": true
                },
                "threadId": null,
                "value": "GET /organizations/hellboy-meowmeow/users/ 403",
                "type": "ForbiddenError"
              }
            ],
            "excOmitted": null,
            "hasSystemFrames": true
          }
        },
        {
          "type": "breadcrumbs",
          "data": {
            "values": [
              {
                "category": "tracing",
                "level": "debug",
                "event_id": null,
                "timestamp": "2020-06-17T22:26:55.266586Z",
                "data": null,
                "message": "[Tracing] pushActivity: idleTransactionStarted#1",
                "type": "debug"
              },
              {
                "category": "xhr",
                "level": "info",
                "event_id": null,
                "timestamp": "2020-06-17T22:26:55.619446Z",
                "data": {
                  "url": "/api/0/internal/health/",
                  "status_code": 200,
                  "method": "GET"
                },
                "message": null,
                "type": "http"
              },
              {
                "category": "sentry.transaction",
                "level": "info",
                "event_id": null,
                "timestamp": "2020-06-17T22:26:55.945016Z",
                "data": null,
                "message": "7787a027f3fb46c985aaa2287b3f4d09",
                "type": "default"
              }
            ]
          }
        },
        {
          "type": "request",
          "data": {
            "fragment": null,
            "cookies": [],
            "inferredContentType": null,
            "env": null,
            "headers": [
              [
                "User-Agent",
                "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.97 Safari/537.36"
              ]
            ],
            "url": "https://sentry.io/organizations/hellboy-meowmeow/issues/",
            "query": [
              [
                "project",
                "5236886"
              ]
            ],
            "data": null,
            "method": null
          }
        }
      ],
      "packages": {},
      "sdk": {
        "version": "5.17.0",
        "name": "sentry.javascript.browser"
      },
      "_meta": {
        "user": null,
        "context": null,
        "entries": {},
        "contexts": null,
        "message": null,
        "packages": null,
        "tags": {},
        "sdk": null
      },
      "contexts": {
        "ForbiddenError": {
          "status": 403,
          "statusText": "Forbidden",
          "responseJSON": {
            "detail": "You do not have permission to perform this action."
          },
          "type": "default"
        },
        "browser": {
          "version": "83.0.4103",
          "type": "browser",
          "name": "Chrome"
        },
        "os": {
          "version": "10",
          "type": "os",
          "name": "Windows"
        },
        "trace": {
          "span_id": "83db1ad17e67dfe7",
          "type": "trace",
          "trace_id": "da6caabcd90e45fdb81f6655824a5f88",
          "op": "navigation"
        },
        "organization": {
          "type": "default",
          "id": "323938",
          "slug": "hellboy-meowmeow"
        }
      },
      "fingerprints": [
        "fbe908cc63d63ea9763fd84cb6bad177"
      ],
      "context": {
        "resp": {
          "status": 403,
          "responseJSON": {
            "detail": "You do not have permission to perform this action."
          },
          "name": "ForbiddenError",
          "statusText": "Forbidden",
          "message": "GET /organizations/hellboy-meowmeow/users/ 403",
          "stack": "Error\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480441\n    at u (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51006)\n    at Generator._invoke (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:50794)\n    at Generator.A.forEach.e.<computed> [as next] (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51429)\n    at n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68684)\n    at s (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68895)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68954\n    at new Promise (<anonymous>)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68835\n    at v (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480924)\n    at m (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480152)\n    at t.fetchMemberList (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:902983)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:900527)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:15597)\n    at Pc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:101023)\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Rc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:97371)\n    at Oc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:87690)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45820\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Zo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45765)\n    at Jo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45700)\n    at gc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:84256)\n    at Object.enqueueSetState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:50481)\n    at t.M.setState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:173:1439)\n    at t.onUpdate (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:543076)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at p.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at p.onInitializeUrlState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:541711)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at Function.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149484\n    at a (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:81:88800)"
        }
      },
      "groupID": "1341191803"
    }
  }
]
```

<h3 id="list-an-issue's-hashes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-an-issue's-hashes-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» latestEvent|object|false|none|none|
|»» eventID|string|true|none|none|
|»» dist|string¦null|true|none|none|
|»» message|string|true|none|none|
|»» id|string|true|none|none|
|»» size|integer|true|none|none|
|»» errors|[object]|true|none|none|
|»»» message|string|false|none|none|
|»»» type|string|false|none|none|
|»»» data|object|false|none|none|
|»»»» column|integer|false|none|none|
|»»»» source|string|false|none|none|
|»»»» row|integer|false|none|none|
|»» platform|string|true|none|none|
|»» type|string|true|none|none|
|»» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» tags|[object]|true|none|none|
|»»» value|string|false|none|none|
|»»» key|string|false|none|none|
|»»» _meta|string¦null|false|none|none|
|»» dateCreated|string|true|none|none|
|»» dateReceived|string|true|none|none|
|»» user|object¦null|true|none|none|
|»»» username|string¦null|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» ip_address|string¦null|true|none|none|
|»»» email|string¦null|true|none|none|
|»»» data|object¦null|true|none|none|
|»»»» isStaff|boolean|false|none|none|
|»»» id|string|true|none|none|
|»» entries|[anyOf]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» values|[object]|true|none|none|
|»»»»»» category|string|true|none|none|
|»»»»»» level|string|true|none|none|
|»»»»»» event_id|string¦null|true|none|none|
|»»»»»» timestamp|string(date-time)|true|none|none|
|»»»»»» data|object¦null|true|none|none|
|»»»»»» message|string¦null|true|none|none|
|»»»»»» type|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» fragment|string¦null|true|none|none|
|»»»»» cookies|[array]¦null|true|none|none|
|»»»»» inferredContentType|string¦null|true|none|none|
|»»»»» env|object¦null|true|none|none|
|»»»»»» ENV|string|false|none|none|
|»»»»» headers|[array]|true|none|none|
|»»»»» url|string|true|none|none|
|»»»»» query|[array]|true|none|none|
|»»»»» data|object¦null|true|none|none|
|»»»»» method|string¦null|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» formatted|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» type|string|true|none|none|
|»»»» data|object|true|none|none|
|»»»»» excOmitted|[integer]¦null|true|none|none|
|»»»»» hasSystemFrames|boolean|true|none|none|
|»»»»» values|[object]|true|none|none|
|»»»»»» stacktrace|object¦null|true|none|none|
|»»»»»»» frames|[object]|true|none|none|
|»»»»»»»» function|string|true|none|none|
|»»»»»»»» errors|string¦null|true|none|none|
|»»»»»»»» colNo|integer¦null|true|none|none|
|»»»»»»»» vars|object¦null|true|none|none|
|»»»»»»»» package|string¦null|true|none|none|
|»»»»»»»» absPath|string¦null|true|none|none|
|»»»»»»»» inApp|boolean|true|none|none|
|»»»»»»»» lineNo|integer|true|none|none|
|»»»»»»»» module|string|true|none|none|
|»»»»»»»» filename|string|true|none|none|
|»»»»»»»» platform|string¦null|true|none|none|
|»»»»»»»» instructionAddr|string¦null|true|none|none|
|»»»»»»»» context|[array]|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»»» *anonymous*|string|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»» symbolAddr|string¦null|true|none|none|
|»»»»»» trust|string¦null|true|none|none|
|»»»»»» symbol|string¦null|true|none|none|
|»»»»» framesOmitted|string¦null|true|none|none|
|»»»»» registers|string¦null|true|none|none|
|»»»»» hasSystemFrames|boolean|true|none|none|
|»»»» module|string¦null|true|none|none|
|»»»» rawStacktrace|object¦null|true|none|none|
|»»»» mechanism|object¦null|true|none|none|
|»»»»» type|string|false|none|none|
|»»»»» handled|boolean|false|none|none|
|»»»» threadId|string¦null|true|none|none|
|»»»» value|string|true|none|none|
|»»»» type|string|true|none|none|
|packages|object|true|none|none|
|sdk|object|true|none|none|
|» version|string|false|none|none|
|» name|string|false|none|none|
|_meta|object|true|none|none|
|» user|string¦null|false|none|none|
|» context|string¦null|false|none|none|
|» entries|object|false|none|none|
|» contexts|string¦null|false|none|none|
|» message|string¦null|false|none|none|
|» packages|string¦null|false|none|none|
|» tags|object|false|none|none|
|» sdk|string¦null|false|none|none|
|contexts|object|true|none|none|
|» ForbiddenError|object|false|none|none|
|»» status|integer|false|none|none|
|»» statusText|string|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» type|string|false|none|none|
|» browser|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» os|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» trace|object|false|none|none|
|»» span_id|string|false|none|none|
|»» type|string|false|none|none|
|»» trace_id|string|false|none|none|
|»» op|string|false|none|none|
|» organization|object|false|none|none|
|»» type|string|false|none|none|
|»» id|string|false|none|none|
|»» slug|string|false|none|none|
|fingerprints|[string]|true|none|none|
|context|object|true|none|none|
|» resp|object|false|none|none|
|»» status|integer|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» name|string|false|none|none|
|»» statusText|string|false|none|none|
|»» message|string|false|none|none|
|»» stack|string|false|none|none|
|» session|object|false|none|none|
|»» foo|string|false|none|none|
|» unauthorized|boolean|false|none|none|
|» url|string|false|none|none|
|groupID|string|true|none|none|
|title|string|true|none|none|
|id|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Retrieve the Oldest Event for an Issue

<a id="opIdRetrieve the Oldest Event for an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/events/oldest/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/events/oldest/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/events/oldest/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/events/oldest/`

Retrieves the details of the oldest event for an issue.

<h3 id="retrieve-the-oldest-event-for-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue.|

> Example responses

> 200 Response

```json
{
  "eventID": "9999aaaaca8b46d797c23c6077c6ff01",
  "dist": null,
  "userReport": null,
  "previousEventID": null,
  "message": "",
  "title": "This is an example Python exception",
  "id": "9999aaafcc8b46d797c23c6077c6ff01",
  "size": 107762,
  "errors": [
    {
      "data": {
        "column": 8,
        "source": "https://s1.sentry-cdn.com/_static/bloopbloop/sentry/dist/app.js.map",
        "row": 15
      },
      "message": "Invalid location in sourcemap",
      "type": "js_invalid_sourcemap_location"
    }
  ],
  "platform": "javascript",
  "nextEventID": "99f9e199e9a74a14bfef6196ad741619",
  "type": "error",
  "metadata": {
    "type": "ForbiddenError",
    "value": "GET /organizations/hellboy-meowmeow/users/ 403"
  },
  "tags": [
    {
      "value": "Chrome 83.0.4103",
      "key": "browser",
      "_meta": null
    },
    {
      "value": "Chrome",
      "key": "browser.name",
      "_meta": null
    },
    {
      "value": "prod",
      "key": "environment",
      "_meta": null
    },
    {
      "value": "yes",
      "key": "handled",
      "_meta": null
    },
    {
      "value": "error",
      "key": "level",
      "_meta": null
    },
    {
      "value": "generic",
      "key": "mechanism",
      "_meta": null
    }
  ],
  "dateCreated": "2020-06-17T22:26:56.098086Z",
  "dateReceived": "2020-06-17T22:26:56.428721Z",
  "user": {
    "username": null,
    "name": "Hell Boy",
    "ip_address": "192.168.1.1",
    "email": "hell@boy.cat",
    "data": {
      "isStaff": false
    },
    "id": "550747"
  },
  "entries": [
    {
      "type": "exception",
      "data": {
        "values": [
          {
            "stacktrace": {
              "frames": [
                {
                  "function": "ignoreOnError",
                  "errors": null,
                  "colNo": 23,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "inApp": false,
                  "lineNo": 71,
                  "module": "usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      66,
                      "            }"
                    ],
                    [
                      67,
                      "            // Attempt to invoke user-land function"
                    ],
                    [
                      68,
                      "            // NOTE: If you are a Sentry user, and you are seeing this stack frame, it"
                    ],
                    [
                      69,
                      "            //       means the sentry.javascript SDK caught an error invoking your application code. This"
                    ],
                    [
                      70,
                      "            //       is expected behavior and NOT indicative of a bug with sentry.javascript."
                    ],
                    [
                      71,
                      "            return fn.apply(this, wrappedArguments);"
                    ],
                    [
                      72,
                      "            // tslint:enable:no-unsafe-any"
                    ],
                    [
                      73,
                      "        }"
                    ],
                    [
                      74,
                      "        catch (ex) {"
                    ],
                    [
                      75,
                      "            ignoreNextOnError();"
                    ],
                    [
                      76,
                      "            withScope(function (scope) {"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": "apply",
                  "errors": null,
                  "colNo": 24,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "inApp": false,
                  "lineNo": 74,
                  "module": "usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      69,
                      "     */"
                    ],
                    [
                      70,
                      "    triggerAsync: function triggerAsync() {"
                    ],
                    [
                      71,
                      "        var args = arguments,"
                    ],
                    [
                      72,
                      "            me = this;"
                    ],
                    [
                      73,
                      "        _.nextTick(function () {"
                    ],
                    [
                      74,
                      "            me.trigger.apply(me, args);"
                    ],
                    [
                      75,
                      "        });"
                    ],
                    [
                      76,
                      "    },"
                    ],
                    [
                      77,
                      ""
                    ],
                    [
                      78,
                      "    /**"
                    ],
                    [
                      79,
                      "     * Wraps the trigger mechanism with a deferral function."
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "module": null,
            "rawStacktrace": {
              "frames": [
                {
                  "function": "a",
                  "errors": null,
                  "colNo": 88800,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 81,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      76,
                      "/*!"
                    ],
                    [
                      77,
                      "  Copyright (c) 2018 Jed Watson."
                    ],
                    [
                      78,
                      "  Licensed under the MIT License (MIT), see"
                    ],
                    [
                      79,
                      "  http://jedwatson.github.io/react-select"
                    ],
                    [
                      80,
                      "*/"
                    ],
                    [
                      81,
                      "{snip} e,t)}));return e.handleEvent?e.handleEvent.apply(this,s):e.apply(this,s)}catch(e){throw c(),Object(o.m)((function(n){n.addEventProcessor((fu {snip}"
                    ],
                    [
                      82,
                      "/*!"
                    ],
                    [
                      83,
                      " * JavaScript Cookie v2.2.1"
                    ],
                    [
                      84,
                      " * https://github.com/js-cookie/js-cookie"
                    ],
                    [
                      85,
                      " *"
                    ],
                    [
                      86,
                      " * Copyright 2006, 2015 Klaus Hartl & Fagner Brack"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": null,
                  "errors": null,
                  "colNo": 149484,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 119,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      114,
                      "/* @license"
                    ],
                    [
                      115,
                      "Papa Parse"
                    ],
                    [
                      116,
                      "v5.2.0"
                    ],
                    [
                      117,
                      "https://github.com/mholt/PapaParse"
                    ],
                    [
                      118,
                      "License: MIT"
                    ],
                    [
                      119,
                      "{snip} (){var e=arguments,t=this;r.nextTick((function(){t.trigger.apply(t,e)}))},deferWith:function(e){var t=this.trigger,n=this,r=function(){t.app {snip}"
                    ],
                    [
                      120,
                      "/**!"
                    ],
                    [
                      121,
                      " * @fileOverview Kickass library to create and place poppers near their reference elements."
                    ],
                    [
                      122,
                      " * @version 1.16.1"
                    ],
                    [
                      123,
                      " * @license"
                    ],
                    [
                      124,
                      " * Copyright (c) 2016 Federico Zivolo and contributors"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "mechanism": {
              "type": "generic",
              "handled": true
            },
            "threadId": null,
            "value": "GET /organizations/hellboy-meowmeow/users/ 403",
            "type": "ForbiddenError"
          }
        ],
        "excOmitted": null,
        "hasSystemFrames": true
      }
    },
    {
      "type": "breadcrumbs",
      "data": {
        "values": [
          {
            "category": "tracing",
            "level": "debug",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.266586Z",
            "data": null,
            "message": "[Tracing] pushActivity: idleTransactionStarted#1",
            "type": "debug"
          },
          {
            "category": "xhr",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.619446Z",
            "data": {
              "url": "/api/0/internal/health/",
              "status_code": 200,
              "method": "GET"
            },
            "message": null,
            "type": "http"
          },
          {
            "category": "sentry.transaction",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.945016Z",
            "data": null,
            "message": "7787a027f3fb46c985aaa2287b3f4d09",
            "type": "default"
          }
        ]
      }
    },
    {
      "type": "request",
      "data": {
        "fragment": null,
        "cookies": [],
        "inferredContentType": null,
        "env": null,
        "headers": [
          [
            "User-Agent",
            "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.97 Safari/537.36"
          ]
        ],
        "url": "https://sentry.io/organizations/hellboy-meowmeow/issues/",
        "query": [
          [
            "project",
            "5236886"
          ]
        ],
        "data": null,
        "method": null
      }
    }
  ],
  "packages": {},
  "sdk": {
    "version": "5.17.0",
    "name": "sentry.javascript.browser"
  },
  "_meta": {
    "user": null,
    "context": null,
    "entries": {},
    "contexts": null,
    "message": null,
    "packages": null,
    "tags": {},
    "sdk": null
  },
  "contexts": {
    "ForbiddenError": {
      "status": 403,
      "statusText": "Forbidden",
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "type": "default"
    },
    "browser": {
      "version": "83.0.4103",
      "type": "browser",
      "name": "Chrome"
    },
    "os": {
      "version": "10",
      "type": "os",
      "name": "Windows"
    },
    "trace": {
      "span_id": "83db1ad17e67dfe7",
      "type": "trace",
      "trace_id": "da6caabcd90e45fdb81f6655824a5f88",
      "op": "navigation"
    },
    "organization": {
      "type": "default",
      "id": "323938",
      "slug": "hellboy-meowmeow"
    }
  },
  "fingerprints": [
    "fbe908cc63d63ea9763fd84cb6bad177"
  ],
  "context": {
    "resp": {
      "status": 403,
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "name": "ForbiddenError",
      "statusText": "Forbidden",
      "message": "GET /organizations/hellboy-meowmeow/users/ 403",
      "stack": "Error\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480441\n    at u (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51006)\n    at Generator._invoke (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:50794)\n    at Generator.A.forEach.e.<computed> [as next] (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51429)\n    at n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68684)\n    at s (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68895)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68954\n    at new Promise (<anonymous>)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68835\n    at v (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480924)\n    at m (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480152)\n    at t.fetchMemberList (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:902983)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:900527)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:15597)\n    at Pc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:101023)\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Rc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:97371)\n    at Oc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:87690)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45820\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Zo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45765)\n    at Jo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45700)\n    at gc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:84256)\n    at Object.enqueueSetState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:50481)\n    at t.M.setState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:173:1439)\n    at t.onUpdate (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:543076)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at p.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at p.onInitializeUrlState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:541711)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at Function.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149484\n    at a (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:81:88800)"
    }
  },
  "release": {
    "dateReleased": "2020-06-17T19:21:02.186004Z",
    "newGroups": 4,
    "commitCount": 11,
    "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
    "data": {},
    "lastDeploy": {
      "name": "b65bc521378269d3eaefdc964f8ef56621414943 to prod",
      "url": null,
      "environment": "prod",
      "dateStarted": null,
      "dateFinished": "2020-06-17T19:20:55.641748Z",
      "id": "6883490"
    },
    "deployCount": 1,
    "dateCreated": "2020-06-17T18:45:31.042157Z",
    "lastEvent": "2020-07-08T21:21:21Z",
    "version": "b65bc521378269d3eaefdc964f8ef56621414943",
    "firstEvent": "2020-06-17T22:25:14Z",
    "lastCommit": {
      "repository": {
        "status": "active",
        "integrationId": "2933",
        "externalSlug": "getsentry/getsentry",
        "name": "getsentry/getsentry",
        "provider": {
          "id": "integrations:github",
          "name": "GitHub"
        },
        "url": "https://github.com/getsentry/getsentry",
        "id": "2",
        "dateCreated": "2016-10-10T21:36:45.373994Z"
      },
      "releases": [
        {
          "dateReleased": "2020-06-23T13:26:18.427090Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/staging/2077/",
          "dateCreated": "2020-06-23T13:22:50.420265Z",
          "version": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "shortVersion": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "ref": "perf/source-maps-test"
        },
        {
          "dateReleased": "2020-06-17T19:21:02.186004Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
          "dateCreated": "2020-06-17T18:45:31.042157Z",
          "version": "b65bc521378269d3eaefdc964f8ef56621414943",
          "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
          "ref": "master"
        }
      ],
      "dateCreated": "2020-06-17T18:43:37Z",
      "message": "feat(billing): Get a lot of money",
      "id": "b65bc521378269d3eaefdc964f8ef56621414943"
    },
    "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
    "authors": [
      {
        "username": "a37a1b4520ce46cea147ae2885a4e7e7",
        "lastLogin": "2020-09-14T22:34:55.550640Z",
        "isSuperuser": false,
        "isManaged": false,
        "experiments": {},
        "lastActive": "2020-09-15T22:13:20.503880Z",
        "isStaff": false,
        "id": "655784",
        "isActive": true,
        "has2fa": false,
        "name": "hell.boy@sentry.io",
        "avatarUrl": "https://secure.gravatar.com/avatar/eaa22e25b3a984659420831a77e4874e?s=32&d=mm",
        "dateJoined": "2020-04-20T16:21:25.365772Z",
        "emails": [
          {
            "is_verified": false,
            "id": "784574",
            "email": "hellboy@gmail.com"
          },
          {
            "is_verified": true,
            "id": "749185",
            "email": "hell.boy@sentry.io"
          }
        ],
        "avatar": {
          "avatarUuid": null,
          "avatarType": "letter_avatar"
        },
        "hasPasswordAuth": false,
        "email": "hell.boy@sentry.io"
      }
    ],
    "owner": null,
    "ref": "master",
    "projects": [
      {
        "name": "Sentry CSP",
        "slug": "sentry-csp"
      },
      {
        "name": "Backend",
        "slug": "sentry"
      },
      {
        "name": "Frontend",
        "slug": "javascript"
      }
    ]
  },
  "groupID": "1341191803"
}
```

<h3 id="retrieve-the-oldest-event-for-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-the-oldest-event-for-an-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» eventID|string|true|none|none|
|» dist|string¦null|true|none|none|
|» userReport|object¦null|true|none|none|
|» previousEventID|string¦null|true|none|none|
|» message|string|true|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|
|» errors|[object]|true|none|none|
|»» message|string|false|none|none|
|»» type|string|false|none|none|
|»» data|object|false|none|none|
|»»» column|integer|false|none|none|
|»»» source|string|false|none|none|
|»»» row|integer|false|none|none|
|» platform|string|true|none|none|
|» nextEventID|string¦null|true|none|none|
|» type|string|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» tags|[object]|true|none|none|
|»» value|string|false|none|none|
|»» key|string|false|none|none|
|»» _meta|string¦null|false|none|none|
|» dateCreated|string|true|none|none|
|» dateReceived|string|true|none|none|
|» user|object¦null|true|none|none|
|»» username|string¦null|true|none|none|
|»» name|string¦null|true|none|none|
|»» ip_address|string¦null|true|none|none|
|»» email|string¦null|true|none|none|
|»» data|object¦null|true|none|none|
|»»» isStaff|boolean|false|none|none|
|»» id|string|true|none|none|
|» entries|[anyOf]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» category|string|true|none|none|
|»»»»» level|string|true|none|none|
|»»»»» event_id|string¦null|true|none|none|
|»»»»» timestamp|string(date-time)|true|none|none|
|»»»»» data|object¦null|true|none|none|
|»»»»» message|string¦null|true|none|none|
|»»»»» type|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» fragment|string¦null|true|none|none|
|»»»» cookies|[array]¦null|true|none|none|
|»»»» inferredContentType|string¦null|true|none|none|
|»»»» env|object¦null|true|none|none|
|»»»»» ENV|string|false|none|none|
|»»»» headers|[array]|true|none|none|
|»»»» url|string|true|none|none|
|»»»» query|[array]|true|none|none|
|»»»» data|object¦null|true|none|none|
|»»»» method|string¦null|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» formatted|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» excOmitted|[integer]¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» stacktrace|object¦null|true|none|none|
|»»»»»» frames|[object]|true|none|none|
|»»»»»»» function|string|true|none|none|
|»»»»»»» errors|string¦null|true|none|none|
|»»»»»»» colNo|integer¦null|true|none|none|
|»»»»»»» vars|object¦null|true|none|none|
|»»»»»»» package|string¦null|true|none|none|
|»»»»»»» absPath|string¦null|true|none|none|
|»»»»»»» inApp|boolean|true|none|none|
|»»»»»»» lineNo|integer|true|none|none|
|»»»»»»» module|string|true|none|none|
|»»»»»»» filename|string|true|none|none|
|»»»»»»» platform|string¦null|true|none|none|
|»»»»»»» instructionAddr|string¦null|true|none|none|
|»»»»»»» context|[array]|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|string|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» symbolAddr|string¦null|true|none|none|
|»»»»» trust|string¦null|true|none|none|
|»»»»» symbol|string¦null|true|none|none|
|»»»» framesOmitted|string¦null|true|none|none|
|»»»» registers|string¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»» module|string¦null|true|none|none|
|»»» rawStacktrace|object¦null|true|none|none|
|»»» mechanism|object¦null|true|none|none|
|»»»» type|string|false|none|none|
|»»»» handled|boolean|false|none|none|
|»»» threadId|string¦null|true|none|none|
|»»» value|string|true|none|none|
|»»» type|string|true|none|none|
|packages|object|true|none|none|
|sdk|object|true|none|none|
|» version|string|false|none|none|
|» name|string|false|none|none|
|_meta|object|true|none|none|
|» user|string¦null|false|none|none|
|» context|string¦null|false|none|none|
|» entries|object|false|none|none|
|» contexts|string¦null|false|none|none|
|» message|string¦null|false|none|none|
|» packages|string¦null|false|none|none|
|» tags|object|false|none|none|
|» sdk|string¦null|false|none|none|
|contexts|object|true|none|none|
|» ForbiddenError|object|false|none|none|
|»» status|integer|false|none|none|
|»» statusText|string|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» type|string|false|none|none|
|» browser|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» os|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» trace|object|false|none|none|
|»» span_id|string|false|none|none|
|»» type|string|false|none|none|
|»» trace_id|string|false|none|none|
|»» op|string|false|none|none|
|» organization|object|false|none|none|
|»» type|string|false|none|none|
|»» id|string|false|none|none|
|»» slug|string|false|none|none|
|fingerprints|[string]|true|none|none|
|context|object|true|none|none|
|» resp|object|false|none|none|
|»» status|integer|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» name|string|false|none|none|
|»» statusText|string|false|none|none|
|»» message|string|false|none|none|
|»» stack|string|false|none|none|
|» session|object|false|none|none|
|»» foo|string|false|none|none|
|» unauthorized|boolean|false|none|none|
|» url|string|false|none|none|
|release|object¦null|true|none|none|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|
|groupID|string|true|none|none|
|title|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Retrieve the Latest Event for an Issue

<a id="opIdRetrieve the Latest Event for an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/events/latest/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/events/latest/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/events/latest/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/events/latest/`

Retrieves the details of the latest event for an issue.

<h3 id="retrieve-the-latest-event-for-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue.|

> Example responses

> 200 Response

```json
{
  "eventID": "9999aaaaca8b46d797c23c6077c6ff01",
  "dist": null,
  "userReport": null,
  "previousEventID": null,
  "message": "",
  "title": "This is an example Python exception",
  "id": "9999aaafcc8b46d797c23c6077c6ff01",
  "size": 107762,
  "errors": [
    {
      "data": {
        "column": 8,
        "source": "https://s1.sentry-cdn.com/_static/bloopbloop/sentry/dist/app.js.map",
        "row": 15
      },
      "message": "Invalid location in sourcemap",
      "type": "js_invalid_sourcemap_location"
    }
  ],
  "platform": "javascript",
  "nextEventID": "99f9e199e9a74a14bfef6196ad741619",
  "type": "error",
  "metadata": {
    "type": "ForbiddenError",
    "value": "GET /organizations/hellboy-meowmeow/users/ 403"
  },
  "tags": [
    {
      "value": "Chrome 83.0.4103",
      "key": "browser",
      "_meta": null
    },
    {
      "value": "Chrome",
      "key": "browser.name",
      "_meta": null
    },
    {
      "value": "prod",
      "key": "environment",
      "_meta": null
    },
    {
      "value": "yes",
      "key": "handled",
      "_meta": null
    },
    {
      "value": "error",
      "key": "level",
      "_meta": null
    },
    {
      "value": "generic",
      "key": "mechanism",
      "_meta": null
    }
  ],
  "dateCreated": "2020-06-17T22:26:56.098086Z",
  "dateReceived": "2020-06-17T22:26:56.428721Z",
  "user": {
    "username": null,
    "name": "Hell Boy",
    "ip_address": "192.168.1.1",
    "email": "hell@boy.cat",
    "data": {
      "isStaff": false
    },
    "id": "550747"
  },
  "entries": [
    {
      "type": "exception",
      "data": {
        "values": [
          {
            "stacktrace": {
              "frames": [
                {
                  "function": "ignoreOnError",
                  "errors": null,
                  "colNo": 23,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "inApp": false,
                  "lineNo": 71,
                  "module": "usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/@sentry/browser/esm/helpers.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      66,
                      "            }"
                    ],
                    [
                      67,
                      "            // Attempt to invoke user-land function"
                    ],
                    [
                      68,
                      "            // NOTE: If you are a Sentry user, and you are seeing this stack frame, it"
                    ],
                    [
                      69,
                      "            //       means the sentry.javascript SDK caught an error invoking your application code. This"
                    ],
                    [
                      70,
                      "            //       is expected behavior and NOT indicative of a bug with sentry.javascript."
                    ],
                    [
                      71,
                      "            return fn.apply(this, wrappedArguments);"
                    ],
                    [
                      72,
                      "            // tslint:enable:no-unsafe-any"
                    ],
                    [
                      73,
                      "        }"
                    ],
                    [
                      74,
                      "        catch (ex) {"
                    ],
                    [
                      75,
                      "            ignoreNextOnError();"
                    ],
                    [
                      76,
                      "            withScope(function (scope) {"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": "apply",
                  "errors": null,
                  "colNo": 24,
                  "vars": null,
                  "package": null,
                  "absPath": "webpack:////usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "inApp": false,
                  "lineNo": 74,
                  "module": "usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods",
                  "filename": "/usr/src/getsentry/src/sentry/node_modules/reflux-core/lib/PublisherMethods.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      69,
                      "     */"
                    ],
                    [
                      70,
                      "    triggerAsync: function triggerAsync() {"
                    ],
                    [
                      71,
                      "        var args = arguments,"
                    ],
                    [
                      72,
                      "            me = this;"
                    ],
                    [
                      73,
                      "        _.nextTick(function () {"
                    ],
                    [
                      74,
                      "            me.trigger.apply(me, args);"
                    ],
                    [
                      75,
                      "        });"
                    ],
                    [
                      76,
                      "    },"
                    ],
                    [
                      77,
                      ""
                    ],
                    [
                      78,
                      "    /**"
                    ],
                    [
                      79,
                      "     * Wraps the trigger mechanism with a deferral function."
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "module": null,
            "rawStacktrace": {
              "frames": [
                {
                  "function": "a",
                  "errors": null,
                  "colNo": 88800,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 81,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      76,
                      "/*!"
                    ],
                    [
                      77,
                      "  Copyright (c) 2018 Jed Watson."
                    ],
                    [
                      78,
                      "  Licensed under the MIT License (MIT), see"
                    ],
                    [
                      79,
                      "  http://jedwatson.github.io/react-select"
                    ],
                    [
                      80,
                      "*/"
                    ],
                    [
                      81,
                      "{snip} e,t)}));return e.handleEvent?e.handleEvent.apply(this,s):e.apply(this,s)}catch(e){throw c(),Object(o.m)((function(n){n.addEventProcessor((fu {snip}"
                    ],
                    [
                      82,
                      "/*!"
                    ],
                    [
                      83,
                      " * JavaScript Cookie v2.2.1"
                    ],
                    [
                      84,
                      " * https://github.com/js-cookie/js-cookie"
                    ],
                    [
                      85,
                      " *"
                    ],
                    [
                      86,
                      " * Copyright 2006, 2015 Klaus Hartl & Fagner Brack"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                },
                {
                  "function": null,
                  "errors": null,
                  "colNo": 149484,
                  "vars": null,
                  "package": null,
                  "absPath": "https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "inApp": false,
                  "lineNo": 119,
                  "module": null,
                  "filename": "/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js",
                  "platform": null,
                  "instructionAddr": null,
                  "context": [
                    [
                      114,
                      "/* @license"
                    ],
                    [
                      115,
                      "Papa Parse"
                    ],
                    [
                      116,
                      "v5.2.0"
                    ],
                    [
                      117,
                      "https://github.com/mholt/PapaParse"
                    ],
                    [
                      118,
                      "License: MIT"
                    ],
                    [
                      119,
                      "{snip} (){var e=arguments,t=this;r.nextTick((function(){t.trigger.apply(t,e)}))},deferWith:function(e){var t=this.trigger,n=this,r=function(){t.app {snip}"
                    ],
                    [
                      120,
                      "/**!"
                    ],
                    [
                      121,
                      " * @fileOverview Kickass library to create and place poppers near their reference elements."
                    ],
                    [
                      122,
                      " * @version 1.16.1"
                    ],
                    [
                      123,
                      " * @license"
                    ],
                    [
                      124,
                      " * Copyright (c) 2016 Federico Zivolo and contributors"
                    ]
                  ],
                  "symbolAddr": null,
                  "trust": null,
                  "symbol": null
                }
              ],
              "framesOmitted": null,
              "registers": null,
              "hasSystemFrames": true
            },
            "mechanism": {
              "type": "generic",
              "handled": true
            },
            "threadId": null,
            "value": "GET /organizations/hellboy-meowmeow/users/ 403",
            "type": "ForbiddenError"
          }
        ],
        "excOmitted": null,
        "hasSystemFrames": true
      }
    },
    {
      "type": "breadcrumbs",
      "data": {
        "values": [
          {
            "category": "tracing",
            "level": "debug",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.266586Z",
            "data": null,
            "message": "[Tracing] pushActivity: idleTransactionStarted#1",
            "type": "debug"
          },
          {
            "category": "xhr",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.619446Z",
            "data": {
              "url": "/api/0/internal/health/",
              "status_code": 200,
              "method": "GET"
            },
            "message": null,
            "type": "http"
          },
          {
            "category": "sentry.transaction",
            "level": "info",
            "event_id": null,
            "timestamp": "2020-06-17T22:26:55.945016Z",
            "data": null,
            "message": "7787a027f3fb46c985aaa2287b3f4d09",
            "type": "default"
          }
        ]
      }
    },
    {
      "type": "request",
      "data": {
        "fragment": null,
        "cookies": [],
        "inferredContentType": null,
        "env": null,
        "headers": [
          [
            "User-Agent",
            "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.97 Safari/537.36"
          ]
        ],
        "url": "https://sentry.io/organizations/hellboy-meowmeow/issues/",
        "query": [
          [
            "project",
            "5236886"
          ]
        ],
        "data": null,
        "method": null
      }
    }
  ],
  "packages": {},
  "sdk": {
    "version": "5.17.0",
    "name": "sentry.javascript.browser"
  },
  "_meta": {
    "user": null,
    "context": null,
    "entries": {},
    "contexts": null,
    "message": null,
    "packages": null,
    "tags": {},
    "sdk": null
  },
  "contexts": {
    "ForbiddenError": {
      "status": 403,
      "statusText": "Forbidden",
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "type": "default"
    },
    "browser": {
      "version": "83.0.4103",
      "type": "browser",
      "name": "Chrome"
    },
    "os": {
      "version": "10",
      "type": "os",
      "name": "Windows"
    },
    "trace": {
      "span_id": "83db1ad17e67dfe7",
      "type": "trace",
      "trace_id": "da6caabcd90e45fdb81f6655824a5f88",
      "op": "navigation"
    },
    "organization": {
      "type": "default",
      "id": "323938",
      "slug": "hellboy-meowmeow"
    }
  },
  "fingerprints": [
    "fbe908cc63d63ea9763fd84cb6bad177"
  ],
  "context": {
    "resp": {
      "status": 403,
      "responseJSON": {
        "detail": "You do not have permission to perform this action."
      },
      "name": "ForbiddenError",
      "statusText": "Forbidden",
      "message": "GET /organizations/hellboy-meowmeow/users/ 403",
      "stack": "Error\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480441\n    at u (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51006)\n    at Generator._invoke (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:50794)\n    at Generator.A.forEach.e.<computed> [as next] (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:165:51429)\n    at n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68684)\n    at s (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68895)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68954\n    at new Promise (<anonymous>)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:16:68835\n    at v (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480924)\n    at m (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:480152)\n    at t.fetchMemberList (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:902983)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:900527)\n    at t.componentDidMount (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:15597)\n    at Pc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:101023)\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Rc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:97371)\n    at Oc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:87690)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45820\n    at t.unstable_runWithPriority (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:3462)\n    at Ko (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45529)\n    at Zo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45765)\n    at Jo (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:45700)\n    at gc (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:84256)\n    at Object.enqueueSetState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:181:50481)\n    at t.M.setState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:173:1439)\n    at t.onUpdate (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:543076)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at p.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at p.onInitializeUrlState (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/app.js:1:541711)\n    at a.n (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149090)\n    at a.emit (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:189:6550)\n    at Function.trigger (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149379)\n    at https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:119:149484\n    at a (https://s1.sentry-cdn.com/_static/dde778f9f93a48e2b6e58ecb0c5eb8f2/sentry/dist/vendor.js:81:88800)"
    }
  },
  "release": {
    "dateReleased": "2020-06-17T19:21:02.186004Z",
    "newGroups": 4,
    "commitCount": 11,
    "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
    "data": {},
    "lastDeploy": {
      "name": "b65bc521378269d3eaefdc964f8ef56621414943 to prod",
      "url": null,
      "environment": "prod",
      "dateStarted": null,
      "dateFinished": "2020-06-17T19:20:55.641748Z",
      "id": "6883490"
    },
    "deployCount": 1,
    "dateCreated": "2020-06-17T18:45:31.042157Z",
    "lastEvent": "2020-07-08T21:21:21Z",
    "version": "b65bc521378269d3eaefdc964f8ef56621414943",
    "firstEvent": "2020-06-17T22:25:14Z",
    "lastCommit": {
      "repository": {
        "status": "active",
        "integrationId": "2933",
        "externalSlug": "getsentry/getsentry",
        "name": "getsentry/getsentry",
        "provider": {
          "id": "integrations:github",
          "name": "GitHub"
        },
        "url": "https://github.com/getsentry/getsentry",
        "id": "2",
        "dateCreated": "2016-10-10T21:36:45.373994Z"
      },
      "releases": [
        {
          "dateReleased": "2020-06-23T13:26:18.427090Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/staging/2077/",
          "dateCreated": "2020-06-23T13:22:50.420265Z",
          "version": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "shortVersion": "f3783e5fe710758724f14267439fd46cc2bf5918",
          "ref": "perf/source-maps-test"
        },
        {
          "dateReleased": "2020-06-17T19:21:02.186004Z",
          "url": "https://freight.getsentry.net/deploys/getsentry/production/8868/",
          "dateCreated": "2020-06-17T18:45:31.042157Z",
          "version": "b65bc521378269d3eaefdc964f8ef56621414943",
          "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
          "ref": "master"
        }
      ],
      "dateCreated": "2020-06-17T18:43:37Z",
      "message": "feat(billing): Get a lot of money",
      "id": "b65bc521378269d3eaefdc964f8ef56621414943"
    },
    "shortVersion": "b65bc521378269d3eaefdc964f8ef56621414943",
    "authors": [
      {
        "username": "a37a1b4520ce46cea147ae2885a4e7e7",
        "lastLogin": "2020-09-14T22:34:55.550640Z",
        "isSuperuser": false,
        "isManaged": false,
        "experiments": {},
        "lastActive": "2020-09-15T22:13:20.503880Z",
        "isStaff": false,
        "id": "655784",
        "isActive": true,
        "has2fa": false,
        "name": "hell.boy@sentry.io",
        "avatarUrl": "https://secure.gravatar.com/avatar/eaa22e25b3a984659420831a77e4874e?s=32&d=mm",
        "dateJoined": "2020-04-20T16:21:25.365772Z",
        "emails": [
          {
            "is_verified": false,
            "id": "784574",
            "email": "hellboy@gmail.com"
          },
          {
            "is_verified": true,
            "id": "749185",
            "email": "hell.boy@sentry.io"
          }
        ],
        "avatar": {
          "avatarUuid": null,
          "avatarType": "letter_avatar"
        },
        "hasPasswordAuth": false,
        "email": "hell.boy@sentry.io"
      }
    ],
    "owner": null,
    "ref": "master",
    "projects": [
      {
        "name": "Sentry CSP",
        "slug": "sentry-csp"
      },
      {
        "name": "Backend",
        "slug": "sentry"
      },
      {
        "name": "Frontend",
        "slug": "javascript"
      }
    ]
  },
  "groupID": "1341191803"
}
```

<h3 id="retrieve-the-latest-event-for-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-the-latest-event-for-an-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» eventID|string|true|none|none|
|» dist|string¦null|true|none|none|
|» userReport|object¦null|true|none|none|
|» previousEventID|string¦null|true|none|none|
|» message|string|true|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|
|» errors|[object]|true|none|none|
|»» message|string|false|none|none|
|»» type|string|false|none|none|
|»» data|object|false|none|none|
|»»» column|integer|false|none|none|
|»»» source|string|false|none|none|
|»»» row|integer|false|none|none|
|» platform|string|true|none|none|
|» nextEventID|string¦null|true|none|none|
|» type|string|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» tags|[object]|true|none|none|
|»» value|string|false|none|none|
|»» key|string|false|none|none|
|»» _meta|string¦null|false|none|none|
|» dateCreated|string|true|none|none|
|» dateReceived|string|true|none|none|
|» user|object¦null|true|none|none|
|»» username|string¦null|true|none|none|
|»» name|string¦null|true|none|none|
|»» ip_address|string¦null|true|none|none|
|»» email|string¦null|true|none|none|
|»» data|object¦null|true|none|none|
|»»» isStaff|boolean|false|none|none|
|»» id|string|true|none|none|
|» entries|[anyOf]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» category|string|true|none|none|
|»»»»» level|string|true|none|none|
|»»»»» event_id|string¦null|true|none|none|
|»»»»» timestamp|string(date-time)|true|none|none|
|»»»»» data|object¦null|true|none|none|
|»»»»» message|string¦null|true|none|none|
|»»»»» type|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» fragment|string¦null|true|none|none|
|»»»» cookies|[array]¦null|true|none|none|
|»»»» inferredContentType|string¦null|true|none|none|
|»»»» env|object¦null|true|none|none|
|»»»»» ENV|string|false|none|none|
|»»»» headers|[array]|true|none|none|
|»»»» url|string|true|none|none|
|»»»» query|[array]|true|none|none|
|»»»» data|object¦null|true|none|none|
|»»»» method|string¦null|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» formatted|string|true|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» type|string|true|none|none|
|»»» data|object|true|none|none|
|»»»» excOmitted|[integer]¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»»» values|[object]|true|none|none|
|»»»»» stacktrace|object¦null|true|none|none|
|»»»»»» frames|[object]|true|none|none|
|»»»»»»» function|string|true|none|none|
|»»»»»»» errors|string¦null|true|none|none|
|»»»»»»» colNo|integer¦null|true|none|none|
|»»»»»»» vars|object¦null|true|none|none|
|»»»»»»» package|string¦null|true|none|none|
|»»»»»»» absPath|string¦null|true|none|none|
|»»»»»»» inApp|boolean|true|none|none|
|»»»»»»» lineNo|integer|true|none|none|
|»»»»»»» module|string|true|none|none|
|»»»»»»» filename|string|true|none|none|
|»»»»»»» platform|string¦null|true|none|none|
|»»»»»»» instructionAddr|string¦null|true|none|none|
|»»»»»»» context|[array]|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|integer|false|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»»» *anonymous*|string|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»» symbolAddr|string¦null|true|none|none|
|»»»»» trust|string¦null|true|none|none|
|»»»»» symbol|string¦null|true|none|none|
|»»»» framesOmitted|string¦null|true|none|none|
|»»»» registers|string¦null|true|none|none|
|»»»» hasSystemFrames|boolean|true|none|none|
|»»» module|string¦null|true|none|none|
|»»» rawStacktrace|object¦null|true|none|none|
|»»» mechanism|object¦null|true|none|none|
|»»»» type|string|false|none|none|
|»»»» handled|boolean|false|none|none|
|»»» threadId|string¦null|true|none|none|
|»»» value|string|true|none|none|
|»»» type|string|true|none|none|
|packages|object|true|none|none|
|sdk|object|true|none|none|
|» version|string|false|none|none|
|» name|string|false|none|none|
|_meta|object|true|none|none|
|» user|string¦null|false|none|none|
|» context|string¦null|false|none|none|
|» entries|object|false|none|none|
|» contexts|string¦null|false|none|none|
|» message|string¦null|false|none|none|
|» packages|string¦null|false|none|none|
|» tags|object|false|none|none|
|» sdk|string¦null|false|none|none|
|contexts|object|true|none|none|
|» ForbiddenError|object|false|none|none|
|»» status|integer|false|none|none|
|»» statusText|string|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» type|string|false|none|none|
|» browser|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» os|object|false|none|none|
|»» version|string|false|none|none|
|»» type|string|false|none|none|
|»» name|string|false|none|none|
|» trace|object|false|none|none|
|»» span_id|string|false|none|none|
|»» type|string|false|none|none|
|»» trace_id|string|false|none|none|
|»» op|string|false|none|none|
|» organization|object|false|none|none|
|»» type|string|false|none|none|
|»» id|string|false|none|none|
|»» slug|string|false|none|none|
|fingerprints|[string]|true|none|none|
|context|object|true|none|none|
|» resp|object|false|none|none|
|»» status|integer|false|none|none|
|»» responseJSON|object|false|none|none|
|»»» detail|string|false|none|none|
|»» name|string|false|none|none|
|»» statusText|string|false|none|none|
|»» message|string|false|none|none|
|»» stack|string|false|none|none|
|» session|object|false|none|none|
|»» foo|string|false|none|none|
|» unauthorized|boolean|false|none|none|
|» url|string|false|none|none|
|release|object¦null|true|none|none|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|
|groupID|string|true|none|none|
|title|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## List an Issue's Events

<a id="opIdList an Issue's Events"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/events/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/events/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/events/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/events/`

This endpoint lists an issue's events.

<h3 id="list-an-issue's-events-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to retrieve.|
|full|query|boolean|false|If this is set to true then the event payload will include the full event body, including the stacktrace. |

#### Detailed descriptions

**full**: If this is set to true then the event payload will include the full event body, including the stacktrace. 
Set to true to enable.

> Example responses

> 200 Response

```json
[
  {
    "eventID": "9fac2ceed9344f2bbfdd1fdacb0ed9b1",
    "tags": [
      {
        "key": "browser",
        "value": "Chrome 60.0"
      },
      {
        "key": "device",
        "value": "Other"
      },
      {
        "key": "environment",
        "value": "production"
      },
      {
        "value": "fatal",
        "key": "level"
      },
      {
        "key": "os",
        "value": "Mac OS X 10.12.6"
      },
      {
        "value": "CPython 2.7.16",
        "key": "runtime"
      },
      {
        "key": "release",
        "value": "17642328ead24b51867165985996d04b29310337"
      },
      {
        "key": "server_name",
        "value": "web1.example.com"
      }
    ],
    "dateCreated": "2020-09-11T17:46:36Z",
    "user": null,
    "message": "",
    "title": "This is an example Python exception",
    "id": "dfb1a2d057194e76a4186cc8a5271553",
    "platform": "python",
    "event.type": "error",
    "groupID": "1889724436"
  }
]
```

<h3 id="list-an-issue's-events-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="list-an-issue's-events-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» eventID|string|true|none|none|
|» tags|[object]|true|none|none|
|»» value|string|false|none|none|
|»» key|string|false|none|none|
|» dateCreated|string|true|none|none|
|» user|object¦null|true|none|none|
|»» username|string¦null|true|none|none|
|»» name|string¦null|true|none|none|
|»» ip_address|string¦null|true|none|none|
|»» email|string¦null|true|none|none|
|»» data|object¦null|true|none|none|
|»»» isStaff|boolean|false|none|none|
|»» id|string|true|none|none|
|» message|string|true|none|none|
|» id|string|true|none|none|
|» platform|string|true|none|none|
|» event.type|string|true|none|none|
|» groupID|string|true|none|none|
|» title|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Retrieve an Issue

<a id="opIdRetrieve an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/issues/{issue_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/issues/{issue_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/issues/{issue_id}/`

Return details on an individual issue. This returns the basic stats for the issue (title, last seen, first seen), some overall numbers (number of comments, user reports) as well as the summarized event data.

<h3 id="retrieve-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to retrieve.|

> Example responses

> 200 Response

```json
{
  "activity": [
    {
      "data": {},
      "dateCreated": "2018-11-06T21:19:55Z",
      "id": "0",
      "type": "first_seen",
      "user": null
    }
  ],
  "annotations": [],
  "assignedTo": null,
  "count": "1",
  "culprit": "raven.scripts.runner in main",
  "firstRelease": {
    "authors": [],
    "commitCount": 0,
    "data": {},
    "dateCreated": "2018-11-06T21:19:55.146Z",
    "dateReleased": null,
    "deployCount": 0,
    "firstEvent": "2018-11-06T21:19:55.271Z",
    "lastCommit": null,
    "lastDeploy": null,
    "lastEvent": "2018-11-06T21:19:55.271Z",
    "newGroups": 0,
    "owner": null,
    "projects": [
      {
        "name": "Pump Station",
        "slug": "pump-station"
      }
    ],
    "ref": null,
    "shortVersion": "1764232",
    "url": null,
    "version": "17642328ead24b51867165985996d04b29310337"
  },
  "firstSeen": "2018-11-06T21:19:55Z",
  "hasSeen": false,
  "id": "1",
  "isBookmarked": false,
  "isPublic": false,
  "isSubscribed": true,
  "lastRelease": null,
  "lastSeen": "2018-11-06T21:19:55Z",
  "level": "error",
  "logger": null,
  "metadata": {
    "title": "This is an example Python exception"
  },
  "numComments": 0,
  "participants": [],
  "permalink": "https://sentry.io/the-interstellar-jurisdiction/pump-station/issues/1/",
  "pluginActions": [],
  "pluginContexts": [],
  "pluginIssues": [],
  "project": {
    "id": "2",
    "name": "Pump Station",
    "slug": "pump-station"
  },
  "seenBy": [],
  "shareId": null,
  "shortId": "PUMP-STATION-1",
  "stats": {
    "24h": [
      [
        1541451600,
        557
      ],
      [
        1541455200,
        473
      ],
      [
        1541458800,
        914
      ],
      [
        1541462400,
        991
      ],
      [
        1541466000,
        925
      ],
      [
        1541469600,
        881
      ],
      [
        1541473200,
        182
      ],
      [
        1541476800,
        490
      ],
      [
        1541480400,
        820
      ],
      [
        1541484000,
        322
      ],
      [
        1541487600,
        836
      ],
      [
        1541491200,
        565
      ],
      [
        1541494800,
        758
      ],
      [
        1541498400,
        880
      ],
      [
        1541502000,
        677
      ],
      [
        1541505600,
        381
      ],
      [
        1541509200,
        814
      ],
      [
        1541512800,
        329
      ],
      [
        1541516400,
        446
      ],
      [
        1541520000,
        731
      ],
      [
        1541523600,
        111
      ],
      [
        1541527200,
        926
      ],
      [
        1541530800,
        772
      ],
      [
        1541534400,
        400
      ],
      [
        1541538000,
        943
      ]
    ],
    "30d": [
      [
        1538870400,
        565
      ],
      [
        1538956800,
        12862
      ],
      [
        1539043200,
        15617
      ],
      [
        1539129600,
        10809
      ],
      [
        1539216000,
        15065
      ],
      [
        1539302400,
        12927
      ],
      [
        1539388800,
        12994
      ],
      [
        1539475200,
        13139
      ],
      [
        1539561600,
        11838
      ],
      [
        1539648000,
        12088
      ],
      [
        1539734400,
        12338
      ],
      [
        1539820800,
        12768
      ],
      [
        1539907200,
        12816
      ],
      [
        1539993600,
        15356
      ],
      [
        1540080000,
        10910
      ],
      [
        1540166400,
        12306
      ],
      [
        1540252800,
        12912
      ],
      [
        1540339200,
        14700
      ],
      [
        1540425600,
        11890
      ],
      [
        1540512000,
        11684
      ],
      [
        1540598400,
        13510
      ],
      [
        1540684800,
        12625
      ],
      [
        1540771200,
        12811
      ],
      [
        1540857600,
        13180
      ],
      [
        1540944000,
        14651
      ],
      [
        1541030400,
        14161
      ],
      [
        1541116800,
        12612
      ],
      [
        1541203200,
        14316
      ],
      [
        1541289600,
        14742
      ],
      [
        1541376000,
        12505
      ],
      [
        1541462400,
        14180
      ]
    ]
  },
  "status": "unresolved",
  "statusDetails": {},
  "subscriptionDetails": null,
  "tags": [],
  "title": "This is an example Python exception",
  "type": "default",
  "userCount": 0,
  "userReportCount": 0
}
```

<h3 id="retrieve-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-an-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» activity|[object]|true|none|none|
|»» data|object|false|none|none|
|»» dateCreated|string|false|none|none|
|»» id|string|false|none|none|
|»» type|string|false|none|none|
|»» user|object¦null|false|none|none|
|» annotations|[string]|true|none|none|
|» assignedTo|object¦null|true|none|none|
|» count|string|true|none|none|
|» culprit|string|true|none|none|
|» firstRelease|object¦null|true|none|none|
|»» authors|[string]|false|none|none|
|»» commitCount|integer|false|none|none|
|»» data|object¦null|false|none|none|
|»» dateCreated|string|false|none|none|
|»» dateReleased|string¦null|false|none|none|
|»» deployCount|integer|false|none|none|
|»» firstEvent|string|false|none|none|
|»» lastCommit|string¦null|false|none|none|
|»» lastDeploy|string¦null|false|none|none|
|»» lastEvent|string|false|none|none|
|»» newGroups|integer|false|none|none|
|»» owner|string¦null|false|none|none|
|»» projects|[object]|false|none|none|
|»»» name|string|false|none|none|
|»»» slug|string|false|none|none|
|»» ref|string¦null|false|none|none|
|»» shortVersion|string|false|none|none|
|»» url|string¦null|false|none|none|
|»» version|string|false|none|none|
|» firstSeen|string|true|none|none|
|» hasSeen|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» isSubscribed|boolean|true|none|none|
|» lastRelease|object¦null|true|none|none|
|» lastSeen|string|true|none|none|
|» level|string|true|none|none|
|» logger|string¦null|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» filename|string|true|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» numComments|integer|true|none|none|
|» participants|[object]|true|none|none|
|» permalink|string|true|none|none|
|» pluginActions|[array]|true|none|none|
|» pluginContexts|[string]|true|none|none|
|» pluginIssues|[object]|true|none|none|
|» project|object|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» seenBy|[object]|true|none|none|
|» shareId|string¦null|true|none|none|
|» shortId|string|true|none|none|
|» stats|object|true|none|none|
|»» 24h|[array]|false|none|none|
|»» 30d|[array]|false|none|none|
|» status|string|true|none|none|
|» statusDetails|object|true|none|none|
|» subscriptionDetails|object¦null|true|none|none|
|» tags|[object]|true|none|none|
|» title|string|true|none|none|
|» type|string|true|none|none|
|» userCount|integer|true|none|none|
|» userReportCount|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|resolved|
|status|unresolved|
|status|ignored|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:read )
</aside>

## Update an Issue

<a id="opIdUpdate an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/issues/{issue_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/issues/{issue_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "status": "string",
  "assignedTo": "string",
  "hasSeen": true,
  "isBookmarked": true,
  "isSubscribed": true,
  "isPublic": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/issues/{issue_id}/`

Updates an individual issue's attributes.  Only the attributes submitted are modified.

> Body parameter

```json
{
  "status": "string",
  "assignedTo": "string",
  "hasSeen": true,
  "isBookmarked": true,
  "isSubscribed": true,
  "isPublic": true
}
```

<h3 id="update-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the group to retrieve.|
|body|body|object|true|none|
|» status|body|string|false|The new status for the issues. Valid values are `"resolved"`, `"resolvedInNextRelease"`, `"unresolved"`, and `"ignored"`.|
|» assignedTo|body|string|false|The actor id (or username) of the user or team that should be assigned to this issue.|
|» hasSeen|body|boolean|false|In case this API call is invoked with a user context this allows changing of the flag that indicates if the user has seen the event.|
|» isBookmarked|body|boolean|false|In case this API call is invoked with a user context this allows changing of the bookmark flag.|
|» isSubscribed|body|boolean|false|none|
|» isPublic|body|boolean|false|Sets the issue to public or private.|

> Example responses

> 200 Response

```json
{
  "annotations": [],
  "assignedTo": null,
  "count": "1",
  "culprit": "raven.scripts.runner in main",
  "firstSeen": "2018-11-06T21:19:55Z",
  "hasSeen": false,
  "id": "1",
  "isBookmarked": false,
  "isPublic": false,
  "isSubscribed": true,
  "lastSeen": "2018-11-06T21:19:55Z",
  "level": "error",
  "logger": null,
  "metadata": {
    "title": "This is an example Python exception"
  },
  "numComments": 0,
  "permalink": "https://sentry.io/the-interstellar-jurisdiction/pump-station/issues/1/",
  "project": {
    "id": "2",
    "name": "Pump Station",
    "slug": "pump-station"
  },
  "shareId": null,
  "shortId": "PUMP-STATION-1",
  "status": "unresolved",
  "statusDetails": {},
  "subscriptionDetails": null,
  "title": "This is an example Python exception",
  "type": "default",
  "userCount": 0
}
```

<h3 id="update-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<h3 id="update-an-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» annotations|[string]|true|none|none|
|» assignedTo|object¦null|true|none|none|
|» count|string|true|none|none|
|» culprit|string|true|none|none|
|» firstSeen|string|true|none|none|
|» hasSeen|boolean|true|none|none|
|» id|string|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» isSubscribed|boolean|true|none|none|
|» lastSeen|string|true|none|none|
|» level|string|true|none|none|
|» logger|string¦null|true|none|none|
|» metadata|any|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» filename|string|true|none|none|
|»»» type|string|true|none|none|
|»»» value|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» title|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» numComments|integer|true|none|none|
|» permalink|string|true|none|none|
|» project|object|true|none|none|
|»» id|string|false|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» shareId|string¦null|true|none|none|
|» shortId|string|true|none|none|
|» status|string|true|none|none|
|» statusDetails|object|true|none|none|
|» subscriptionDetails|object¦null|true|none|none|
|» title|string|true|none|none|
|» type|string|true|none|none|
|» userCount|integer|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|resolved|
|status|unresolved|
|status|ignored|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:write )
</aside>

## Remove an Issue

<a id="opIdRemove an Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/issues/{issue_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/issues/{issue_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/issues/{issue_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/issues/{issue_id}/`

Removes an individual issue.

<h3 id="remove-an-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|issue_id|path|string|true|The ID of the issue to delete.|

<h3 id="remove-an-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The requested resource does not exist|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:admin )
</aside>

<h1 id="api-reference-releases">Releases</h1>

Endpoints for releases

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/releases/&template=api_error_template.md">Found an error? Let us know.</a>

## Retrieve Release Health Session Statistics

<a id="opIdRetrieve Release Health Session Statistics"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/sessions/',
  params: {
  'project' => 'array[integer]',
'field' => 'array[string]'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/sessions/', params={
  'project': [
  0
],  'field': [
  "string"
]
}, headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/sessions/?project=0&field=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/sessions/`

Returns a time series of release health session statistics for projects bound to an organization.

The interval and date range are subject to certain restrictions and rounding rules.

The date range is rounded to align with the interval, and is rounded to at least one hour. The interval can at most be one day and at least one hour currently. It has to cleanly divide one day, for rounding reasons.

Apart from the query parameters listed below, this endpoint also supports the usual [pagination parameters](https://docs.sentry.io/api/pagination/).

<h3 id="retrieve-release-health-session-statistics-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project|query|array[integer]|true|The ID of the projects to filter by.|
|field|query|array[string]|true|The list of fields to query.|
|environment|query|array[string]|false|The name of environments to filter by.|
|groupBy|query|array[string]|false|The list of properties to group by.|
|orderBy|query|string|false|An optional field to order by, which must be one of the fields provided in `field`. Use `-` for descending order, for example `-sum(session)`. |
|query|query|string|false|A free-form query that is applied as a filter.|
|statsPeriod|query|string|false|This defines the range of the time series, relative to now.|
|interval|query|string|false|This is the resolution of the time series, given in the same format as `statsPeriod`.|
|statsPeriodStart|query|string|false|This defines the start of the time series range, in the same format as the `interval`, relative to now.|
|statsPeriodEnd|query|string|false|This defines the end of the time series range, in the same format as the `interval`, relative to now.|
|start|query|string(date-time)|false|This defines the start of the time series range as an explicit datetime.|
|end|query|string(date-time)|false|This defines the inclusive end of the time series range as an explicit datetime.|

#### Detailed descriptions

**project**: The ID of the projects to filter by.

Use `-1` to include all accessible projects.

**field**: The list of fields to query.

The available fields are
  - `sum(session)`
  - `count_unique(user)`
  - `avg`, `p50`, `p75`, `p90`, `p95`, `p99`, `max` applied to `session.duration`. For example, `p99(session.duration)`. Session duration is [no longer being recorded](https://github.com/getsentry/sentry/discussions/42716) as of on Jan 12, 2023. Returned data may be incomplete.
  - `crash_rate`, `crash_free_rate` applied to `user` or `session`. For example, `crash_free_rate(user)`

**groupBy**: The list of properties to group by.

The available groupBy conditions are `project`, `release`, `environment` and `session.status`.

Grouping by `session.status` does not work when `crash_rate` or `crash_free_rate` are queried.

**orderBy**: An optional field to order by, which must be one of the fields provided in `field`. Use `-` for descending order, for example `-sum(session)`. 

This alters the order of the `groups` returned, so it only makes sense in combination with `groupBy`. 

Ordering by more than one field is currently not supported.

**query**: A free-form query that is applied as a filter.

An example query could be `release:"1.1.0" or release:"1.2.0"`.

**statsPeriod**: This defines the range of the time series, relative to now.

The range is given in a `"<number><unit>"` format.

For example `1d` for a one day range. Possible units are `m` for minutes, `h` for hours, `d` for days and `w` for weeks.

It defaults to `90d`.

**interval**: This is the resolution of the time series, given in the same format as `statsPeriod`.

The default resolution is `1h` and the minimum resolution is currently restricted to `1h` as well.

Intervals larger than `1d` are not supported, and the interval has to cleanly divide one day.

> Example responses

> 200 Response

```json
{
  "start": "2021-02-01T00:00:00Z",
  "end": "2021-02-04T00:00:00Z",
  "intervals": [
    "2021-02-01T00:00:00Z",
    "2021-02-02T00:00:00Z",
    "2021-02-03T00:00:00Z"
  ],
  "groups": [
    {
      "by": {
        "session.status": "healthy"
      },
      "totals": {
        "sum(session)": 1715553
      },
      "series": {
        "sum(session)": [
          683772,
          677788,
          353993
        ]
      }
    },
    {
      "by": {
        "session.status": "abnormal"
      },
      "totals": {
        "sum(session)": 0
      },
      "series": {
        "sum(session)": [
          0,
          0,
          0
        ]
      }
    },
    {
      "by": {
        "session.status": "crashed"
      },
      "totals": {
        "sum(session)": 383
      },
      "series": {
        "sum(session)": [
          33,
          26,
          324
        ]
      }
    },
    {
      "by": {
        "session.status": "errored"
      },
      "totals": {
        "sum(session)": 1565
      },
      "series": {
        "sum(session)": [
          163,
          201,
          1201
        ]
      }
    }
  ]
}
```

> 400 Response

```json
{
  "detail": "string"
}
```

<h3 id="retrieve-release-health-session-statistics-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Time-series Session Statistics.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Wrong Parameters|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="retrieve-release-health-session-statistics-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» start|string(date-time)|true|none|The start time of the data being returned.|
|» end|string(date-time)|true|none|The exclusive end time of the data being returned.|
|» intervals|[string]|true|none|The time slices of the timeseries data given in the `groups[].series` field.|
|» groups|[object]|true|none|none|
|»» by|object|true|none|These are key/value pairs, the key being the requested `groupBy` property with its corresponding value.|
|»»» session.status|string|false|none|Example `groupBy` property|
|»» totals|object|true|none|These are key/value pairs, the key being the requested `field`, and the value the corresponding total over the requested time frame.|
|»»» sum(session)|integer|false|none|Example `field` value|
|»» series|object|true|none|These are key/value pairs, the key being the requested `field`, and the value is an array of aggregated values. The array corresponds to the times given in the `intervals` array.|
|»»» **additionalProperties**|[integer]|false|none|none|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» detail|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org: read )
</aside>

## List an Organization's Releases

<a id="opIdList an Organization's Releases"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/`

Return a list of releases for a given organization.

<h3 id="list-an-organization's-releases-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|query|query|string|false|This parameter can be used to create a "starts with" filter for the version.|

> Example responses

> 200 Response

```json
[
  {
    "id": 2,
    "authors": [],
    "commitCount": 0,
    "data": {},
    "dateCreated": "2018-11-06T21:20:08.033Z",
    "dateReleased": null,
    "deployCount": 0,
    "firstEvent": null,
    "lastCommit": null,
    "lastDeploy": null,
    "lastEvent": null,
    "newGroups": 0,
    "owner": null,
    "projects": [
      {
        "name": "Pump Station",
        "slug": "pump-station"
      }
    ],
    "ref": "6ba09a7c53235ee8a8fa5ee4c1ca8ca886e7fdbb",
    "shortVersion": "2.0rc2",
    "url": null,
    "version": "2.0rc2"
  },
  {
    "id": 1,
    "authors": [],
    "commitCount": 0,
    "data": {},
    "dateCreated": "2018-11-06T21:19:58.559Z",
    "dateReleased": null,
    "deployCount": 0,
    "firstEvent": "2018-11-06T21:19:58.639Z",
    "lastCommit": null,
    "lastDeploy": null,
    "lastEvent": "2018-11-06T21:19:58.639Z",
    "newGroups": 0,
    "owner": null,
    "projects": [
      {
        "name": "Prime Mover",
        "slug": "prime-mover"
      }
    ],
    "ref": null,
    "shortVersion": "2b6af31",
    "url": null,
    "version": "2b6af31b2edccc73a629108b17344dfe20858780"
  }
]
```

<h3 id="list-an-organization's-releases-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Permission Denied|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-releases-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Create a New Release for an Organization

<a id="opIdCreate a New Release for an Organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/releases/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/releases/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "version": "string",
  "ref": "string",
  "url": "string",
  "projects": [
    "string"
  ],
  "dateReleased": "2019-08-24T14:15:22Z",
  "commits": [
    {
      "patch_set": [
        {
          "path": "string",
          "type": "A"
        }
      ],
      "repository": "string",
      "author_name": "string",
      "author_email": "string",
      "timestamp": "2019-08-24T14:15:22Z",
      "message": "string",
      "id": "string"
    }
  ],
  "refs": [
    {
      "repository": "string",
      "commit": "string",
      "previousCommit": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/releases/`

Create a new release for the given organization.  Releases are used by
Sentry to improve its error reporting abilities by correlating
first seen events with the release that might have introduced the
problem.
Releases are also necessary for source maps and other debug features
that require manual upload for functioning well.

> Body parameter

```json
{
  "version": "string",
  "ref": "string",
  "url": "string",
  "projects": [
    "string"
  ],
  "dateReleased": "2019-08-24T14:15:22Z",
  "commits": [
    {
      "patch_set": [
        {
          "path": "string",
          "type": "A"
        }
      ],
      "repository": "string",
      "author_name": "string",
      "author_email": "string",
      "timestamp": "2019-08-24T14:15:22Z",
      "message": "string",
      "id": "string"
    }
  ],
  "refs": [
    {
      "repository": "string",
      "commit": "string",
      "previousCommit": "string"
    }
  ]
}
```

<h3 id="create-a-new-release-for-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|body|body|object|false|none|
|» version|body|string|true|A version identifier for this release. Can be a version number, a commit hash, etc.|
|» ref|body|string|false|An optional commit reference. This is useful if a tagged version has been provided.|
|» url|body|string|false|A URL that points to the release. This can be the path to an online interface to the source code for instance|
|» projects|body|[string]|true|A list of project slugs that are involved in this release.|
|» dateReleased|body|string(date-time)|false|An optional date that indicates when the release went live. If not provided the current time is assumed.|
|» commits|body|[object]|false|An optional list of commit data to be associated with the release. Commits must include parameters `id` (the SHA of the commit), and can optionally include `repository`, `message`, `patch_set`, `author_name`, `author_email`, and `timestamp`.|
|»» patch_set|body|[object]|false|A list of the files that have been changed in the commit. Specifying the patch_set is necessary to power suspect commits and suggested assignees.|
|»»» path|body|string|true|The path to the file. Both forward and backward slashes are supported.|
|»»» type|body|string|true|The type of change that happened in the commit.|
|»» repository|body|string|false|The full name of the repository the commit belongs to. If this field is not given Sentry will generate a name in the form: u'organization-<organization_id>' (i.e. if the organization id is 123, then the generated repository name will be u'organization-123).|
|»» author_name|body|string|false|The name of the commit author.|
|»» author_email|body|string|false|The email of the commit author. The commit author's email is required to enable the suggested assignee feature.|
|»» timestamp|body|string(date-time)|false|The commit timestamp is used to sort the commits given. If a timestamp is not included, the commits will remain sorted in the order given.|
|»» message|body|string|false|The commit message.|
|»» id|body|string|false|The commit ID (the commit SHA).|
|» refs|body|[object]|false|An optional way to indicate the start and end commits for each repository included in a release. Head commits must include parameters `repository` and `commit` (the HEAD sha). They can optionally include `previousCommit` (the sha of the HEAD of the previous release), which should be specified if this is the first time you've sent commit data. `commit` may contain a range in the form of `previousCommit..commit`.|
|»» repository|body|string|false|The full name of the repository the commit belongs to.|
|»» commit|body|string|false|The current release's commit.|
|»» previousCommit|body|string|false|The previous release's commit.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»»» type|A|
|»»» type|M|
|»»» type|D|

> Example responses

> 201 Response

```json
{
  "id": 2,
  "authors": [],
  "commitCount": 0,
  "data": {},
  "dateCreated": "2019-01-03T00:12:55.109Z",
  "dateReleased": null,
  "deployCount": 0,
  "firstEvent": null,
  "lastCommit": null,
  "lastDeploy": null,
  "lastEvent": null,
  "newGroups": 0,
  "owner": null,
  "projects": [
    {
      "name": "Pump Station",
      "slug": "pump-station"
    }
  ],
  "ref": "6ba09a7c53235ee8a8fa5ee4c1ca8ca886e7fdbb",
  "shortVersion": "2.0rc2",
  "url": null,
  "version": "2.0rc2"
}
```

<h3 id="create-a-new-release-for-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="create-a-new-release-for-an-organization-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Retrieve an Organization's Releases

<a id="opIdRetrieve an Organization's Releases"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/`

Return a release for a given organization.

<h3 id="retrieve-an-organization's-releases-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
{
  "id": 2,
  "authors": [],
  "commitCount": 0,
  "data": {},
  "dateCreated": "2018-11-06T21:20:08.033Z",
  "dateReleased": null,
  "deployCount": 0,
  "firstEvent": null,
  "lastCommit": null,
  "lastDeploy": null,
  "lastEvent": null,
  "newGroups": 0,
  "owner": null,
  "projects": [
    {
      "name": "Pump Station",
      "slug": "pump-station"
    }
  ],
  "ref": "6ba09a7c53235ee8a8fa5ee4c1ca8ca886e7fdbb",
  "shortVersion": "2.0rc2",
  "url": null,
  "version": "2.0rc2"
}
```

<h3 id="retrieve-an-organization's-releases-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-an-organization's-releases-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Update an Organization's Release

<a id="opIdUpdate an Organization's Release"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "ref": "string",
  "url": "string",
  "dateReleased": "2019-08-24T14:15:22Z",
  "commits": [
    {}
  ],
  "refs": [
    {}
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/organizations/{organization_slug}/releases/{version}/`

Update a release for a given organization.

> Body parameter

```json
{
  "ref": "string",
  "url": "string",
  "dateReleased": "2019-08-24T14:15:22Z",
  "commits": [
    {}
  ],
  "refs": [
    {}
  ]
}
```

<h3 id="update-an-organization's-release-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|
|body|body|object|false|none|
|» ref|body|string|false|An optional commit reference. This is useful if a tagged version has been provided.|
|» url|body|string|false|A URL that points to the release. This can be the path to an online interface to the source code for instance.|
|» dateReleased|body|string(date-time)|false|An optional date that indicates when the release went live. If not provided the current time is assumed.|
|» commits|body|[object]|false|An optional list of commit data to be associated with the release. Commits must include parameters `id` (the sha of the commit), and can optionally include `repository`, `message`, `author_name`, `author_email`, and `timestamp`.|
|» refs|body|[object]|false|An optional way to indicate the start and end commits for each repository included in a release. Head commits must include parameters `repository` and `commit` (the HEAD sha). They can optionally include `previousCommit` (the sha of the HEAD of the previous release), which should be specified if this is the first time you've sent commit data.|

> Example responses

> 200 Response

```json
{
  "id": 2,
  "authors": [],
  "commitCount": 0,
  "data": {},
  "dateCreated": "2019-01-03T00:12:55.109Z",
  "dateReleased": null,
  "deployCount": 0,
  "firstEvent": null,
  "lastCommit": null,
  "lastDeploy": null,
  "lastEvent": null,
  "newGroups": 0,
  "owner": null,
  "projects": [
    {
      "name": "Pump Station",
      "slug": "pump-station"
    }
  ],
  "ref": "6ba09a7c53235ee8a8fa5ee4c1ca8ca886e7fdbb",
  "shortVersion": "2.0rc2",
  "url": null,
  "version": "2.0rc2"
}
```

<h3 id="update-an-organization's-release-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-an-organization's-release-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|integer|false|none|none|
|» authors|[object]|true|none|none|
|» commitCount|integer(int64)|true|none|none|
|» data|object|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» dateReleased|string(date-time)¦null|true|none|none|
|» deployCount|integer(int64)|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» lastCommit|object¦null|true|none|none|
|» lastDeploy|object¦null|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|object|false|none|none|
|»»» environment|string|true|none|none|
|»»» name|string¦null|true|none|none|
|»»» dateStarted|string(date-time)¦null|true|none|none|
|»»» dateFinished|string(date-time)|true|none|none|
|»»» url|string¦null|true|none|none|
|»»» id|string|true|none|none|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|string¦null|false|none|none|

*not*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|any|false|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|string|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|number|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|boolean|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[any]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» lastEvent|string(date-time)¦null|true|none|none|
|» newGroups|integer(int64)|true|none|none|
|» owner|object¦null|true|none|none|
|» projects|[object]|true|none|none|
|»» name|string|false|none|none|
|»» slug|string|false|none|none|
|» ref|string¦null|true|none|none|
|» shortVersion|string|true|none|none|
|» version|string|true|none|none|
|» url|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Delete an Organization's Release

<a id="opIdDelete an Organization's Release"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/releases/{version}/`

Delete a release for a given organization.

<h3 id="delete-an-organization's-release-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|

<h3 id="delete-an-organization's-release-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List an Organization's Release Files

<a id="opIdList an Organization's Release Files"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/files/`

Return a list of files for a given release.

<h3 id="list-an-organization's-release-files-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:20:22.894Z",
    "dist": null,
    "headers": {
      "Content-Type": "text/plain; encoding=utf-8"
    },
    "id": "3",
    "name": "/demo/goodbye.txt",
    "sha1": "94d6b21e962a9fc65889617ec1f17a1e2fe11b65",
    "size": 15
  }
]
```

<h3 id="list-an-organization's-release-files-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-release-files-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Upload a New Organization Release File

<a id="opIdUpload a New Organization Release File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "file": "string",
  "dist": "string",
  "header": "string"
}';
const headers = {
  'Content-Type':'multipart/form-data',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/releases/{version}/files/`

Upload a new organization release file.

> Body parameter

```yaml
name: string
file: string
dist: string
header: string

```

<h3 id="upload-a-new-organization-release-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|
|body|body|object|false|none|
|» name|body|string|false|The name (full path) of the file.|
|» file|body|string(binary)|true|The multipart encoded file.|
|» dist|body|string|false|The name of the dist.|
|» header|body|string|false|This parameter can be supplied multiple times to attach headers to the file. Each header is a string in the format `key:value`. For instance it can be used to define a content type.|

<h3 id="upload-a-new-organization-release-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List a Project's Release Files

<a id="opIdList a Project's Release Files"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/`

Return a list of files for a given release.

<h3 id="list-a-project's-release-files-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:20:22.894Z",
    "dist": null,
    "headers": {
      "Content-Type": "text/plain; encoding=utf-8"
    },
    "id": "3",
    "name": "/demo/goodbye.txt",
    "sha1": "94d6b21e962a9fc65889617ec1f17a1e2fe11b65",
    "size": 15
  }
]
```

<h3 id="list-a-project's-release-files-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-a-project's-release-files-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Upload a New Project Release File

<a id="opIdUpload a New Project Release File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "file": "string",
  "dist": "string",
  "header": "string"
}';
const headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/`

Upload a new project release file.

> Body parameter

```yaml
name: string
file: string
dist: string
header: string

```

<h3 id="upload-a-new-project-release-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|
|body|body|object|false|none|
|» name|body|string|false|The name (full path) of the file.|
|» file|body|string(binary)|true|The multipart encoded file.|
|» dist|body|string|false|The name of the dist.|
|» header|body|string|false|This parameter can be supplied multiple times to attach headers to the file. Each header is a string in the format `key:value`. For instance it can be used to define a content type.|

> Example responses

> 201 Response

```json
{
  "dateCreated": "2018-11-06T21:20:22.894Z",
  "dist": null,
  "headers": {
    "Content-Type": "text/plain; encoding=utf-8"
  },
  "id": "3",
  "name": "/demo/goodbye.txt",
  "sha1": "94d6b21e962a9fc65889617ec1f17a1e2fe11b65",
  "size": 15
}
```

<h3 id="upload-a-new-project-release-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="upload-a-new-project-release-file-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Retrieve an Organization Release's File

<a id="opIdRetrieve an Organization Release's File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/`

Retrieve a file for a given release.

<h3 id="retrieve-an-organization-release's-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to retrieve.|
|download|query|boolean|false|If this is set to true, then the response payload will be the raw file contents. Otherwise, the response will be the file metadata as JSON.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:19.150Z",
  "dist": null,
  "headers": {
    "Content-Type": "text/plain; encoding=utf-8"
  },
  "id": "1",
  "name": "/demo/message-for-you.txt",
  "sha1": "2ef7bde608ce5404e97d5f042f95f89f1c232871",
  "size": 12
}
```

<h3 id="retrieve-an-organization-release's-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-an-organization-release's-file-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Update an Organization Release File

<a id="opIdUpdate an Organization Release File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "dist": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/`

Update an organization release file.

> Body parameter

```json
{
  "name": "string",
  "dist": "string"
}
```

<h3 id="update-an-organization-release-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to retrieve.|
|body|body|object|false|none|
|» name|body|string|false|The new name (full path) of the file.|
|» dist|body|string|false|The new name of the dist.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:22.894Z",
  "dist": null,
  "headers": {
    "Content-Type": "text/plain; encoding=utf-8"
  },
  "id": "3",
  "name": "/demo/goodbye.txt",
  "sha1": "94d6b21e962a9fc65889617ec1f17a1e2fe11b65",
  "size": 15
}
```

<h3 id="update-an-organization-release-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-an-organization-release-file-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Delete an Organization Release's File

<a id="opIdDelete an Organization Release's File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/releases/{version}/files/{file_id}/`

Delete a file for a given release.

<h3 id="delete-an-organization-release's-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to delete.|

<h3 id="delete-an-organization-release's-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Retrieve a Project Release's File

<a id="opIdRetrieve a Project Release's File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/`

Retrieve a file for a given release.

<h3 id="retrieve-a-project-release's-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to retrieve.|
|download|query|boolean|false|If this is set to true, then the response payload will be the raw file contents. Otherwise, the response will be the file metadata as JSON.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:19.150Z",
  "dist": null,
  "headers": {
    "Content-Type": "text/plain; encoding=utf-8"
  },
  "id": "1",
  "name": "/demo/message-for-you.txt",
  "sha1": "2ef7bde608ce5404e97d5f042f95f89f1c232871",
  "size": 12
}
```

<h3 id="retrieve-a-project-release's-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-a-project-release's-file-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Update a Project Release File

<a id="opIdUpdate a Project Release File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "name": "string",
  "dist": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/`

Update a project release file.

> Body parameter

```json
{
  "name": "string",
  "dist": "string"
}
```

<h3 id="update-a-project-release-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to retrieve.|
|body|body|object|false|none|
|» name|body|string|false|The new name (full path) of the file.|
|» dist|body|string|false|The new name of the dist.|

> Example responses

> 200 Response

```json
{
  "dateCreated": "2018-11-06T21:20:22.894Z",
  "dist": null,
  "headers": {
    "Content-Type": "text/plain; encoding=utf-8"
  },
  "id": "3",
  "name": "/demo/goodbye.txt",
  "sha1": "94d6b21e962a9fc65889617ec1f17a1e2fe11b65",
  "size": 15
}
```

<h3 id="update-a-project-release-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-a-project-release-file-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» sha1|string|true|none|none|
|» dist|string¦null|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» headers|object|true|none|none|
|»» Content-Type|string|false|none|none|
|» id|string|true|none|none|
|» size|integer|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Delete a Project Release's File

<a id="opIdDelete a Project Release's File"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/files/{file_id}/`

Delete a file for a given release.

<h3 id="delete-a-project-release's-file-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|
|file_id|path|string|true|The ID of the file to delete.|

<h3 id="delete-a-project-release's-file-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List an Organization Release's Commits

<a id="opIdList an Organization Release's Commits"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commits/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commits/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commits/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/commits/`

List an organization release's commits.

<h3 id="list-an-organization-release's-commits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "id": "acbafc639127fd89d10f474520104517ff1d709e",
    "message": "Initial commit from Create Next App"
  }
]
```

<h3 id="list-an-organization-release's-commits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization-release's-commits-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string(date-time)|true|none|none|
|» id|string|true|none|none|
|» message|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List a Project Release's Commits

<a id="opIdList a Project Release's Commits"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/commits/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/commits/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/commits/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/commits/`

List a project release's commits.

<h3 id="list-a-project-release's-commits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|project_slug|path|string|true|The slug of the project the release belongs to.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
[
  {
    "dateCreated": "2018-11-06T21:19:58.536Z",
    "id": "acbafc639127fd89d10f474520104517ff1d709e",
    "message": "Initial commit from Create Next App"
  }
]
```

<h3 id="list-a-project-release's-commits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-a-project-release's-commits-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» dateCreated|string(date-time)|true|none|none|
|» id|string|true|none|none|
|» message|string¦null|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Retrieve Files Changed in a Release's Commits

<a id="opIdRetrieve Files Changed in a Release's Commits"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commitfiles/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commitfiles/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/commitfiles/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/commitfiles/`

Retrieve files changed in a release's commits

<h3 id="retrieve-files-changed-in-a-release's-commits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the release belongs to.|
|version|path|string|true|The version identifier of the release.|

<h3 id="retrieve-files-changed-in-a-release's-commits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List Issues to be Resolved in a Particular Release

<a id="opIdList Issues to be Resolved in a Particular Release"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/resolved/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/resolved/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/projects/{organization_slug}/{project_slug}/releases/{version}/resolved/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/projects/{organization_slug}/{project_slug}/releases/{version}/resolved/`

List issues to be resolved in a particular release.

<h3 id="list-issues-to-be-resolved-in-a-particular-release-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|project_slug|path|string|true|The slug of the project.|
|version|path|string|true|The version identifier of the release.|

<h3 id="list-issues-to-be-resolved-in-a-particular-release-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## List a Release's Deploys

<a id="opIdList a Release's Deploys"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/releases/{version}/deploys/`

Return a list of deploys for a given release.

<h3 id="list-a-release's-deploys-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|

> Example responses

> 200 Response

```json
[
  {
    "environment": "prod",
    "name": null,
    "url": null,
    "dateStarted": null,
    "dateFinished": "2020-08-31T19:40:38.651670Z",
    "id": "1234567"
  }
]
```

<h3 id="list-a-release's-deploys-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-a-release's-deploys-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» environment|string|true|none|none|
|» name|string¦null|true|none|none|
|» dateStarted|string(date-time)¦null|true|none|none|
|» dateFinished|string(date-time)|true|none|none|
|» url|string¦null|true|none|none|
|» id|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

## Create a New Deploy for an Organization

<a id="opIdCreate a New Deploy for an Organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "environment": "string",
  "url": "string",
  "name": "string",
  "projects": [
    "string"
  ],
  "dateStarted": "2019-08-24T14:15:22Z",
  "dateFinished": "2019-08-24T14:15:22Z"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/releases/{version}/deploys/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/releases/{version}/deploys/`

Create a deploy.

> Body parameter

```json
{
  "environment": "string",
  "url": "string",
  "name": "string",
  "projects": [
    "string"
  ],
  "dateStarted": "2019-08-24T14:15:22Z",
  "dateFinished": "2019-08-24T14:15:22Z"
}
```

<h3 id="create-a-new-deploy-for-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|version|path|string|true|The version identifier of the release.|
|body|body|object|false|none|
|» environment|body|string|true|The environment you're deploying to.|
|» url|body|string|false|The optional URL that points to the deploy.|
|» name|body|string|false|The optional name of the deploy.|
|» projects|body|[string]|false|The optional list of projects to deploy.|
|» dateStarted|body|string(date-time)|false|An optional date that indicates when the deploy started.|
|» dateFinished|body|string(date-time)|false|An optional date that indicates when the deploy ended. If not provided, the current time is used.|

> Example responses

> 201 Response

```json
{
  "environment": "prod",
  "name": null,
  "url": null,
  "dateStarted": null,
  "dateFinished": "2020-08-31T19:40:38.651670Z",
  "id": "1234567"
}
```

<h3 id="create-a-new-deploy-for-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|208|Unknown|Already Reported|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="create-a-new-deploy-for-an-organization-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» environment|string|true|none|none|
|» name|string¦null|true|none|none|
|» dateStarted|string(date-time)¦null|true|none|none|
|» dateFinished|string(date-time)|true|none|none|
|» url|string¦null|true|none|none|
|» id|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:releases )
</aside>

<h1 id="api-reference-integration">Integration</h1>

Endpoints for the integration platform

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/integration-platform/&template=api_error_template.md">Found an error? Let us know.</a>

## List an Organization's Integration Platform Installations

<a id="opIdList an Organization's Integration Platform Installations"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/sentry-app-installations/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/sentry-app-installations/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/sentry-app-installations/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/sentry-app-installations/`

Return a list of integration platform installations for a given organization.

<h3 id="list-an-organization's-integration-platform-installations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The organization short name.|

> Example responses

> 200 Response

```json
[
  {
    "app": {
      "uuid": "a9988ad6-meow-4905-bb93-f7cbf4c96bbb",
      "slug": "cat-75c19a"
    },
    "organization": {
      "slug": "sentry"
    },
    "uuid": "01635075-m30w-4f96-8fc8-ff9680780a13",
    "status": "installed"
  }
]
```

<h3 id="list-an-organization's-integration-platform-installations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-integration-platform-installations-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» app|object|true|none|none|
|»» uuid|string|true|none|none|
|»» slug|string|true|none|none|
|» organization|object|true|none|none|
|»» slug|string|true|none|none|
|» uuid|string|true|none|none|
|» status|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:read org:integrations )
</aside>

## Create an External Issue

<a id="opIdCreate an External Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "issueId": 0,
  "webUrl": "string",
  "project": "string",
  "identifier": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/sentry-app-installations/{uuid}/external-issues/`

Create an external issue from an integration platform integration.

> Body parameter

```json
{
  "issueId": 0,
  "webUrl": "string",
  "project": "string",
  "identifier": "string"
}
```

<h3 id="create-an-external-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|uuid|path|string|true|The uuid of the integration platform integration.|
|body|body|object|true|none|
|» issueId|body|integer|true|The ID of the Sentry issue to link the external issue to.|
|» webUrl|body|string|true|The URL of the external service to link the issue to.|
|» project|body|string|true|The external service's project.|
|» identifier|body|string|true|A unique identifier of the external issue.|

> Example responses

> 200 Response

```json
{
  "id": "1",
  "issueId": "1",
  "serviceType": "testing",
  "displayName": "ExternalProj#issue-1",
  "webUrl": "https://somerandom.io/project/issue-id"
}
```

<h3 id="create-an-external-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="create-an-external-issue-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» issueId|string|true|none|none|
|» serviceType|string|true|none|none|
|» displayName|string|true|none|none|
|» webUrl|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:write )
</aside>

## Delete an External Issue

<a id="opIdDelete an External Issue"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/{external_issue_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/{external_issue_id}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/sentry-app-installations/{uuid}/external-issues/{external_issue_id}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/sentry-app-installations/{uuid}/external-issues/{external_issue_id}/`

Delete an external issue.

<h3 id="delete-an-external-issue-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|uuid|path|string|true|The uuid of the integration platform integration.|
|external_issue_id|path|string|true|The id of the external issue.|

<h3 id="delete-an-external-issue-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|External issue not found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: event:admin )
</aside>

<h1 id="api-reference-scim">SCIM</h1>

System for Cross-Domain Identity Management ([SCIM](http://www.simplecloud.info/)) is a standard implemented by Identity Providers and applications in order to facilitate federated identity management. Through these APIs you can add and delete members as well as teams. Sentry SaaS customers must be on a Business Plan with SAML2 Enabled. SCIM uses a bearer token for authentication that is created when SCIM is enabled. For how to enable SCIM, see our docs [here](/product/accounts/sso/#scim-provisioning).
 Sentry's SCIM API does not currently support syncing passwords, or setting any User attributes other than `active`.

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/integration-platform/&template=api_error_template.md">Found an error? Let us know.</a>

## List an Organization's Paginated Teams

<a id="opIdList an Organization's Paginated Teams"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/scim/v2/Groups`

Returns a paginated list of teams bound to a organization with a SCIM Groups GET Request.
- Note that the members field will only contain up to 10000 members.

<h3 id="list-an-organization's-paginated-teams-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|startIndex|query|integer|false|SCIM 1-offset based index for pagination.|
|filter|query|string|false|A SCIM filter expression. The only operator currently supported is `eq`.|
|count|query|integer|false|The maximum number of results the query should return, maximum of 100.|
|excludedAttributes|query|string|false|Fields that should be left off of return values. Right now the only supported field for this query is `members`.|

> Example responses

> 200 Response

```json
{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:ListResponse"
  ],
  "totalResults": 1,
  "startIndex": 1,
  "itemsPerPage": 1,
  "Resources": [
    {
      "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:Group"
      ],
      "id": "23232",
      "displayName": "test-scimv2",
      "members": [],
      "meta": {
        "resourceType": "Group"
      }
    }
  ]
}
```

<h3 id="list-an-organization's-paginated-teams-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Permission Denied|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-paginated-teams-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» schemas|[string]|false|none|none|
|» totalResults|integer|true|none|none|
|» itemsPerPage|integer|true|none|none|
|» startIndex|integer|true|none|none|
|» Resources|[object]|true|none|none|
|»» schemas|[string]|true|none|none|
|»» id|string|true|none|none|
|»» displayName|string|true|none|none|
|»» members|[object]|true|none|none|
|»»» value|string|true|none|none|
|»»» display|string|true|none|none|
|»» meta|object|true|none|none|
|»»» resourceType|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:read )
</aside>

## Provision a New Team

<a id="opIdProvision a New Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "schemas": [
    "string"
  ],
  "displayName": "string",
  "members": [
    {
      "value": "string",
      "display": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/scim/v2/Groups`

Create a new team bound to an organization via a SCIM Groups POST Request. Note that teams are always created with an empty member set. The endpoint will also do a normalization of uppercase / spaces to lowercase and dashes.

> Body parameter

```json
{
  "schemas": [
    "string"
  ],
  "displayName": "string",
  "members": [
    {
      "value": "string",
      "display": "string"
    }
  ]
}
```

<h3 id="provision-a-new-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization.|
|body|body|object|true|none|
|» schemas|body|[string]|true|none|
|» displayName|body|string|true|none|
|» members|body|[object]|false|none|
|»» value|body|string|true|none|
|»» display|body|string|true|none|

> Example responses

> 201 Response

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:Group"
  ],
  "displayName": "Test SCIMv2",
  "members": [],
  "meta": {
    "resourceType": "Group"
  },
  "id": "123"
}
```

<h3 id="provision-a-new-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Success|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad input|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Team slug already exists|None|

<h3 id="provision-a-new-team-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» displayName|string|true|none|none|
|» members|[object]|true|none|none|
|»» value|string|true|none|none|
|»» display|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:write )
</aside>

## Query an Individual Team

<a id="opIdQuery an Individual Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}`

Query an individual team with a SCIM Group GET Request.
- Note that the members field will only contain up to 10000 members.

<h3 id="query-an-individual-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|team_id|path|integer|true|The id of the team you'd like to query / update.|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|

> Example responses

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:Group"
  ],
  "id": "23232",
  "displayName": "test-scimv2",
  "members": [],
  "meta": {
    "resourceType": "Group"
  }
}
```

<h3 id="query-an-individual-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="query-an-individual-team-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» displayName|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|true|none|none|
|» members|[object]|false|none|none|
|»» value|string|true|none|none|
|»» display|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:admin team:read team:write )
</aside>

## Update a Team's Attributes

<a id="opIdUpdate a Team's Attributes"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "path": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PATCH /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}`

Update a team's attributes with a SCIM Group PATCH Request. Valid operations are:

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

> Body parameter

```json
{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "path": "string"
    }
  ]
}
```

<h3 id="update-a-team's-attributes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|team_id|path|integer|true|The id of the team you'd like to query / update.|
|body|body|object|true|none|
|» schemas|body|[string]|true|none|
|» Operations|body|[object]|true|none|
|»» op|body|string|true|none|
|»» value|body|[any]|true|none|
|»» path|body|string|false|none|

<h3 id="update-a-team's-attributes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:admin team:write )
</aside>

## Delete an Individual Team

<a id="opIdDelete an Individual Team"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/scim/v2/Groups/{team_id}`

Delete a team with a SCIM Group DELETE Request.

<h3 id="delete-an-individual-team-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|team_id|path|integer|true|The id of the team you'd like to query / update.|

<h3 id="delete-an-individual-team-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: team:admin )
</aside>

## List an Organization's Members

<a id="opIdList an Organization's Members"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/scim/v2/Users`

Returns a paginated list of members bound to a organization with a SCIM Users GET Request.

<h3 id="list-an-organization's-members-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|startIndex|query|integer|false|SCIM 1-offset based index for pagination.|
|count|query|integer|false|The maximum number of results the query should return, maximum of 100.|
|filter|query|string|false|A SCIM filter expression. The only operator currently supported is `eq`.|
|excludedAttributes|query|array[string]|false|Fields that should be left off of return values. Right now the only supported field for this query is members.|

> Example responses

```json
{
  "schemas": [
    "urn:ietf:params:scim:api:messages:2.0:ListResponse"
  ],
  "totalResults": 1,
  "startIndex": 1,
  "itemsPerPage": 1,
  "Resources": [
    {
      "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:User"
      ],
      "id": "102",
      "userName": "test.user@okta.local",
      "emails": [
        {
          "primary": true,
          "value": "test.user@okta.local",
          "type": "work"
        }
      ],
      "name": {
        "familyName": "N/A",
        "givenName": "N/A"
      },
      "active": true,
      "meta": {
        "resourceType": "User"
      },
      "sentryOrgRole": "member"
    }
  ]
}
```

<h3 id="list-an-organization's-members-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="list-an-organization's-members-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» schemas|[string]|true|none|none|
|» totalResults|integer|true|none|none|
|» startIndex|integer|true|none|none|
|» itemsPerPage|integer|true|none|none|
|» Resources|[object]|true|none|none|
|»» active|boolean|false|none|none|
|»» schemas|[string]|true|none|none|
|»» id|string|true|none|none|
|»» userName|string|true|none|none|
|»» name|object|true|none|none|
|»»» givenName|string|true|none|none|
|»»» familyName|string|true|none|none|
|»» emails|[object]|true|none|none|
|»»» primary|boolean|true|none|none|
|»»» value|string|true|none|none|
|»»» type|string|true|none|none|
|»» meta|object|true|none|none|
|»»» resourceType|string|true|none|none|
|»» sentryOrgRole|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:read member:write )
</aside>

## Provision a New Organization Member

<a id="opIdProvision a New Organization Member"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "userName": "user@example.com",
  "sentryOrgRole": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/scim/v2/Users`

Create a new Organization Member via a SCIM Users POST Request.
- `userName` should be set to the SAML field used for email, and active should be set to `true`.
- `sentryOrgRole` can only be `admin`, `manager`, `billing`, or `member`.
- Sentry's SCIM API doesn't currently support setting users to inactive,
and the member will be deleted if active is set to `false`.
- The API also does not support setting secondary emails.

> Body parameter

```json
{
  "userName": "user@example.com",
  "sentryOrgRole": "string"
}
```

<h3 id="provision-a-new-organization-member-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|body|body|object|true|none|
|» userName|body|string(email)|true|none|
|» sentryOrgRole|body|string|false|none|

> Example responses

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "id": "242",
  "userName": "test.user@okta.local",
  "emails": [
    {
      "primary": true,
      "value": "test.user@okta.local",
      "type": "work"
    }
  ],
  "active": true,
  "name": {
    "familyName": "N/A",
    "givenName": "N/A"
  },
  "meta": {
    "resourceType": "User"
  },
  "sentryOrgRole": "member"
}
```

<h3 id="provision-a-new-organization-member-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="provision-a-new-organization-member-responseschema">Response Schema</h3>

Status Code **201**

*Conforming to the SCIM RFC, this represents a Sentry Org Member
as a SCIM user object.*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» active|boolean|false|none|none|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» userName|string|true|none|none|
|» name|object|true|none|none|
|»» givenName|string|true|none|none|
|»» familyName|string|true|none|none|
|» emails|[object]|true|none|none|
|»» primary|boolean|true|none|none|
|»» value|string|true|none|none|
|»» type|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|true|none|none|
|» sentryOrgRole|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:write )
</aside>

## Query an Individual Organization Member

<a id="opIdQuery an Individual Organization Member"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}`

Query an individual organization member with a SCIM User GET Request.
- The `name` object will contain fields `firstName` and `lastName` with the values of `N/A`.
Sentry's SCIM API does not currently support these fields but returns them for compatibility purposes.

<h3 id="query-an-individual-organization-member-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|member_id|path|integer|true|The id of the member you'd like to query.|

> Example responses

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "id": "102",
  "userName": "test.user@okta.local",
  "emails": [
    {
      "primary": true,
      "value": "test.user@okta.local",
      "type": "work"
    }
  ],
  "name": {
    "familyName": "N/A",
    "givenName": "N/A"
  },
  "active": true,
  "meta": {
    "resourceType": "User"
  },
  "sentryOrgRole": "member"
}
```

<h3 id="query-an-individual-organization-member-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="query-an-individual-organization-member-responseschema">Response Schema</h3>

Status Code **200**

*Conforming to the SCIM RFC, this represents a Sentry Org Member
as a SCIM user object.*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» active|boolean|false|none|none|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» userName|string|true|none|none|
|» name|object|true|none|none|
|»» givenName|string|true|none|none|
|»» familyName|string|true|none|none|
|» emails|[object]|true|none|none|
|»» primary|boolean|true|none|none|
|»» value|string|true|none|none|
|»» type|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|true|none|none|
|» sentryOrgRole|string|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:read member:write )
</aside>

## Update an Organization Member's Attributes

<a id="opIdUpdate an Organization Member's Attributes"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.patch 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.patch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "value": null,
      "path": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PATCH /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}`

Update an organization member's attributes with a SCIM PATCH Request.
The only supported attribute is `active`. After setting `active` to false
Sentry will permanently delete the Organization Member.

> Body parameter

```json
{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "value": null,
      "path": "string"
    }
  ]
}
```

<h3 id="update-an-organization-member's-attributes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|member_id|path|integer|true|The id of the member you'd like to query.|
|body|body|object|true|none|
|» schemas|body|[string]|false|none|
|» Operations|body|[object]|true|none|
|»» op|body|string|true|none|
|»» value|body|any|true|none|
|»» path|body|string|false|none|

<h3 id="update-an-organization-member's-attributes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin member:write )
</aside>

## Delete an Organization Member via SCIM

<a id="opIdDelete an Organization Member via SCIM"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/scim/v2/Users/{member_id}`

Delete an organization member with a SCIM User DELETE Request.

<h3 id="delete-an-organization-member-via-scim-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|member_id|path|integer|true|The id of the member you'd like to query.|

<h3 id="delete-an-organization-member-via-scim-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Success|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: member:admin )
</aside>

<h1 id="api-reference-discover">Discover</h1>

Discover and Performance allow you to slice and dice your Error and Transaction events

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/integration-platform/&template=api_error_template.md">Found an error? Let us know.</a>

## Query Discover Events in Table Format

<a id="opIdQuery Discover Events in Table Format"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/events/',
  params: {
  'field' => 'array[string]'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/events/', params={
  'field': [
  "string"
]
}, headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/events/?field=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/events/`

Retrieves discover (also known as events) data for a given organization.

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

<h3 id="query-discover-events-in-table-format-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end|query|string(date-time)|false|The end of the period of time for the query, expected in ISO-8601 format. For example `2001-12-14T12:34:56.7890`|
|environment|query|array[string]|false|The name of environments to filter by.|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|project|query|array[integer]|false|The ids of projects to filter by. `-1` means all available projects. If this parameter is omitted, the request will default to using 'My Projects'|
|start|query|string(date-time)|false|The start of the period of time for the query, expected in ISO-8601 format. For example `2001-12-14T12:34:56.7890`|
|statsPeriod|query|string|false|The period of time for the query, will override the start & end parameters, a number followed by one of:|
|field|query|array[string]|true|The fields, functions, or equations to request for the query. At most 20 fields can be selected per request. Each field can be one of the following types:|
|per_page|query|integer|false|Limit the number of rows to return in the result. Default and maximum allowed is 100.|
|query|query|string|false|The search filter for your query, read more about query syntax [here](https://docs.sentry.io/product/sentry-basics/search/)|
|sort|query|string|false|What to order the results of the query by. Must be something in the `field` list, excluding equations.|

#### Detailed descriptions

**statsPeriod**: The period of time for the query, will override the start & end parameters, a number followed by one of:
- `d` for days
- `h` for hours
- `m` for minutes
- `s` for seconds
- `w` for weeks

For example `24h`, to mean query data starting from 24 hours ago to now.

**field**: The fields, functions, or equations to request for the query. At most 20 fields can be selected per request. Each field can be one of the following types:
- A built-in key field. See possible fields in the [properties table](/product/sentry-basics/search/searchable-properties/#properties-table), under any field that is an event property
    - example: `field=transaction`
- A tag. Tags should use the `tag[]` formatting to avoid ambiguity with any fields
    - example: `field=tag[isEnterprise]`
- A function which will be in the format of `function_name(parameters,...)`. See possible functions in the [query builder documentation](/product/discover-queries/query-builder/#stacking-functions)
    - when a function is included, Discover will group by any tags or fields
    - example: `field=count_if(transaction.duration,greater,300)`
- An equation when prefixed with `equation|`. Read more about [equations here](https://docs.sentry.io/product/discover-queries/query-builder/query-equations/)
    - example: `field=equation|count_if(transaction.duration,greater,300) / count() * 100`

**query**: The search filter for your query, read more about query syntax [here](https://docs.sentry.io/product/sentry-basics/search/)

example: `query=(transaction:foo AND release:abc) OR (transaction:[bar,baz] AND release:def)`

> Example responses

```json
{
  "data": [
    {
      "count_if(transaction.duration,greater,300)": 5,
      "count()": 10,
      "equation|count_if(transaction.duration,greater,300) / count() * 100": 50,
      "transaction": "foo"
    },
    {
      "count_if(transaction.duration,greater,300)": 3,
      "count()": 20,
      "equation|count_if(transaction.duration,greater,300) / count() * 100": 15,
      "transaction": "bar"
    },
    {
      "count_if(transaction.duration,greater,300)": 8,
      "count()": 40,
      "equation|count_if(transaction.duration,greater,300) / count() * 100": 20,
      "transaction": "baz"
    }
  ],
  "meta": {
    "fields": {
      "count_if(transaction.duration,greater,300)": "integer",
      "count()": "integer",
      "equation|count_if(transaction.duration,greater,300) / count() * 100": "number",
      "transaction": "string"
    }
  }
}
```

<h3 id="query-discover-events-in-table-format-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid Query|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="query-discover-events-in-table-format-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[object]|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» meta|object|true|none|none|
|»» fields|object|true|none|none|
|»»» **additionalProperties**|string|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

<h1 id="api-reference-crons">Crons</h1>

Endpoints for Crons

<a href="https://github.com/getsentry/sentry-docs/issues/new/?title=API%20Documentation%20Error:%20/api/integration-platform/&template=api_error_template.md">Found an error? Let us know.</a>

## Retrieve check-ins for a monitor

<a id="opIdRetrieve check-ins for a monitor"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/`

Retrieve a list of check-ins for a monitor

<h3 id="retrieve-check-ins-for-a-monitor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|checkin_id|path|string(uuid)|true|The id of the check-in|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "environment": "string",
    "status": "string",
    "duration": 0,
    "dateCreated": "2019-08-24T14:15:22Z",
    "attachmentId": "string",
    "expectedTime": "2019-08-24T14:15:22Z",
    "monitorConfig": null
  }
]
```

<h3 id="retrieve-check-ins-for-a-monitor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-check-ins-for-a-monitor-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» environment|string|true|none|none|
|» status|string|true|none|none|
|» duration|integer|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» attachmentId|string|true|none|none|
|» expectedTime|string(date-time)|true|none|none|
|» monitorConfig|any|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Create a new check-in

<a id="opIdCreate a new check-in"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "status": "ok",
  "duration": 2147483647,
  "environment": "string",
  "monitor_config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/`

Creates a new check-in for a monitor.

If `status` is not present, it will be assumed that the check-in is starting, and be marked as `in_progress`.

To achieve a ping-like behavior, you can simply define `status` and optionally `duration` and
this check-in will be automatically marked as finished.

Note: If a DSN is utilized for authentication, the response will be limited in details.

> Body parameter

```json
{
  "status": "ok",
  "duration": 2147483647,
  "environment": "string",
  "monitor_config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  }
}
```

<h3 id="create-a-new-check-in-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|body|body|object|true|none|
|» status|body|string|true|none|
|» duration|body|integer¦null|false|none|
|» environment|body|string¦null|false|none|
|» monitor_config|body|object|false|none|
|»» schedule_type|body|string|false|Currently supports "crontab" or "interval"|
|»» schedule|body|any|true|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|»» checkin_margin|body|integer¦null|false|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|»» max_runtime|body|integer¦null|false|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|»» timezone|body|string|false|tz database style timezone string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|ok|
|» status|error|
|» status|in_progress|
|»» schedule_type|crontab|
|»» schedule_type|interval|
|»» timezone|Africa/Abidjan|
|»» timezone|Africa/Accra|
|»» timezone|Africa/Addis_Ababa|
|»» timezone|Africa/Algiers|
|»» timezone|Africa/Asmara|
|»» timezone|Africa/Asmera|
|»» timezone|Africa/Bamako|
|»» timezone|Africa/Bangui|
|»» timezone|Africa/Banjul|
|»» timezone|Africa/Bissau|
|»» timezone|Africa/Blantyre|
|»» timezone|Africa/Brazzaville|
|»» timezone|Africa/Bujumbura|
|»» timezone|Africa/Cairo|
|»» timezone|Africa/Casablanca|
|»» timezone|Africa/Ceuta|
|»» timezone|Africa/Conakry|
|»» timezone|Africa/Dakar|
|»» timezone|Africa/Dar_es_Salaam|
|»» timezone|Africa/Djibouti|
|»» timezone|Africa/Douala|
|»» timezone|Africa/El_Aaiun|
|»» timezone|Africa/Freetown|
|»» timezone|Africa/Gaborone|
|»» timezone|Africa/Harare|
|»» timezone|Africa/Johannesburg|
|»» timezone|Africa/Juba|
|»» timezone|Africa/Kampala|
|»» timezone|Africa/Khartoum|
|»» timezone|Africa/Kigali|
|»» timezone|Africa/Kinshasa|
|»» timezone|Africa/Lagos|
|»» timezone|Africa/Libreville|
|»» timezone|Africa/Lome|
|»» timezone|Africa/Luanda|
|»» timezone|Africa/Lubumbashi|
|»» timezone|Africa/Lusaka|
|»» timezone|Africa/Malabo|
|»» timezone|Africa/Maputo|
|»» timezone|Africa/Maseru|
|»» timezone|Africa/Mbabane|
|»» timezone|Africa/Mogadishu|
|»» timezone|Africa/Monrovia|
|»» timezone|Africa/Nairobi|
|»» timezone|Africa/Ndjamena|
|»» timezone|Africa/Niamey|
|»» timezone|Africa/Nouakchott|
|»» timezone|Africa/Ouagadougou|
|»» timezone|Africa/Porto-Novo|
|»» timezone|Africa/Sao_Tome|
|»» timezone|Africa/Timbuktu|
|»» timezone|Africa/Tripoli|
|»» timezone|Africa/Tunis|
|»» timezone|Africa/Windhoek|
|»» timezone|America/Adak|
|»» timezone|America/Anchorage|
|»» timezone|America/Anguilla|
|»» timezone|America/Antigua|
|»» timezone|America/Araguaina|
|»» timezone|America/Argentina/Buenos_Aires|
|»» timezone|America/Argentina/Catamarca|
|»» timezone|America/Argentina/ComodRivadavia|
|»» timezone|America/Argentina/Cordoba|
|»» timezone|America/Argentina/Jujuy|
|»» timezone|America/Argentina/La_Rioja|
|»» timezone|America/Argentina/Mendoza|
|»» timezone|America/Argentina/Rio_Gallegos|
|»» timezone|America/Argentina/Salta|
|»» timezone|America/Argentina/San_Juan|
|»» timezone|America/Argentina/San_Luis|
|»» timezone|America/Argentina/Tucuman|
|»» timezone|America/Argentina/Ushuaia|
|»» timezone|America/Aruba|
|»» timezone|America/Asuncion|
|»» timezone|America/Atikokan|
|»» timezone|America/Atka|
|»» timezone|America/Bahia|
|»» timezone|America/Bahia_Banderas|
|»» timezone|America/Barbados|
|»» timezone|America/Belem|
|»» timezone|America/Belize|
|»» timezone|America/Blanc-Sablon|
|»» timezone|America/Boa_Vista|
|»» timezone|America/Bogota|
|»» timezone|America/Boise|
|»» timezone|America/Buenos_Aires|
|»» timezone|America/Cambridge_Bay|
|»» timezone|America/Campo_Grande|
|»» timezone|America/Cancun|
|»» timezone|America/Caracas|
|»» timezone|America/Catamarca|
|»» timezone|America/Cayenne|
|»» timezone|America/Cayman|
|»» timezone|America/Chicago|
|»» timezone|America/Chihuahua|
|»» timezone|America/Coral_Harbour|
|»» timezone|America/Cordoba|
|»» timezone|America/Costa_Rica|
|»» timezone|America/Creston|
|»» timezone|America/Cuiaba|
|»» timezone|America/Curacao|
|»» timezone|America/Danmarkshavn|
|»» timezone|America/Dawson|
|»» timezone|America/Dawson_Creek|
|»» timezone|America/Denver|
|»» timezone|America/Detroit|
|»» timezone|America/Dominica|
|»» timezone|America/Edmonton|
|»» timezone|America/Eirunepe|
|»» timezone|America/El_Salvador|
|»» timezone|America/Ensenada|
|»» timezone|America/Fort_Nelson|
|»» timezone|America/Fort_Wayne|
|»» timezone|America/Fortaleza|
|»» timezone|America/Glace_Bay|
|»» timezone|America/Godthab|
|»» timezone|America/Goose_Bay|
|»» timezone|America/Grand_Turk|
|»» timezone|America/Grenada|
|»» timezone|America/Guadeloupe|
|»» timezone|America/Guatemala|
|»» timezone|America/Guayaquil|
|»» timezone|America/Guyana|
|»» timezone|America/Halifax|
|»» timezone|America/Havana|
|»» timezone|America/Hermosillo|
|»» timezone|America/Indiana/Indianapolis|
|»» timezone|America/Indiana/Knox|
|»» timezone|America/Indiana/Marengo|
|»» timezone|America/Indiana/Petersburg|
|»» timezone|America/Indiana/Tell_City|
|»» timezone|America/Indiana/Vevay|
|»» timezone|America/Indiana/Vincennes|
|»» timezone|America/Indiana/Winamac|
|»» timezone|America/Indianapolis|
|»» timezone|America/Inuvik|
|»» timezone|America/Iqaluit|
|»» timezone|America/Jamaica|
|»» timezone|America/Jujuy|
|»» timezone|America/Juneau|
|»» timezone|America/Kentucky/Louisville|
|»» timezone|America/Kentucky/Monticello|
|»» timezone|America/Knox_IN|
|»» timezone|America/Kralendijk|
|»» timezone|America/La_Paz|
|»» timezone|America/Lima|
|»» timezone|America/Los_Angeles|
|»» timezone|America/Louisville|
|»» timezone|America/Lower_Princes|
|»» timezone|America/Maceio|
|»» timezone|America/Managua|
|»» timezone|America/Manaus|
|»» timezone|America/Marigot|
|»» timezone|America/Martinique|
|»» timezone|America/Matamoros|
|»» timezone|America/Mazatlan|
|»» timezone|America/Mendoza|
|»» timezone|America/Menominee|
|»» timezone|America/Merida|
|»» timezone|America/Metlakatla|
|»» timezone|America/Mexico_City|
|»» timezone|America/Miquelon|
|»» timezone|America/Moncton|
|»» timezone|America/Monterrey|
|»» timezone|America/Montevideo|
|»» timezone|America/Montreal|
|»» timezone|America/Montserrat|
|»» timezone|America/Nassau|
|»» timezone|America/New_York|
|»» timezone|America/Nipigon|
|»» timezone|America/Nome|
|»» timezone|America/Noronha|
|»» timezone|America/North_Dakota/Beulah|
|»» timezone|America/North_Dakota/Center|
|»» timezone|America/North_Dakota/New_Salem|
|»» timezone|America/Ojinaga|
|»» timezone|America/Panama|
|»» timezone|America/Pangnirtung|
|»» timezone|America/Paramaribo|
|»» timezone|America/Phoenix|
|»» timezone|America/Port-au-Prince|
|»» timezone|America/Port_of_Spain|
|»» timezone|America/Porto_Acre|
|»» timezone|America/Porto_Velho|
|»» timezone|America/Puerto_Rico|
|»» timezone|America/Punta_Arenas|
|»» timezone|America/Rainy_River|
|»» timezone|America/Rankin_Inlet|
|»» timezone|America/Recife|
|»» timezone|America/Regina|
|»» timezone|America/Resolute|
|»» timezone|America/Rio_Branco|
|»» timezone|America/Rosario|
|»» timezone|America/Santa_Isabel|
|»» timezone|America/Santarem|
|»» timezone|America/Santiago|
|»» timezone|America/Santo_Domingo|
|»» timezone|America/Sao_Paulo|
|»» timezone|America/Scoresbysund|
|»» timezone|America/Shiprock|
|»» timezone|America/Sitka|
|»» timezone|America/St_Barthelemy|
|»» timezone|America/St_Johns|
|»» timezone|America/St_Kitts|
|»» timezone|America/St_Lucia|
|»» timezone|America/St_Thomas|
|»» timezone|America/St_Vincent|
|»» timezone|America/Swift_Current|
|»» timezone|America/Tegucigalpa|
|»» timezone|America/Thule|
|»» timezone|America/Thunder_Bay|
|»» timezone|America/Tijuana|
|»» timezone|America/Toronto|
|»» timezone|America/Tortola|
|»» timezone|America/Vancouver|
|»» timezone|America/Virgin|
|»» timezone|America/Whitehorse|
|»» timezone|America/Winnipeg|
|»» timezone|America/Yakutat|
|»» timezone|America/Yellowknife|
|»» timezone|Antarctica/Casey|
|»» timezone|Antarctica/Davis|
|»» timezone|Antarctica/DumontDUrville|
|»» timezone|Antarctica/Macquarie|
|»» timezone|Antarctica/Mawson|
|»» timezone|Antarctica/McMurdo|
|»» timezone|Antarctica/Palmer|
|»» timezone|Antarctica/Rothera|
|»» timezone|Antarctica/South_Pole|
|»» timezone|Antarctica/Syowa|
|»» timezone|Antarctica/Troll|
|»» timezone|Antarctica/Vostok|
|»» timezone|Arctic/Longyearbyen|
|»» timezone|Asia/Aden|
|»» timezone|Asia/Almaty|
|»» timezone|Asia/Amman|
|»» timezone|Asia/Anadyr|
|»» timezone|Asia/Aqtau|
|»» timezone|Asia/Aqtobe|
|»» timezone|Asia/Ashgabat|
|»» timezone|Asia/Ashkhabad|
|»» timezone|Asia/Atyrau|
|»» timezone|Asia/Baghdad|
|»» timezone|Asia/Bahrain|
|»» timezone|Asia/Baku|
|»» timezone|Asia/Bangkok|
|»» timezone|Asia/Barnaul|
|»» timezone|Asia/Beirut|
|»» timezone|Asia/Bishkek|
|»» timezone|Asia/Brunei|
|»» timezone|Asia/Calcutta|
|»» timezone|Asia/Chita|
|»» timezone|Asia/Choibalsan|
|»» timezone|Asia/Chongqing|
|»» timezone|Asia/Chungking|
|»» timezone|Asia/Colombo|
|»» timezone|Asia/Dacca|
|»» timezone|Asia/Damascus|
|»» timezone|Asia/Dhaka|
|»» timezone|Asia/Dili|
|»» timezone|Asia/Dubai|
|»» timezone|Asia/Dushanbe|
|»» timezone|Asia/Famagusta|
|»» timezone|Asia/Gaza|
|»» timezone|Asia/Harbin|
|»» timezone|Asia/Hebron|
|»» timezone|Asia/Ho_Chi_Minh|
|»» timezone|Asia/Hong_Kong|
|»» timezone|Asia/Hovd|
|»» timezone|Asia/Irkutsk|
|»» timezone|Asia/Istanbul|
|»» timezone|Asia/Jakarta|
|»» timezone|Asia/Jayapura|
|»» timezone|Asia/Jerusalem|
|»» timezone|Asia/Kabul|
|»» timezone|Asia/Kamchatka|
|»» timezone|Asia/Karachi|
|»» timezone|Asia/Kashgar|
|»» timezone|Asia/Kathmandu|
|»» timezone|Asia/Katmandu|
|»» timezone|Asia/Khandyga|
|»» timezone|Asia/Kolkata|
|»» timezone|Asia/Krasnoyarsk|
|»» timezone|Asia/Kuala_Lumpur|
|»» timezone|Asia/Kuching|
|»» timezone|Asia/Kuwait|
|»» timezone|Asia/Macao|
|»» timezone|Asia/Macau|
|»» timezone|Asia/Magadan|
|»» timezone|Asia/Makassar|
|»» timezone|Asia/Manila|
|»» timezone|Asia/Muscat|
|»» timezone|Asia/Nicosia|
|»» timezone|Asia/Novokuznetsk|
|»» timezone|Asia/Novosibirsk|
|»» timezone|Asia/Omsk|
|»» timezone|Asia/Oral|
|»» timezone|Asia/Phnom_Penh|
|»» timezone|Asia/Pontianak|
|»» timezone|Asia/Pyongyang|
|»» timezone|Asia/Qatar|
|»» timezone|Asia/Qostanay|
|»» timezone|Asia/Qyzylorda|
|»» timezone|Asia/Rangoon|
|»» timezone|Asia/Riyadh|
|»» timezone|Asia/Saigon|
|»» timezone|Asia/Sakhalin|
|»» timezone|Asia/Samarkand|
|»» timezone|Asia/Seoul|
|»» timezone|Asia/Shanghai|
|»» timezone|Asia/Singapore|
|»» timezone|Asia/Srednekolymsk|
|»» timezone|Asia/Taipei|
|»» timezone|Asia/Tashkent|
|»» timezone|Asia/Tbilisi|
|»» timezone|Asia/Tehran|
|»» timezone|Asia/Tel_Aviv|
|»» timezone|Asia/Thimbu|
|»» timezone|Asia/Thimphu|
|»» timezone|Asia/Tokyo|
|»» timezone|Asia/Tomsk|
|»» timezone|Asia/Ujung_Pandang|
|»» timezone|Asia/Ulaanbaatar|
|»» timezone|Asia/Ulan_Bator|
|»» timezone|Asia/Urumqi|
|»» timezone|Asia/Ust-Nera|
|»» timezone|Asia/Vientiane|
|»» timezone|Asia/Vladivostok|
|»» timezone|Asia/Yakutsk|
|»» timezone|Asia/Yangon|
|»» timezone|Asia/Yekaterinburg|
|»» timezone|Asia/Yerevan|
|»» timezone|Atlantic/Azores|
|»» timezone|Atlantic/Bermuda|
|»» timezone|Atlantic/Canary|
|»» timezone|Atlantic/Cape_Verde|
|»» timezone|Atlantic/Faeroe|
|»» timezone|Atlantic/Faroe|
|»» timezone|Atlantic/Jan_Mayen|
|»» timezone|Atlantic/Madeira|
|»» timezone|Atlantic/Reykjavik|
|»» timezone|Atlantic/South_Georgia|
|»» timezone|Atlantic/St_Helena|
|»» timezone|Atlantic/Stanley|
|»» timezone|Australia/ACT|
|»» timezone|Australia/Adelaide|
|»» timezone|Australia/Brisbane|
|»» timezone|Australia/Broken_Hill|
|»» timezone|Australia/Canberra|
|»» timezone|Australia/Currie|
|»» timezone|Australia/Darwin|
|»» timezone|Australia/Eucla|
|»» timezone|Australia/Hobart|
|»» timezone|Australia/LHI|
|»» timezone|Australia/Lindeman|
|»» timezone|Australia/Lord_Howe|
|»» timezone|Australia/Melbourne|
|»» timezone|Australia/NSW|
|»» timezone|Australia/North|
|»» timezone|Australia/Perth|
|»» timezone|Australia/Queensland|
|»» timezone|Australia/South|
|»» timezone|Australia/Sydney|
|»» timezone|Australia/Tasmania|
|»» timezone|Australia/Victoria|
|»» timezone|Australia/West|
|»» timezone|Australia/Yancowinna|
|»» timezone|Brazil/Acre|
|»» timezone|Brazil/DeNoronha|
|»» timezone|Brazil/East|
|»» timezone|Brazil/West|
|»» timezone|CET|
|»» timezone|CST6CDT|
|»» timezone|Canada/Atlantic|
|»» timezone|Canada/Central|
|»» timezone|Canada/Eastern|
|»» timezone|Canada/Mountain|
|»» timezone|Canada/Newfoundland|
|»» timezone|Canada/Pacific|
|»» timezone|Canada/Saskatchewan|
|»» timezone|Canada/Yukon|
|»» timezone|Chile/Continental|
|»» timezone|Chile/EasterIsland|
|»» timezone|Cuba|
|»» timezone|EET|
|»» timezone|EST|
|»» timezone|EST5EDT|
|»» timezone|Egypt|
|»» timezone|Eire|
|»» timezone|Etc/GMT|
|»» timezone|Etc/GMT+0|
|»» timezone|Etc/GMT+1|
|»» timezone|Etc/GMT+10|
|»» timezone|Etc/GMT+11|
|»» timezone|Etc/GMT+12|
|»» timezone|Etc/GMT+2|
|»» timezone|Etc/GMT+3|
|»» timezone|Etc/GMT+4|
|»» timezone|Etc/GMT+5|
|»» timezone|Etc/GMT+6|
|»» timezone|Etc/GMT+7|
|»» timezone|Etc/GMT+8|
|»» timezone|Etc/GMT+9|
|»» timezone|Etc/GMT-0|
|»» timezone|Etc/GMT-1|
|»» timezone|Etc/GMT-10|
|»» timezone|Etc/GMT-11|
|»» timezone|Etc/GMT-12|
|»» timezone|Etc/GMT-13|
|»» timezone|Etc/GMT-14|
|»» timezone|Etc/GMT-2|
|»» timezone|Etc/GMT-3|
|»» timezone|Etc/GMT-4|
|»» timezone|Etc/GMT-5|
|»» timezone|Etc/GMT-6|
|»» timezone|Etc/GMT-7|
|»» timezone|Etc/GMT-8|
|»» timezone|Etc/GMT-9|
|»» timezone|Etc/GMT0|
|»» timezone|Etc/Greenwich|
|»» timezone|Etc/UCT|
|»» timezone|Etc/UTC|
|»» timezone|Etc/Universal|
|»» timezone|Etc/Zulu|
|»» timezone|Europe/Amsterdam|
|»» timezone|Europe/Andorra|
|»» timezone|Europe/Astrakhan|
|»» timezone|Europe/Athens|
|»» timezone|Europe/Belfast|
|»» timezone|Europe/Belgrade|
|»» timezone|Europe/Berlin|
|»» timezone|Europe/Bratislava|
|»» timezone|Europe/Brussels|
|»» timezone|Europe/Bucharest|
|»» timezone|Europe/Budapest|
|»» timezone|Europe/Busingen|
|»» timezone|Europe/Chisinau|
|»» timezone|Europe/Copenhagen|
|»» timezone|Europe/Dublin|
|»» timezone|Europe/Gibraltar|
|»» timezone|Europe/Guernsey|
|»» timezone|Europe/Helsinki|
|»» timezone|Europe/Isle_of_Man|
|»» timezone|Europe/Istanbul|
|»» timezone|Europe/Jersey|
|»» timezone|Europe/Kaliningrad|
|»» timezone|Europe/Kiev|
|»» timezone|Europe/Kirov|
|»» timezone|Europe/Lisbon|
|»» timezone|Europe/Ljubljana|
|»» timezone|Europe/London|
|»» timezone|Europe/Luxembourg|
|»» timezone|Europe/Madrid|
|»» timezone|Europe/Malta|
|»» timezone|Europe/Mariehamn|
|»» timezone|Europe/Minsk|
|»» timezone|Europe/Monaco|
|»» timezone|Europe/Moscow|
|»» timezone|Europe/Nicosia|
|»» timezone|Europe/Oslo|
|»» timezone|Europe/Paris|
|»» timezone|Europe/Podgorica|
|»» timezone|Europe/Prague|
|»» timezone|Europe/Riga|
|»» timezone|Europe/Rome|
|»» timezone|Europe/Samara|
|»» timezone|Europe/San_Marino|
|»» timezone|Europe/Sarajevo|
|»» timezone|Europe/Saratov|
|»» timezone|Europe/Simferopol|
|»» timezone|Europe/Skopje|
|»» timezone|Europe/Sofia|
|»» timezone|Europe/Stockholm|
|»» timezone|Europe/Tallinn|
|»» timezone|Europe/Tirane|
|»» timezone|Europe/Tiraspol|
|»» timezone|Europe/Ulyanovsk|
|»» timezone|Europe/Uzhgorod|
|»» timezone|Europe/Vaduz|
|»» timezone|Europe/Vatican|
|»» timezone|Europe/Vienna|
|»» timezone|Europe/Vilnius|
|»» timezone|Europe/Volgograd|
|»» timezone|Europe/Warsaw|
|»» timezone|Europe/Zagreb|
|»» timezone|Europe/Zaporozhye|
|»» timezone|Europe/Zurich|
|»» timezone|GB|
|»» timezone|GB-Eire|
|»» timezone|GMT|
|»» timezone|GMT+0|
|»» timezone|GMT-0|
|»» timezone|GMT0|
|»» timezone|Greenwich|
|»» timezone|HST|
|»» timezone|Hongkong|
|»» timezone|Iceland|
|»» timezone|Indian/Antananarivo|
|»» timezone|Indian/Chagos|
|»» timezone|Indian/Christmas|
|»» timezone|Indian/Cocos|
|»» timezone|Indian/Comoro|
|»» timezone|Indian/Kerguelen|
|»» timezone|Indian/Mahe|
|»» timezone|Indian/Maldives|
|»» timezone|Indian/Mauritius|
|»» timezone|Indian/Mayotte|
|»» timezone|Indian/Reunion|
|»» timezone|Iran|
|»» timezone|Israel|
|»» timezone|Jamaica|
|»» timezone|Japan|
|»» timezone|Kwajalein|
|»» timezone|Libya|
|»» timezone|MET|
|»» timezone|MST|
|»» timezone|MST7MDT|
|»» timezone|Mexico/BajaNorte|
|»» timezone|Mexico/BajaSur|
|»» timezone|Mexico/General|
|»» timezone|NZ|
|»» timezone|NZ-CHAT|
|»» timezone|Navajo|
|»» timezone|PRC|
|»» timezone|PST8PDT|
|»» timezone|Pacific/Apia|
|»» timezone|Pacific/Auckland|
|»» timezone|Pacific/Bougainville|
|»» timezone|Pacific/Chatham|
|»» timezone|Pacific/Chuuk|
|»» timezone|Pacific/Easter|
|»» timezone|Pacific/Efate|
|»» timezone|Pacific/Enderbury|
|»» timezone|Pacific/Fakaofo|
|»» timezone|Pacific/Fiji|
|»» timezone|Pacific/Funafuti|
|»» timezone|Pacific/Galapagos|
|»» timezone|Pacific/Gambier|
|»» timezone|Pacific/Guadalcanal|
|»» timezone|Pacific/Guam|
|»» timezone|Pacific/Honolulu|
|»» timezone|Pacific/Johnston|
|»» timezone|Pacific/Kiritimati|
|»» timezone|Pacific/Kosrae|
|»» timezone|Pacific/Kwajalein|
|»» timezone|Pacific/Majuro|
|»» timezone|Pacific/Marquesas|
|»» timezone|Pacific/Midway|
|»» timezone|Pacific/Nauru|
|»» timezone|Pacific/Niue|
|»» timezone|Pacific/Norfolk|
|»» timezone|Pacific/Noumea|
|»» timezone|Pacific/Pago_Pago|
|»» timezone|Pacific/Palau|
|»» timezone|Pacific/Pitcairn|
|»» timezone|Pacific/Pohnpei|
|»» timezone|Pacific/Ponape|
|»» timezone|Pacific/Port_Moresby|
|»» timezone|Pacific/Rarotonga|
|»» timezone|Pacific/Saipan|
|»» timezone|Pacific/Samoa|
|»» timezone|Pacific/Tahiti|
|»» timezone|Pacific/Tarawa|
|»» timezone|Pacific/Tongatapu|
|»» timezone|Pacific/Truk|
|»» timezone|Pacific/Wake|
|»» timezone|Pacific/Wallis|
|»» timezone|Pacific/Yap|
|»» timezone|Poland|
|»» timezone|Portugal|
|»» timezone|ROC|
|»» timezone|ROK|
|»» timezone|Singapore|
|»» timezone|Turkey|
|»» timezone|UCT|
|»» timezone|US/Alaska|
|»» timezone|US/Aleutian|
|»» timezone|US/Arizona|
|»» timezone|US/Central|
|»» timezone|US/East-Indiana|
|»» timezone|US/Eastern|
|»» timezone|US/Hawaii|
|»» timezone|US/Indiana-Starke|
|»» timezone|US/Michigan|
|»» timezone|US/Mountain|
|»» timezone|US/Pacific|
|»» timezone|US/Samoa|
|»» timezone|UTC|
|»» timezone|Universal|
|»» timezone|W-SU|
|»» timezone|WET|
|»» timezone|Zulu|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "environment": "string",
  "status": "string",
  "duration": 0,
  "dateCreated": "2019-08-24T14:15:22Z",
  "attachmentId": "string",
  "expectedTime": "2019-08-24T14:15:22Z",
  "monitorConfig": null
}
```

<h3 id="create-a-new-check-in-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="create-a-new-check-in-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» environment|string|true|none|none|
|» status|string|true|none|none|
|» duration|integer|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» attachmentId|string|true|none|none|
|» expectedTime|string(date-time)|true|none|none|
|» monitorConfig|any|true|none|none|

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» environment|string|true|none|none|
|» status|string|true|none|none|
|» duration|integer|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» attachmentId|string|true|none|none|
|» expectedTime|string(date-time)|true|none|none|
|» monitorConfig|any|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Update a check-in

<a id="opIdUpdate a check-in"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/{checkin_id}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/{checkin_id}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "status": "ok",
  "duration": 2147483647,
  "environment": "string",
  "monitor_config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/{checkin_id}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/organization/{organization_slug}/monitors/{monitor_slug}/checkins/{checkin_id}/`

Updates a check-in.

Once a check-in is finished (indicated via an `ok` or `error` status) it can no longer be changed.

If you simply wish to update that the task is still running, you can simply send an empty payload.

You may use `latest` for the `checkin_id` parameter in order to retrieve
the most recent (by creation date) check-in which is still mutable (not marked as finished).

> Body parameter

```json
{
  "status": "ok",
  "duration": 2147483647,
  "environment": "string",
  "monitor_config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  }
}
```

<h3 id="update-a-check-in-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|checkin_id|path|string(uuid)|true|The id of the check-in|
|body|body|object|true|none|
|» status|body|string|true|none|
|» duration|body|integer¦null|false|none|
|» environment|body|string¦null|false|none|
|» monitor_config|body|object|false|none|
|»» schedule_type|body|string|false|Currently supports "crontab" or "interval"|
|»» schedule|body|any|true|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|»» checkin_margin|body|integer¦null|false|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|»» max_runtime|body|integer¦null|false|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|»» timezone|body|string|false|tz database style timezone string|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|ok|
|» status|error|
|» status|in_progress|
|»» schedule_type|crontab|
|»» schedule_type|interval|
|»» timezone|Africa/Abidjan|
|»» timezone|Africa/Accra|
|»» timezone|Africa/Addis_Ababa|
|»» timezone|Africa/Algiers|
|»» timezone|Africa/Asmara|
|»» timezone|Africa/Asmera|
|»» timezone|Africa/Bamako|
|»» timezone|Africa/Bangui|
|»» timezone|Africa/Banjul|
|»» timezone|Africa/Bissau|
|»» timezone|Africa/Blantyre|
|»» timezone|Africa/Brazzaville|
|»» timezone|Africa/Bujumbura|
|»» timezone|Africa/Cairo|
|»» timezone|Africa/Casablanca|
|»» timezone|Africa/Ceuta|
|»» timezone|Africa/Conakry|
|»» timezone|Africa/Dakar|
|»» timezone|Africa/Dar_es_Salaam|
|»» timezone|Africa/Djibouti|
|»» timezone|Africa/Douala|
|»» timezone|Africa/El_Aaiun|
|»» timezone|Africa/Freetown|
|»» timezone|Africa/Gaborone|
|»» timezone|Africa/Harare|
|»» timezone|Africa/Johannesburg|
|»» timezone|Africa/Juba|
|»» timezone|Africa/Kampala|
|»» timezone|Africa/Khartoum|
|»» timezone|Africa/Kigali|
|»» timezone|Africa/Kinshasa|
|»» timezone|Africa/Lagos|
|»» timezone|Africa/Libreville|
|»» timezone|Africa/Lome|
|»» timezone|Africa/Luanda|
|»» timezone|Africa/Lubumbashi|
|»» timezone|Africa/Lusaka|
|»» timezone|Africa/Malabo|
|»» timezone|Africa/Maputo|
|»» timezone|Africa/Maseru|
|»» timezone|Africa/Mbabane|
|»» timezone|Africa/Mogadishu|
|»» timezone|Africa/Monrovia|
|»» timezone|Africa/Nairobi|
|»» timezone|Africa/Ndjamena|
|»» timezone|Africa/Niamey|
|»» timezone|Africa/Nouakchott|
|»» timezone|Africa/Ouagadougou|
|»» timezone|Africa/Porto-Novo|
|»» timezone|Africa/Sao_Tome|
|»» timezone|Africa/Timbuktu|
|»» timezone|Africa/Tripoli|
|»» timezone|Africa/Tunis|
|»» timezone|Africa/Windhoek|
|»» timezone|America/Adak|
|»» timezone|America/Anchorage|
|»» timezone|America/Anguilla|
|»» timezone|America/Antigua|
|»» timezone|America/Araguaina|
|»» timezone|America/Argentina/Buenos_Aires|
|»» timezone|America/Argentina/Catamarca|
|»» timezone|America/Argentina/ComodRivadavia|
|»» timezone|America/Argentina/Cordoba|
|»» timezone|America/Argentina/Jujuy|
|»» timezone|America/Argentina/La_Rioja|
|»» timezone|America/Argentina/Mendoza|
|»» timezone|America/Argentina/Rio_Gallegos|
|»» timezone|America/Argentina/Salta|
|»» timezone|America/Argentina/San_Juan|
|»» timezone|America/Argentina/San_Luis|
|»» timezone|America/Argentina/Tucuman|
|»» timezone|America/Argentina/Ushuaia|
|»» timezone|America/Aruba|
|»» timezone|America/Asuncion|
|»» timezone|America/Atikokan|
|»» timezone|America/Atka|
|»» timezone|America/Bahia|
|»» timezone|America/Bahia_Banderas|
|»» timezone|America/Barbados|
|»» timezone|America/Belem|
|»» timezone|America/Belize|
|»» timezone|America/Blanc-Sablon|
|»» timezone|America/Boa_Vista|
|»» timezone|America/Bogota|
|»» timezone|America/Boise|
|»» timezone|America/Buenos_Aires|
|»» timezone|America/Cambridge_Bay|
|»» timezone|America/Campo_Grande|
|»» timezone|America/Cancun|
|»» timezone|America/Caracas|
|»» timezone|America/Catamarca|
|»» timezone|America/Cayenne|
|»» timezone|America/Cayman|
|»» timezone|America/Chicago|
|»» timezone|America/Chihuahua|
|»» timezone|America/Coral_Harbour|
|»» timezone|America/Cordoba|
|»» timezone|America/Costa_Rica|
|»» timezone|America/Creston|
|»» timezone|America/Cuiaba|
|»» timezone|America/Curacao|
|»» timezone|America/Danmarkshavn|
|»» timezone|America/Dawson|
|»» timezone|America/Dawson_Creek|
|»» timezone|America/Denver|
|»» timezone|America/Detroit|
|»» timezone|America/Dominica|
|»» timezone|America/Edmonton|
|»» timezone|America/Eirunepe|
|»» timezone|America/El_Salvador|
|»» timezone|America/Ensenada|
|»» timezone|America/Fort_Nelson|
|»» timezone|America/Fort_Wayne|
|»» timezone|America/Fortaleza|
|»» timezone|America/Glace_Bay|
|»» timezone|America/Godthab|
|»» timezone|America/Goose_Bay|
|»» timezone|America/Grand_Turk|
|»» timezone|America/Grenada|
|»» timezone|America/Guadeloupe|
|»» timezone|America/Guatemala|
|»» timezone|America/Guayaquil|
|»» timezone|America/Guyana|
|»» timezone|America/Halifax|
|»» timezone|America/Havana|
|»» timezone|America/Hermosillo|
|»» timezone|America/Indiana/Indianapolis|
|»» timezone|America/Indiana/Knox|
|»» timezone|America/Indiana/Marengo|
|»» timezone|America/Indiana/Petersburg|
|»» timezone|America/Indiana/Tell_City|
|»» timezone|America/Indiana/Vevay|
|»» timezone|America/Indiana/Vincennes|
|»» timezone|America/Indiana/Winamac|
|»» timezone|America/Indianapolis|
|»» timezone|America/Inuvik|
|»» timezone|America/Iqaluit|
|»» timezone|America/Jamaica|
|»» timezone|America/Jujuy|
|»» timezone|America/Juneau|
|»» timezone|America/Kentucky/Louisville|
|»» timezone|America/Kentucky/Monticello|
|»» timezone|America/Knox_IN|
|»» timezone|America/Kralendijk|
|»» timezone|America/La_Paz|
|»» timezone|America/Lima|
|»» timezone|America/Los_Angeles|
|»» timezone|America/Louisville|
|»» timezone|America/Lower_Princes|
|»» timezone|America/Maceio|
|»» timezone|America/Managua|
|»» timezone|America/Manaus|
|»» timezone|America/Marigot|
|»» timezone|America/Martinique|
|»» timezone|America/Matamoros|
|»» timezone|America/Mazatlan|
|»» timezone|America/Mendoza|
|»» timezone|America/Menominee|
|»» timezone|America/Merida|
|»» timezone|America/Metlakatla|
|»» timezone|America/Mexico_City|
|»» timezone|America/Miquelon|
|»» timezone|America/Moncton|
|»» timezone|America/Monterrey|
|»» timezone|America/Montevideo|
|»» timezone|America/Montreal|
|»» timezone|America/Montserrat|
|»» timezone|America/Nassau|
|»» timezone|America/New_York|
|»» timezone|America/Nipigon|
|»» timezone|America/Nome|
|»» timezone|America/Noronha|
|»» timezone|America/North_Dakota/Beulah|
|»» timezone|America/North_Dakota/Center|
|»» timezone|America/North_Dakota/New_Salem|
|»» timezone|America/Ojinaga|
|»» timezone|America/Panama|
|»» timezone|America/Pangnirtung|
|»» timezone|America/Paramaribo|
|»» timezone|America/Phoenix|
|»» timezone|America/Port-au-Prince|
|»» timezone|America/Port_of_Spain|
|»» timezone|America/Porto_Acre|
|»» timezone|America/Porto_Velho|
|»» timezone|America/Puerto_Rico|
|»» timezone|America/Punta_Arenas|
|»» timezone|America/Rainy_River|
|»» timezone|America/Rankin_Inlet|
|»» timezone|America/Recife|
|»» timezone|America/Regina|
|»» timezone|America/Resolute|
|»» timezone|America/Rio_Branco|
|»» timezone|America/Rosario|
|»» timezone|America/Santa_Isabel|
|»» timezone|America/Santarem|
|»» timezone|America/Santiago|
|»» timezone|America/Santo_Domingo|
|»» timezone|America/Sao_Paulo|
|»» timezone|America/Scoresbysund|
|»» timezone|America/Shiprock|
|»» timezone|America/Sitka|
|»» timezone|America/St_Barthelemy|
|»» timezone|America/St_Johns|
|»» timezone|America/St_Kitts|
|»» timezone|America/St_Lucia|
|»» timezone|America/St_Thomas|
|»» timezone|America/St_Vincent|
|»» timezone|America/Swift_Current|
|»» timezone|America/Tegucigalpa|
|»» timezone|America/Thule|
|»» timezone|America/Thunder_Bay|
|»» timezone|America/Tijuana|
|»» timezone|America/Toronto|
|»» timezone|America/Tortola|
|»» timezone|America/Vancouver|
|»» timezone|America/Virgin|
|»» timezone|America/Whitehorse|
|»» timezone|America/Winnipeg|
|»» timezone|America/Yakutat|
|»» timezone|America/Yellowknife|
|»» timezone|Antarctica/Casey|
|»» timezone|Antarctica/Davis|
|»» timezone|Antarctica/DumontDUrville|
|»» timezone|Antarctica/Macquarie|
|»» timezone|Antarctica/Mawson|
|»» timezone|Antarctica/McMurdo|
|»» timezone|Antarctica/Palmer|
|»» timezone|Antarctica/Rothera|
|»» timezone|Antarctica/South_Pole|
|»» timezone|Antarctica/Syowa|
|»» timezone|Antarctica/Troll|
|»» timezone|Antarctica/Vostok|
|»» timezone|Arctic/Longyearbyen|
|»» timezone|Asia/Aden|
|»» timezone|Asia/Almaty|
|»» timezone|Asia/Amman|
|»» timezone|Asia/Anadyr|
|»» timezone|Asia/Aqtau|
|»» timezone|Asia/Aqtobe|
|»» timezone|Asia/Ashgabat|
|»» timezone|Asia/Ashkhabad|
|»» timezone|Asia/Atyrau|
|»» timezone|Asia/Baghdad|
|»» timezone|Asia/Bahrain|
|»» timezone|Asia/Baku|
|»» timezone|Asia/Bangkok|
|»» timezone|Asia/Barnaul|
|»» timezone|Asia/Beirut|
|»» timezone|Asia/Bishkek|
|»» timezone|Asia/Brunei|
|»» timezone|Asia/Calcutta|
|»» timezone|Asia/Chita|
|»» timezone|Asia/Choibalsan|
|»» timezone|Asia/Chongqing|
|»» timezone|Asia/Chungking|
|»» timezone|Asia/Colombo|
|»» timezone|Asia/Dacca|
|»» timezone|Asia/Damascus|
|»» timezone|Asia/Dhaka|
|»» timezone|Asia/Dili|
|»» timezone|Asia/Dubai|
|»» timezone|Asia/Dushanbe|
|»» timezone|Asia/Famagusta|
|»» timezone|Asia/Gaza|
|»» timezone|Asia/Harbin|
|»» timezone|Asia/Hebron|
|»» timezone|Asia/Ho_Chi_Minh|
|»» timezone|Asia/Hong_Kong|
|»» timezone|Asia/Hovd|
|»» timezone|Asia/Irkutsk|
|»» timezone|Asia/Istanbul|
|»» timezone|Asia/Jakarta|
|»» timezone|Asia/Jayapura|
|»» timezone|Asia/Jerusalem|
|»» timezone|Asia/Kabul|
|»» timezone|Asia/Kamchatka|
|»» timezone|Asia/Karachi|
|»» timezone|Asia/Kashgar|
|»» timezone|Asia/Kathmandu|
|»» timezone|Asia/Katmandu|
|»» timezone|Asia/Khandyga|
|»» timezone|Asia/Kolkata|
|»» timezone|Asia/Krasnoyarsk|
|»» timezone|Asia/Kuala_Lumpur|
|»» timezone|Asia/Kuching|
|»» timezone|Asia/Kuwait|
|»» timezone|Asia/Macao|
|»» timezone|Asia/Macau|
|»» timezone|Asia/Magadan|
|»» timezone|Asia/Makassar|
|»» timezone|Asia/Manila|
|»» timezone|Asia/Muscat|
|»» timezone|Asia/Nicosia|
|»» timezone|Asia/Novokuznetsk|
|»» timezone|Asia/Novosibirsk|
|»» timezone|Asia/Omsk|
|»» timezone|Asia/Oral|
|»» timezone|Asia/Phnom_Penh|
|»» timezone|Asia/Pontianak|
|»» timezone|Asia/Pyongyang|
|»» timezone|Asia/Qatar|
|»» timezone|Asia/Qostanay|
|»» timezone|Asia/Qyzylorda|
|»» timezone|Asia/Rangoon|
|»» timezone|Asia/Riyadh|
|»» timezone|Asia/Saigon|
|»» timezone|Asia/Sakhalin|
|»» timezone|Asia/Samarkand|
|»» timezone|Asia/Seoul|
|»» timezone|Asia/Shanghai|
|»» timezone|Asia/Singapore|
|»» timezone|Asia/Srednekolymsk|
|»» timezone|Asia/Taipei|
|»» timezone|Asia/Tashkent|
|»» timezone|Asia/Tbilisi|
|»» timezone|Asia/Tehran|
|»» timezone|Asia/Tel_Aviv|
|»» timezone|Asia/Thimbu|
|»» timezone|Asia/Thimphu|
|»» timezone|Asia/Tokyo|
|»» timezone|Asia/Tomsk|
|»» timezone|Asia/Ujung_Pandang|
|»» timezone|Asia/Ulaanbaatar|
|»» timezone|Asia/Ulan_Bator|
|»» timezone|Asia/Urumqi|
|»» timezone|Asia/Ust-Nera|
|»» timezone|Asia/Vientiane|
|»» timezone|Asia/Vladivostok|
|»» timezone|Asia/Yakutsk|
|»» timezone|Asia/Yangon|
|»» timezone|Asia/Yekaterinburg|
|»» timezone|Asia/Yerevan|
|»» timezone|Atlantic/Azores|
|»» timezone|Atlantic/Bermuda|
|»» timezone|Atlantic/Canary|
|»» timezone|Atlantic/Cape_Verde|
|»» timezone|Atlantic/Faeroe|
|»» timezone|Atlantic/Faroe|
|»» timezone|Atlantic/Jan_Mayen|
|»» timezone|Atlantic/Madeira|
|»» timezone|Atlantic/Reykjavik|
|»» timezone|Atlantic/South_Georgia|
|»» timezone|Atlantic/St_Helena|
|»» timezone|Atlantic/Stanley|
|»» timezone|Australia/ACT|
|»» timezone|Australia/Adelaide|
|»» timezone|Australia/Brisbane|
|»» timezone|Australia/Broken_Hill|
|»» timezone|Australia/Canberra|
|»» timezone|Australia/Currie|
|»» timezone|Australia/Darwin|
|»» timezone|Australia/Eucla|
|»» timezone|Australia/Hobart|
|»» timezone|Australia/LHI|
|»» timezone|Australia/Lindeman|
|»» timezone|Australia/Lord_Howe|
|»» timezone|Australia/Melbourne|
|»» timezone|Australia/NSW|
|»» timezone|Australia/North|
|»» timezone|Australia/Perth|
|»» timezone|Australia/Queensland|
|»» timezone|Australia/South|
|»» timezone|Australia/Sydney|
|»» timezone|Australia/Tasmania|
|»» timezone|Australia/Victoria|
|»» timezone|Australia/West|
|»» timezone|Australia/Yancowinna|
|»» timezone|Brazil/Acre|
|»» timezone|Brazil/DeNoronha|
|»» timezone|Brazil/East|
|»» timezone|Brazil/West|
|»» timezone|CET|
|»» timezone|CST6CDT|
|»» timezone|Canada/Atlantic|
|»» timezone|Canada/Central|
|»» timezone|Canada/Eastern|
|»» timezone|Canada/Mountain|
|»» timezone|Canada/Newfoundland|
|»» timezone|Canada/Pacific|
|»» timezone|Canada/Saskatchewan|
|»» timezone|Canada/Yukon|
|»» timezone|Chile/Continental|
|»» timezone|Chile/EasterIsland|
|»» timezone|Cuba|
|»» timezone|EET|
|»» timezone|EST|
|»» timezone|EST5EDT|
|»» timezone|Egypt|
|»» timezone|Eire|
|»» timezone|Etc/GMT|
|»» timezone|Etc/GMT+0|
|»» timezone|Etc/GMT+1|
|»» timezone|Etc/GMT+10|
|»» timezone|Etc/GMT+11|
|»» timezone|Etc/GMT+12|
|»» timezone|Etc/GMT+2|
|»» timezone|Etc/GMT+3|
|»» timezone|Etc/GMT+4|
|»» timezone|Etc/GMT+5|
|»» timezone|Etc/GMT+6|
|»» timezone|Etc/GMT+7|
|»» timezone|Etc/GMT+8|
|»» timezone|Etc/GMT+9|
|»» timezone|Etc/GMT-0|
|»» timezone|Etc/GMT-1|
|»» timezone|Etc/GMT-10|
|»» timezone|Etc/GMT-11|
|»» timezone|Etc/GMT-12|
|»» timezone|Etc/GMT-13|
|»» timezone|Etc/GMT-14|
|»» timezone|Etc/GMT-2|
|»» timezone|Etc/GMT-3|
|»» timezone|Etc/GMT-4|
|»» timezone|Etc/GMT-5|
|»» timezone|Etc/GMT-6|
|»» timezone|Etc/GMT-7|
|»» timezone|Etc/GMT-8|
|»» timezone|Etc/GMT-9|
|»» timezone|Etc/GMT0|
|»» timezone|Etc/Greenwich|
|»» timezone|Etc/UCT|
|»» timezone|Etc/UTC|
|»» timezone|Etc/Universal|
|»» timezone|Etc/Zulu|
|»» timezone|Europe/Amsterdam|
|»» timezone|Europe/Andorra|
|»» timezone|Europe/Astrakhan|
|»» timezone|Europe/Athens|
|»» timezone|Europe/Belfast|
|»» timezone|Europe/Belgrade|
|»» timezone|Europe/Berlin|
|»» timezone|Europe/Bratislava|
|»» timezone|Europe/Brussels|
|»» timezone|Europe/Bucharest|
|»» timezone|Europe/Budapest|
|»» timezone|Europe/Busingen|
|»» timezone|Europe/Chisinau|
|»» timezone|Europe/Copenhagen|
|»» timezone|Europe/Dublin|
|»» timezone|Europe/Gibraltar|
|»» timezone|Europe/Guernsey|
|»» timezone|Europe/Helsinki|
|»» timezone|Europe/Isle_of_Man|
|»» timezone|Europe/Istanbul|
|»» timezone|Europe/Jersey|
|»» timezone|Europe/Kaliningrad|
|»» timezone|Europe/Kiev|
|»» timezone|Europe/Kirov|
|»» timezone|Europe/Lisbon|
|»» timezone|Europe/Ljubljana|
|»» timezone|Europe/London|
|»» timezone|Europe/Luxembourg|
|»» timezone|Europe/Madrid|
|»» timezone|Europe/Malta|
|»» timezone|Europe/Mariehamn|
|»» timezone|Europe/Minsk|
|»» timezone|Europe/Monaco|
|»» timezone|Europe/Moscow|
|»» timezone|Europe/Nicosia|
|»» timezone|Europe/Oslo|
|»» timezone|Europe/Paris|
|»» timezone|Europe/Podgorica|
|»» timezone|Europe/Prague|
|»» timezone|Europe/Riga|
|»» timezone|Europe/Rome|
|»» timezone|Europe/Samara|
|»» timezone|Europe/San_Marino|
|»» timezone|Europe/Sarajevo|
|»» timezone|Europe/Saratov|
|»» timezone|Europe/Simferopol|
|»» timezone|Europe/Skopje|
|»» timezone|Europe/Sofia|
|»» timezone|Europe/Stockholm|
|»» timezone|Europe/Tallinn|
|»» timezone|Europe/Tirane|
|»» timezone|Europe/Tiraspol|
|»» timezone|Europe/Ulyanovsk|
|»» timezone|Europe/Uzhgorod|
|»» timezone|Europe/Vaduz|
|»» timezone|Europe/Vatican|
|»» timezone|Europe/Vienna|
|»» timezone|Europe/Vilnius|
|»» timezone|Europe/Volgograd|
|»» timezone|Europe/Warsaw|
|»» timezone|Europe/Zagreb|
|»» timezone|Europe/Zaporozhye|
|»» timezone|Europe/Zurich|
|»» timezone|GB|
|»» timezone|GB-Eire|
|»» timezone|GMT|
|»» timezone|GMT+0|
|»» timezone|GMT-0|
|»» timezone|GMT0|
|»» timezone|Greenwich|
|»» timezone|HST|
|»» timezone|Hongkong|
|»» timezone|Iceland|
|»» timezone|Indian/Antananarivo|
|»» timezone|Indian/Chagos|
|»» timezone|Indian/Christmas|
|»» timezone|Indian/Cocos|
|»» timezone|Indian/Comoro|
|»» timezone|Indian/Kerguelen|
|»» timezone|Indian/Mahe|
|»» timezone|Indian/Maldives|
|»» timezone|Indian/Mauritius|
|»» timezone|Indian/Mayotte|
|»» timezone|Indian/Reunion|
|»» timezone|Iran|
|»» timezone|Israel|
|»» timezone|Jamaica|
|»» timezone|Japan|
|»» timezone|Kwajalein|
|»» timezone|Libya|
|»» timezone|MET|
|»» timezone|MST|
|»» timezone|MST7MDT|
|»» timezone|Mexico/BajaNorte|
|»» timezone|Mexico/BajaSur|
|»» timezone|Mexico/General|
|»» timezone|NZ|
|»» timezone|NZ-CHAT|
|»» timezone|Navajo|
|»» timezone|PRC|
|»» timezone|PST8PDT|
|»» timezone|Pacific/Apia|
|»» timezone|Pacific/Auckland|
|»» timezone|Pacific/Bougainville|
|»» timezone|Pacific/Chatham|
|»» timezone|Pacific/Chuuk|
|»» timezone|Pacific/Easter|
|»» timezone|Pacific/Efate|
|»» timezone|Pacific/Enderbury|
|»» timezone|Pacific/Fakaofo|
|»» timezone|Pacific/Fiji|
|»» timezone|Pacific/Funafuti|
|»» timezone|Pacific/Galapagos|
|»» timezone|Pacific/Gambier|
|»» timezone|Pacific/Guadalcanal|
|»» timezone|Pacific/Guam|
|»» timezone|Pacific/Honolulu|
|»» timezone|Pacific/Johnston|
|»» timezone|Pacific/Kiritimati|
|»» timezone|Pacific/Kosrae|
|»» timezone|Pacific/Kwajalein|
|»» timezone|Pacific/Majuro|
|»» timezone|Pacific/Marquesas|
|»» timezone|Pacific/Midway|
|»» timezone|Pacific/Nauru|
|»» timezone|Pacific/Niue|
|»» timezone|Pacific/Norfolk|
|»» timezone|Pacific/Noumea|
|»» timezone|Pacific/Pago_Pago|
|»» timezone|Pacific/Palau|
|»» timezone|Pacific/Pitcairn|
|»» timezone|Pacific/Pohnpei|
|»» timezone|Pacific/Ponape|
|»» timezone|Pacific/Port_Moresby|
|»» timezone|Pacific/Rarotonga|
|»» timezone|Pacific/Saipan|
|»» timezone|Pacific/Samoa|
|»» timezone|Pacific/Tahiti|
|»» timezone|Pacific/Tarawa|
|»» timezone|Pacific/Tongatapu|
|»» timezone|Pacific/Truk|
|»» timezone|Pacific/Wake|
|»» timezone|Pacific/Wallis|
|»» timezone|Pacific/Yap|
|»» timezone|Poland|
|»» timezone|Portugal|
|»» timezone|ROC|
|»» timezone|ROK|
|»» timezone|Singapore|
|»» timezone|Turkey|
|»» timezone|UCT|
|»» timezone|US/Alaska|
|»» timezone|US/Aleutian|
|»» timezone|US/Arizona|
|»» timezone|US/Central|
|»» timezone|US/East-Indiana|
|»» timezone|US/Eastern|
|»» timezone|US/Hawaii|
|»» timezone|US/Indiana-Starke|
|»» timezone|US/Michigan|
|»» timezone|US/Mountain|
|»» timezone|US/Pacific|
|»» timezone|US/Samoa|
|»» timezone|UTC|
|»» timezone|Universal|
|»» timezone|W-SU|
|»» timezone|WET|
|»» timezone|Zulu|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "environment": "string",
  "status": "string",
  "duration": 0,
  "dateCreated": "2019-08-24T14:15:22Z",
  "attachmentId": "string",
  "expectedTime": "2019-08-24T14:15:22Z",
  "monitorConfig": null
}
```

<h3 id="update-a-check-in-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|208|Unknown|Already Reported|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-a-check-in-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» environment|string|true|none|none|
|» status|string|true|none|none|
|» duration|integer|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» attachmentId|string|true|none|none|
|» expectedTime|string(date-time)|true|none|none|
|» monitorConfig|any|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Retrieve monitors for an organization

<a id="opIdRetrieve monitors for an organization"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/monitors/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/monitors/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/monitors/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/monitors/`

Lists monitors, including nested monitor enviroments. May be filtered to a project or environment.

<h3 id="retrieve-monitors-for-an-organization-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|project|query|array[integer]|false|The ids of projects to filter by. `-1` means all available projects. If this parameter is omitted, the request will default to using 'My Projects'|
|environment|query|array[string]|false|The name of environments to filter by.|

> Example responses

> 200 Response

```json
[
  {
    "id": "string",
    "name": "string",
    "slug": "string",
    "status": "string",
    "type": "string",
    "config": null,
    "dateCreated": "2019-08-24T14:15:22Z",
    "project": {
      "stats": null,
      "transactionStats": null,
      "sessionStats": null,
      "id": "string",
      "slug": "string",
      "name": "string",
      "platform": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "isBookmarked": true,
      "isMember": true,
      "features": [
        "string"
      ],
      "firstEvent": "2019-08-24T14:15:22Z",
      "firstTransactionEvent": true,
      "access": [
        "string"
      ],
      "hasAccess": true,
      "hasMinifiedStackTrace": true,
      "hasMonitors": true,
      "hasProfiles": true,
      "hasReplays": true,
      "hasSessions": true,
      "isInternal": true,
      "isPublic": true,
      "avatar": null,
      "color": "string",
      "status": "string"
    },
    "environments": {
      "name": "string",
      "status": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "lastCheckIn": "2019-08-24T14:15:22Z",
      "nextCheckIn": "2019-08-24T14:15:22Z"
    }
  }
]
```

<h3 id="retrieve-monitors-for-an-organization-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-monitors-for-an-organization-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» type|string|true|none|none|
|» config|any|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» project|object|true|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» environments|object|true|none|none|
|»» name|string|true|none|none|
|»» status|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» lastCheckIn|string(date-time)|true|none|none|
|»» nextCheckIn|string(date-time)|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

## Create a monitor

<a id="opIdCreate a monitor"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://sentry.io/api/0/organizations/{organization_slug}/monitors/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://sentry.io/api/0/organizations/{organization_slug}/monitors/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "project": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "type": "cron_job",
  "config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  },
  "alert_rule": {
    "environment": "string",
    "targets": [
      {
        "target_identifier": 0,
        "target_type": "string"
      }
    ]
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/monitors/',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /api/0/organizations/{organization_slug}/monitors/`

Create a new monitor.

> Body parameter

```json
{
  "project": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "type": "cron_job",
  "config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  },
  "alert_rule": {
    "environment": "string",
    "targets": [
      {
        "target_identifier": 0,
        "target_type": "string"
      }
    ]
  }
}
```

<h3 id="create-a-monitor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|body|body|object|true|none|
|» project|body|string|true|none|
|» name|body|string|true|none|
|» slug|body|string|false|none|
|» status|body|string|false|none|
|» type|body|string|true|none|
|» config|body|object|true|none|
|»» schedule_type|body|string|false|Currently supports "crontab" or "interval"|
|»» schedule|body|any|true|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|»» checkin_margin|body|integer¦null|false|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|»» max_runtime|body|integer¦null|false|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|»» timezone|body|string|false|tz database style timezone string|
|» alert_rule|body|object|false|none|
|»» environment|body|string¦null|false|Name of the environment|
|»» targets|body|[object]|true|Array of dictionaries with information of the user or team to be notified|
|»»» target_identifier|body|integer|true|ID of target object|
|»»» target_type|body|string|true|One of [Member, Team]|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|active|
|» status|disabled|
|» type|cron_job|
|»» schedule_type|crontab|
|»» schedule_type|interval|
|»» timezone|Africa/Abidjan|
|»» timezone|Africa/Accra|
|»» timezone|Africa/Addis_Ababa|
|»» timezone|Africa/Algiers|
|»» timezone|Africa/Asmara|
|»» timezone|Africa/Asmera|
|»» timezone|Africa/Bamako|
|»» timezone|Africa/Bangui|
|»» timezone|Africa/Banjul|
|»» timezone|Africa/Bissau|
|»» timezone|Africa/Blantyre|
|»» timezone|Africa/Brazzaville|
|»» timezone|Africa/Bujumbura|
|»» timezone|Africa/Cairo|
|»» timezone|Africa/Casablanca|
|»» timezone|Africa/Ceuta|
|»» timezone|Africa/Conakry|
|»» timezone|Africa/Dakar|
|»» timezone|Africa/Dar_es_Salaam|
|»» timezone|Africa/Djibouti|
|»» timezone|Africa/Douala|
|»» timezone|Africa/El_Aaiun|
|»» timezone|Africa/Freetown|
|»» timezone|Africa/Gaborone|
|»» timezone|Africa/Harare|
|»» timezone|Africa/Johannesburg|
|»» timezone|Africa/Juba|
|»» timezone|Africa/Kampala|
|»» timezone|Africa/Khartoum|
|»» timezone|Africa/Kigali|
|»» timezone|Africa/Kinshasa|
|»» timezone|Africa/Lagos|
|»» timezone|Africa/Libreville|
|»» timezone|Africa/Lome|
|»» timezone|Africa/Luanda|
|»» timezone|Africa/Lubumbashi|
|»» timezone|Africa/Lusaka|
|»» timezone|Africa/Malabo|
|»» timezone|Africa/Maputo|
|»» timezone|Africa/Maseru|
|»» timezone|Africa/Mbabane|
|»» timezone|Africa/Mogadishu|
|»» timezone|Africa/Monrovia|
|»» timezone|Africa/Nairobi|
|»» timezone|Africa/Ndjamena|
|»» timezone|Africa/Niamey|
|»» timezone|Africa/Nouakchott|
|»» timezone|Africa/Ouagadougou|
|»» timezone|Africa/Porto-Novo|
|»» timezone|Africa/Sao_Tome|
|»» timezone|Africa/Timbuktu|
|»» timezone|Africa/Tripoli|
|»» timezone|Africa/Tunis|
|»» timezone|Africa/Windhoek|
|»» timezone|America/Adak|
|»» timezone|America/Anchorage|
|»» timezone|America/Anguilla|
|»» timezone|America/Antigua|
|»» timezone|America/Araguaina|
|»» timezone|America/Argentina/Buenos_Aires|
|»» timezone|America/Argentina/Catamarca|
|»» timezone|America/Argentina/ComodRivadavia|
|»» timezone|America/Argentina/Cordoba|
|»» timezone|America/Argentina/Jujuy|
|»» timezone|America/Argentina/La_Rioja|
|»» timezone|America/Argentina/Mendoza|
|»» timezone|America/Argentina/Rio_Gallegos|
|»» timezone|America/Argentina/Salta|
|»» timezone|America/Argentina/San_Juan|
|»» timezone|America/Argentina/San_Luis|
|»» timezone|America/Argentina/Tucuman|
|»» timezone|America/Argentina/Ushuaia|
|»» timezone|America/Aruba|
|»» timezone|America/Asuncion|
|»» timezone|America/Atikokan|
|»» timezone|America/Atka|
|»» timezone|America/Bahia|
|»» timezone|America/Bahia_Banderas|
|»» timezone|America/Barbados|
|»» timezone|America/Belem|
|»» timezone|America/Belize|
|»» timezone|America/Blanc-Sablon|
|»» timezone|America/Boa_Vista|
|»» timezone|America/Bogota|
|»» timezone|America/Boise|
|»» timezone|America/Buenos_Aires|
|»» timezone|America/Cambridge_Bay|
|»» timezone|America/Campo_Grande|
|»» timezone|America/Cancun|
|»» timezone|America/Caracas|
|»» timezone|America/Catamarca|
|»» timezone|America/Cayenne|
|»» timezone|America/Cayman|
|»» timezone|America/Chicago|
|»» timezone|America/Chihuahua|
|»» timezone|America/Coral_Harbour|
|»» timezone|America/Cordoba|
|»» timezone|America/Costa_Rica|
|»» timezone|America/Creston|
|»» timezone|America/Cuiaba|
|»» timezone|America/Curacao|
|»» timezone|America/Danmarkshavn|
|»» timezone|America/Dawson|
|»» timezone|America/Dawson_Creek|
|»» timezone|America/Denver|
|»» timezone|America/Detroit|
|»» timezone|America/Dominica|
|»» timezone|America/Edmonton|
|»» timezone|America/Eirunepe|
|»» timezone|America/El_Salvador|
|»» timezone|America/Ensenada|
|»» timezone|America/Fort_Nelson|
|»» timezone|America/Fort_Wayne|
|»» timezone|America/Fortaleza|
|»» timezone|America/Glace_Bay|
|»» timezone|America/Godthab|
|»» timezone|America/Goose_Bay|
|»» timezone|America/Grand_Turk|
|»» timezone|America/Grenada|
|»» timezone|America/Guadeloupe|
|»» timezone|America/Guatemala|
|»» timezone|America/Guayaquil|
|»» timezone|America/Guyana|
|»» timezone|America/Halifax|
|»» timezone|America/Havana|
|»» timezone|America/Hermosillo|
|»» timezone|America/Indiana/Indianapolis|
|»» timezone|America/Indiana/Knox|
|»» timezone|America/Indiana/Marengo|
|»» timezone|America/Indiana/Petersburg|
|»» timezone|America/Indiana/Tell_City|
|»» timezone|America/Indiana/Vevay|
|»» timezone|America/Indiana/Vincennes|
|»» timezone|America/Indiana/Winamac|
|»» timezone|America/Indianapolis|
|»» timezone|America/Inuvik|
|»» timezone|America/Iqaluit|
|»» timezone|America/Jamaica|
|»» timezone|America/Jujuy|
|»» timezone|America/Juneau|
|»» timezone|America/Kentucky/Louisville|
|»» timezone|America/Kentucky/Monticello|
|»» timezone|America/Knox_IN|
|»» timezone|America/Kralendijk|
|»» timezone|America/La_Paz|
|»» timezone|America/Lima|
|»» timezone|America/Los_Angeles|
|»» timezone|America/Louisville|
|»» timezone|America/Lower_Princes|
|»» timezone|America/Maceio|
|»» timezone|America/Managua|
|»» timezone|America/Manaus|
|»» timezone|America/Marigot|
|»» timezone|America/Martinique|
|»» timezone|America/Matamoros|
|»» timezone|America/Mazatlan|
|»» timezone|America/Mendoza|
|»» timezone|America/Menominee|
|»» timezone|America/Merida|
|»» timezone|America/Metlakatla|
|»» timezone|America/Mexico_City|
|»» timezone|America/Miquelon|
|»» timezone|America/Moncton|
|»» timezone|America/Monterrey|
|»» timezone|America/Montevideo|
|»» timezone|America/Montreal|
|»» timezone|America/Montserrat|
|»» timezone|America/Nassau|
|»» timezone|America/New_York|
|»» timezone|America/Nipigon|
|»» timezone|America/Nome|
|»» timezone|America/Noronha|
|»» timezone|America/North_Dakota/Beulah|
|»» timezone|America/North_Dakota/Center|
|»» timezone|America/North_Dakota/New_Salem|
|»» timezone|America/Ojinaga|
|»» timezone|America/Panama|
|»» timezone|America/Pangnirtung|
|»» timezone|America/Paramaribo|
|»» timezone|America/Phoenix|
|»» timezone|America/Port-au-Prince|
|»» timezone|America/Port_of_Spain|
|»» timezone|America/Porto_Acre|
|»» timezone|America/Porto_Velho|
|»» timezone|America/Puerto_Rico|
|»» timezone|America/Punta_Arenas|
|»» timezone|America/Rainy_River|
|»» timezone|America/Rankin_Inlet|
|»» timezone|America/Recife|
|»» timezone|America/Regina|
|»» timezone|America/Resolute|
|»» timezone|America/Rio_Branco|
|»» timezone|America/Rosario|
|»» timezone|America/Santa_Isabel|
|»» timezone|America/Santarem|
|»» timezone|America/Santiago|
|»» timezone|America/Santo_Domingo|
|»» timezone|America/Sao_Paulo|
|»» timezone|America/Scoresbysund|
|»» timezone|America/Shiprock|
|»» timezone|America/Sitka|
|»» timezone|America/St_Barthelemy|
|»» timezone|America/St_Johns|
|»» timezone|America/St_Kitts|
|»» timezone|America/St_Lucia|
|»» timezone|America/St_Thomas|
|»» timezone|America/St_Vincent|
|»» timezone|America/Swift_Current|
|»» timezone|America/Tegucigalpa|
|»» timezone|America/Thule|
|»» timezone|America/Thunder_Bay|
|»» timezone|America/Tijuana|
|»» timezone|America/Toronto|
|»» timezone|America/Tortola|
|»» timezone|America/Vancouver|
|»» timezone|America/Virgin|
|»» timezone|America/Whitehorse|
|»» timezone|America/Winnipeg|
|»» timezone|America/Yakutat|
|»» timezone|America/Yellowknife|
|»» timezone|Antarctica/Casey|
|»» timezone|Antarctica/Davis|
|»» timezone|Antarctica/DumontDUrville|
|»» timezone|Antarctica/Macquarie|
|»» timezone|Antarctica/Mawson|
|»» timezone|Antarctica/McMurdo|
|»» timezone|Antarctica/Palmer|
|»» timezone|Antarctica/Rothera|
|»» timezone|Antarctica/South_Pole|
|»» timezone|Antarctica/Syowa|
|»» timezone|Antarctica/Troll|
|»» timezone|Antarctica/Vostok|
|»» timezone|Arctic/Longyearbyen|
|»» timezone|Asia/Aden|
|»» timezone|Asia/Almaty|
|»» timezone|Asia/Amman|
|»» timezone|Asia/Anadyr|
|»» timezone|Asia/Aqtau|
|»» timezone|Asia/Aqtobe|
|»» timezone|Asia/Ashgabat|
|»» timezone|Asia/Ashkhabad|
|»» timezone|Asia/Atyrau|
|»» timezone|Asia/Baghdad|
|»» timezone|Asia/Bahrain|
|»» timezone|Asia/Baku|
|»» timezone|Asia/Bangkok|
|»» timezone|Asia/Barnaul|
|»» timezone|Asia/Beirut|
|»» timezone|Asia/Bishkek|
|»» timezone|Asia/Brunei|
|»» timezone|Asia/Calcutta|
|»» timezone|Asia/Chita|
|»» timezone|Asia/Choibalsan|
|»» timezone|Asia/Chongqing|
|»» timezone|Asia/Chungking|
|»» timezone|Asia/Colombo|
|»» timezone|Asia/Dacca|
|»» timezone|Asia/Damascus|
|»» timezone|Asia/Dhaka|
|»» timezone|Asia/Dili|
|»» timezone|Asia/Dubai|
|»» timezone|Asia/Dushanbe|
|»» timezone|Asia/Famagusta|
|»» timezone|Asia/Gaza|
|»» timezone|Asia/Harbin|
|»» timezone|Asia/Hebron|
|»» timezone|Asia/Ho_Chi_Minh|
|»» timezone|Asia/Hong_Kong|
|»» timezone|Asia/Hovd|
|»» timezone|Asia/Irkutsk|
|»» timezone|Asia/Istanbul|
|»» timezone|Asia/Jakarta|
|»» timezone|Asia/Jayapura|
|»» timezone|Asia/Jerusalem|
|»» timezone|Asia/Kabul|
|»» timezone|Asia/Kamchatka|
|»» timezone|Asia/Karachi|
|»» timezone|Asia/Kashgar|
|»» timezone|Asia/Kathmandu|
|»» timezone|Asia/Katmandu|
|»» timezone|Asia/Khandyga|
|»» timezone|Asia/Kolkata|
|»» timezone|Asia/Krasnoyarsk|
|»» timezone|Asia/Kuala_Lumpur|
|»» timezone|Asia/Kuching|
|»» timezone|Asia/Kuwait|
|»» timezone|Asia/Macao|
|»» timezone|Asia/Macau|
|»» timezone|Asia/Magadan|
|»» timezone|Asia/Makassar|
|»» timezone|Asia/Manila|
|»» timezone|Asia/Muscat|
|»» timezone|Asia/Nicosia|
|»» timezone|Asia/Novokuznetsk|
|»» timezone|Asia/Novosibirsk|
|»» timezone|Asia/Omsk|
|»» timezone|Asia/Oral|
|»» timezone|Asia/Phnom_Penh|
|»» timezone|Asia/Pontianak|
|»» timezone|Asia/Pyongyang|
|»» timezone|Asia/Qatar|
|»» timezone|Asia/Qostanay|
|»» timezone|Asia/Qyzylorda|
|»» timezone|Asia/Rangoon|
|»» timezone|Asia/Riyadh|
|»» timezone|Asia/Saigon|
|»» timezone|Asia/Sakhalin|
|»» timezone|Asia/Samarkand|
|»» timezone|Asia/Seoul|
|»» timezone|Asia/Shanghai|
|»» timezone|Asia/Singapore|
|»» timezone|Asia/Srednekolymsk|
|»» timezone|Asia/Taipei|
|»» timezone|Asia/Tashkent|
|»» timezone|Asia/Tbilisi|
|»» timezone|Asia/Tehran|
|»» timezone|Asia/Tel_Aviv|
|»» timezone|Asia/Thimbu|
|»» timezone|Asia/Thimphu|
|»» timezone|Asia/Tokyo|
|»» timezone|Asia/Tomsk|
|»» timezone|Asia/Ujung_Pandang|
|»» timezone|Asia/Ulaanbaatar|
|»» timezone|Asia/Ulan_Bator|
|»» timezone|Asia/Urumqi|
|»» timezone|Asia/Ust-Nera|
|»» timezone|Asia/Vientiane|
|»» timezone|Asia/Vladivostok|
|»» timezone|Asia/Yakutsk|
|»» timezone|Asia/Yangon|
|»» timezone|Asia/Yekaterinburg|
|»» timezone|Asia/Yerevan|
|»» timezone|Atlantic/Azores|
|»» timezone|Atlantic/Bermuda|
|»» timezone|Atlantic/Canary|
|»» timezone|Atlantic/Cape_Verde|
|»» timezone|Atlantic/Faeroe|
|»» timezone|Atlantic/Faroe|
|»» timezone|Atlantic/Jan_Mayen|
|»» timezone|Atlantic/Madeira|
|»» timezone|Atlantic/Reykjavik|
|»» timezone|Atlantic/South_Georgia|
|»» timezone|Atlantic/St_Helena|
|»» timezone|Atlantic/Stanley|
|»» timezone|Australia/ACT|
|»» timezone|Australia/Adelaide|
|»» timezone|Australia/Brisbane|
|»» timezone|Australia/Broken_Hill|
|»» timezone|Australia/Canberra|
|»» timezone|Australia/Currie|
|»» timezone|Australia/Darwin|
|»» timezone|Australia/Eucla|
|»» timezone|Australia/Hobart|
|»» timezone|Australia/LHI|
|»» timezone|Australia/Lindeman|
|»» timezone|Australia/Lord_Howe|
|»» timezone|Australia/Melbourne|
|»» timezone|Australia/NSW|
|»» timezone|Australia/North|
|»» timezone|Australia/Perth|
|»» timezone|Australia/Queensland|
|»» timezone|Australia/South|
|»» timezone|Australia/Sydney|
|»» timezone|Australia/Tasmania|
|»» timezone|Australia/Victoria|
|»» timezone|Australia/West|
|»» timezone|Australia/Yancowinna|
|»» timezone|Brazil/Acre|
|»» timezone|Brazil/DeNoronha|
|»» timezone|Brazil/East|
|»» timezone|Brazil/West|
|»» timezone|CET|
|»» timezone|CST6CDT|
|»» timezone|Canada/Atlantic|
|»» timezone|Canada/Central|
|»» timezone|Canada/Eastern|
|»» timezone|Canada/Mountain|
|»» timezone|Canada/Newfoundland|
|»» timezone|Canada/Pacific|
|»» timezone|Canada/Saskatchewan|
|»» timezone|Canada/Yukon|
|»» timezone|Chile/Continental|
|»» timezone|Chile/EasterIsland|
|»» timezone|Cuba|
|»» timezone|EET|
|»» timezone|EST|
|»» timezone|EST5EDT|
|»» timezone|Egypt|
|»» timezone|Eire|
|»» timezone|Etc/GMT|
|»» timezone|Etc/GMT+0|
|»» timezone|Etc/GMT+1|
|»» timezone|Etc/GMT+10|
|»» timezone|Etc/GMT+11|
|»» timezone|Etc/GMT+12|
|»» timezone|Etc/GMT+2|
|»» timezone|Etc/GMT+3|
|»» timezone|Etc/GMT+4|
|»» timezone|Etc/GMT+5|
|»» timezone|Etc/GMT+6|
|»» timezone|Etc/GMT+7|
|»» timezone|Etc/GMT+8|
|»» timezone|Etc/GMT+9|
|»» timezone|Etc/GMT-0|
|»» timezone|Etc/GMT-1|
|»» timezone|Etc/GMT-10|
|»» timezone|Etc/GMT-11|
|»» timezone|Etc/GMT-12|
|»» timezone|Etc/GMT-13|
|»» timezone|Etc/GMT-14|
|»» timezone|Etc/GMT-2|
|»» timezone|Etc/GMT-3|
|»» timezone|Etc/GMT-4|
|»» timezone|Etc/GMT-5|
|»» timezone|Etc/GMT-6|
|»» timezone|Etc/GMT-7|
|»» timezone|Etc/GMT-8|
|»» timezone|Etc/GMT-9|
|»» timezone|Etc/GMT0|
|»» timezone|Etc/Greenwich|
|»» timezone|Etc/UCT|
|»» timezone|Etc/UTC|
|»» timezone|Etc/Universal|
|»» timezone|Etc/Zulu|
|»» timezone|Europe/Amsterdam|
|»» timezone|Europe/Andorra|
|»» timezone|Europe/Astrakhan|
|»» timezone|Europe/Athens|
|»» timezone|Europe/Belfast|
|»» timezone|Europe/Belgrade|
|»» timezone|Europe/Berlin|
|»» timezone|Europe/Bratislava|
|»» timezone|Europe/Brussels|
|»» timezone|Europe/Bucharest|
|»» timezone|Europe/Budapest|
|»» timezone|Europe/Busingen|
|»» timezone|Europe/Chisinau|
|»» timezone|Europe/Copenhagen|
|»» timezone|Europe/Dublin|
|»» timezone|Europe/Gibraltar|
|»» timezone|Europe/Guernsey|
|»» timezone|Europe/Helsinki|
|»» timezone|Europe/Isle_of_Man|
|»» timezone|Europe/Istanbul|
|»» timezone|Europe/Jersey|
|»» timezone|Europe/Kaliningrad|
|»» timezone|Europe/Kiev|
|»» timezone|Europe/Kirov|
|»» timezone|Europe/Lisbon|
|»» timezone|Europe/Ljubljana|
|»» timezone|Europe/London|
|»» timezone|Europe/Luxembourg|
|»» timezone|Europe/Madrid|
|»» timezone|Europe/Malta|
|»» timezone|Europe/Mariehamn|
|»» timezone|Europe/Minsk|
|»» timezone|Europe/Monaco|
|»» timezone|Europe/Moscow|
|»» timezone|Europe/Nicosia|
|»» timezone|Europe/Oslo|
|»» timezone|Europe/Paris|
|»» timezone|Europe/Podgorica|
|»» timezone|Europe/Prague|
|»» timezone|Europe/Riga|
|»» timezone|Europe/Rome|
|»» timezone|Europe/Samara|
|»» timezone|Europe/San_Marino|
|»» timezone|Europe/Sarajevo|
|»» timezone|Europe/Saratov|
|»» timezone|Europe/Simferopol|
|»» timezone|Europe/Skopje|
|»» timezone|Europe/Sofia|
|»» timezone|Europe/Stockholm|
|»» timezone|Europe/Tallinn|
|»» timezone|Europe/Tirane|
|»» timezone|Europe/Tiraspol|
|»» timezone|Europe/Ulyanovsk|
|»» timezone|Europe/Uzhgorod|
|»» timezone|Europe/Vaduz|
|»» timezone|Europe/Vatican|
|»» timezone|Europe/Vienna|
|»» timezone|Europe/Vilnius|
|»» timezone|Europe/Volgograd|
|»» timezone|Europe/Warsaw|
|»» timezone|Europe/Zagreb|
|»» timezone|Europe/Zaporozhye|
|»» timezone|Europe/Zurich|
|»» timezone|GB|
|»» timezone|GB-Eire|
|»» timezone|GMT|
|»» timezone|GMT+0|
|»» timezone|GMT-0|
|»» timezone|GMT0|
|»» timezone|Greenwich|
|»» timezone|HST|
|»» timezone|Hongkong|
|»» timezone|Iceland|
|»» timezone|Indian/Antananarivo|
|»» timezone|Indian/Chagos|
|»» timezone|Indian/Christmas|
|»» timezone|Indian/Cocos|
|»» timezone|Indian/Comoro|
|»» timezone|Indian/Kerguelen|
|»» timezone|Indian/Mahe|
|»» timezone|Indian/Maldives|
|»» timezone|Indian/Mauritius|
|»» timezone|Indian/Mayotte|
|»» timezone|Indian/Reunion|
|»» timezone|Iran|
|»» timezone|Israel|
|»» timezone|Jamaica|
|»» timezone|Japan|
|»» timezone|Kwajalein|
|»» timezone|Libya|
|»» timezone|MET|
|»» timezone|MST|
|»» timezone|MST7MDT|
|»» timezone|Mexico/BajaNorte|
|»» timezone|Mexico/BajaSur|
|»» timezone|Mexico/General|
|»» timezone|NZ|
|»» timezone|NZ-CHAT|
|»» timezone|Navajo|
|»» timezone|PRC|
|»» timezone|PST8PDT|
|»» timezone|Pacific/Apia|
|»» timezone|Pacific/Auckland|
|»» timezone|Pacific/Bougainville|
|»» timezone|Pacific/Chatham|
|»» timezone|Pacific/Chuuk|
|»» timezone|Pacific/Easter|
|»» timezone|Pacific/Efate|
|»» timezone|Pacific/Enderbury|
|»» timezone|Pacific/Fakaofo|
|»» timezone|Pacific/Fiji|
|»» timezone|Pacific/Funafuti|
|»» timezone|Pacific/Galapagos|
|»» timezone|Pacific/Gambier|
|»» timezone|Pacific/Guadalcanal|
|»» timezone|Pacific/Guam|
|»» timezone|Pacific/Honolulu|
|»» timezone|Pacific/Johnston|
|»» timezone|Pacific/Kiritimati|
|»» timezone|Pacific/Kosrae|
|»» timezone|Pacific/Kwajalein|
|»» timezone|Pacific/Majuro|
|»» timezone|Pacific/Marquesas|
|»» timezone|Pacific/Midway|
|»» timezone|Pacific/Nauru|
|»» timezone|Pacific/Niue|
|»» timezone|Pacific/Norfolk|
|»» timezone|Pacific/Noumea|
|»» timezone|Pacific/Pago_Pago|
|»» timezone|Pacific/Palau|
|»» timezone|Pacific/Pitcairn|
|»» timezone|Pacific/Pohnpei|
|»» timezone|Pacific/Ponape|
|»» timezone|Pacific/Port_Moresby|
|»» timezone|Pacific/Rarotonga|
|»» timezone|Pacific/Saipan|
|»» timezone|Pacific/Samoa|
|»» timezone|Pacific/Tahiti|
|»» timezone|Pacific/Tarawa|
|»» timezone|Pacific/Tongatapu|
|»» timezone|Pacific/Truk|
|»» timezone|Pacific/Wake|
|»» timezone|Pacific/Wallis|
|»» timezone|Pacific/Yap|
|»» timezone|Poland|
|»» timezone|Portugal|
|»» timezone|ROC|
|»» timezone|ROK|
|»» timezone|Singapore|
|»» timezone|Turkey|
|»» timezone|UCT|
|»» timezone|US/Alaska|
|»» timezone|US/Aleutian|
|»» timezone|US/Arizona|
|»» timezone|US/Central|
|»» timezone|US/East-Indiana|
|»» timezone|US/Eastern|
|»» timezone|US/Hawaii|
|»» timezone|US/Indiana-Starke|
|»» timezone|US/Michigan|
|»» timezone|US/Mountain|
|»» timezone|US/Pacific|
|»» timezone|US/Samoa|
|»» timezone|UTC|
|»» timezone|Universal|
|»» timezone|W-SU|
|»» timezone|WET|
|»» timezone|Zulu|

> Example responses

> 201 Response

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "status": "string",
  "type": "string",
  "config": null,
  "dateCreated": "2019-08-24T14:15:22Z",
  "project": {
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "isInternal": true,
    "isPublic": true,
    "avatar": null,
    "color": "string",
    "status": "string"
  },
  "environments": {
    "name": "string",
    "status": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "lastCheckIn": "2019-08-24T14:15:22Z",
    "nextCheckIn": "2019-08-24T14:15:22Z"
  }
}
```

<h3 id="create-a-monitor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="create-a-monitor-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» type|string|true|none|none|
|» config|any|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» project|object|true|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» environments|object|true|none|none|
|»» name|string|true|none|none|
|»» status|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» lastCheckIn|string(date-time)|true|none|none|
|»» nextCheckIn|string(date-time)|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: org:admin org:read org:write )
</aside>

## Retrieve a monitor

<a id="opIdRetrieve a monitor"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/`

Retrieves details for a monitor.

<h3 id="retrieve-a-monitor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|environment|query|array[string]|false|The name of environments to filter by.|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "status": "string",
  "type": "string",
  "config": null,
  "dateCreated": "2019-08-24T14:15:22Z",
  "project": {
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "isInternal": true,
    "isPublic": true,
    "avatar": null,
    "color": "string",
    "status": "string"
  },
  "environments": {
    "name": "string",
    "status": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "lastCheckIn": "2019-08-24T14:15:22Z",
    "nextCheckIn": "2019-08-24T14:15:22Z"
  }
}
```

<h3 id="retrieve-a-monitor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="retrieve-a-monitor-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» type|string|true|none|none|
|» config|any|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» project|object|true|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» environments|object|true|none|none|
|»» name|string|true|none|none|
|»» status|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» lastCheckIn|string(date-time)|true|none|none|
|»» nextCheckIn|string(date-time)|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Update a monitor

<a id="opIdUpdate a monitor"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.put 'https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.put('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/', headers = headers)

print(r.json())

```

```javascript
const inputBody = '{
  "project": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "type": "cron_job",
  "config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  },
  "alert_rule": {
    "environment": "string",
    "targets": [
      {
        "target_identifier": 0,
        "target_type": "string"
      }
    ]
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`PUT /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/`

Update a monitor.

> Body parameter

```json
{
  "project": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "type": "cron_job",
  "config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  },
  "alert_rule": {
    "environment": "string",
    "targets": [
      {
        "target_identifier": 0,
        "target_type": "string"
      }
    ]
  }
}
```

<h3 id="update-a-monitor-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|body|body|object|true|none|
|» project|body|string|true|none|
|» name|body|string|true|none|
|» slug|body|string|false|none|
|» status|body|string|false|none|
|» type|body|string|true|none|
|» config|body|object|true|none|
|»» schedule_type|body|string|false|Currently supports "crontab" or "interval"|
|»» schedule|body|any|true|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|»» checkin_margin|body|integer¦null|false|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|»» max_runtime|body|integer¦null|false|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|»» timezone|body|string|false|tz database style timezone string|
|» alert_rule|body|object|false|none|
|»» environment|body|string¦null|false|Name of the environment|
|»» targets|body|[object]|true|Array of dictionaries with information of the user or team to be notified|
|»»» target_identifier|body|integer|true|ID of target object|
|»»» target_type|body|string|true|One of [Member, Team]|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|active|
|» status|disabled|
|» type|cron_job|
|»» schedule_type|crontab|
|»» schedule_type|interval|
|»» timezone|Africa/Abidjan|
|»» timezone|Africa/Accra|
|»» timezone|Africa/Addis_Ababa|
|»» timezone|Africa/Algiers|
|»» timezone|Africa/Asmara|
|»» timezone|Africa/Asmera|
|»» timezone|Africa/Bamako|
|»» timezone|Africa/Bangui|
|»» timezone|Africa/Banjul|
|»» timezone|Africa/Bissau|
|»» timezone|Africa/Blantyre|
|»» timezone|Africa/Brazzaville|
|»» timezone|Africa/Bujumbura|
|»» timezone|Africa/Cairo|
|»» timezone|Africa/Casablanca|
|»» timezone|Africa/Ceuta|
|»» timezone|Africa/Conakry|
|»» timezone|Africa/Dakar|
|»» timezone|Africa/Dar_es_Salaam|
|»» timezone|Africa/Djibouti|
|»» timezone|Africa/Douala|
|»» timezone|Africa/El_Aaiun|
|»» timezone|Africa/Freetown|
|»» timezone|Africa/Gaborone|
|»» timezone|Africa/Harare|
|»» timezone|Africa/Johannesburg|
|»» timezone|Africa/Juba|
|»» timezone|Africa/Kampala|
|»» timezone|Africa/Khartoum|
|»» timezone|Africa/Kigali|
|»» timezone|Africa/Kinshasa|
|»» timezone|Africa/Lagos|
|»» timezone|Africa/Libreville|
|»» timezone|Africa/Lome|
|»» timezone|Africa/Luanda|
|»» timezone|Africa/Lubumbashi|
|»» timezone|Africa/Lusaka|
|»» timezone|Africa/Malabo|
|»» timezone|Africa/Maputo|
|»» timezone|Africa/Maseru|
|»» timezone|Africa/Mbabane|
|»» timezone|Africa/Mogadishu|
|»» timezone|Africa/Monrovia|
|»» timezone|Africa/Nairobi|
|»» timezone|Africa/Ndjamena|
|»» timezone|Africa/Niamey|
|»» timezone|Africa/Nouakchott|
|»» timezone|Africa/Ouagadougou|
|»» timezone|Africa/Porto-Novo|
|»» timezone|Africa/Sao_Tome|
|»» timezone|Africa/Timbuktu|
|»» timezone|Africa/Tripoli|
|»» timezone|Africa/Tunis|
|»» timezone|Africa/Windhoek|
|»» timezone|America/Adak|
|»» timezone|America/Anchorage|
|»» timezone|America/Anguilla|
|»» timezone|America/Antigua|
|»» timezone|America/Araguaina|
|»» timezone|America/Argentina/Buenos_Aires|
|»» timezone|America/Argentina/Catamarca|
|»» timezone|America/Argentina/ComodRivadavia|
|»» timezone|America/Argentina/Cordoba|
|»» timezone|America/Argentina/Jujuy|
|»» timezone|America/Argentina/La_Rioja|
|»» timezone|America/Argentina/Mendoza|
|»» timezone|America/Argentina/Rio_Gallegos|
|»» timezone|America/Argentina/Salta|
|»» timezone|America/Argentina/San_Juan|
|»» timezone|America/Argentina/San_Luis|
|»» timezone|America/Argentina/Tucuman|
|»» timezone|America/Argentina/Ushuaia|
|»» timezone|America/Aruba|
|»» timezone|America/Asuncion|
|»» timezone|America/Atikokan|
|»» timezone|America/Atka|
|»» timezone|America/Bahia|
|»» timezone|America/Bahia_Banderas|
|»» timezone|America/Barbados|
|»» timezone|America/Belem|
|»» timezone|America/Belize|
|»» timezone|America/Blanc-Sablon|
|»» timezone|America/Boa_Vista|
|»» timezone|America/Bogota|
|»» timezone|America/Boise|
|»» timezone|America/Buenos_Aires|
|»» timezone|America/Cambridge_Bay|
|»» timezone|America/Campo_Grande|
|»» timezone|America/Cancun|
|»» timezone|America/Caracas|
|»» timezone|America/Catamarca|
|»» timezone|America/Cayenne|
|»» timezone|America/Cayman|
|»» timezone|America/Chicago|
|»» timezone|America/Chihuahua|
|»» timezone|America/Coral_Harbour|
|»» timezone|America/Cordoba|
|»» timezone|America/Costa_Rica|
|»» timezone|America/Creston|
|»» timezone|America/Cuiaba|
|»» timezone|America/Curacao|
|»» timezone|America/Danmarkshavn|
|»» timezone|America/Dawson|
|»» timezone|America/Dawson_Creek|
|»» timezone|America/Denver|
|»» timezone|America/Detroit|
|»» timezone|America/Dominica|
|»» timezone|America/Edmonton|
|»» timezone|America/Eirunepe|
|»» timezone|America/El_Salvador|
|»» timezone|America/Ensenada|
|»» timezone|America/Fort_Nelson|
|»» timezone|America/Fort_Wayne|
|»» timezone|America/Fortaleza|
|»» timezone|America/Glace_Bay|
|»» timezone|America/Godthab|
|»» timezone|America/Goose_Bay|
|»» timezone|America/Grand_Turk|
|»» timezone|America/Grenada|
|»» timezone|America/Guadeloupe|
|»» timezone|America/Guatemala|
|»» timezone|America/Guayaquil|
|»» timezone|America/Guyana|
|»» timezone|America/Halifax|
|»» timezone|America/Havana|
|»» timezone|America/Hermosillo|
|»» timezone|America/Indiana/Indianapolis|
|»» timezone|America/Indiana/Knox|
|»» timezone|America/Indiana/Marengo|
|»» timezone|America/Indiana/Petersburg|
|»» timezone|America/Indiana/Tell_City|
|»» timezone|America/Indiana/Vevay|
|»» timezone|America/Indiana/Vincennes|
|»» timezone|America/Indiana/Winamac|
|»» timezone|America/Indianapolis|
|»» timezone|America/Inuvik|
|»» timezone|America/Iqaluit|
|»» timezone|America/Jamaica|
|»» timezone|America/Jujuy|
|»» timezone|America/Juneau|
|»» timezone|America/Kentucky/Louisville|
|»» timezone|America/Kentucky/Monticello|
|»» timezone|America/Knox_IN|
|»» timezone|America/Kralendijk|
|»» timezone|America/La_Paz|
|»» timezone|America/Lima|
|»» timezone|America/Los_Angeles|
|»» timezone|America/Louisville|
|»» timezone|America/Lower_Princes|
|»» timezone|America/Maceio|
|»» timezone|America/Managua|
|»» timezone|America/Manaus|
|»» timezone|America/Marigot|
|»» timezone|America/Martinique|
|»» timezone|America/Matamoros|
|»» timezone|America/Mazatlan|
|»» timezone|America/Mendoza|
|»» timezone|America/Menominee|
|»» timezone|America/Merida|
|»» timezone|America/Metlakatla|
|»» timezone|America/Mexico_City|
|»» timezone|America/Miquelon|
|»» timezone|America/Moncton|
|»» timezone|America/Monterrey|
|»» timezone|America/Montevideo|
|»» timezone|America/Montreal|
|»» timezone|America/Montserrat|
|»» timezone|America/Nassau|
|»» timezone|America/New_York|
|»» timezone|America/Nipigon|
|»» timezone|America/Nome|
|»» timezone|America/Noronha|
|»» timezone|America/North_Dakota/Beulah|
|»» timezone|America/North_Dakota/Center|
|»» timezone|America/North_Dakota/New_Salem|
|»» timezone|America/Ojinaga|
|»» timezone|America/Panama|
|»» timezone|America/Pangnirtung|
|»» timezone|America/Paramaribo|
|»» timezone|America/Phoenix|
|»» timezone|America/Port-au-Prince|
|»» timezone|America/Port_of_Spain|
|»» timezone|America/Porto_Acre|
|»» timezone|America/Porto_Velho|
|»» timezone|America/Puerto_Rico|
|»» timezone|America/Punta_Arenas|
|»» timezone|America/Rainy_River|
|»» timezone|America/Rankin_Inlet|
|»» timezone|America/Recife|
|»» timezone|America/Regina|
|»» timezone|America/Resolute|
|»» timezone|America/Rio_Branco|
|»» timezone|America/Rosario|
|»» timezone|America/Santa_Isabel|
|»» timezone|America/Santarem|
|»» timezone|America/Santiago|
|»» timezone|America/Santo_Domingo|
|»» timezone|America/Sao_Paulo|
|»» timezone|America/Scoresbysund|
|»» timezone|America/Shiprock|
|»» timezone|America/Sitka|
|»» timezone|America/St_Barthelemy|
|»» timezone|America/St_Johns|
|»» timezone|America/St_Kitts|
|»» timezone|America/St_Lucia|
|»» timezone|America/St_Thomas|
|»» timezone|America/St_Vincent|
|»» timezone|America/Swift_Current|
|»» timezone|America/Tegucigalpa|
|»» timezone|America/Thule|
|»» timezone|America/Thunder_Bay|
|»» timezone|America/Tijuana|
|»» timezone|America/Toronto|
|»» timezone|America/Tortola|
|»» timezone|America/Vancouver|
|»» timezone|America/Virgin|
|»» timezone|America/Whitehorse|
|»» timezone|America/Winnipeg|
|»» timezone|America/Yakutat|
|»» timezone|America/Yellowknife|
|»» timezone|Antarctica/Casey|
|»» timezone|Antarctica/Davis|
|»» timezone|Antarctica/DumontDUrville|
|»» timezone|Antarctica/Macquarie|
|»» timezone|Antarctica/Mawson|
|»» timezone|Antarctica/McMurdo|
|»» timezone|Antarctica/Palmer|
|»» timezone|Antarctica/Rothera|
|»» timezone|Antarctica/South_Pole|
|»» timezone|Antarctica/Syowa|
|»» timezone|Antarctica/Troll|
|»» timezone|Antarctica/Vostok|
|»» timezone|Arctic/Longyearbyen|
|»» timezone|Asia/Aden|
|»» timezone|Asia/Almaty|
|»» timezone|Asia/Amman|
|»» timezone|Asia/Anadyr|
|»» timezone|Asia/Aqtau|
|»» timezone|Asia/Aqtobe|
|»» timezone|Asia/Ashgabat|
|»» timezone|Asia/Ashkhabad|
|»» timezone|Asia/Atyrau|
|»» timezone|Asia/Baghdad|
|»» timezone|Asia/Bahrain|
|»» timezone|Asia/Baku|
|»» timezone|Asia/Bangkok|
|»» timezone|Asia/Barnaul|
|»» timezone|Asia/Beirut|
|»» timezone|Asia/Bishkek|
|»» timezone|Asia/Brunei|
|»» timezone|Asia/Calcutta|
|»» timezone|Asia/Chita|
|»» timezone|Asia/Choibalsan|
|»» timezone|Asia/Chongqing|
|»» timezone|Asia/Chungking|
|»» timezone|Asia/Colombo|
|»» timezone|Asia/Dacca|
|»» timezone|Asia/Damascus|
|»» timezone|Asia/Dhaka|
|»» timezone|Asia/Dili|
|»» timezone|Asia/Dubai|
|»» timezone|Asia/Dushanbe|
|»» timezone|Asia/Famagusta|
|»» timezone|Asia/Gaza|
|»» timezone|Asia/Harbin|
|»» timezone|Asia/Hebron|
|»» timezone|Asia/Ho_Chi_Minh|
|»» timezone|Asia/Hong_Kong|
|»» timezone|Asia/Hovd|
|»» timezone|Asia/Irkutsk|
|»» timezone|Asia/Istanbul|
|»» timezone|Asia/Jakarta|
|»» timezone|Asia/Jayapura|
|»» timezone|Asia/Jerusalem|
|»» timezone|Asia/Kabul|
|»» timezone|Asia/Kamchatka|
|»» timezone|Asia/Karachi|
|»» timezone|Asia/Kashgar|
|»» timezone|Asia/Kathmandu|
|»» timezone|Asia/Katmandu|
|»» timezone|Asia/Khandyga|
|»» timezone|Asia/Kolkata|
|»» timezone|Asia/Krasnoyarsk|
|»» timezone|Asia/Kuala_Lumpur|
|»» timezone|Asia/Kuching|
|»» timezone|Asia/Kuwait|
|»» timezone|Asia/Macao|
|»» timezone|Asia/Macau|
|»» timezone|Asia/Magadan|
|»» timezone|Asia/Makassar|
|»» timezone|Asia/Manila|
|»» timezone|Asia/Muscat|
|»» timezone|Asia/Nicosia|
|»» timezone|Asia/Novokuznetsk|
|»» timezone|Asia/Novosibirsk|
|»» timezone|Asia/Omsk|
|»» timezone|Asia/Oral|
|»» timezone|Asia/Phnom_Penh|
|»» timezone|Asia/Pontianak|
|»» timezone|Asia/Pyongyang|
|»» timezone|Asia/Qatar|
|»» timezone|Asia/Qostanay|
|»» timezone|Asia/Qyzylorda|
|»» timezone|Asia/Rangoon|
|»» timezone|Asia/Riyadh|
|»» timezone|Asia/Saigon|
|»» timezone|Asia/Sakhalin|
|»» timezone|Asia/Samarkand|
|»» timezone|Asia/Seoul|
|»» timezone|Asia/Shanghai|
|»» timezone|Asia/Singapore|
|»» timezone|Asia/Srednekolymsk|
|»» timezone|Asia/Taipei|
|»» timezone|Asia/Tashkent|
|»» timezone|Asia/Tbilisi|
|»» timezone|Asia/Tehran|
|»» timezone|Asia/Tel_Aviv|
|»» timezone|Asia/Thimbu|
|»» timezone|Asia/Thimphu|
|»» timezone|Asia/Tokyo|
|»» timezone|Asia/Tomsk|
|»» timezone|Asia/Ujung_Pandang|
|»» timezone|Asia/Ulaanbaatar|
|»» timezone|Asia/Ulan_Bator|
|»» timezone|Asia/Urumqi|
|»» timezone|Asia/Ust-Nera|
|»» timezone|Asia/Vientiane|
|»» timezone|Asia/Vladivostok|
|»» timezone|Asia/Yakutsk|
|»» timezone|Asia/Yangon|
|»» timezone|Asia/Yekaterinburg|
|»» timezone|Asia/Yerevan|
|»» timezone|Atlantic/Azores|
|»» timezone|Atlantic/Bermuda|
|»» timezone|Atlantic/Canary|
|»» timezone|Atlantic/Cape_Verde|
|»» timezone|Atlantic/Faeroe|
|»» timezone|Atlantic/Faroe|
|»» timezone|Atlantic/Jan_Mayen|
|»» timezone|Atlantic/Madeira|
|»» timezone|Atlantic/Reykjavik|
|»» timezone|Atlantic/South_Georgia|
|»» timezone|Atlantic/St_Helena|
|»» timezone|Atlantic/Stanley|
|»» timezone|Australia/ACT|
|»» timezone|Australia/Adelaide|
|»» timezone|Australia/Brisbane|
|»» timezone|Australia/Broken_Hill|
|»» timezone|Australia/Canberra|
|»» timezone|Australia/Currie|
|»» timezone|Australia/Darwin|
|»» timezone|Australia/Eucla|
|»» timezone|Australia/Hobart|
|»» timezone|Australia/LHI|
|»» timezone|Australia/Lindeman|
|»» timezone|Australia/Lord_Howe|
|»» timezone|Australia/Melbourne|
|»» timezone|Australia/NSW|
|»» timezone|Australia/North|
|»» timezone|Australia/Perth|
|»» timezone|Australia/Queensland|
|»» timezone|Australia/South|
|»» timezone|Australia/Sydney|
|»» timezone|Australia/Tasmania|
|»» timezone|Australia/Victoria|
|»» timezone|Australia/West|
|»» timezone|Australia/Yancowinna|
|»» timezone|Brazil/Acre|
|»» timezone|Brazil/DeNoronha|
|»» timezone|Brazil/East|
|»» timezone|Brazil/West|
|»» timezone|CET|
|»» timezone|CST6CDT|
|»» timezone|Canada/Atlantic|
|»» timezone|Canada/Central|
|»» timezone|Canada/Eastern|
|»» timezone|Canada/Mountain|
|»» timezone|Canada/Newfoundland|
|»» timezone|Canada/Pacific|
|»» timezone|Canada/Saskatchewan|
|»» timezone|Canada/Yukon|
|»» timezone|Chile/Continental|
|»» timezone|Chile/EasterIsland|
|»» timezone|Cuba|
|»» timezone|EET|
|»» timezone|EST|
|»» timezone|EST5EDT|
|»» timezone|Egypt|
|»» timezone|Eire|
|»» timezone|Etc/GMT|
|»» timezone|Etc/GMT+0|
|»» timezone|Etc/GMT+1|
|»» timezone|Etc/GMT+10|
|»» timezone|Etc/GMT+11|
|»» timezone|Etc/GMT+12|
|»» timezone|Etc/GMT+2|
|»» timezone|Etc/GMT+3|
|»» timezone|Etc/GMT+4|
|»» timezone|Etc/GMT+5|
|»» timezone|Etc/GMT+6|
|»» timezone|Etc/GMT+7|
|»» timezone|Etc/GMT+8|
|»» timezone|Etc/GMT+9|
|»» timezone|Etc/GMT-0|
|»» timezone|Etc/GMT-1|
|»» timezone|Etc/GMT-10|
|»» timezone|Etc/GMT-11|
|»» timezone|Etc/GMT-12|
|»» timezone|Etc/GMT-13|
|»» timezone|Etc/GMT-14|
|»» timezone|Etc/GMT-2|
|»» timezone|Etc/GMT-3|
|»» timezone|Etc/GMT-4|
|»» timezone|Etc/GMT-5|
|»» timezone|Etc/GMT-6|
|»» timezone|Etc/GMT-7|
|»» timezone|Etc/GMT-8|
|»» timezone|Etc/GMT-9|
|»» timezone|Etc/GMT0|
|»» timezone|Etc/Greenwich|
|»» timezone|Etc/UCT|
|»» timezone|Etc/UTC|
|»» timezone|Etc/Universal|
|»» timezone|Etc/Zulu|
|»» timezone|Europe/Amsterdam|
|»» timezone|Europe/Andorra|
|»» timezone|Europe/Astrakhan|
|»» timezone|Europe/Athens|
|»» timezone|Europe/Belfast|
|»» timezone|Europe/Belgrade|
|»» timezone|Europe/Berlin|
|»» timezone|Europe/Bratislava|
|»» timezone|Europe/Brussels|
|»» timezone|Europe/Bucharest|
|»» timezone|Europe/Budapest|
|»» timezone|Europe/Busingen|
|»» timezone|Europe/Chisinau|
|»» timezone|Europe/Copenhagen|
|»» timezone|Europe/Dublin|
|»» timezone|Europe/Gibraltar|
|»» timezone|Europe/Guernsey|
|»» timezone|Europe/Helsinki|
|»» timezone|Europe/Isle_of_Man|
|»» timezone|Europe/Istanbul|
|»» timezone|Europe/Jersey|
|»» timezone|Europe/Kaliningrad|
|»» timezone|Europe/Kiev|
|»» timezone|Europe/Kirov|
|»» timezone|Europe/Lisbon|
|»» timezone|Europe/Ljubljana|
|»» timezone|Europe/London|
|»» timezone|Europe/Luxembourg|
|»» timezone|Europe/Madrid|
|»» timezone|Europe/Malta|
|»» timezone|Europe/Mariehamn|
|»» timezone|Europe/Minsk|
|»» timezone|Europe/Monaco|
|»» timezone|Europe/Moscow|
|»» timezone|Europe/Nicosia|
|»» timezone|Europe/Oslo|
|»» timezone|Europe/Paris|
|»» timezone|Europe/Podgorica|
|»» timezone|Europe/Prague|
|»» timezone|Europe/Riga|
|»» timezone|Europe/Rome|
|»» timezone|Europe/Samara|
|»» timezone|Europe/San_Marino|
|»» timezone|Europe/Sarajevo|
|»» timezone|Europe/Saratov|
|»» timezone|Europe/Simferopol|
|»» timezone|Europe/Skopje|
|»» timezone|Europe/Sofia|
|»» timezone|Europe/Stockholm|
|»» timezone|Europe/Tallinn|
|»» timezone|Europe/Tirane|
|»» timezone|Europe/Tiraspol|
|»» timezone|Europe/Ulyanovsk|
|»» timezone|Europe/Uzhgorod|
|»» timezone|Europe/Vaduz|
|»» timezone|Europe/Vatican|
|»» timezone|Europe/Vienna|
|»» timezone|Europe/Vilnius|
|»» timezone|Europe/Volgograd|
|»» timezone|Europe/Warsaw|
|»» timezone|Europe/Zagreb|
|»» timezone|Europe/Zaporozhye|
|»» timezone|Europe/Zurich|
|»» timezone|GB|
|»» timezone|GB-Eire|
|»» timezone|GMT|
|»» timezone|GMT+0|
|»» timezone|GMT-0|
|»» timezone|GMT0|
|»» timezone|Greenwich|
|»» timezone|HST|
|»» timezone|Hongkong|
|»» timezone|Iceland|
|»» timezone|Indian/Antananarivo|
|»» timezone|Indian/Chagos|
|»» timezone|Indian/Christmas|
|»» timezone|Indian/Cocos|
|»» timezone|Indian/Comoro|
|»» timezone|Indian/Kerguelen|
|»» timezone|Indian/Mahe|
|»» timezone|Indian/Maldives|
|»» timezone|Indian/Mauritius|
|»» timezone|Indian/Mayotte|
|»» timezone|Indian/Reunion|
|»» timezone|Iran|
|»» timezone|Israel|
|»» timezone|Jamaica|
|»» timezone|Japan|
|»» timezone|Kwajalein|
|»» timezone|Libya|
|»» timezone|MET|
|»» timezone|MST|
|»» timezone|MST7MDT|
|»» timezone|Mexico/BajaNorte|
|»» timezone|Mexico/BajaSur|
|»» timezone|Mexico/General|
|»» timezone|NZ|
|»» timezone|NZ-CHAT|
|»» timezone|Navajo|
|»» timezone|PRC|
|»» timezone|PST8PDT|
|»» timezone|Pacific/Apia|
|»» timezone|Pacific/Auckland|
|»» timezone|Pacific/Bougainville|
|»» timezone|Pacific/Chatham|
|»» timezone|Pacific/Chuuk|
|»» timezone|Pacific/Easter|
|»» timezone|Pacific/Efate|
|»» timezone|Pacific/Enderbury|
|»» timezone|Pacific/Fakaofo|
|»» timezone|Pacific/Fiji|
|»» timezone|Pacific/Funafuti|
|»» timezone|Pacific/Galapagos|
|»» timezone|Pacific/Gambier|
|»» timezone|Pacific/Guadalcanal|
|»» timezone|Pacific/Guam|
|»» timezone|Pacific/Honolulu|
|»» timezone|Pacific/Johnston|
|»» timezone|Pacific/Kiritimati|
|»» timezone|Pacific/Kosrae|
|»» timezone|Pacific/Kwajalein|
|»» timezone|Pacific/Majuro|
|»» timezone|Pacific/Marquesas|
|»» timezone|Pacific/Midway|
|»» timezone|Pacific/Nauru|
|»» timezone|Pacific/Niue|
|»» timezone|Pacific/Norfolk|
|»» timezone|Pacific/Noumea|
|»» timezone|Pacific/Pago_Pago|
|»» timezone|Pacific/Palau|
|»» timezone|Pacific/Pitcairn|
|»» timezone|Pacific/Pohnpei|
|»» timezone|Pacific/Ponape|
|»» timezone|Pacific/Port_Moresby|
|»» timezone|Pacific/Rarotonga|
|»» timezone|Pacific/Saipan|
|»» timezone|Pacific/Samoa|
|»» timezone|Pacific/Tahiti|
|»» timezone|Pacific/Tarawa|
|»» timezone|Pacific/Tongatapu|
|»» timezone|Pacific/Truk|
|»» timezone|Pacific/Wake|
|»» timezone|Pacific/Wallis|
|»» timezone|Pacific/Yap|
|»» timezone|Poland|
|»» timezone|Portugal|
|»» timezone|ROC|
|»» timezone|ROK|
|»» timezone|Singapore|
|»» timezone|Turkey|
|»» timezone|UCT|
|»» timezone|US/Alaska|
|»» timezone|US/Aleutian|
|»» timezone|US/Arizona|
|»» timezone|US/Central|
|»» timezone|US/East-Indiana|
|»» timezone|US/Eastern|
|»» timezone|US/Hawaii|
|»» timezone|US/Indiana-Starke|
|»» timezone|US/Michigan|
|»» timezone|US/Mountain|
|»» timezone|US/Pacific|
|»» timezone|US/Samoa|
|»» timezone|UTC|
|»» timezone|Universal|
|»» timezone|W-SU|
|»» timezone|WET|
|»» timezone|Zulu|

> Example responses

> 200 Response

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "status": "string",
  "type": "string",
  "config": null,
  "dateCreated": "2019-08-24T14:15:22Z",
  "project": {
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "isInternal": true,
    "isPublic": true,
    "avatar": null,
    "color": "string",
    "status": "string"
  },
  "environments": {
    "name": "string",
    "status": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "lastCheckIn": "2019-08-24T14:15:22Z",
    "nextCheckIn": "2019-08-24T14:15:22Z"
  }
}
```

<h3 id="update-a-monitor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="update-a-monitor-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» status|string|true|none|none|
|» type|string|true|none|none|
|» config|any|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» project|object|true|none|none|
|»» stats|any|false|none|none|
|»» transactionStats|any|false|none|none|
|»» sessionStats|any|false|none|none|
|»» id|string|true|none|none|
|»» slug|string|true|none|none|
|»» name|string|true|none|none|
|»» platform|string¦null|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» isBookmarked|boolean|true|none|none|
|»» isMember|boolean|true|none|none|
|»» features|[string]|true|none|none|
|»» firstEvent|string(date-time)¦null|true|none|none|
|»» firstTransactionEvent|boolean|true|none|none|
|»» access|[string]|true|none|none|
|»» hasAccess|boolean|true|none|none|
|»» hasMinifiedStackTrace|boolean|true|none|none|
|»» hasMonitors|boolean|true|none|none|
|»» hasProfiles|boolean|true|none|none|
|»» hasReplays|boolean|true|none|none|
|»» hasSessions|boolean|true|none|none|
|»» isInternal|boolean|true|none|none|
|»» isPublic|boolean|true|none|none|
|»» avatar|any|true|none|none|
|»» color|string|true|none|none|
|»» status|string|true|none|none|
|» environments|object|true|none|none|
|»» name|string|true|none|none|
|»» status|string|true|none|none|
|»» dateCreated|string(date-time)|true|none|none|
|»» lastCheckIn|string(date-time)|true|none|none|
|»» nextCheckIn|string(date-time)|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

## Delete a monitor or monitor environments

<a id="opIdDelete a monitor or monitor environments"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/', headers = headers)

print(r.json())

```

```javascript

const headers = {
  'Authorization':'Bearer {access-token}'
};

fetch('https://sentry.io/api/0/organizations/{organization_slug}/monitors/{monitor_slug}/',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /api/0/organizations/{organization_slug}/monitors/{monitor_slug}/`

Delete a monitor or monitor environments.

<h3 id="delete-a-monitor-or-monitor-environments-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|organization_slug|path|string|true|The slug of the organization the resource belongs to.|
|monitor_slug|path|string|true|The slug of the monitor|
|environment|query|array[string]|false|The name of environments to filter by.|

<h3 id="delete-a-monitor-or-monitor-environments-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Accepted|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
auth_token ( Scopes: project:admin project:read project:write )
</aside>

# Schemas

<h2 id="tocS_CheckInList">CheckInList</h2>
<!-- backwards compatibility -->
<a id="schemacheckinlist"></a>
<a id="schema_CheckInList"></a>
<a id="tocScheckinlist"></a>
<a id="tocscheckinlist"></a>

```json
[
  {
    "id": "string",
    "environment": "string",
    "status": "string",
    "duration": 0,
    "dateCreated": "2019-08-24T14:15:22Z",
    "attachmentId": "string",
    "expectedTime": "2019-08-24T14:15:22Z",
    "monitorConfig": null
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|environment|string|true|none|none|
|status|string|true|none|none|
|duration|integer|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|attachmentId|string|true|none|none|
|expectedTime|string(date-time)|true|none|none|
|monitorConfig|any|true|none|none|

<h2 id="tocS_ConfigValidator">ConfigValidator</h2>
<!-- backwards compatibility -->
<a id="schemaconfigvalidator"></a>
<a id="schema_ConfigValidator"></a>
<a id="tocSconfigvalidator"></a>
<a id="tocsconfigvalidator"></a>

```json
{
  "schedule_type": "crontab",
  "schedule": null,
  "checkin_margin": 0,
  "max_runtime": 1,
  "timezone": "Africa/Abidjan"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schedule_type|string|false|none|Currently supports "crontab" or "interval"|
|schedule|any|true|none|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|checkin_margin|integer¦null|false|none|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|max_runtime|integer¦null|false|none|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|timezone|string|false|none|tz database style timezone string|

#### Enumerated Values

|Property|Value|
|---|---|
|schedule_type|crontab|
|schedule_type|interval|
|timezone|Africa/Abidjan|
|timezone|Africa/Accra|
|timezone|Africa/Addis_Ababa|
|timezone|Africa/Algiers|
|timezone|Africa/Asmara|
|timezone|Africa/Asmera|
|timezone|Africa/Bamako|
|timezone|Africa/Bangui|
|timezone|Africa/Banjul|
|timezone|Africa/Bissau|
|timezone|Africa/Blantyre|
|timezone|Africa/Brazzaville|
|timezone|Africa/Bujumbura|
|timezone|Africa/Cairo|
|timezone|Africa/Casablanca|
|timezone|Africa/Ceuta|
|timezone|Africa/Conakry|
|timezone|Africa/Dakar|
|timezone|Africa/Dar_es_Salaam|
|timezone|Africa/Djibouti|
|timezone|Africa/Douala|
|timezone|Africa/El_Aaiun|
|timezone|Africa/Freetown|
|timezone|Africa/Gaborone|
|timezone|Africa/Harare|
|timezone|Africa/Johannesburg|
|timezone|Africa/Juba|
|timezone|Africa/Kampala|
|timezone|Africa/Khartoum|
|timezone|Africa/Kigali|
|timezone|Africa/Kinshasa|
|timezone|Africa/Lagos|
|timezone|Africa/Libreville|
|timezone|Africa/Lome|
|timezone|Africa/Luanda|
|timezone|Africa/Lubumbashi|
|timezone|Africa/Lusaka|
|timezone|Africa/Malabo|
|timezone|Africa/Maputo|
|timezone|Africa/Maseru|
|timezone|Africa/Mbabane|
|timezone|Africa/Mogadishu|
|timezone|Africa/Monrovia|
|timezone|Africa/Nairobi|
|timezone|Africa/Ndjamena|
|timezone|Africa/Niamey|
|timezone|Africa/Nouakchott|
|timezone|Africa/Ouagadougou|
|timezone|Africa/Porto-Novo|
|timezone|Africa/Sao_Tome|
|timezone|Africa/Timbuktu|
|timezone|Africa/Tripoli|
|timezone|Africa/Tunis|
|timezone|Africa/Windhoek|
|timezone|America/Adak|
|timezone|America/Anchorage|
|timezone|America/Anguilla|
|timezone|America/Antigua|
|timezone|America/Araguaina|
|timezone|America/Argentina/Buenos_Aires|
|timezone|America/Argentina/Catamarca|
|timezone|America/Argentina/ComodRivadavia|
|timezone|America/Argentina/Cordoba|
|timezone|America/Argentina/Jujuy|
|timezone|America/Argentina/La_Rioja|
|timezone|America/Argentina/Mendoza|
|timezone|America/Argentina/Rio_Gallegos|
|timezone|America/Argentina/Salta|
|timezone|America/Argentina/San_Juan|
|timezone|America/Argentina/San_Luis|
|timezone|America/Argentina/Tucuman|
|timezone|America/Argentina/Ushuaia|
|timezone|America/Aruba|
|timezone|America/Asuncion|
|timezone|America/Atikokan|
|timezone|America/Atka|
|timezone|America/Bahia|
|timezone|America/Bahia_Banderas|
|timezone|America/Barbados|
|timezone|America/Belem|
|timezone|America/Belize|
|timezone|America/Blanc-Sablon|
|timezone|America/Boa_Vista|
|timezone|America/Bogota|
|timezone|America/Boise|
|timezone|America/Buenos_Aires|
|timezone|America/Cambridge_Bay|
|timezone|America/Campo_Grande|
|timezone|America/Cancun|
|timezone|America/Caracas|
|timezone|America/Catamarca|
|timezone|America/Cayenne|
|timezone|America/Cayman|
|timezone|America/Chicago|
|timezone|America/Chihuahua|
|timezone|America/Coral_Harbour|
|timezone|America/Cordoba|
|timezone|America/Costa_Rica|
|timezone|America/Creston|
|timezone|America/Cuiaba|
|timezone|America/Curacao|
|timezone|America/Danmarkshavn|
|timezone|America/Dawson|
|timezone|America/Dawson_Creek|
|timezone|America/Denver|
|timezone|America/Detroit|
|timezone|America/Dominica|
|timezone|America/Edmonton|
|timezone|America/Eirunepe|
|timezone|America/El_Salvador|
|timezone|America/Ensenada|
|timezone|America/Fort_Nelson|
|timezone|America/Fort_Wayne|
|timezone|America/Fortaleza|
|timezone|America/Glace_Bay|
|timezone|America/Godthab|
|timezone|America/Goose_Bay|
|timezone|America/Grand_Turk|
|timezone|America/Grenada|
|timezone|America/Guadeloupe|
|timezone|America/Guatemala|
|timezone|America/Guayaquil|
|timezone|America/Guyana|
|timezone|America/Halifax|
|timezone|America/Havana|
|timezone|America/Hermosillo|
|timezone|America/Indiana/Indianapolis|
|timezone|America/Indiana/Knox|
|timezone|America/Indiana/Marengo|
|timezone|America/Indiana/Petersburg|
|timezone|America/Indiana/Tell_City|
|timezone|America/Indiana/Vevay|
|timezone|America/Indiana/Vincennes|
|timezone|America/Indiana/Winamac|
|timezone|America/Indianapolis|
|timezone|America/Inuvik|
|timezone|America/Iqaluit|
|timezone|America/Jamaica|
|timezone|America/Jujuy|
|timezone|America/Juneau|
|timezone|America/Kentucky/Louisville|
|timezone|America/Kentucky/Monticello|
|timezone|America/Knox_IN|
|timezone|America/Kralendijk|
|timezone|America/La_Paz|
|timezone|America/Lima|
|timezone|America/Los_Angeles|
|timezone|America/Louisville|
|timezone|America/Lower_Princes|
|timezone|America/Maceio|
|timezone|America/Managua|
|timezone|America/Manaus|
|timezone|America/Marigot|
|timezone|America/Martinique|
|timezone|America/Matamoros|
|timezone|America/Mazatlan|
|timezone|America/Mendoza|
|timezone|America/Menominee|
|timezone|America/Merida|
|timezone|America/Metlakatla|
|timezone|America/Mexico_City|
|timezone|America/Miquelon|
|timezone|America/Moncton|
|timezone|America/Monterrey|
|timezone|America/Montevideo|
|timezone|America/Montreal|
|timezone|America/Montserrat|
|timezone|America/Nassau|
|timezone|America/New_York|
|timezone|America/Nipigon|
|timezone|America/Nome|
|timezone|America/Noronha|
|timezone|America/North_Dakota/Beulah|
|timezone|America/North_Dakota/Center|
|timezone|America/North_Dakota/New_Salem|
|timezone|America/Ojinaga|
|timezone|America/Panama|
|timezone|America/Pangnirtung|
|timezone|America/Paramaribo|
|timezone|America/Phoenix|
|timezone|America/Port-au-Prince|
|timezone|America/Port_of_Spain|
|timezone|America/Porto_Acre|
|timezone|America/Porto_Velho|
|timezone|America/Puerto_Rico|
|timezone|America/Punta_Arenas|
|timezone|America/Rainy_River|
|timezone|America/Rankin_Inlet|
|timezone|America/Recife|
|timezone|America/Regina|
|timezone|America/Resolute|
|timezone|America/Rio_Branco|
|timezone|America/Rosario|
|timezone|America/Santa_Isabel|
|timezone|America/Santarem|
|timezone|America/Santiago|
|timezone|America/Santo_Domingo|
|timezone|America/Sao_Paulo|
|timezone|America/Scoresbysund|
|timezone|America/Shiprock|
|timezone|America/Sitka|
|timezone|America/St_Barthelemy|
|timezone|America/St_Johns|
|timezone|America/St_Kitts|
|timezone|America/St_Lucia|
|timezone|America/St_Thomas|
|timezone|America/St_Vincent|
|timezone|America/Swift_Current|
|timezone|America/Tegucigalpa|
|timezone|America/Thule|
|timezone|America/Thunder_Bay|
|timezone|America/Tijuana|
|timezone|America/Toronto|
|timezone|America/Tortola|
|timezone|America/Vancouver|
|timezone|America/Virgin|
|timezone|America/Whitehorse|
|timezone|America/Winnipeg|
|timezone|America/Yakutat|
|timezone|America/Yellowknife|
|timezone|Antarctica/Casey|
|timezone|Antarctica/Davis|
|timezone|Antarctica/DumontDUrville|
|timezone|Antarctica/Macquarie|
|timezone|Antarctica/Mawson|
|timezone|Antarctica/McMurdo|
|timezone|Antarctica/Palmer|
|timezone|Antarctica/Rothera|
|timezone|Antarctica/South_Pole|
|timezone|Antarctica/Syowa|
|timezone|Antarctica/Troll|
|timezone|Antarctica/Vostok|
|timezone|Arctic/Longyearbyen|
|timezone|Asia/Aden|
|timezone|Asia/Almaty|
|timezone|Asia/Amman|
|timezone|Asia/Anadyr|
|timezone|Asia/Aqtau|
|timezone|Asia/Aqtobe|
|timezone|Asia/Ashgabat|
|timezone|Asia/Ashkhabad|
|timezone|Asia/Atyrau|
|timezone|Asia/Baghdad|
|timezone|Asia/Bahrain|
|timezone|Asia/Baku|
|timezone|Asia/Bangkok|
|timezone|Asia/Barnaul|
|timezone|Asia/Beirut|
|timezone|Asia/Bishkek|
|timezone|Asia/Brunei|
|timezone|Asia/Calcutta|
|timezone|Asia/Chita|
|timezone|Asia/Choibalsan|
|timezone|Asia/Chongqing|
|timezone|Asia/Chungking|
|timezone|Asia/Colombo|
|timezone|Asia/Dacca|
|timezone|Asia/Damascus|
|timezone|Asia/Dhaka|
|timezone|Asia/Dili|
|timezone|Asia/Dubai|
|timezone|Asia/Dushanbe|
|timezone|Asia/Famagusta|
|timezone|Asia/Gaza|
|timezone|Asia/Harbin|
|timezone|Asia/Hebron|
|timezone|Asia/Ho_Chi_Minh|
|timezone|Asia/Hong_Kong|
|timezone|Asia/Hovd|
|timezone|Asia/Irkutsk|
|timezone|Asia/Istanbul|
|timezone|Asia/Jakarta|
|timezone|Asia/Jayapura|
|timezone|Asia/Jerusalem|
|timezone|Asia/Kabul|
|timezone|Asia/Kamchatka|
|timezone|Asia/Karachi|
|timezone|Asia/Kashgar|
|timezone|Asia/Kathmandu|
|timezone|Asia/Katmandu|
|timezone|Asia/Khandyga|
|timezone|Asia/Kolkata|
|timezone|Asia/Krasnoyarsk|
|timezone|Asia/Kuala_Lumpur|
|timezone|Asia/Kuching|
|timezone|Asia/Kuwait|
|timezone|Asia/Macao|
|timezone|Asia/Macau|
|timezone|Asia/Magadan|
|timezone|Asia/Makassar|
|timezone|Asia/Manila|
|timezone|Asia/Muscat|
|timezone|Asia/Nicosia|
|timezone|Asia/Novokuznetsk|
|timezone|Asia/Novosibirsk|
|timezone|Asia/Omsk|
|timezone|Asia/Oral|
|timezone|Asia/Phnom_Penh|
|timezone|Asia/Pontianak|
|timezone|Asia/Pyongyang|
|timezone|Asia/Qatar|
|timezone|Asia/Qostanay|
|timezone|Asia/Qyzylorda|
|timezone|Asia/Rangoon|
|timezone|Asia/Riyadh|
|timezone|Asia/Saigon|
|timezone|Asia/Sakhalin|
|timezone|Asia/Samarkand|
|timezone|Asia/Seoul|
|timezone|Asia/Shanghai|
|timezone|Asia/Singapore|
|timezone|Asia/Srednekolymsk|
|timezone|Asia/Taipei|
|timezone|Asia/Tashkent|
|timezone|Asia/Tbilisi|
|timezone|Asia/Tehran|
|timezone|Asia/Tel_Aviv|
|timezone|Asia/Thimbu|
|timezone|Asia/Thimphu|
|timezone|Asia/Tokyo|
|timezone|Asia/Tomsk|
|timezone|Asia/Ujung_Pandang|
|timezone|Asia/Ulaanbaatar|
|timezone|Asia/Ulan_Bator|
|timezone|Asia/Urumqi|
|timezone|Asia/Ust-Nera|
|timezone|Asia/Vientiane|
|timezone|Asia/Vladivostok|
|timezone|Asia/Yakutsk|
|timezone|Asia/Yangon|
|timezone|Asia/Yekaterinburg|
|timezone|Asia/Yerevan|
|timezone|Atlantic/Azores|
|timezone|Atlantic/Bermuda|
|timezone|Atlantic/Canary|
|timezone|Atlantic/Cape_Verde|
|timezone|Atlantic/Faeroe|
|timezone|Atlantic/Faroe|
|timezone|Atlantic/Jan_Mayen|
|timezone|Atlantic/Madeira|
|timezone|Atlantic/Reykjavik|
|timezone|Atlantic/South_Georgia|
|timezone|Atlantic/St_Helena|
|timezone|Atlantic/Stanley|
|timezone|Australia/ACT|
|timezone|Australia/Adelaide|
|timezone|Australia/Brisbane|
|timezone|Australia/Broken_Hill|
|timezone|Australia/Canberra|
|timezone|Australia/Currie|
|timezone|Australia/Darwin|
|timezone|Australia/Eucla|
|timezone|Australia/Hobart|
|timezone|Australia/LHI|
|timezone|Australia/Lindeman|
|timezone|Australia/Lord_Howe|
|timezone|Australia/Melbourne|
|timezone|Australia/NSW|
|timezone|Australia/North|
|timezone|Australia/Perth|
|timezone|Australia/Queensland|
|timezone|Australia/South|
|timezone|Australia/Sydney|
|timezone|Australia/Tasmania|
|timezone|Australia/Victoria|
|timezone|Australia/West|
|timezone|Australia/Yancowinna|
|timezone|Brazil/Acre|
|timezone|Brazil/DeNoronha|
|timezone|Brazil/East|
|timezone|Brazil/West|
|timezone|CET|
|timezone|CST6CDT|
|timezone|Canada/Atlantic|
|timezone|Canada/Central|
|timezone|Canada/Eastern|
|timezone|Canada/Mountain|
|timezone|Canada/Newfoundland|
|timezone|Canada/Pacific|
|timezone|Canada/Saskatchewan|
|timezone|Canada/Yukon|
|timezone|Chile/Continental|
|timezone|Chile/EasterIsland|
|timezone|Cuba|
|timezone|EET|
|timezone|EST|
|timezone|EST5EDT|
|timezone|Egypt|
|timezone|Eire|
|timezone|Etc/GMT|
|timezone|Etc/GMT+0|
|timezone|Etc/GMT+1|
|timezone|Etc/GMT+10|
|timezone|Etc/GMT+11|
|timezone|Etc/GMT+12|
|timezone|Etc/GMT+2|
|timezone|Etc/GMT+3|
|timezone|Etc/GMT+4|
|timezone|Etc/GMT+5|
|timezone|Etc/GMT+6|
|timezone|Etc/GMT+7|
|timezone|Etc/GMT+8|
|timezone|Etc/GMT+9|
|timezone|Etc/GMT-0|
|timezone|Etc/GMT-1|
|timezone|Etc/GMT-10|
|timezone|Etc/GMT-11|
|timezone|Etc/GMT-12|
|timezone|Etc/GMT-13|
|timezone|Etc/GMT-14|
|timezone|Etc/GMT-2|
|timezone|Etc/GMT-3|
|timezone|Etc/GMT-4|
|timezone|Etc/GMT-5|
|timezone|Etc/GMT-6|
|timezone|Etc/GMT-7|
|timezone|Etc/GMT-8|
|timezone|Etc/GMT-9|
|timezone|Etc/GMT0|
|timezone|Etc/Greenwich|
|timezone|Etc/UCT|
|timezone|Etc/UTC|
|timezone|Etc/Universal|
|timezone|Etc/Zulu|
|timezone|Europe/Amsterdam|
|timezone|Europe/Andorra|
|timezone|Europe/Astrakhan|
|timezone|Europe/Athens|
|timezone|Europe/Belfast|
|timezone|Europe/Belgrade|
|timezone|Europe/Berlin|
|timezone|Europe/Bratislava|
|timezone|Europe/Brussels|
|timezone|Europe/Bucharest|
|timezone|Europe/Budapest|
|timezone|Europe/Busingen|
|timezone|Europe/Chisinau|
|timezone|Europe/Copenhagen|
|timezone|Europe/Dublin|
|timezone|Europe/Gibraltar|
|timezone|Europe/Guernsey|
|timezone|Europe/Helsinki|
|timezone|Europe/Isle_of_Man|
|timezone|Europe/Istanbul|
|timezone|Europe/Jersey|
|timezone|Europe/Kaliningrad|
|timezone|Europe/Kiev|
|timezone|Europe/Kirov|
|timezone|Europe/Lisbon|
|timezone|Europe/Ljubljana|
|timezone|Europe/London|
|timezone|Europe/Luxembourg|
|timezone|Europe/Madrid|
|timezone|Europe/Malta|
|timezone|Europe/Mariehamn|
|timezone|Europe/Minsk|
|timezone|Europe/Monaco|
|timezone|Europe/Moscow|
|timezone|Europe/Nicosia|
|timezone|Europe/Oslo|
|timezone|Europe/Paris|
|timezone|Europe/Podgorica|
|timezone|Europe/Prague|
|timezone|Europe/Riga|
|timezone|Europe/Rome|
|timezone|Europe/Samara|
|timezone|Europe/San_Marino|
|timezone|Europe/Sarajevo|
|timezone|Europe/Saratov|
|timezone|Europe/Simferopol|
|timezone|Europe/Skopje|
|timezone|Europe/Sofia|
|timezone|Europe/Stockholm|
|timezone|Europe/Tallinn|
|timezone|Europe/Tirane|
|timezone|Europe/Tiraspol|
|timezone|Europe/Ulyanovsk|
|timezone|Europe/Uzhgorod|
|timezone|Europe/Vaduz|
|timezone|Europe/Vatican|
|timezone|Europe/Vienna|
|timezone|Europe/Vilnius|
|timezone|Europe/Volgograd|
|timezone|Europe/Warsaw|
|timezone|Europe/Zagreb|
|timezone|Europe/Zaporozhye|
|timezone|Europe/Zurich|
|timezone|GB|
|timezone|GB-Eire|
|timezone|GMT|
|timezone|GMT+0|
|timezone|GMT-0|
|timezone|GMT0|
|timezone|Greenwich|
|timezone|HST|
|timezone|Hongkong|
|timezone|Iceland|
|timezone|Indian/Antananarivo|
|timezone|Indian/Chagos|
|timezone|Indian/Christmas|
|timezone|Indian/Cocos|
|timezone|Indian/Comoro|
|timezone|Indian/Kerguelen|
|timezone|Indian/Mahe|
|timezone|Indian/Maldives|
|timezone|Indian/Mauritius|
|timezone|Indian/Mayotte|
|timezone|Indian/Reunion|
|timezone|Iran|
|timezone|Israel|
|timezone|Jamaica|
|timezone|Japan|
|timezone|Kwajalein|
|timezone|Libya|
|timezone|MET|
|timezone|MST|
|timezone|MST7MDT|
|timezone|Mexico/BajaNorte|
|timezone|Mexico/BajaSur|
|timezone|Mexico/General|
|timezone|NZ|
|timezone|NZ-CHAT|
|timezone|Navajo|
|timezone|PRC|
|timezone|PST8PDT|
|timezone|Pacific/Apia|
|timezone|Pacific/Auckland|
|timezone|Pacific/Bougainville|
|timezone|Pacific/Chatham|
|timezone|Pacific/Chuuk|
|timezone|Pacific/Easter|
|timezone|Pacific/Efate|
|timezone|Pacific/Enderbury|
|timezone|Pacific/Fakaofo|
|timezone|Pacific/Fiji|
|timezone|Pacific/Funafuti|
|timezone|Pacific/Galapagos|
|timezone|Pacific/Gambier|
|timezone|Pacific/Guadalcanal|
|timezone|Pacific/Guam|
|timezone|Pacific/Honolulu|
|timezone|Pacific/Johnston|
|timezone|Pacific/Kiritimati|
|timezone|Pacific/Kosrae|
|timezone|Pacific/Kwajalein|
|timezone|Pacific/Majuro|
|timezone|Pacific/Marquesas|
|timezone|Pacific/Midway|
|timezone|Pacific/Nauru|
|timezone|Pacific/Niue|
|timezone|Pacific/Norfolk|
|timezone|Pacific/Noumea|
|timezone|Pacific/Pago_Pago|
|timezone|Pacific/Palau|
|timezone|Pacific/Pitcairn|
|timezone|Pacific/Pohnpei|
|timezone|Pacific/Ponape|
|timezone|Pacific/Port_Moresby|
|timezone|Pacific/Rarotonga|
|timezone|Pacific/Saipan|
|timezone|Pacific/Samoa|
|timezone|Pacific/Tahiti|
|timezone|Pacific/Tarawa|
|timezone|Pacific/Tongatapu|
|timezone|Pacific/Truk|
|timezone|Pacific/Wake|
|timezone|Pacific/Wallis|
|timezone|Pacific/Yap|
|timezone|Poland|
|timezone|Portugal|
|timezone|ROC|
|timezone|ROK|
|timezone|Singapore|
|timezone|Turkey|
|timezone|UCT|
|timezone|US/Alaska|
|timezone|US/Aleutian|
|timezone|US/Arizona|
|timezone|US/Central|
|timezone|US/East-Indiana|
|timezone|US/Eastern|
|timezone|US/Hawaii|
|timezone|US/Indiana-Starke|
|timezone|US/Michigan|
|timezone|US/Mountain|
|timezone|US/Pacific|
|timezone|US/Samoa|
|timezone|UTC|
|timezone|Universal|
|timezone|W-SU|
|timezone|WET|
|timezone|Zulu|

<h2 id="tocS_ListOrgTeamResponse">ListOrgTeamResponse</h2>
<!-- backwards compatibility -->
<a id="schemalistorgteamresponse"></a>
<a id="schema_ListOrgTeamResponse"></a>
<a id="tocSlistorgteamresponse"></a>
<a id="tocslistorgteamresponse"></a>

```json
[
  {
    "externalTeams": [
      {
        "externalId": "string",
        "userId": "string",
        "teamId": "string",
        "id": "string",
        "provider": "string",
        "externalName": "string",
        "integrationId": "string"
      }
    ],
    "organization": {
      "id": "string",
      "slug": "string",
      "status": {
        "id": "string",
        "name": "string"
      },
      "name": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "isEarlyAdopter": true,
      "require2FA": true,
      "requireEmailVerification": true,
      "avatar": null,
      "features": null,
      "links": {
        "organizationUrl": "string",
        "regionUrl": "string"
      },
      "hasAuthProvider": true
    },
    "projects": [
      {
        "stats": null,
        "transactionStats": null,
        "sessionStats": null,
        "id": "string",
        "slug": "string",
        "name": "string",
        "platform": "string",
        "dateCreated": "2019-08-24T14:15:22Z",
        "isBookmarked": true,
        "isMember": true,
        "features": [
          "string"
        ],
        "firstEvent": "2019-08-24T14:15:22Z",
        "firstTransactionEvent": true,
        "access": [
          "string"
        ],
        "hasAccess": true,
        "hasMinifiedStackTrace": true,
        "hasMonitors": true,
        "hasProfiles": true,
        "hasReplays": true,
        "hasSessions": true,
        "isInternal": true,
        "isPublic": true,
        "avatar": null,
        "color": "string",
        "status": "string"
      }
    ],
    "id": "string",
    "slug": "string",
    "name": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isMember": true,
    "teamRole": "string",
    "flags": {
      "property1": null,
      "property2": null
    },
    "access": [
      "string"
    ],
    "hasAccess": true,
    "isPending": true,
    "memberCount": 0,
    "avatar": {
      "avatarType": "string",
      "avatarUuid": "string"
    },
    "orgRole": "string"
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|externalTeams|[object]|false|none|none|
|» externalId|string|false|none|none|
|» userId|string|false|none|none|
|» teamId|string|false|none|none|
|» id|string|true|none|none|
|» provider|string|true|none|none|
|» externalName|string|true|none|none|
|» integrationId|string|true|none|none|
|organization|object|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» status|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isEarlyAdopter|boolean|true|none|none|
|» require2FA|boolean|true|none|none|
|» requireEmailVerification|boolean|true|none|none|
|» avatar|any|true|none|none|
|» features|any|true|none|none|
|» links|object|true|none|none|
|»» organizationUrl|string|true|none|none|
|»» regionUrl|string|true|none|none|
|» hasAuthProvider|boolean|true|none|none|
|projects|[object]|false|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» avatar|any|true|none|none|
|» color|string|true|none|none|
|» status|string|true|none|none|
|id|string|true|none|none|
|slug|string|true|none|none|
|name|string|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|isMember|boolean|true|none|none|
|teamRole|string¦null|true|none|none|
|flags|object|true|none|none|
|» **additionalProperties**|any|false|none|none|
|access|[string]|true|none|none|
|hasAccess|boolean|true|none|none|
|isPending|boolean|true|none|none|
|memberCount|integer|true|none|none|
|avatar|object|true|none|none|
|» avatarType|string|true|none|none|
|» avatarUuid|string¦null|true|none|none|
|orgRole|string¦null|true|none|none|

<h2 id="tocS_ListTeamProjectResponse">ListTeamProjectResponse</h2>
<!-- backwards compatibility -->
<a id="schemalistteamprojectresponse"></a>
<a id="schema_ListTeamProjectResponse"></a>
<a id="tocSlistteamprojectresponse"></a>
<a id="tocslistteamprojectresponse"></a>

```json
[
  {
    "latestDeploys": {
      "property1": {
        "property1": "string",
        "property2": "string"
      },
      "property2": {
        "property1": "string",
        "property2": "string"
      }
    },
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "team": {
      "id": "string",
      "name": "string",
      "slug": "string"
    },
    "teams": [
      {
        "id": "string",
        "name": "string",
        "slug": "string"
      }
    ],
    "eventProcessing": {
      "symbolicationDegraded": true
    },
    "platforms": [
      "string"
    ],
    "hasUserReports": true,
    "environments": [
      "string"
    ],
    "latestRelease": {
      "version": "string"
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|latestDeploys|object¦null|false|none|none|
|» **additionalProperties**|object|false|none|none|
|»» **additionalProperties**|string|false|none|none|
|stats|any|false|none|none|
|transactionStats|any|false|none|none|
|sessionStats|any|false|none|none|
|id|string|true|none|none|
|slug|string|true|none|none|
|name|string|true|none|none|
|platform|string¦null|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|isBookmarked|boolean|true|none|none|
|isMember|boolean|true|none|none|
|features|[string]|true|none|none|
|firstEvent|string(date-time)¦null|true|none|none|
|firstTransactionEvent|boolean|true|none|none|
|access|[string]|true|none|none|
|hasAccess|boolean|true|none|none|
|hasMinifiedStackTrace|boolean|true|none|none|
|hasMonitors|boolean|true|none|none|
|hasProfiles|boolean|true|none|none|
|hasReplays|boolean|true|none|none|
|hasSessions|boolean|true|none|none|
|team|object¦null|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|teams|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|eventProcessing|object|true|none|none|
|» symbolicationDegraded|boolean|true|none|none|
|platforms|[string]|true|none|none|
|hasUserReports|boolean|true|none|none|
|environments|[string]|true|none|none|
|latestRelease|object¦null|true|none|none|
|» version|string|true|none|none|

<h2 id="tocS_Monitor">Monitor</h2>
<!-- backwards compatibility -->
<a id="schemamonitor"></a>
<a id="schema_Monitor"></a>
<a id="tocSmonitor"></a>
<a id="tocsmonitor"></a>

```json
{
  "id": "string",
  "name": "string",
  "slug": "string",
  "status": "string",
  "type": "string",
  "config": null,
  "dateCreated": "2019-08-24T14:15:22Z",
  "project": {
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "isInternal": true,
    "isPublic": true,
    "avatar": null,
    "color": "string",
    "status": "string"
  },
  "environments": {
    "name": "string",
    "status": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "lastCheckIn": "2019-08-24T14:15:22Z",
    "nextCheckIn": "2019-08-24T14:15:22Z"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|slug|string|true|none|none|
|status|string|true|none|none|
|type|string|true|none|none|
|config|any|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|project|object|true|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» avatar|any|true|none|none|
|» color|string|true|none|none|
|» status|string|true|none|none|
|environments|object|true|none|none|
|» name|string|true|none|none|
|» status|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» lastCheckIn|string(date-time)|true|none|none|
|» nextCheckIn|string(date-time)|true|none|none|

<h2 id="tocS_MonitorAlertRuleTargetValidator">MonitorAlertRuleTargetValidator</h2>
<!-- backwards compatibility -->
<a id="schemamonitoralertruletargetvalidator"></a>
<a id="schema_MonitorAlertRuleTargetValidator"></a>
<a id="tocSmonitoralertruletargetvalidator"></a>
<a id="tocsmonitoralertruletargetvalidator"></a>

```json
{
  "target_identifier": 0,
  "target_type": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|target_identifier|integer|true|none|ID of target object|
|target_type|string|true|none|One of [Member, Team]|

<h2 id="tocS_MonitorAlertRuleValidator">MonitorAlertRuleValidator</h2>
<!-- backwards compatibility -->
<a id="schemamonitoralertrulevalidator"></a>
<a id="schema_MonitorAlertRuleValidator"></a>
<a id="tocSmonitoralertrulevalidator"></a>
<a id="tocsmonitoralertrulevalidator"></a>

```json
{
  "environment": "string",
  "targets": [
    {
      "target_identifier": 0,
      "target_type": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|environment|string¦null|false|none|Name of the environment|
|targets|[object]|true|none|Array of dictionaries with information of the user or team to be notified|
|» target_identifier|integer|true|none|ID of target object|
|» target_type|string|true|none|One of [Member, Team]|

<h2 id="tocS_MonitorCheckIn">MonitorCheckIn</h2>
<!-- backwards compatibility -->
<a id="schemamonitorcheckin"></a>
<a id="schema_MonitorCheckIn"></a>
<a id="tocSmonitorcheckin"></a>
<a id="tocsmonitorcheckin"></a>

```json
{
  "id": "string",
  "environment": "string",
  "status": "string",
  "duration": 0,
  "dateCreated": "2019-08-24T14:15:22Z",
  "attachmentId": "string",
  "expectedTime": "2019-08-24T14:15:22Z",
  "monitorConfig": null
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|environment|string|true|none|none|
|status|string|true|none|none|
|duration|integer|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|attachmentId|string|true|none|none|
|expectedTime|string(date-time)|true|none|none|
|monitorConfig|any|true|none|none|

<h2 id="tocS_MonitorCheckInValidator">MonitorCheckInValidator</h2>
<!-- backwards compatibility -->
<a id="schemamonitorcheckinvalidator"></a>
<a id="schema_MonitorCheckInValidator"></a>
<a id="tocSmonitorcheckinvalidator"></a>
<a id="tocsmonitorcheckinvalidator"></a>

```json
{
  "status": "ok",
  "duration": 2147483647,
  "environment": "string",
  "monitor_config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|string|true|none|none|
|duration|integer¦null|false|none|none|
|environment|string¦null|false|none|none|
|monitor_config|object|false|none|none|
|» schedule_type|string|false|none|Currently supports "crontab" or "interval"|
|» schedule|any|true|none|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|» checkin_margin|integer¦null|false|none|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|» max_runtime|integer¦null|false|none|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|» timezone|string|false|none|tz database style timezone string|

#### Enumerated Values

|Property|Value|
|---|---|
|status|ok|
|status|error|
|status|in_progress|
|schedule_type|crontab|
|schedule_type|interval|
|timezone|Africa/Abidjan|
|timezone|Africa/Accra|
|timezone|Africa/Addis_Ababa|
|timezone|Africa/Algiers|
|timezone|Africa/Asmara|
|timezone|Africa/Asmera|
|timezone|Africa/Bamako|
|timezone|Africa/Bangui|
|timezone|Africa/Banjul|
|timezone|Africa/Bissau|
|timezone|Africa/Blantyre|
|timezone|Africa/Brazzaville|
|timezone|Africa/Bujumbura|
|timezone|Africa/Cairo|
|timezone|Africa/Casablanca|
|timezone|Africa/Ceuta|
|timezone|Africa/Conakry|
|timezone|Africa/Dakar|
|timezone|Africa/Dar_es_Salaam|
|timezone|Africa/Djibouti|
|timezone|Africa/Douala|
|timezone|Africa/El_Aaiun|
|timezone|Africa/Freetown|
|timezone|Africa/Gaborone|
|timezone|Africa/Harare|
|timezone|Africa/Johannesburg|
|timezone|Africa/Juba|
|timezone|Africa/Kampala|
|timezone|Africa/Khartoum|
|timezone|Africa/Kigali|
|timezone|Africa/Kinshasa|
|timezone|Africa/Lagos|
|timezone|Africa/Libreville|
|timezone|Africa/Lome|
|timezone|Africa/Luanda|
|timezone|Africa/Lubumbashi|
|timezone|Africa/Lusaka|
|timezone|Africa/Malabo|
|timezone|Africa/Maputo|
|timezone|Africa/Maseru|
|timezone|Africa/Mbabane|
|timezone|Africa/Mogadishu|
|timezone|Africa/Monrovia|
|timezone|Africa/Nairobi|
|timezone|Africa/Ndjamena|
|timezone|Africa/Niamey|
|timezone|Africa/Nouakchott|
|timezone|Africa/Ouagadougou|
|timezone|Africa/Porto-Novo|
|timezone|Africa/Sao_Tome|
|timezone|Africa/Timbuktu|
|timezone|Africa/Tripoli|
|timezone|Africa/Tunis|
|timezone|Africa/Windhoek|
|timezone|America/Adak|
|timezone|America/Anchorage|
|timezone|America/Anguilla|
|timezone|America/Antigua|
|timezone|America/Araguaina|
|timezone|America/Argentina/Buenos_Aires|
|timezone|America/Argentina/Catamarca|
|timezone|America/Argentina/ComodRivadavia|
|timezone|America/Argentina/Cordoba|
|timezone|America/Argentina/Jujuy|
|timezone|America/Argentina/La_Rioja|
|timezone|America/Argentina/Mendoza|
|timezone|America/Argentina/Rio_Gallegos|
|timezone|America/Argentina/Salta|
|timezone|America/Argentina/San_Juan|
|timezone|America/Argentina/San_Luis|
|timezone|America/Argentina/Tucuman|
|timezone|America/Argentina/Ushuaia|
|timezone|America/Aruba|
|timezone|America/Asuncion|
|timezone|America/Atikokan|
|timezone|America/Atka|
|timezone|America/Bahia|
|timezone|America/Bahia_Banderas|
|timezone|America/Barbados|
|timezone|America/Belem|
|timezone|America/Belize|
|timezone|America/Blanc-Sablon|
|timezone|America/Boa_Vista|
|timezone|America/Bogota|
|timezone|America/Boise|
|timezone|America/Buenos_Aires|
|timezone|America/Cambridge_Bay|
|timezone|America/Campo_Grande|
|timezone|America/Cancun|
|timezone|America/Caracas|
|timezone|America/Catamarca|
|timezone|America/Cayenne|
|timezone|America/Cayman|
|timezone|America/Chicago|
|timezone|America/Chihuahua|
|timezone|America/Coral_Harbour|
|timezone|America/Cordoba|
|timezone|America/Costa_Rica|
|timezone|America/Creston|
|timezone|America/Cuiaba|
|timezone|America/Curacao|
|timezone|America/Danmarkshavn|
|timezone|America/Dawson|
|timezone|America/Dawson_Creek|
|timezone|America/Denver|
|timezone|America/Detroit|
|timezone|America/Dominica|
|timezone|America/Edmonton|
|timezone|America/Eirunepe|
|timezone|America/El_Salvador|
|timezone|America/Ensenada|
|timezone|America/Fort_Nelson|
|timezone|America/Fort_Wayne|
|timezone|America/Fortaleza|
|timezone|America/Glace_Bay|
|timezone|America/Godthab|
|timezone|America/Goose_Bay|
|timezone|America/Grand_Turk|
|timezone|America/Grenada|
|timezone|America/Guadeloupe|
|timezone|America/Guatemala|
|timezone|America/Guayaquil|
|timezone|America/Guyana|
|timezone|America/Halifax|
|timezone|America/Havana|
|timezone|America/Hermosillo|
|timezone|America/Indiana/Indianapolis|
|timezone|America/Indiana/Knox|
|timezone|America/Indiana/Marengo|
|timezone|America/Indiana/Petersburg|
|timezone|America/Indiana/Tell_City|
|timezone|America/Indiana/Vevay|
|timezone|America/Indiana/Vincennes|
|timezone|America/Indiana/Winamac|
|timezone|America/Indianapolis|
|timezone|America/Inuvik|
|timezone|America/Iqaluit|
|timezone|America/Jamaica|
|timezone|America/Jujuy|
|timezone|America/Juneau|
|timezone|America/Kentucky/Louisville|
|timezone|America/Kentucky/Monticello|
|timezone|America/Knox_IN|
|timezone|America/Kralendijk|
|timezone|America/La_Paz|
|timezone|America/Lima|
|timezone|America/Los_Angeles|
|timezone|America/Louisville|
|timezone|America/Lower_Princes|
|timezone|America/Maceio|
|timezone|America/Managua|
|timezone|America/Manaus|
|timezone|America/Marigot|
|timezone|America/Martinique|
|timezone|America/Matamoros|
|timezone|America/Mazatlan|
|timezone|America/Mendoza|
|timezone|America/Menominee|
|timezone|America/Merida|
|timezone|America/Metlakatla|
|timezone|America/Mexico_City|
|timezone|America/Miquelon|
|timezone|America/Moncton|
|timezone|America/Monterrey|
|timezone|America/Montevideo|
|timezone|America/Montreal|
|timezone|America/Montserrat|
|timezone|America/Nassau|
|timezone|America/New_York|
|timezone|America/Nipigon|
|timezone|America/Nome|
|timezone|America/Noronha|
|timezone|America/North_Dakota/Beulah|
|timezone|America/North_Dakota/Center|
|timezone|America/North_Dakota/New_Salem|
|timezone|America/Ojinaga|
|timezone|America/Panama|
|timezone|America/Pangnirtung|
|timezone|America/Paramaribo|
|timezone|America/Phoenix|
|timezone|America/Port-au-Prince|
|timezone|America/Port_of_Spain|
|timezone|America/Porto_Acre|
|timezone|America/Porto_Velho|
|timezone|America/Puerto_Rico|
|timezone|America/Punta_Arenas|
|timezone|America/Rainy_River|
|timezone|America/Rankin_Inlet|
|timezone|America/Recife|
|timezone|America/Regina|
|timezone|America/Resolute|
|timezone|America/Rio_Branco|
|timezone|America/Rosario|
|timezone|America/Santa_Isabel|
|timezone|America/Santarem|
|timezone|America/Santiago|
|timezone|America/Santo_Domingo|
|timezone|America/Sao_Paulo|
|timezone|America/Scoresbysund|
|timezone|America/Shiprock|
|timezone|America/Sitka|
|timezone|America/St_Barthelemy|
|timezone|America/St_Johns|
|timezone|America/St_Kitts|
|timezone|America/St_Lucia|
|timezone|America/St_Thomas|
|timezone|America/St_Vincent|
|timezone|America/Swift_Current|
|timezone|America/Tegucigalpa|
|timezone|America/Thule|
|timezone|America/Thunder_Bay|
|timezone|America/Tijuana|
|timezone|America/Toronto|
|timezone|America/Tortola|
|timezone|America/Vancouver|
|timezone|America/Virgin|
|timezone|America/Whitehorse|
|timezone|America/Winnipeg|
|timezone|America/Yakutat|
|timezone|America/Yellowknife|
|timezone|Antarctica/Casey|
|timezone|Antarctica/Davis|
|timezone|Antarctica/DumontDUrville|
|timezone|Antarctica/Macquarie|
|timezone|Antarctica/Mawson|
|timezone|Antarctica/McMurdo|
|timezone|Antarctica/Palmer|
|timezone|Antarctica/Rothera|
|timezone|Antarctica/South_Pole|
|timezone|Antarctica/Syowa|
|timezone|Antarctica/Troll|
|timezone|Antarctica/Vostok|
|timezone|Arctic/Longyearbyen|
|timezone|Asia/Aden|
|timezone|Asia/Almaty|
|timezone|Asia/Amman|
|timezone|Asia/Anadyr|
|timezone|Asia/Aqtau|
|timezone|Asia/Aqtobe|
|timezone|Asia/Ashgabat|
|timezone|Asia/Ashkhabad|
|timezone|Asia/Atyrau|
|timezone|Asia/Baghdad|
|timezone|Asia/Bahrain|
|timezone|Asia/Baku|
|timezone|Asia/Bangkok|
|timezone|Asia/Barnaul|
|timezone|Asia/Beirut|
|timezone|Asia/Bishkek|
|timezone|Asia/Brunei|
|timezone|Asia/Calcutta|
|timezone|Asia/Chita|
|timezone|Asia/Choibalsan|
|timezone|Asia/Chongqing|
|timezone|Asia/Chungking|
|timezone|Asia/Colombo|
|timezone|Asia/Dacca|
|timezone|Asia/Damascus|
|timezone|Asia/Dhaka|
|timezone|Asia/Dili|
|timezone|Asia/Dubai|
|timezone|Asia/Dushanbe|
|timezone|Asia/Famagusta|
|timezone|Asia/Gaza|
|timezone|Asia/Harbin|
|timezone|Asia/Hebron|
|timezone|Asia/Ho_Chi_Minh|
|timezone|Asia/Hong_Kong|
|timezone|Asia/Hovd|
|timezone|Asia/Irkutsk|
|timezone|Asia/Istanbul|
|timezone|Asia/Jakarta|
|timezone|Asia/Jayapura|
|timezone|Asia/Jerusalem|
|timezone|Asia/Kabul|
|timezone|Asia/Kamchatka|
|timezone|Asia/Karachi|
|timezone|Asia/Kashgar|
|timezone|Asia/Kathmandu|
|timezone|Asia/Katmandu|
|timezone|Asia/Khandyga|
|timezone|Asia/Kolkata|
|timezone|Asia/Krasnoyarsk|
|timezone|Asia/Kuala_Lumpur|
|timezone|Asia/Kuching|
|timezone|Asia/Kuwait|
|timezone|Asia/Macao|
|timezone|Asia/Macau|
|timezone|Asia/Magadan|
|timezone|Asia/Makassar|
|timezone|Asia/Manila|
|timezone|Asia/Muscat|
|timezone|Asia/Nicosia|
|timezone|Asia/Novokuznetsk|
|timezone|Asia/Novosibirsk|
|timezone|Asia/Omsk|
|timezone|Asia/Oral|
|timezone|Asia/Phnom_Penh|
|timezone|Asia/Pontianak|
|timezone|Asia/Pyongyang|
|timezone|Asia/Qatar|
|timezone|Asia/Qostanay|
|timezone|Asia/Qyzylorda|
|timezone|Asia/Rangoon|
|timezone|Asia/Riyadh|
|timezone|Asia/Saigon|
|timezone|Asia/Sakhalin|
|timezone|Asia/Samarkand|
|timezone|Asia/Seoul|
|timezone|Asia/Shanghai|
|timezone|Asia/Singapore|
|timezone|Asia/Srednekolymsk|
|timezone|Asia/Taipei|
|timezone|Asia/Tashkent|
|timezone|Asia/Tbilisi|
|timezone|Asia/Tehran|
|timezone|Asia/Tel_Aviv|
|timezone|Asia/Thimbu|
|timezone|Asia/Thimphu|
|timezone|Asia/Tokyo|
|timezone|Asia/Tomsk|
|timezone|Asia/Ujung_Pandang|
|timezone|Asia/Ulaanbaatar|
|timezone|Asia/Ulan_Bator|
|timezone|Asia/Urumqi|
|timezone|Asia/Ust-Nera|
|timezone|Asia/Vientiane|
|timezone|Asia/Vladivostok|
|timezone|Asia/Yakutsk|
|timezone|Asia/Yangon|
|timezone|Asia/Yekaterinburg|
|timezone|Asia/Yerevan|
|timezone|Atlantic/Azores|
|timezone|Atlantic/Bermuda|
|timezone|Atlantic/Canary|
|timezone|Atlantic/Cape_Verde|
|timezone|Atlantic/Faeroe|
|timezone|Atlantic/Faroe|
|timezone|Atlantic/Jan_Mayen|
|timezone|Atlantic/Madeira|
|timezone|Atlantic/Reykjavik|
|timezone|Atlantic/South_Georgia|
|timezone|Atlantic/St_Helena|
|timezone|Atlantic/Stanley|
|timezone|Australia/ACT|
|timezone|Australia/Adelaide|
|timezone|Australia/Brisbane|
|timezone|Australia/Broken_Hill|
|timezone|Australia/Canberra|
|timezone|Australia/Currie|
|timezone|Australia/Darwin|
|timezone|Australia/Eucla|
|timezone|Australia/Hobart|
|timezone|Australia/LHI|
|timezone|Australia/Lindeman|
|timezone|Australia/Lord_Howe|
|timezone|Australia/Melbourne|
|timezone|Australia/NSW|
|timezone|Australia/North|
|timezone|Australia/Perth|
|timezone|Australia/Queensland|
|timezone|Australia/South|
|timezone|Australia/Sydney|
|timezone|Australia/Tasmania|
|timezone|Australia/Victoria|
|timezone|Australia/West|
|timezone|Australia/Yancowinna|
|timezone|Brazil/Acre|
|timezone|Brazil/DeNoronha|
|timezone|Brazil/East|
|timezone|Brazil/West|
|timezone|CET|
|timezone|CST6CDT|
|timezone|Canada/Atlantic|
|timezone|Canada/Central|
|timezone|Canada/Eastern|
|timezone|Canada/Mountain|
|timezone|Canada/Newfoundland|
|timezone|Canada/Pacific|
|timezone|Canada/Saskatchewan|
|timezone|Canada/Yukon|
|timezone|Chile/Continental|
|timezone|Chile/EasterIsland|
|timezone|Cuba|
|timezone|EET|
|timezone|EST|
|timezone|EST5EDT|
|timezone|Egypt|
|timezone|Eire|
|timezone|Etc/GMT|
|timezone|Etc/GMT+0|
|timezone|Etc/GMT+1|
|timezone|Etc/GMT+10|
|timezone|Etc/GMT+11|
|timezone|Etc/GMT+12|
|timezone|Etc/GMT+2|
|timezone|Etc/GMT+3|
|timezone|Etc/GMT+4|
|timezone|Etc/GMT+5|
|timezone|Etc/GMT+6|
|timezone|Etc/GMT+7|
|timezone|Etc/GMT+8|
|timezone|Etc/GMT+9|
|timezone|Etc/GMT-0|
|timezone|Etc/GMT-1|
|timezone|Etc/GMT-10|
|timezone|Etc/GMT-11|
|timezone|Etc/GMT-12|
|timezone|Etc/GMT-13|
|timezone|Etc/GMT-14|
|timezone|Etc/GMT-2|
|timezone|Etc/GMT-3|
|timezone|Etc/GMT-4|
|timezone|Etc/GMT-5|
|timezone|Etc/GMT-6|
|timezone|Etc/GMT-7|
|timezone|Etc/GMT-8|
|timezone|Etc/GMT-9|
|timezone|Etc/GMT0|
|timezone|Etc/Greenwich|
|timezone|Etc/UCT|
|timezone|Etc/UTC|
|timezone|Etc/Universal|
|timezone|Etc/Zulu|
|timezone|Europe/Amsterdam|
|timezone|Europe/Andorra|
|timezone|Europe/Astrakhan|
|timezone|Europe/Athens|
|timezone|Europe/Belfast|
|timezone|Europe/Belgrade|
|timezone|Europe/Berlin|
|timezone|Europe/Bratislava|
|timezone|Europe/Brussels|
|timezone|Europe/Bucharest|
|timezone|Europe/Budapest|
|timezone|Europe/Busingen|
|timezone|Europe/Chisinau|
|timezone|Europe/Copenhagen|
|timezone|Europe/Dublin|
|timezone|Europe/Gibraltar|
|timezone|Europe/Guernsey|
|timezone|Europe/Helsinki|
|timezone|Europe/Isle_of_Man|
|timezone|Europe/Istanbul|
|timezone|Europe/Jersey|
|timezone|Europe/Kaliningrad|
|timezone|Europe/Kiev|
|timezone|Europe/Kirov|
|timezone|Europe/Lisbon|
|timezone|Europe/Ljubljana|
|timezone|Europe/London|
|timezone|Europe/Luxembourg|
|timezone|Europe/Madrid|
|timezone|Europe/Malta|
|timezone|Europe/Mariehamn|
|timezone|Europe/Minsk|
|timezone|Europe/Monaco|
|timezone|Europe/Moscow|
|timezone|Europe/Nicosia|
|timezone|Europe/Oslo|
|timezone|Europe/Paris|
|timezone|Europe/Podgorica|
|timezone|Europe/Prague|
|timezone|Europe/Riga|
|timezone|Europe/Rome|
|timezone|Europe/Samara|
|timezone|Europe/San_Marino|
|timezone|Europe/Sarajevo|
|timezone|Europe/Saratov|
|timezone|Europe/Simferopol|
|timezone|Europe/Skopje|
|timezone|Europe/Sofia|
|timezone|Europe/Stockholm|
|timezone|Europe/Tallinn|
|timezone|Europe/Tirane|
|timezone|Europe/Tiraspol|
|timezone|Europe/Ulyanovsk|
|timezone|Europe/Uzhgorod|
|timezone|Europe/Vaduz|
|timezone|Europe/Vatican|
|timezone|Europe/Vienna|
|timezone|Europe/Vilnius|
|timezone|Europe/Volgograd|
|timezone|Europe/Warsaw|
|timezone|Europe/Zagreb|
|timezone|Europe/Zaporozhye|
|timezone|Europe/Zurich|
|timezone|GB|
|timezone|GB-Eire|
|timezone|GMT|
|timezone|GMT+0|
|timezone|GMT-0|
|timezone|GMT0|
|timezone|Greenwich|
|timezone|HST|
|timezone|Hongkong|
|timezone|Iceland|
|timezone|Indian/Antananarivo|
|timezone|Indian/Chagos|
|timezone|Indian/Christmas|
|timezone|Indian/Cocos|
|timezone|Indian/Comoro|
|timezone|Indian/Kerguelen|
|timezone|Indian/Mahe|
|timezone|Indian/Maldives|
|timezone|Indian/Mauritius|
|timezone|Indian/Mayotte|
|timezone|Indian/Reunion|
|timezone|Iran|
|timezone|Israel|
|timezone|Jamaica|
|timezone|Japan|
|timezone|Kwajalein|
|timezone|Libya|
|timezone|MET|
|timezone|MST|
|timezone|MST7MDT|
|timezone|Mexico/BajaNorte|
|timezone|Mexico/BajaSur|
|timezone|Mexico/General|
|timezone|NZ|
|timezone|NZ-CHAT|
|timezone|Navajo|
|timezone|PRC|
|timezone|PST8PDT|
|timezone|Pacific/Apia|
|timezone|Pacific/Auckland|
|timezone|Pacific/Bougainville|
|timezone|Pacific/Chatham|
|timezone|Pacific/Chuuk|
|timezone|Pacific/Easter|
|timezone|Pacific/Efate|
|timezone|Pacific/Enderbury|
|timezone|Pacific/Fakaofo|
|timezone|Pacific/Fiji|
|timezone|Pacific/Funafuti|
|timezone|Pacific/Galapagos|
|timezone|Pacific/Gambier|
|timezone|Pacific/Guadalcanal|
|timezone|Pacific/Guam|
|timezone|Pacific/Honolulu|
|timezone|Pacific/Johnston|
|timezone|Pacific/Kiritimati|
|timezone|Pacific/Kosrae|
|timezone|Pacific/Kwajalein|
|timezone|Pacific/Majuro|
|timezone|Pacific/Marquesas|
|timezone|Pacific/Midway|
|timezone|Pacific/Nauru|
|timezone|Pacific/Niue|
|timezone|Pacific/Norfolk|
|timezone|Pacific/Noumea|
|timezone|Pacific/Pago_Pago|
|timezone|Pacific/Palau|
|timezone|Pacific/Pitcairn|
|timezone|Pacific/Pohnpei|
|timezone|Pacific/Ponape|
|timezone|Pacific/Port_Moresby|
|timezone|Pacific/Rarotonga|
|timezone|Pacific/Saipan|
|timezone|Pacific/Samoa|
|timezone|Pacific/Tahiti|
|timezone|Pacific/Tarawa|
|timezone|Pacific/Tongatapu|
|timezone|Pacific/Truk|
|timezone|Pacific/Wake|
|timezone|Pacific/Wallis|
|timezone|Pacific/Yap|
|timezone|Poland|
|timezone|Portugal|
|timezone|ROC|
|timezone|ROK|
|timezone|Singapore|
|timezone|Turkey|
|timezone|UCT|
|timezone|US/Alaska|
|timezone|US/Aleutian|
|timezone|US/Arizona|
|timezone|US/Central|
|timezone|US/East-Indiana|
|timezone|US/Eastern|
|timezone|US/Hawaii|
|timezone|US/Indiana-Starke|
|timezone|US/Michigan|
|timezone|US/Mountain|
|timezone|US/Pacific|
|timezone|US/Samoa|
|timezone|UTC|
|timezone|Universal|
|timezone|W-SU|
|timezone|WET|
|timezone|Zulu|

<h2 id="tocS_MonitorList">MonitorList</h2>
<!-- backwards compatibility -->
<a id="schemamonitorlist"></a>
<a id="schema_MonitorList"></a>
<a id="tocSmonitorlist"></a>
<a id="tocsmonitorlist"></a>

```json
[
  {
    "id": "string",
    "name": "string",
    "slug": "string",
    "status": "string",
    "type": "string",
    "config": null,
    "dateCreated": "2019-08-24T14:15:22Z",
    "project": {
      "stats": null,
      "transactionStats": null,
      "sessionStats": null,
      "id": "string",
      "slug": "string",
      "name": "string",
      "platform": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "isBookmarked": true,
      "isMember": true,
      "features": [
        "string"
      ],
      "firstEvent": "2019-08-24T14:15:22Z",
      "firstTransactionEvent": true,
      "access": [
        "string"
      ],
      "hasAccess": true,
      "hasMinifiedStackTrace": true,
      "hasMonitors": true,
      "hasProfiles": true,
      "hasReplays": true,
      "hasSessions": true,
      "isInternal": true,
      "isPublic": true,
      "avatar": null,
      "color": "string",
      "status": "string"
    },
    "environments": {
      "name": "string",
      "status": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "lastCheckIn": "2019-08-24T14:15:22Z",
      "nextCheckIn": "2019-08-24T14:15:22Z"
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|name|string|true|none|none|
|slug|string|true|none|none|
|status|string|true|none|none|
|type|string|true|none|none|
|config|any|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|project|object|true|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» avatar|any|true|none|none|
|» color|string|true|none|none|
|» status|string|true|none|none|
|environments|object|true|none|none|
|» name|string|true|none|none|
|» status|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» lastCheckIn|string(date-time)|true|none|none|
|» nextCheckIn|string(date-time)|true|none|none|

<h2 id="tocS_MonitorValidator">MonitorValidator</h2>
<!-- backwards compatibility -->
<a id="schemamonitorvalidator"></a>
<a id="schema_MonitorValidator"></a>
<a id="tocSmonitorvalidator"></a>
<a id="tocsmonitorvalidator"></a>

```json
{
  "project": "string",
  "name": "string",
  "slug": "string",
  "status": "active",
  "type": "cron_job",
  "config": {
    "schedule_type": "crontab",
    "schedule": null,
    "checkin_margin": 0,
    "max_runtime": 1,
    "timezone": "Africa/Abidjan"
  },
  "alert_rule": {
    "environment": "string",
    "targets": [
      {
        "target_identifier": 0,
        "target_type": "string"
      }
    ]
  }
}

```

Allows parameters to be defined in snake case, but passed as camel case.

Errors are output in camel case.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|project|string|true|none|none|
|name|string|true|none|none|
|slug|string|false|none|none|
|status|string|false|none|none|
|type|string|true|none|none|
|config|object|true|none|none|
|» schedule_type|string|false|none|Currently supports "crontab" or "interval"|
|» schedule|any|true|none|Varies depending on the schedule_type. Is either a crontab string, or a 2 element tuple for intervals (e.g. [1, 'day'])|
|» checkin_margin|integer¦null|false|none|How long (in minutes) after the expected checkin time will we wait until we consider the checkin to have been missed.|
|» max_runtime|integer¦null|false|none|How long (in minutes) is the checkin allowed to run for in CheckInStatus.IN_PROGRESS before it is considered failed.|
|» timezone|string|false|none|tz database style timezone string|
|alert_rule|object|false|none|none|
|» environment|string¦null|false|none|Name of the environment|
|» targets|[object]|true|none|Array of dictionaries with information of the user or team to be notified|
|»» target_identifier|integer|true|none|ID of target object|
|»» target_type|string|true|none|One of [Member, Team]|

#### Enumerated Values

|Property|Value|
|---|---|
|status|active|
|status|disabled|
|type|cron_job|
|schedule_type|crontab|
|schedule_type|interval|
|timezone|Africa/Abidjan|
|timezone|Africa/Accra|
|timezone|Africa/Addis_Ababa|
|timezone|Africa/Algiers|
|timezone|Africa/Asmara|
|timezone|Africa/Asmera|
|timezone|Africa/Bamako|
|timezone|Africa/Bangui|
|timezone|Africa/Banjul|
|timezone|Africa/Bissau|
|timezone|Africa/Blantyre|
|timezone|Africa/Brazzaville|
|timezone|Africa/Bujumbura|
|timezone|Africa/Cairo|
|timezone|Africa/Casablanca|
|timezone|Africa/Ceuta|
|timezone|Africa/Conakry|
|timezone|Africa/Dakar|
|timezone|Africa/Dar_es_Salaam|
|timezone|Africa/Djibouti|
|timezone|Africa/Douala|
|timezone|Africa/El_Aaiun|
|timezone|Africa/Freetown|
|timezone|Africa/Gaborone|
|timezone|Africa/Harare|
|timezone|Africa/Johannesburg|
|timezone|Africa/Juba|
|timezone|Africa/Kampala|
|timezone|Africa/Khartoum|
|timezone|Africa/Kigali|
|timezone|Africa/Kinshasa|
|timezone|Africa/Lagos|
|timezone|Africa/Libreville|
|timezone|Africa/Lome|
|timezone|Africa/Luanda|
|timezone|Africa/Lubumbashi|
|timezone|Africa/Lusaka|
|timezone|Africa/Malabo|
|timezone|Africa/Maputo|
|timezone|Africa/Maseru|
|timezone|Africa/Mbabane|
|timezone|Africa/Mogadishu|
|timezone|Africa/Monrovia|
|timezone|Africa/Nairobi|
|timezone|Africa/Ndjamena|
|timezone|Africa/Niamey|
|timezone|Africa/Nouakchott|
|timezone|Africa/Ouagadougou|
|timezone|Africa/Porto-Novo|
|timezone|Africa/Sao_Tome|
|timezone|Africa/Timbuktu|
|timezone|Africa/Tripoli|
|timezone|Africa/Tunis|
|timezone|Africa/Windhoek|
|timezone|America/Adak|
|timezone|America/Anchorage|
|timezone|America/Anguilla|
|timezone|America/Antigua|
|timezone|America/Araguaina|
|timezone|America/Argentina/Buenos_Aires|
|timezone|America/Argentina/Catamarca|
|timezone|America/Argentina/ComodRivadavia|
|timezone|America/Argentina/Cordoba|
|timezone|America/Argentina/Jujuy|
|timezone|America/Argentina/La_Rioja|
|timezone|America/Argentina/Mendoza|
|timezone|America/Argentina/Rio_Gallegos|
|timezone|America/Argentina/Salta|
|timezone|America/Argentina/San_Juan|
|timezone|America/Argentina/San_Luis|
|timezone|America/Argentina/Tucuman|
|timezone|America/Argentina/Ushuaia|
|timezone|America/Aruba|
|timezone|America/Asuncion|
|timezone|America/Atikokan|
|timezone|America/Atka|
|timezone|America/Bahia|
|timezone|America/Bahia_Banderas|
|timezone|America/Barbados|
|timezone|America/Belem|
|timezone|America/Belize|
|timezone|America/Blanc-Sablon|
|timezone|America/Boa_Vista|
|timezone|America/Bogota|
|timezone|America/Boise|
|timezone|America/Buenos_Aires|
|timezone|America/Cambridge_Bay|
|timezone|America/Campo_Grande|
|timezone|America/Cancun|
|timezone|America/Caracas|
|timezone|America/Catamarca|
|timezone|America/Cayenne|
|timezone|America/Cayman|
|timezone|America/Chicago|
|timezone|America/Chihuahua|
|timezone|America/Coral_Harbour|
|timezone|America/Cordoba|
|timezone|America/Costa_Rica|
|timezone|America/Creston|
|timezone|America/Cuiaba|
|timezone|America/Curacao|
|timezone|America/Danmarkshavn|
|timezone|America/Dawson|
|timezone|America/Dawson_Creek|
|timezone|America/Denver|
|timezone|America/Detroit|
|timezone|America/Dominica|
|timezone|America/Edmonton|
|timezone|America/Eirunepe|
|timezone|America/El_Salvador|
|timezone|America/Ensenada|
|timezone|America/Fort_Nelson|
|timezone|America/Fort_Wayne|
|timezone|America/Fortaleza|
|timezone|America/Glace_Bay|
|timezone|America/Godthab|
|timezone|America/Goose_Bay|
|timezone|America/Grand_Turk|
|timezone|America/Grenada|
|timezone|America/Guadeloupe|
|timezone|America/Guatemala|
|timezone|America/Guayaquil|
|timezone|America/Guyana|
|timezone|America/Halifax|
|timezone|America/Havana|
|timezone|America/Hermosillo|
|timezone|America/Indiana/Indianapolis|
|timezone|America/Indiana/Knox|
|timezone|America/Indiana/Marengo|
|timezone|America/Indiana/Petersburg|
|timezone|America/Indiana/Tell_City|
|timezone|America/Indiana/Vevay|
|timezone|America/Indiana/Vincennes|
|timezone|America/Indiana/Winamac|
|timezone|America/Indianapolis|
|timezone|America/Inuvik|
|timezone|America/Iqaluit|
|timezone|America/Jamaica|
|timezone|America/Jujuy|
|timezone|America/Juneau|
|timezone|America/Kentucky/Louisville|
|timezone|America/Kentucky/Monticello|
|timezone|America/Knox_IN|
|timezone|America/Kralendijk|
|timezone|America/La_Paz|
|timezone|America/Lima|
|timezone|America/Los_Angeles|
|timezone|America/Louisville|
|timezone|America/Lower_Princes|
|timezone|America/Maceio|
|timezone|America/Managua|
|timezone|America/Manaus|
|timezone|America/Marigot|
|timezone|America/Martinique|
|timezone|America/Matamoros|
|timezone|America/Mazatlan|
|timezone|America/Mendoza|
|timezone|America/Menominee|
|timezone|America/Merida|
|timezone|America/Metlakatla|
|timezone|America/Mexico_City|
|timezone|America/Miquelon|
|timezone|America/Moncton|
|timezone|America/Monterrey|
|timezone|America/Montevideo|
|timezone|America/Montreal|
|timezone|America/Montserrat|
|timezone|America/Nassau|
|timezone|America/New_York|
|timezone|America/Nipigon|
|timezone|America/Nome|
|timezone|America/Noronha|
|timezone|America/North_Dakota/Beulah|
|timezone|America/North_Dakota/Center|
|timezone|America/North_Dakota/New_Salem|
|timezone|America/Ojinaga|
|timezone|America/Panama|
|timezone|America/Pangnirtung|
|timezone|America/Paramaribo|
|timezone|America/Phoenix|
|timezone|America/Port-au-Prince|
|timezone|America/Port_of_Spain|
|timezone|America/Porto_Acre|
|timezone|America/Porto_Velho|
|timezone|America/Puerto_Rico|
|timezone|America/Punta_Arenas|
|timezone|America/Rainy_River|
|timezone|America/Rankin_Inlet|
|timezone|America/Recife|
|timezone|America/Regina|
|timezone|America/Resolute|
|timezone|America/Rio_Branco|
|timezone|America/Rosario|
|timezone|America/Santa_Isabel|
|timezone|America/Santarem|
|timezone|America/Santiago|
|timezone|America/Santo_Domingo|
|timezone|America/Sao_Paulo|
|timezone|America/Scoresbysund|
|timezone|America/Shiprock|
|timezone|America/Sitka|
|timezone|America/St_Barthelemy|
|timezone|America/St_Johns|
|timezone|America/St_Kitts|
|timezone|America/St_Lucia|
|timezone|America/St_Thomas|
|timezone|America/St_Vincent|
|timezone|America/Swift_Current|
|timezone|America/Tegucigalpa|
|timezone|America/Thule|
|timezone|America/Thunder_Bay|
|timezone|America/Tijuana|
|timezone|America/Toronto|
|timezone|America/Tortola|
|timezone|America/Vancouver|
|timezone|America/Virgin|
|timezone|America/Whitehorse|
|timezone|America/Winnipeg|
|timezone|America/Yakutat|
|timezone|America/Yellowknife|
|timezone|Antarctica/Casey|
|timezone|Antarctica/Davis|
|timezone|Antarctica/DumontDUrville|
|timezone|Antarctica/Macquarie|
|timezone|Antarctica/Mawson|
|timezone|Antarctica/McMurdo|
|timezone|Antarctica/Palmer|
|timezone|Antarctica/Rothera|
|timezone|Antarctica/South_Pole|
|timezone|Antarctica/Syowa|
|timezone|Antarctica/Troll|
|timezone|Antarctica/Vostok|
|timezone|Arctic/Longyearbyen|
|timezone|Asia/Aden|
|timezone|Asia/Almaty|
|timezone|Asia/Amman|
|timezone|Asia/Anadyr|
|timezone|Asia/Aqtau|
|timezone|Asia/Aqtobe|
|timezone|Asia/Ashgabat|
|timezone|Asia/Ashkhabad|
|timezone|Asia/Atyrau|
|timezone|Asia/Baghdad|
|timezone|Asia/Bahrain|
|timezone|Asia/Baku|
|timezone|Asia/Bangkok|
|timezone|Asia/Barnaul|
|timezone|Asia/Beirut|
|timezone|Asia/Bishkek|
|timezone|Asia/Brunei|
|timezone|Asia/Calcutta|
|timezone|Asia/Chita|
|timezone|Asia/Choibalsan|
|timezone|Asia/Chongqing|
|timezone|Asia/Chungking|
|timezone|Asia/Colombo|
|timezone|Asia/Dacca|
|timezone|Asia/Damascus|
|timezone|Asia/Dhaka|
|timezone|Asia/Dili|
|timezone|Asia/Dubai|
|timezone|Asia/Dushanbe|
|timezone|Asia/Famagusta|
|timezone|Asia/Gaza|
|timezone|Asia/Harbin|
|timezone|Asia/Hebron|
|timezone|Asia/Ho_Chi_Minh|
|timezone|Asia/Hong_Kong|
|timezone|Asia/Hovd|
|timezone|Asia/Irkutsk|
|timezone|Asia/Istanbul|
|timezone|Asia/Jakarta|
|timezone|Asia/Jayapura|
|timezone|Asia/Jerusalem|
|timezone|Asia/Kabul|
|timezone|Asia/Kamchatka|
|timezone|Asia/Karachi|
|timezone|Asia/Kashgar|
|timezone|Asia/Kathmandu|
|timezone|Asia/Katmandu|
|timezone|Asia/Khandyga|
|timezone|Asia/Kolkata|
|timezone|Asia/Krasnoyarsk|
|timezone|Asia/Kuala_Lumpur|
|timezone|Asia/Kuching|
|timezone|Asia/Kuwait|
|timezone|Asia/Macao|
|timezone|Asia/Macau|
|timezone|Asia/Magadan|
|timezone|Asia/Makassar|
|timezone|Asia/Manila|
|timezone|Asia/Muscat|
|timezone|Asia/Nicosia|
|timezone|Asia/Novokuznetsk|
|timezone|Asia/Novosibirsk|
|timezone|Asia/Omsk|
|timezone|Asia/Oral|
|timezone|Asia/Phnom_Penh|
|timezone|Asia/Pontianak|
|timezone|Asia/Pyongyang|
|timezone|Asia/Qatar|
|timezone|Asia/Qostanay|
|timezone|Asia/Qyzylorda|
|timezone|Asia/Rangoon|
|timezone|Asia/Riyadh|
|timezone|Asia/Saigon|
|timezone|Asia/Sakhalin|
|timezone|Asia/Samarkand|
|timezone|Asia/Seoul|
|timezone|Asia/Shanghai|
|timezone|Asia/Singapore|
|timezone|Asia/Srednekolymsk|
|timezone|Asia/Taipei|
|timezone|Asia/Tashkent|
|timezone|Asia/Tbilisi|
|timezone|Asia/Tehran|
|timezone|Asia/Tel_Aviv|
|timezone|Asia/Thimbu|
|timezone|Asia/Thimphu|
|timezone|Asia/Tokyo|
|timezone|Asia/Tomsk|
|timezone|Asia/Ujung_Pandang|
|timezone|Asia/Ulaanbaatar|
|timezone|Asia/Ulan_Bator|
|timezone|Asia/Urumqi|
|timezone|Asia/Ust-Nera|
|timezone|Asia/Vientiane|
|timezone|Asia/Vladivostok|
|timezone|Asia/Yakutsk|
|timezone|Asia/Yangon|
|timezone|Asia/Yekaterinburg|
|timezone|Asia/Yerevan|
|timezone|Atlantic/Azores|
|timezone|Atlantic/Bermuda|
|timezone|Atlantic/Canary|
|timezone|Atlantic/Cape_Verde|
|timezone|Atlantic/Faeroe|
|timezone|Atlantic/Faroe|
|timezone|Atlantic/Jan_Mayen|
|timezone|Atlantic/Madeira|
|timezone|Atlantic/Reykjavik|
|timezone|Atlantic/South_Georgia|
|timezone|Atlantic/St_Helena|
|timezone|Atlantic/Stanley|
|timezone|Australia/ACT|
|timezone|Australia/Adelaide|
|timezone|Australia/Brisbane|
|timezone|Australia/Broken_Hill|
|timezone|Australia/Canberra|
|timezone|Australia/Currie|
|timezone|Australia/Darwin|
|timezone|Australia/Eucla|
|timezone|Australia/Hobart|
|timezone|Australia/LHI|
|timezone|Australia/Lindeman|
|timezone|Australia/Lord_Howe|
|timezone|Australia/Melbourne|
|timezone|Australia/NSW|
|timezone|Australia/North|
|timezone|Australia/Perth|
|timezone|Australia/Queensland|
|timezone|Australia/South|
|timezone|Australia/Sydney|
|timezone|Australia/Tasmania|
|timezone|Australia/Victoria|
|timezone|Australia/West|
|timezone|Australia/Yancowinna|
|timezone|Brazil/Acre|
|timezone|Brazil/DeNoronha|
|timezone|Brazil/East|
|timezone|Brazil/West|
|timezone|CET|
|timezone|CST6CDT|
|timezone|Canada/Atlantic|
|timezone|Canada/Central|
|timezone|Canada/Eastern|
|timezone|Canada/Mountain|
|timezone|Canada/Newfoundland|
|timezone|Canada/Pacific|
|timezone|Canada/Saskatchewan|
|timezone|Canada/Yukon|
|timezone|Chile/Continental|
|timezone|Chile/EasterIsland|
|timezone|Cuba|
|timezone|EET|
|timezone|EST|
|timezone|EST5EDT|
|timezone|Egypt|
|timezone|Eire|
|timezone|Etc/GMT|
|timezone|Etc/GMT+0|
|timezone|Etc/GMT+1|
|timezone|Etc/GMT+10|
|timezone|Etc/GMT+11|
|timezone|Etc/GMT+12|
|timezone|Etc/GMT+2|
|timezone|Etc/GMT+3|
|timezone|Etc/GMT+4|
|timezone|Etc/GMT+5|
|timezone|Etc/GMT+6|
|timezone|Etc/GMT+7|
|timezone|Etc/GMT+8|
|timezone|Etc/GMT+9|
|timezone|Etc/GMT-0|
|timezone|Etc/GMT-1|
|timezone|Etc/GMT-10|
|timezone|Etc/GMT-11|
|timezone|Etc/GMT-12|
|timezone|Etc/GMT-13|
|timezone|Etc/GMT-14|
|timezone|Etc/GMT-2|
|timezone|Etc/GMT-3|
|timezone|Etc/GMT-4|
|timezone|Etc/GMT-5|
|timezone|Etc/GMT-6|
|timezone|Etc/GMT-7|
|timezone|Etc/GMT-8|
|timezone|Etc/GMT-9|
|timezone|Etc/GMT0|
|timezone|Etc/Greenwich|
|timezone|Etc/UCT|
|timezone|Etc/UTC|
|timezone|Etc/Universal|
|timezone|Etc/Zulu|
|timezone|Europe/Amsterdam|
|timezone|Europe/Andorra|
|timezone|Europe/Astrakhan|
|timezone|Europe/Athens|
|timezone|Europe/Belfast|
|timezone|Europe/Belgrade|
|timezone|Europe/Berlin|
|timezone|Europe/Bratislava|
|timezone|Europe/Brussels|
|timezone|Europe/Bucharest|
|timezone|Europe/Budapest|
|timezone|Europe/Busingen|
|timezone|Europe/Chisinau|
|timezone|Europe/Copenhagen|
|timezone|Europe/Dublin|
|timezone|Europe/Gibraltar|
|timezone|Europe/Guernsey|
|timezone|Europe/Helsinki|
|timezone|Europe/Isle_of_Man|
|timezone|Europe/Istanbul|
|timezone|Europe/Jersey|
|timezone|Europe/Kaliningrad|
|timezone|Europe/Kiev|
|timezone|Europe/Kirov|
|timezone|Europe/Lisbon|
|timezone|Europe/Ljubljana|
|timezone|Europe/London|
|timezone|Europe/Luxembourg|
|timezone|Europe/Madrid|
|timezone|Europe/Malta|
|timezone|Europe/Mariehamn|
|timezone|Europe/Minsk|
|timezone|Europe/Monaco|
|timezone|Europe/Moscow|
|timezone|Europe/Nicosia|
|timezone|Europe/Oslo|
|timezone|Europe/Paris|
|timezone|Europe/Podgorica|
|timezone|Europe/Prague|
|timezone|Europe/Riga|
|timezone|Europe/Rome|
|timezone|Europe/Samara|
|timezone|Europe/San_Marino|
|timezone|Europe/Sarajevo|
|timezone|Europe/Saratov|
|timezone|Europe/Simferopol|
|timezone|Europe/Skopje|
|timezone|Europe/Sofia|
|timezone|Europe/Stockholm|
|timezone|Europe/Tallinn|
|timezone|Europe/Tirane|
|timezone|Europe/Tiraspol|
|timezone|Europe/Ulyanovsk|
|timezone|Europe/Uzhgorod|
|timezone|Europe/Vaduz|
|timezone|Europe/Vatican|
|timezone|Europe/Vienna|
|timezone|Europe/Vilnius|
|timezone|Europe/Volgograd|
|timezone|Europe/Warsaw|
|timezone|Europe/Zagreb|
|timezone|Europe/Zaporozhye|
|timezone|Europe/Zurich|
|timezone|GB|
|timezone|GB-Eire|
|timezone|GMT|
|timezone|GMT+0|
|timezone|GMT-0|
|timezone|GMT0|
|timezone|Greenwich|
|timezone|HST|
|timezone|Hongkong|
|timezone|Iceland|
|timezone|Indian/Antananarivo|
|timezone|Indian/Chagos|
|timezone|Indian/Christmas|
|timezone|Indian/Cocos|
|timezone|Indian/Comoro|
|timezone|Indian/Kerguelen|
|timezone|Indian/Mahe|
|timezone|Indian/Maldives|
|timezone|Indian/Mauritius|
|timezone|Indian/Mayotte|
|timezone|Indian/Reunion|
|timezone|Iran|
|timezone|Israel|
|timezone|Jamaica|
|timezone|Japan|
|timezone|Kwajalein|
|timezone|Libya|
|timezone|MET|
|timezone|MST|
|timezone|MST7MDT|
|timezone|Mexico/BajaNorte|
|timezone|Mexico/BajaSur|
|timezone|Mexico/General|
|timezone|NZ|
|timezone|NZ-CHAT|
|timezone|Navajo|
|timezone|PRC|
|timezone|PST8PDT|
|timezone|Pacific/Apia|
|timezone|Pacific/Auckland|
|timezone|Pacific/Bougainville|
|timezone|Pacific/Chatham|
|timezone|Pacific/Chuuk|
|timezone|Pacific/Easter|
|timezone|Pacific/Efate|
|timezone|Pacific/Enderbury|
|timezone|Pacific/Fakaofo|
|timezone|Pacific/Fiji|
|timezone|Pacific/Funafuti|
|timezone|Pacific/Galapagos|
|timezone|Pacific/Gambier|
|timezone|Pacific/Guadalcanal|
|timezone|Pacific/Guam|
|timezone|Pacific/Honolulu|
|timezone|Pacific/Johnston|
|timezone|Pacific/Kiritimati|
|timezone|Pacific/Kosrae|
|timezone|Pacific/Kwajalein|
|timezone|Pacific/Majuro|
|timezone|Pacific/Marquesas|
|timezone|Pacific/Midway|
|timezone|Pacific/Nauru|
|timezone|Pacific/Niue|
|timezone|Pacific/Norfolk|
|timezone|Pacific/Noumea|
|timezone|Pacific/Pago_Pago|
|timezone|Pacific/Palau|
|timezone|Pacific/Pitcairn|
|timezone|Pacific/Pohnpei|
|timezone|Pacific/Ponape|
|timezone|Pacific/Port_Moresby|
|timezone|Pacific/Rarotonga|
|timezone|Pacific/Saipan|
|timezone|Pacific/Samoa|
|timezone|Pacific/Tahiti|
|timezone|Pacific/Tarawa|
|timezone|Pacific/Tongatapu|
|timezone|Pacific/Truk|
|timezone|Pacific/Wake|
|timezone|Pacific/Wallis|
|timezone|Pacific/Yap|
|timezone|Poland|
|timezone|Portugal|
|timezone|ROC|
|timezone|ROK|
|timezone|Singapore|
|timezone|Turkey|
|timezone|UCT|
|timezone|US/Alaska|
|timezone|US/Aleutian|
|timezone|US/Arizona|
|timezone|US/Central|
|timezone|US/East-Indiana|
|timezone|US/Eastern|
|timezone|US/Hawaii|
|timezone|US/Indiana-Starke|
|timezone|US/Michigan|
|timezone|US/Mountain|
|timezone|US/Pacific|
|timezone|US/Samoa|
|timezone|UTC|
|timezone|Universal|
|timezone|W-SU|
|timezone|WET|
|timezone|Zulu|

<h2 id="tocS_OrganizationEventsResponseDict">OrganizationEventsResponseDict</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationeventsresponsedict"></a>
<a id="schema_OrganizationEventsResponseDict"></a>
<a id="tocSorganizationeventsresponsedict"></a>
<a id="tocsorganizationeventsresponsedict"></a>

```json
{
  "data": [
    {
      "property1": null,
      "property2": null
    }
  ],
  "meta": {
    "fields": {
      "property1": "string",
      "property2": "string"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[object]|true|none|none|
|» **additionalProperties**|any|false|none|none|
|meta|object|true|none|none|
|» fields|object|true|none|none|
|»» **additionalProperties**|string|false|none|none|

<h2 id="tocS_OrganizationMemberSCIM">OrganizationMemberSCIM</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationmemberscim"></a>
<a id="schema_OrganizationMemberSCIM"></a>
<a id="tocSorganizationmemberscim"></a>
<a id="tocsorganizationmemberscim"></a>

```json
{
  "active": true,
  "schemas": [
    "string"
  ],
  "id": "string",
  "userName": "string",
  "name": {
    "givenName": "string",
    "familyName": "string"
  },
  "emails": [
    {
      "primary": true,
      "value": "string",
      "type": "string"
    }
  ],
  "meta": {
    "resourceType": "string"
  },
  "sentryOrgRole": "string"
}

```

Conforming to the SCIM RFC, this represents a Sentry Org Member
as a SCIM user object.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|active|boolean|false|none|none|
|schemas|[string]|true|none|none|
|id|string|true|none|none|
|userName|string|true|none|none|
|name|object|true|none|none|
|» givenName|string|true|none|none|
|» familyName|string|true|none|none|
|emails|[object]|true|none|none|
|» primary|boolean|true|none|none|
|» value|string|true|none|none|
|» type|string|true|none|none|
|meta|object|true|none|none|
|» resourceType|string|true|none|none|
|sentryOrgRole|string|true|none|none|

<h2 id="tocS_OrganizationMemberWithRoles">OrganizationMemberWithRoles</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationmemberwithroles"></a>
<a id="schema_OrganizationMemberWithRoles"></a>
<a id="tocSorganizationmemberwithroles"></a>
<a id="tocsorganizationmemberwithroles"></a>

```json
{
  "externalUsers": [
    {
      "externalId": "string",
      "userId": "string",
      "teamId": "string",
      "id": "string",
      "provider": "string",
      "externalName": "string",
      "integrationId": "string"
    }
  ],
  "id": "string",
  "email": "string",
  "name": "string",
  "user": {
    "identities": [
      {
        "id": "string",
        "name": "string",
        "organization": {
          "slug": "string",
          "name": "string"
        },
        "provider": {
          "id": "string",
          "name": "string"
        },
        "dateVerified": "2019-08-24T14:15:22Z",
        "dateSynced": "2019-08-24T14:15:22Z"
      }
    ],
    "avatar": {
      "avatarType": "string",
      "avatarUuid": "string"
    },
    "id": "string",
    "name": "string",
    "username": "string",
    "email": "string",
    "avatarUrl": "string",
    "isActive": true,
    "hasPasswordAuth": true,
    "isManaged": true,
    "dateJoined": "2019-08-24T14:15:22Z",
    "lastLogin": "2019-08-24T14:15:22Z",
    "has2fa": true,
    "lastActive": "2019-08-24T14:15:22Z",
    "isSuperuser": true,
    "isStaff": true,
    "experiments": {
      "property1": null,
      "property2": null
    },
    "emails": [
      {
        "id": "string",
        "email": "string",
        "is_verified": true
      }
    ]
  },
  "role": "string",
  "roleName": "string",
  "orgRole": "string",
  "groupOrgRoles": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "pending": true,
  "expired": "string",
  "flags": {
    "idp:provisioned": true,
    "idp:role-restricted": true,
    "sso:linked": true,
    "sso:invalid": true,
    "member-limit:restricted": true
  },
  "dateCreated": "2019-08-24T14:15:22Z",
  "inviteStatus": "string",
  "inviterName": "string",
  "teams": [
    "string"
  ],
  "teamRoles": [
    {
      "teamSlug": "string",
      "role": "string"
    }
  ],
  "invite_link": "string",
  "isOnlyOwner": true,
  "roles": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "orgRoleList": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ],
  "teamRoleList": [
    {
      "id": "string",
      "name": "string",
      "desc": "string",
      "scopes": [
        "string"
      ],
      "is_global": true,
      "allowed": true
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|externalUsers|[object]|false|none|none|
|» externalId|string|false|none|none|
|» userId|string|false|none|none|
|» teamId|string|false|none|none|
|» id|string|true|none|none|
|» provider|string|true|none|none|
|» externalName|string|true|none|none|
|» integrationId|string|true|none|none|
|id|string|true|none|none|
|email|string|true|none|none|
|name|string|true|none|none|
|user|object|true|none|none|
|» identities|[object]|false|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|»» organization|object|true|none|none|
|»»» slug|string|true|none|none|
|»»» name|string|true|none|none|
|»» provider|object|true|none|none|
|»»» id|string|true|none|none|
|»»» name|string|true|none|none|
|»» dateVerified|string(date-time)|true|none|none|
|»» dateSynced|string(date-time)|true|none|none|
|» avatar|object|false|none|none|
|»» avatarType|string|true|none|none|
|»» avatarUuid|string¦null|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» username|string|true|none|none|
|» email|string|true|none|none|
|» avatarUrl|string|true|none|none|
|» isActive|boolean|true|none|none|
|» hasPasswordAuth|boolean|true|none|none|
|» isManaged|boolean|true|none|none|
|» dateJoined|string(date-time)|true|none|none|
|» lastLogin|string(date-time)|true|none|none|
|» has2fa|boolean|true|none|none|
|» lastActive|string(date-time)|true|none|none|
|» isSuperuser|boolean|true|none|none|
|» isStaff|boolean|true|none|none|
|» experiments|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» emails|[object]|true|none|none|
|»» id|string|true|none|none|
|»» email|string|true|none|none|
|»» is_verified|boolean|true|none|none|
|role|string|true|none|none|
|roleName|string|true|none|none|
|orgRole|string|true|none|none|
|groupOrgRoles|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» desc|string|true|none|none|
|» scopes|[string]|true|none|none|
|» is_global|boolean|true|none|none|
|» allowed|boolean|true|none|none|
|pending|boolean|true|none|none|
|expired|string|true|none|none|
|flags|object|true|none|none|
|» idp:provisioned|boolean|true|none|none|
|» idp:role-restricted|boolean|true|none|none|
|» sso:linked|boolean|true|none|none|
|» sso:invalid|boolean|true|none|none|
|» member-limit:restricted|boolean|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|inviteStatus|string|true|none|none|
|inviterName|string¦null|true|none|none|
|teams|[string]|true|none|none|
|teamRoles|[object]|true|none|none|
|» teamSlug|string|true|none|none|
|» role|string|true|none|none|
|invite_link|string¦null|true|none|none|
|isOnlyOwner|boolean|true|none|none|
|roles|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» desc|string|true|none|none|
|» scopes|[string]|true|none|none|
|» is_global|boolean|true|none|none|
|» allowed|boolean|true|none|none|
|orgRoleList|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» desc|string|true|none|none|
|» scopes|[string]|true|none|none|
|» is_global|boolean|true|none|none|
|» allowed|boolean|true|none|none|
|teamRoleList|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» desc|string|true|none|none|
|» scopes|[string]|true|none|none|
|» is_global|boolean|true|none|none|
|» allowed|boolean|true|none|none|

<h2 id="tocS_OrganizationProjectResponseDict">OrganizationProjectResponseDict</h2>
<!-- backwards compatibility -->
<a id="schemaorganizationprojectresponsedict"></a>
<a id="schema_OrganizationProjectResponseDict"></a>
<a id="tocSorganizationprojectresponsedict"></a>
<a id="tocsorganizationprojectresponsedict"></a>

```json
[
  {
    "latestDeploys": {
      "property1": {
        "property1": "string",
        "property2": "string"
      },
      "property2": {
        "property1": "string",
        "property2": "string"
      }
    },
    "stats": null,
    "transactionStats": null,
    "sessionStats": null,
    "id": "string",
    "slug": "string",
    "name": "string",
    "platform": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isBookmarked": true,
    "isMember": true,
    "features": [
      "string"
    ],
    "firstEvent": "2019-08-24T14:15:22Z",
    "firstTransactionEvent": true,
    "access": [
      "string"
    ],
    "hasAccess": true,
    "hasMinifiedStackTrace": true,
    "hasMonitors": true,
    "hasProfiles": true,
    "hasReplays": true,
    "hasSessions": true,
    "team": {
      "id": "string",
      "name": "string",
      "slug": "string"
    },
    "teams": [
      {
        "id": "string",
        "name": "string",
        "slug": "string"
      }
    ],
    "eventProcessing": {
      "symbolicationDegraded": true
    },
    "platforms": [
      "string"
    ],
    "hasUserReports": true,
    "environments": [
      "string"
    ],
    "latestRelease": {
      "version": "string"
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|latestDeploys|object¦null|false|none|none|
|» **additionalProperties**|object|false|none|none|
|»» **additionalProperties**|string|false|none|none|
|stats|any|false|none|none|
|transactionStats|any|false|none|none|
|sessionStats|any|false|none|none|
|id|string|true|none|none|
|slug|string|true|none|none|
|name|string|true|none|none|
|platform|string¦null|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|isBookmarked|boolean|true|none|none|
|isMember|boolean|true|none|none|
|features|[string]|true|none|none|
|firstEvent|string(date-time)¦null|true|none|none|
|firstTransactionEvent|boolean|true|none|none|
|access|[string]|true|none|none|
|hasAccess|boolean|true|none|none|
|hasMinifiedStackTrace|boolean|true|none|none|
|hasMonitors|boolean|true|none|none|
|hasProfiles|boolean|true|none|none|
|hasReplays|boolean|true|none|none|
|hasSessions|boolean|true|none|none|
|team|object¦null|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|teams|[object]|true|none|none|
|» id|string|true|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|eventProcessing|object|true|none|none|
|» symbolicationDegraded|boolean|true|none|none|
|platforms|[string]|true|none|none|
|hasUserReports|boolean|true|none|none|
|environments|[string]|true|none|none|
|latestRelease|object¦null|true|none|none|
|» version|string|true|none|none|

<h2 id="tocS_OutcomesResponse">OutcomesResponse</h2>
<!-- backwards compatibility -->
<a id="schemaoutcomesresponse"></a>
<a id="schema_OutcomesResponse"></a>
<a id="tocSoutcomesresponse"></a>
<a id="tocsoutcomesresponse"></a>

```json
{
  "start": "string",
  "end": "string",
  "intervals": [
    "string"
  ],
  "groups": [
    {
      "by": {
        "property1": null,
        "property2": null
      },
      "totals": {
        "property1": null,
        "property2": null
      },
      "series": {
        "property1": null,
        "property2": null
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|start|string|true|none|none|
|end|string|true|none|none|
|intervals|[string]|true|none|none|
|groups|[object]|true|none|none|
|» by|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» totals|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|
|» series|object|true|none|none|
|»» **additionalProperties**|any|false|none|none|

<h2 id="tocS_Project">Project</h2>
<!-- backwards compatibility -->
<a id="schemaproject"></a>
<a id="schema_Project"></a>
<a id="tocSproject"></a>
<a id="tocsproject"></a>

```json
{
  "stats": null,
  "transactionStats": null,
  "sessionStats": null,
  "id": "string",
  "slug": "string",
  "name": "string",
  "platform": "string",
  "dateCreated": "2019-08-24T14:15:22Z",
  "isBookmarked": true,
  "isMember": true,
  "features": [
    "string"
  ],
  "firstEvent": "2019-08-24T14:15:22Z",
  "firstTransactionEvent": true,
  "access": [
    "string"
  ],
  "hasAccess": true,
  "hasMinifiedStackTrace": true,
  "hasMonitors": true,
  "hasProfiles": true,
  "hasReplays": true,
  "hasSessions": true,
  "isInternal": true,
  "isPublic": true,
  "avatar": null,
  "color": "string",
  "status": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|stats|any|false|none|none|
|transactionStats|any|false|none|none|
|sessionStats|any|false|none|none|
|id|string|true|none|none|
|slug|string|true|none|none|
|name|string|true|none|none|
|platform|string¦null|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|isBookmarked|boolean|true|none|none|
|isMember|boolean|true|none|none|
|features|[string]|true|none|none|
|firstEvent|string(date-time)¦null|true|none|none|
|firstTransactionEvent|boolean|true|none|none|
|access|[string]|true|none|none|
|hasAccess|boolean|true|none|none|
|hasMinifiedStackTrace|boolean|true|none|none|
|hasMonitors|boolean|true|none|none|
|hasProfiles|boolean|true|none|none|
|hasReplays|boolean|true|none|none|
|hasSessions|boolean|true|none|none|
|isInternal|boolean|true|none|none|
|isPublic|boolean|true|none|none|
|avatar|any|true|none|none|
|color|string|true|none|none|
|status|string|true|none|none|

<h2 id="tocS_ProjectPost">ProjectPost</h2>
<!-- backwards compatibility -->
<a id="schemaprojectpost"></a>
<a id="schema_ProjectPost"></a>
<a id="tocSprojectpost"></a>
<a id="tocsprojectpost"></a>

```json
{
  "name": "string",
  "slug": "string",
  "platform": "string",
  "default_rules": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|true|none|none|
|slug|string¦null|false|none|none|
|platform|string¦null|false|none|none|
|default_rules|boolean|false|none|none|

<h2 id="tocS_SCIMListResponseEnvelopeSCIMMemberIndexResponse">SCIMListResponseEnvelopeSCIMMemberIndexResponse</h2>
<!-- backwards compatibility -->
<a id="schemascimlistresponseenvelopescimmemberindexresponse"></a>
<a id="schema_SCIMListResponseEnvelopeSCIMMemberIndexResponse"></a>
<a id="tocSscimlistresponseenvelopescimmemberindexresponse"></a>
<a id="tocsscimlistresponseenvelopescimmemberindexresponse"></a>

```json
{
  "schemas": [
    "string"
  ],
  "totalResults": 0,
  "startIndex": 0,
  "itemsPerPage": 0,
  "Resources": [
    {
      "active": true,
      "schemas": [
        "string"
      ],
      "id": "string",
      "userName": "string",
      "name": {
        "givenName": "string",
        "familyName": "string"
      },
      "emails": [
        {
          "primary": true,
          "value": "string",
          "type": "string"
        }
      ],
      "meta": {
        "resourceType": "string"
      },
      "sentryOrgRole": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[string]|true|none|none|
|totalResults|integer|true|none|none|
|startIndex|integer|true|none|none|
|itemsPerPage|integer|true|none|none|
|Resources|[object]|true|none|none|
|» active|boolean|false|none|none|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» userName|string|true|none|none|
|» name|object|true|none|none|
|»» givenName|string|true|none|none|
|»» familyName|string|true|none|none|
|» emails|[object]|true|none|none|
|»» primary|boolean|true|none|none|
|»» value|string|true|none|none|
|»» type|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|true|none|none|
|» sentryOrgRole|string|true|none|none|

<h2 id="tocS_SCIMListResponseEnvelopeSCIMTeamIndexResponse">SCIMListResponseEnvelopeSCIMTeamIndexResponse</h2>
<!-- backwards compatibility -->
<a id="schemascimlistresponseenvelopescimteamindexresponse"></a>
<a id="schema_SCIMListResponseEnvelopeSCIMTeamIndexResponse"></a>
<a id="tocSscimlistresponseenvelopescimteamindexresponse"></a>
<a id="tocsscimlistresponseenvelopescimteamindexresponse"></a>

```json
{
  "schemas": [
    "string"
  ],
  "totalResults": 0,
  "startIndex": 0,
  "itemsPerPage": 0,
  "Resources": [
    {
      "schemas": [
        "string"
      ],
      "id": "string",
      "displayName": "string",
      "meta": {
        "resourceType": "string"
      },
      "members": [
        {
          "value": "string",
          "display": "string"
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[string]|true|none|none|
|totalResults|integer|true|none|none|
|startIndex|integer|true|none|none|
|itemsPerPage|integer|true|none|none|
|Resources|[object]|true|none|none|
|» schemas|[string]|true|none|none|
|» id|string|true|none|none|
|» displayName|string|true|none|none|
|» meta|object|true|none|none|
|»» resourceType|string|true|none|none|
|» members|[object]|false|none|none|
|»» value|string|true|none|none|
|»» display|string|true|none|none|

<h2 id="tocS_SCIMMemberProvision">SCIMMemberProvision</h2>
<!-- backwards compatibility -->
<a id="schemascimmemberprovision"></a>
<a id="schema_SCIMMemberProvision"></a>
<a id="tocSscimmemberprovision"></a>
<a id="tocsscimmemberprovision"></a>

```json
{
  "userName": "user@example.com",
  "sentryOrgRole": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|userName|string(email)|true|none|none|
|sentryOrgRole|string|false|none|none|

<h2 id="tocS_SCIMPatchOperation">SCIMPatchOperation</h2>
<!-- backwards compatibility -->
<a id="schemascimpatchoperation"></a>
<a id="schema_SCIMPatchOperation"></a>
<a id="tocSscimpatchoperation"></a>
<a id="tocsscimpatchoperation"></a>

```json
{
  "op": "string",
  "value": null,
  "path": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|op|string|true|none|none|
|value|any|true|none|none|
|path|string|false|none|none|

<h2 id="tocS_SCIMPatchRequest">SCIMPatchRequest</h2>
<!-- backwards compatibility -->
<a id="schemascimpatchrequest"></a>
<a id="schema_SCIMPatchRequest"></a>
<a id="tocSscimpatchrequest"></a>
<a id="tocsscimpatchrequest"></a>

```json
{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "value": null,
      "path": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[string]|false|none|none|
|Operations|[object]|true|none|none|
|» op|string|true|none|none|
|» value|any|true|none|none|
|» path|string|false|none|none|

<h2 id="tocS_SCIMTeamPatchOperation">SCIMTeamPatchOperation</h2>
<!-- backwards compatibility -->
<a id="schemascimteampatchoperation"></a>
<a id="schema_SCIMTeamPatchOperation"></a>
<a id="tocSscimteampatchoperation"></a>
<a id="tocsscimteampatchoperation"></a>

```json
{
  "op": "string",
  "value": [
    null
  ],
  "path": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|op|string|true|none|none|
|value|[any]|true|read-only|none|
|path|string|false|none|none|

<h2 id="tocS_SCIMTeamPatchRequest">SCIMTeamPatchRequest</h2>
<!-- backwards compatibility -->
<a id="schemascimteampatchrequest"></a>
<a id="schema_SCIMTeamPatchRequest"></a>
<a id="tocSscimteampatchrequest"></a>
<a id="tocsscimteampatchrequest"></a>

```json
{
  "schemas": [
    "string"
  ],
  "Operations": [
    {
      "op": "string",
      "value": [
        null
      ],
      "path": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[string]|true|none|none|
|Operations|[object]|true|none|none|
|» op|string|true|none|none|
|» value|[any]|true|read-only|none|
|» path|string|false|none|none|

<h2 id="tocS_SCIMTeamRequestBody">SCIMTeamRequestBody</h2>
<!-- backwards compatibility -->
<a id="schemascimteamrequestbody"></a>
<a id="schema_SCIMTeamRequestBody"></a>
<a id="tocSscimteamrequestbody"></a>
<a id="tocsscimteamrequestbody"></a>

```json
{
  "schemas": [
    null
  ],
  "displayName": "string",
  "members": [
    null
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[any]|true|read-only|none|
|displayName|string|true|none|none|
|members|[any]|true|read-only|none|

<h2 id="tocS_SourceMapDebug">SourceMapDebug</h2>
<!-- backwards compatibility -->
<a id="schemasourcemapdebug"></a>
<a id="schema_SourceMapDebug"></a>
<a id="tocSsourcemapdebug"></a>
<a id="tocssourcemapdebug"></a>

```json
{
  "errors": [
    {
      "type": "string",
      "message": "string",
      "data": {
        "property1": null,
        "property2": null
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errors|[object]|true|none|none|
|» type|string|true|none|none|
|» message|string|true|none|none|
|» data|object¦null|true|none|none|
|»» **additionalProperties**|any|false|none|none|

<h2 id="tocS_Team">Team</h2>
<!-- backwards compatibility -->
<a id="schemateam"></a>
<a id="schema_Team"></a>
<a id="tocSteam"></a>
<a id="tocsteam"></a>

```json
{
  "externalTeams": [
    {
      "externalId": "string",
      "userId": "string",
      "teamId": "string",
      "id": "string",
      "provider": "string",
      "externalName": "string",
      "integrationId": "string"
    }
  ],
  "organization": {
    "id": "string",
    "slug": "string",
    "status": {
      "id": "string",
      "name": "string"
    },
    "name": "string",
    "dateCreated": "2019-08-24T14:15:22Z",
    "isEarlyAdopter": true,
    "require2FA": true,
    "requireEmailVerification": true,
    "avatar": null,
    "features": null,
    "links": {
      "organizationUrl": "string",
      "regionUrl": "string"
    },
    "hasAuthProvider": true
  },
  "projects": [
    {
      "stats": null,
      "transactionStats": null,
      "sessionStats": null,
      "id": "string",
      "slug": "string",
      "name": "string",
      "platform": "string",
      "dateCreated": "2019-08-24T14:15:22Z",
      "isBookmarked": true,
      "isMember": true,
      "features": [
        "string"
      ],
      "firstEvent": "2019-08-24T14:15:22Z",
      "firstTransactionEvent": true,
      "access": [
        "string"
      ],
      "hasAccess": true,
      "hasMinifiedStackTrace": true,
      "hasMonitors": true,
      "hasProfiles": true,
      "hasReplays": true,
      "hasSessions": true,
      "isInternal": true,
      "isPublic": true,
      "avatar": null,
      "color": "string",
      "status": "string"
    }
  ],
  "id": "string",
  "slug": "string",
  "name": "string",
  "dateCreated": "2019-08-24T14:15:22Z",
  "isMember": true,
  "teamRole": "string",
  "flags": {
    "property1": null,
    "property2": null
  },
  "access": [
    "string"
  ],
  "hasAccess": true,
  "isPending": true,
  "memberCount": 0,
  "avatar": {
    "avatarType": "string",
    "avatarUuid": "string"
  },
  "orgRole": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|externalTeams|[object]|false|none|none|
|» externalId|string|false|none|none|
|» userId|string|false|none|none|
|» teamId|string|false|none|none|
|» id|string|true|none|none|
|» provider|string|true|none|none|
|» externalName|string|true|none|none|
|» integrationId|string|true|none|none|
|organization|object|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» status|object|true|none|none|
|»» id|string|true|none|none|
|»» name|string|true|none|none|
|» name|string|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isEarlyAdopter|boolean|true|none|none|
|» require2FA|boolean|true|none|none|
|» requireEmailVerification|boolean|true|none|none|
|» avatar|any|true|none|none|
|» features|any|true|none|none|
|» links|object|true|none|none|
|»» organizationUrl|string|true|none|none|
|»» regionUrl|string|true|none|none|
|» hasAuthProvider|boolean|true|none|none|
|projects|[object]|false|none|none|
|» stats|any|false|none|none|
|» transactionStats|any|false|none|none|
|» sessionStats|any|false|none|none|
|» id|string|true|none|none|
|» slug|string|true|none|none|
|» name|string|true|none|none|
|» platform|string¦null|true|none|none|
|» dateCreated|string(date-time)|true|none|none|
|» isBookmarked|boolean|true|none|none|
|» isMember|boolean|true|none|none|
|» features|[string]|true|none|none|
|» firstEvent|string(date-time)¦null|true|none|none|
|» firstTransactionEvent|boolean|true|none|none|
|» access|[string]|true|none|none|
|» hasAccess|boolean|true|none|none|
|» hasMinifiedStackTrace|boolean|true|none|none|
|» hasMonitors|boolean|true|none|none|
|» hasProfiles|boolean|true|none|none|
|» hasReplays|boolean|true|none|none|
|» hasSessions|boolean|true|none|none|
|» isInternal|boolean|true|none|none|
|» isPublic|boolean|true|none|none|
|» avatar|any|true|none|none|
|» color|string|true|none|none|
|» status|string|true|none|none|
|id|string|true|none|none|
|slug|string|true|none|none|
|name|string|true|none|none|
|dateCreated|string(date-time)|true|none|none|
|isMember|boolean|true|none|none|
|teamRole|string¦null|true|none|none|
|flags|object|true|none|none|
|» **additionalProperties**|any|false|none|none|
|access|[string]|true|none|none|
|hasAccess|boolean|true|none|none|
|isPending|boolean|true|none|none|
|memberCount|integer|true|none|none|
|avatar|object|true|none|none|
|» avatarType|string|true|none|none|
|» avatarUuid|string¦null|true|none|none|
|orgRole|string¦null|true|none|none|

<h2 id="tocS_TeamPost">TeamPost</h2>
<!-- backwards compatibility -->
<a id="schemateampost"></a>
<a id="schema_TeamPost"></a>
<a id="tocSteampost"></a>
<a id="tocsteampost"></a>

```json
{
  "name": "string",
  "slug": "string",
  "idp_provisioned": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string¦null|false|none|none|
|slug|string¦null|false|none|none|
|idp_provisioned|boolean|false|none|none|

<h2 id="tocS_TeamSCIM">TeamSCIM</h2>
<!-- backwards compatibility -->
<a id="schemateamscim"></a>
<a id="schema_TeamSCIM"></a>
<a id="tocSteamscim"></a>
<a id="tocsteamscim"></a>

```json
{
  "schemas": [
    "string"
  ],
  "id": "string",
  "displayName": "string",
  "meta": {
    "resourceType": "string"
  },
  "members": [
    {
      "value": "string",
      "display": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|schemas|[string]|true|none|none|
|id|string|true|none|none|
|displayName|string|true|none|none|
|meta|object|true|none|none|
|» resourceType|string|true|none|none|
|members|[object]|false|none|none|
|» value|string|true|none|none|
|» display|string|true|none|none|

