---
title: API Reference

language_tabs:
  - shell

footer:
  - <a href='#'>Get API Key</a>
  - <a href='https://github.com/shamin/greenboard'>Powered by Greenboard</a>

includes:
  - errors

search: true

attachments:
  - "./logo.png"
---

# Introduction

Welcome to the Pandora API! You can use our API to access Pandora API endpoints, which can get information on various cats, organizations, and breeds in our database.

We have language bindings in Shell. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> Make sure to replace `EXAMPLE_API_KEY` with your API key.

Pandora uses API keys to allow access to the API. You can create a new API key at our [dashboard](https://api.projectpandora.xyz/developers).

Pandora expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X-Pandora-Token: EXAMPLE_API_KEY`

<aside class="notice">
You must replace <code>EXAMPLE_API_KEY</code> with your personal API key.
</aside>

# Organizations

## Create a new organization

```shell
curl "https://api.projectpandora.xyz/api/organizations/2"
  -X POST
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2
}
```

This endpoint creates a new organization.

### HTTP Request

`POST https://api.projectpandora.xyz/organizations/<ID>`

### URL Parameters

| Parameter | Description                      | Required |
| --------- | -------------------------------- | -------- |
| name      | The name of the new organization | yes      |
| slug      | The slug of the new organization | yes      |

## List organizations

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all organizations.

### HTTP Request

`GET https://api.projectpandora.xyz/api/organizations`

### Query Parameters

| Parameter    | Default | Description                                                                            |
| ------------ | ------- | -------------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                                     |
| available    | true    | If set to false, the result will include organizations that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a specific organization

```shell
curl "https://api.projectpandora.xyz/api/organizations/my-organization"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<ID>`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |
