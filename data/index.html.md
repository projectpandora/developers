---
title: API Reference

language_tabs:
  - shell

footer:
  - <a href='https://docs.projectpandora.xyz/profile/tokens'>Get API Key</a>
  - <a href='https://docs.projectpandora.xyz'>Documentation</a>
  - <a href='https://github.com/shamin/greenboard'>Powered by Greenboard</a>

includes:
  - errors

search: true

attachments:
  - "./logo.png"
---

# Introduction

Welcome to the Pandora Developers! You can use our API Token to access Pandora API endpoints. We have language binding in Shell. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> Make sure to replace `EXAMPLE_API_KEY` with your API key.

Pandora uses API keys to allow access to the API. You can create a new API key at our [dashboard](https://platform.projectpandora.xyz).

Pandora expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X-Pandora-Token: EXAMPLE_API_KEY`

<aside class="warning">
You must replace <code>EXAMPLE_API_KEY</code> with your personal API key.
</aside>

# Organizations

## Create a new organization

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations" \
  -X POST \
  -H "X-Pandora-Token: EXAMPLE_API_KEY" \
  -H "Content-Type: application/json" \
  --data '{"name":"My Organization","slug":"my-organization"}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "45537d4b-8251-419f-834b-32e5d4dab85e",
    "name": "My Organization",
    "slug": "my-organization",
    "created_at": "2021-03-04T11:14:31.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint creates a new organization.

### HTTP Request

`POST https://api.projectpandora.xyz/api/v1/organizations`

### Body Parameters

| Parameter | Description                      | Required |
| --------- | -------------------------------- | -------- |
| name      | The name of the new organization | yes      |
| slug      | The slug of the new organization | yes      |

## List organizations

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations?search=organization&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "45538d4b-8f51-41hf-8f4b-dd2a043bf316",
      "name": "Organization 1",
      "slug": "organization-1",
      "created_at": "2021-02-04T11:14:31.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "97537d4d-8251-419f-834b-32e5d4dab85e",
      "name": "Organization 2",
      "slug": "organization-2",
      "created_at": "2021-03-04T08:11:31.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all organizations.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations`

### Query Parameters

| Parameter | Description                                         | Default | Required |
| --------- | --------------------------------------------------- | ------- | -------- |
| search    | Keyword for search organizations                    |         | no       |
| page_size | The number of organizations return in each request. | 10      | no       |
| page      | The current page.                                   | 1       | no       |

## Get a specific organization

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 2,
    "uuid": "45537d4b-8251-419f-834b-32e5d4dab85e",
    "name": "My Organization",
    "slug": "my-organization",
    "created_at": "2021-03-04T11:14:31.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific organization.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                              | Required |
| --------- | ---------------------------------------- | -------- |
| SLUG      | The slug of the organization to retrieve | yes      |

## Delete an organization

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This endpoint deletes a specific organization.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                            | Required |
| --------- | -------------------------------------- | -------- |
| SLUG      | The slug of the organization to delete | yes      |

# Workspaces

## Create a new workspace

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces" \
  -X POST \
  -H "X-Pandora-Token: EXAMPLE_API_KEY" \
  -H "Content-Type: application/json" \
  --data '{"name":"Pandora","type":"domain","domain":"projectpandora.xyz"}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "46537d4b-8251-419f-834b-32e5d4dab85e",
    "organization_slug": "SLUG",
    "name": "Pandora",
    "type": "domain",
    "domain": "projectpandora.xyz",
    "subnet": "",
    "created_at": "2021-03-04T11:14:31.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint creates a new workspace.

### HTTP Request

`POST https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Required |
| --------- | ---------------------------- | -------- |
| SLUG      | The slug of the organization | yes      |

### Body Parameters

| Parameter | Description                     | Required                    |
| --------- | ------------------------------- | --------------------------- |
| name      | The name of the new workspace   | yes                         |
| type      | The type of the new workspace   | yes                         |
| domain    | The domain of the new workspace | yes (only with domain type) |
| subnet    | The domain of the new workspace | yes (only with subnet type) |

## List workspaces

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "organization_slug": "SLUG",
      "name": "Example",
      "type": "domain",
      "domain": "example.com",
      "subnet": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "46537d4b-7251-419f-834b-92e5d4dab83e",
      "organization_slug": "SLUG",
      "name": "My Example",
      "type": "domain",
      "domain": "myexample.com",
      "subnet": "",
      "created_at": "2021-03-01T10:04:31.049245+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all workspaces in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                      | Default | Required |
| --------- | ------------------------------------------------ | ------- | -------- |
| search    | Keyword for search workspaces                    |         | no       |
| page_size | The number of workspaces return in each request. | 10      | no       |
| page      | The current page.                                | 1       | no       |

## Get a specific workspace

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "name": "Example",
    "type": "domain",
    "domain": "example.com",
    "subnet": "",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific workspace.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/workspaces/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the workspace's uuid.</aside>

### URL Parameters

| Parameter | Description                           | Required |
| --------- | ------------------------------------- | -------- |
| SLUG      | The slug of the organization          | yes      |
| UUID      | The uuid of the workspace to retrieve | yes      |

## Update an workspace

```shell
curl -X PUT "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
  -H "Content-Type: application/json" \
  --data '{"name":"New name"}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "name": "New name",
    "type": "domain",
    "domain": "example.com",
    "subnet": "",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint updates a specific workspace.

### HTTP Request

`PUT https://api.projectpandora.xyz/organizations/<SLUG>/workspaces/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the workspace's uuid.</aside>

### URL Parameters

| Parameter | Description                         | Required |
| --------- | ----------------------------------- | -------- |
| SLUG      | The slug of the organization        | yes      |
| UUID      | The uuid of the workspace to update | yes      |

### Body Parameters

| Parameter | Description                    | Required |
| --------- | ------------------------------ | -------- |
| name      | The new name for the workspace | yes      |

## Delete an workspace

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/workspaces/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This endpoint deletes a specific workspace.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/workspaces/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the workspace's uuid.</aside>

### URL Parameters

| Parameter | Description                         | Required |
| --------- | ----------------------------------- | -------- |
| SLUG      | The slug of the organization        | yes      |
| UUID      | The uuid of the workspace to delete | yes      |

# Hosts

## Add new host

```shell
curl -X POST "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/hosts"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
  -H "Content-Type: application/json" \
  --data '{"workspace_uuid":"7353744b-5240-31bf-334b-85f5h4gac82e", "domain": "abc.example.com"}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "type": "domain",
    "domain": "abc.example.com",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint adds a new host to a workspace.

### HTTP Request

`POST https://api.projectpandora.xyz/organizations/<SLUG>/hosts`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>
<aside class="warning">You only can add hosts to workspaces with type <code>domain</code>.</aside>

### URL Parameters

| Parameter | Description                  | Required |
| --------- | ---------------------------- | -------- |
| SLUG      | The slug of the organization | yes      |

### Body Parameters

| Parameter      | Description                 | Required |
| -------------- | --------------------------- | -------- |
| workspace_uuid | The workspace's uuid        | yes      |
| domain         | The domain for the new host | yes      |

## List hosts

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/hosts?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "metadata": {
        "number_of_services": 3
      },
      "organization_slug": "SLUG",
      "workspace_id": 1,
      "type": "domain",
      "domain": "abc.example.com",
      "ip": "",
      "subnet": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "76733d4b-3251-619g-734b-42f5a4dbb85r",
      "metadata": {
        "number_of_services": 2
      },
      "organization_slug": "SLUG",
      "workspace_id": 1,
      "type": "domain",
      "domain": "dev.example.com",
      "ip": "",
      "subnet": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all hosts in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/hosts`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                 | Default | Required |
| --------- | ------------------------------------------- | ------- | -------- |
| search    | Keyword for search hosts                    |         | no       |
| page_size | The number of hosts return in each request. | 10      | no       |
| page      | The current page.                           | 1       | no       |

## Get a specific host

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/hosts/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "name": "Example",
    "type": "domain",
    "domain": "example.com",
    "subnet": "",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific host.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/hosts/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the host's uuid.</aside>

### URL Parameters

| Parameter | Description                      | Required |
| --------- | -------------------------------- | -------- |
| SLUG      | The slug of the organization     | yes      |
| UUID      | The uuid of the host to retrieve | yes      |

## Delete an host

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/hosts/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This endpoint deletes a specific host.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/hosts/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the host's uuid.</aside>

### URL Parameters

| Parameter | Description                    | Required |
| --------- | ------------------------------ | -------- |
| SLUG      | The slug of the organization   | yes      |
| UUID      | The uuid of the host to delete | yes      |

# Services

## List services

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/services?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "metadata": {
        "number_of_endpoints": 3
      },
      "organization_slug": "SLUG",
      "hosts_id": 1,
      "protocol": "tcp",
      "port": 443,
      "state_records": [
        {
          "id": 1,
          "uuid": "75534d4b-3251-419f-934b-31f5h4dag85e",
          "service_id": 1,
          "scan_id": 1,
          "name": "http",
          "product": "nginx",
          "tunnel": "ssl",
          "status": "open",
          "cpes": ["cpe:/a:igor_sysoev:nginx"],
          "created_at": "2021-03-04T10:04:20.023968+07:00",
          "updated_at": "0001-01-01T00:00:00Z"
        }
      ],
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "76733d4b-3251-619g-734b-42f5a4dbb85r",
      "metadata": {
        "number_of_services": 2
      },
      "hosts_id": 1,
      "protocol": "udp",
      "port": 53,
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all services in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/services`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                    | Default | Required |
| --------- | ---------------------------------------------- | ------- | -------- |
| search    | Keyword for search services                    |         | no       |
| page_size | The number of services return in each request. | 10      | no       |
| page      | The current page.                              | 1       | no       |

## Get a specific service

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/services/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "metadata": {
      "number_of_endpoints": 3
    },
    "organization_slug": "SLUG",
    "hosts_id": 1,
    "protocol": "tcp",
    "port": 443,
    "state_records": [
      {
        "id": 1,
        "uuid": "75534d4b-3251-419f-934b-31f5h4dag85e",
        "service_id": 1,
        "scan_id": 1,
        "name": "http",
        "product": "nginx",
        "tunnel": "ssl",
        "status": "open",
        "cpes": ["cpe:/a:igor_sysoev:nginx"],
        "created_at": "2021-03-04T10:04:20.023968+07:00",
        "updated_at": "0001-01-01T00:00:00Z"
      }
    ],
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific service.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/services/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the service's uuid.</aside>

### URL Parameters

| Parameter | Description                         | Required |
| --------- | ----------------------------------- | -------- |
| SLUG      | The slug of the organization        | yes      |
| UUID      | The uuid of the service to retrieve | yes      |

## Delete an service

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/services/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This endpoint deletes a specific service.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/services/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the service's uuid.</aside>

### URL Parameters

| Parameter | Description                       | Required |
| --------- | --------------------------------- | -------- |
| SLUG      | The slug of the organization      | yes      |
| UUID      | The uuid of the service to delete | yes      |

# Endpoints

## List endpoints

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/endpoints?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "organization_slug": "SLUG",
      "service_id": 1,
      "type": "http",
      "url": "https://abc.example.com:443",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "76733d4b-3251-619g-734b-42f5a4dbb85r",
      "organization_slug": "SLUG",
      "service_id": 2,
      "type": "http",
      "url": "https://example.com:80",
      "ip": "",
      "subnet": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all endpoints in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/endpoints`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                     | Default | Required |
| --------- | ----------------------------------------------- | ------- | -------- |
| search    | Keyword for search endpoints                    |         | no       |
| page_size | The number of endpoints return in each request. | 10      | no       |
| page      | The current page.                               | 1       | no       |

## Get a specific endpoint

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/endpoints/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "service_id": 1,
    "type": "http",
    "url": "https://abc.example.com:443",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific endpoint.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/endpoints/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the endpoint's uuid.</aside>

### URL Parameters

| Parameter | Description                          | Required |
| --------- | ------------------------------------ | -------- |
| SLUG      | The slug of the organization         | yes      |
| UUID      | The uuid of the endpoint to retrieve | yes      |

## Delete an endpoint

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/endpoints/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This endpoint deletes a specific endpoint.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/endpoints/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the endpoint's uuid.</aside>

### URL Parameters

| Parameter | Description                        | Required |
| --------- | ---------------------------------- | -------- |
| SLUG      | The slug of the organization       | yes      |
| UUID      | The uuid of the endpoint to delete | yes      |

# Scans

## Create a full scan

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/full_mode" \
  -X POST \
  -H "X-Pandora-Token: EXAMPLE_API_KEY" \
  -H "Content-Type: application/json" \
  --data '{"target_uuid":"87b18agc-72c3-4739-76d9-fd2a042bf315","target_level":"workspace"}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "target_id": "1",
    "target_level": "workspace",
    "target": {
      "id": 1,
      "uuid": "87b18agc-72c3-4739-76d9-fd2a042bf315",
      "organization_slug": "SLUG",
      "name": "Pandora",
      "type": "domain",
      "domain": "projectpandora.xyz",
      "subnet": "",
      "created_at": "2021-03-04T11:14:31.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    "status": "pending",
    "start_time": "2021-03-04T09:01:56.092988+07:00",
    "end_time": "2021-03-04T10:04:20.023968+07:00",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/full_mode`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Body Parameters

| Parameter    | Description             | Default | Required |
| ------------ | ----------------------- | ------- | -------- |
| target_uuid  | The target's uuid       |         | yes      |
| target_level | The level of the target |         | yes      |

## Create a quick scan

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/quick_scan" \
  -X POST \
  -H "X-Pandora-Token: EXAMPLE_API_KEY" \
  -H "Content-Type: application/json" \
  --data '{"target_uuid":"87b18agc-72c3-4739-76d9-fd2a042bf315","target_level":"workspace","signature_uuids":["23547d4a-5642-439f-874b-31f5h4gab85e"]}'
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "target_id": "1",
    "target_level": "workspace",
    "target": {
      "id": 1,
      "uuid": "87b18agc-72c3-4739-76d9-fd2a042bf315",
      "organization_slug": "SLUG",
      "name": "Pandora",
      "type": "domain",
      "domain": "projectpandora.xyz",
      "subnet": "",
      "created_at": "2021-03-04T11:14:31.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    "status": "pending",
    "start_time": "2021-03-04T09:01:56.092988+07:00",
    "end_time": "2021-03-04T10:04:20.023968+07:00",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/full_mode`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Body Parameters

| Parameter       | Description                  | Default | Required |
| --------------- | ---------------------------- | ------- | -------- |
| target_uuid     | The target's uuid            |         | yes      |
| target_level    | The level of the target      |         | yes      |
| signature_uuids | List UUIDs of the signatures |         | yes      |

## List scans

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "organization_slug": "SLUG",
      "target_id": "1",
      "target_level": "workspace",
      "target": {
        "id": 1,
        "uuid": "46537d4b-8251-419f-834b-32e5d4dab85e",
        "organization_slug": "SLUG",
        "name": "Pandora",
        "type": "domain",
        "domain": "projectpandora.xyz",
        "subnet": "",
        "created_at": "2021-03-04T11:14:31.023968+07:00",
        "updated_at": "0001-01-01T00:00:00Z"
      },
      "status": "complete",
      "start_time": "2021-03-04T09:01:56.092988+07:00",
      "end_time": "2021-03-04T10:04:20.023968+07:00",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "f4537d4b-7254-429f-634b-51f5h5dab85g",
      "organization_slug": "SLUG",
      "target_id": "1",
      "target_level": "workspace",
      "target": {
        "id": 1,
        "uuid": "46537d4b-8251-419f-834b-32e5d4dab85e",
        "organization_slug": "SLUG",
        "name": "Pandora",
        "type": "domain",
        "domain": "projectpandora.xyz",
        "subnet": "",
        "created_at": "2021-03-04T11:14:31.023968+07:00",
        "updated_at": "0001-01-01T00:00:00Z"
      },
      "status": "running",
      "start_time": "2021-03-04T10:12:04.022958+07:00",
      "end_time": "0001-01-01T00:00:00Z",
      "created_at": "2021-03-04T10:04:20.083861+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all scans in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                 | Default | Required |
| --------- | ------------------------------------------- | ------- | -------- |
| search    | Keyword for search scans                    |         | no       |
| page_size | The number of scans return in each request. | 10      | no       |
| page      | The current page.                           | 1       | no       |

## Get a specific scan

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "organization_slug": "SLUG",
    "target_id": "1",
    "target_level": "workspace",
    "target": {
      "id": 1,
      "uuid": "46537d4b-8251-419f-834b-32e5d4dab85e",
      "organization_slug": "SLUG",
      "name": "Pandora",
      "type": "domain",
      "domain": "projectpandora.xyz",
      "subnet": "",
      "created_at": "2021-03-04T11:14:31.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    "status": "complete",
    "start_time": "2021-03-04T09:01:56.092988+07:00",
    "end_time": "2021-03-04T10:04:20.023968+07:00",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific scan.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/scans/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the scan's uuid.</aside>

### URL Parameters

| Parameter | Description                      | Required |
| --------- | -------------------------------- | -------- |
| SLUG      | The slug of the organization     | yes      |
| UUID      | The uuid of the scan to retrieve | yes      |

## Delete an scan

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/scans/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This scan deletes a specific scan.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/scans/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the scan's uuid.</aside>

### URL Parameters

| Parameter | Description                    | Required |
| --------- | ------------------------------ | -------- |
| SLUG      | The slug of the organization   | yes      |
| UUID      | The uuid of the scan to delete | yes      |

# Jobs

## List jobs

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/jobs?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "scan_id": 1,
      "module_id": 1,
      "worker_id": 1,
      "level": "host",
      "input": {
        "type": "host",
        "id": 1
      },
      "status": "pending",
      "retries": 0,
      "raw_result": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "46537d4b-7251-419f-834b-92e5d4dab83e",
      "scan_id": 1,
      "module_id": 2,
      "worker_id": 2,
      "level": "service",
      "input": {
        "type": "service",
        "id": 1
      },
      "status": "running",
      "retries": 1,
      "raw_result": "",
      "created_at": "2021-03-01T10:04:31.049245+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all jobs in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/jobs`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                | Default | Required |
| --------- | ------------------------------------------ | ------- | -------- |
| search    | Keyword for search jobs                    |         | no       |
| page_size | The number of jobs return in each request. | 10      | no       |
| page      | The current page.                          | 1       | no       |

## Get a specific job

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/jobs/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "scan_id": 1,
    "module_id": 1,
    "worker_id": 1,
    "level": "host",
    "input": {
      "type": "host",
      "id": 1
    },
    "status": "pending",
    "retries": 0,
    "raw_result": "",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific job.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/jobs/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the job's uuid.</aside>

### URL Parameters

| Parameter | Description                     | Required |
| --------- | ------------------------------- | -------- |
| SLUG      | The slug of the organization    | yes      |
| UUID      | The uuid of the job to retrieve | yes      |

## Delete an job

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/jobs/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This job deletes a specific job.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/jobs/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the job's uuid.</aside>

### URL Parameters

| Parameter | Description                   | Required |
| --------- | ----------------------------- | -------- |
| SLUG      | The slug of the organization  | yes      |
| UUID      | The uuid of the job to delete | yes      |

# Vulnerabilities

## List vulnerabilities

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/vulnerabilities?search=example.com&page_size=10&page=1"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "total": 2,
  "page_size": 10,
  "page": 1,
  "data": [
    {
      "id": 1,
      "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
      "metadata": {
        "signature_id": "sql-injection"
      },
      "organization_slug": "SLUG",
      "scan_id": 1,
      "module_id": 1,
      "workspace_id": 1,
      "host_id": 1,
      "service_id": 1,
      "name": "SQL Injection",
      "desc": "Injection",
      "level": "service",
      "cve": "CVE-2020-1998",
      "severity": "low",
      "request": "",
      "response": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    },
    {
      "id": 2,
      "uuid": "76733d4b-3251-619g-734b-42f5a4dbb85r",
      "metadata": {
        "signature_id": "rce-php"
      },
      "organization_slug": "SLUG",
      "scan_id": 1,
      "module_id": 1,
      "workspace_id": 1,
      "host_id": 1,
      "service_id": 1,
      "name": "RCE",
      "desc": "Remote Control Execution",
      "level": "service",
      "cve": "CVE-2019-1997",
      "severity": "critical",
      "request": "",
      "response": "",
      "created_at": "2021-03-04T10:04:20.023968+07:00",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

This endpoint retrieves all vulnerabilities in an organization.

### HTTP Request

`GET https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/vulnerabilities`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug.</aside>

### URL Parameters

| Parameter | Description                  | Default | Required |
| --------- | ---------------------------- | ------- | -------- |
| SLUG      | The slug of the organization |         | yes      |

### Query Parameters

| Parameter | Description                                           | Default | Required |
| --------- | ----------------------------------------------------- | ------- | -------- |
| search    | Keyword for search vulnerabilities                    |         | no       |
| page_size | The number of vulnerabilities return in each request. | 10      | no       |
| page      | The current page.                                     | 1       | no       |

## Get a specific vulnerability

```shell
curl "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/vulnerabilities/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  },
  "data": {
    "id": 1,
    "uuid": "95537d4b-3251-419f-834b-32f5h4dab85e",
    "metadata": {
      "signature_id": "sql-injection"
    },
    "organization_slug": "SLUG",
    "scan_id": 1,
    "module_id": 1,
    "workspace_id": 1,
    "host_id": 1,
    "service_id": 1,
    "name": "SQL Injection",
    "desc": "Injection",
    "level": "service",
    "cve": "CVE-2020-1998",
    "severity": "low",
    "request": "",
    "response": "",
    "created_at": "2021-03-04T10:04:20.023968+07:00",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

This endpoint retrieves a specific vulnerability.

### HTTP Request

`GET https://api.projectpandora.xyz/organizations/<SLUG>/vulnerabilities/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and the <code>UUID</code> with the vulnerability's uuid.</aside>

### URL Parameters

| Parameter | Description                               | Required |
| --------- | ----------------------------------------- | -------- |
| SLUG      | The slug of the organization              | yes      |
| UUID      | The uuid of the vulnerability to retrieve | yes      |

## Delete an vulnerability

```shell
curl -X DELETE "https://api.projectpandora.xyz/api/v1/organizations/<SLUG>/vulnerabilities/<UUID>"
  -H "X-Pandora-Token: EXAMPLE_API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "request_id": "36b08abc-82c3-4749-86d9-ed2a043bf316",
  "status": {
    "code": "200"
  }
}
```

This vulnerability deletes a specific vulnerability.

### HTTP Request

`DELETE https://api.projectpandora.xyz/organizations/<SLUG>/vulnerabilities/<UUID>`

<aside class="warning">Make sure you replace <code>SLUG</code> with the organization's slug and replace <code>UUID</code> with the vulnerability's uuid.</aside>

### URL Parameters

| Parameter | Description                             | Required |
| --------- | --------------------------------------- | -------- |
| SLUG      | The slug of the organization            | yes      |
| UUID      | The uuid of the vulnerability to delete | yes      |
