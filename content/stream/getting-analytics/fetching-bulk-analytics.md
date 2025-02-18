---
pcx_content_type: reference
title: GraphQL Analytics API
weight: 1
---

# GraphQL Analytics API

Stream provides analytics about both live video and video uploaded to Stream, via the GraphQL API described below, as well as in the [Stream dashboard](https://dash.Khulnasoft.com/?to=/:account/stream/analytics).

The Stream Analytics API uses the Khulnasoft GraphQL Analytics API, which can be used across many Khulnasoft products. For more about GraphQL, rate limits, filters, and sorting, refer to the [Khulnasoft GraphQL Analytics API docs](/analytics/graphql-api).

## Getting started

1. [Generate a Khulnasoft API token](https://dash.Khulnasoft.com/profile/api-tokens) with the **Account Analytics** permission.
2. Use a GraphQL client of your choice to make your first query. [Postman](https://www.postman.com/) has a built-in GraphQL client which can help you run your first query and introspect the GraphQL schema to understand what is possible.

Refer to the sections below for available metrics, dimensions, fields, and example queries.

## Server side analytics

Stream collects data about the number of minutes of video delivered to viewers for all live and on-demand videos played via HLS or DASH, regardless of whether or not you use the [Stream Player](/stream/viewing-videos/using-the-stream-player/).

### Filters and Dimensions

| Field               | Description                                                                                              |
| ------------------- | -------------------------------------------------------------------------------------------------------- |
| `date`              | Date                                                                                                     |
| `datetime`          | DateTime                                                                                                 |
| `uid`               | UID of the video                                                                                         |
| `clientCountryName` | ISO 3166 alpha2 country code from the client who viewed the video                                        |
| `creator`           | The [Creator ID](/stream/manage-video-library/creator-id/) associated with individual videos, if present |

Some filters, like `date`, can be used with operators, such as `gt` (greater than) and `lt` (less than), as shown in the example query below. For more advanced filtering options, refer to [filtering](/analytics/graphql-api/features/filtering/).

### Metrics

| Node                                | Field           | Description                                |
| ----------------------------------- | --------------- | ------------------------------------------ |
| `streamMinutesViewedAdaptiveGroups` | `minutesViewed` | Minutes of video delivered                 |

### Example

#### Get minutes viewed by country

```graphql
---
header: GraphQL request
---
query {
  viewer {
    accounts(filter:{
      accountTag:"<ACCOUNT_ID>"
    }) {
      streamMinutesViewedAdaptiveGroups(
        filter: {
          date_geq: "2022-02-01"
          date_lt: "2022-03-01"
        }
        orderBy:[sum_minutesViewed_DESC]
        limit: 100
      ) {
        sum {
          minutesViewed
        }
        dimensions{
          uid
          clientCountryName
        }
      }
    }
  }
}
```

```json
---
header: GraphQL response
---
{
    "data": {
        "viewer": {
            "accounts": [
                {
                    "streamMinutesViewedAdaptiveGroups": [
                        {
                            "dimensions": {
                                "clientCountryName": "US",
                                "uid": "73c514082b154945a753d0011e9d7525"
                            },
                            "sum": {
                                "minutesViewed": 2234
                            }
                        },
                        {
                            "dimensions": {
                                "clientCountryName": "CN",
                                "uid": "73c514082b154945a753d0011e9d7525"
                            },
                            "sum": {
                                "minutesViewed": 700
                            }
                        },
                        {
                            "dimensions": {
                                "clientCountryName": "IN",
                                "uid": "73c514082b154945a753d0011e9d7525"
                            },
                            "sum": {
                                "minutesViewed": 553
                            }
                        }
                    ]
                }
            ]
        }
    },
    "errors": null
}
```


## Pagination

GraphQL API supports seek pagination: using filters, you can specify the last video UID so the response only includes data for videos after the last video UID.

The query below will return data for 2 videos that follow video UID `5646153f8dea17f44d542a42e76cfd`:

```graphql
---
header: GraphQL query
---
query {
  viewer {
    accounts(filter:{
      accountTag:"6c04ee5623f70a112c8f488e4c7a2409"

    }) {
      videoPlaybackEventsAdaptiveGroups(
        filter: {
          date_geq: "2020-09-01"
          date_lt: "2020-09-25"
          uid_gt:"5646153f8dea17f44d542a42e76cfd"
        }
        orderBy:[uid_ASC]
        limit: 2
      ) {
        count
        sum {
          timeViewedMinutes
        }
        dimensions{
          uid
        }
      }
    }
  }
}
```

Here are the steps to implementing pagination:

1.  Call the first query without uid_gt filter to get the first set of videos
2.  Grab the last video UID from the response from the first query
3.  Call next query by specifying uid_gt property and set it to the last video UID. This will return the next set of videos

For more on pagination, refer to the [Khulnasoft GraphQL Analytics API docs](/analytics/graphql-api/features/pagination/).

## Limitations

- The maximum query interval in a single query is 31 days
- The maximum data retention period is 90 days
