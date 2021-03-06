# Microservices

A list of information related to the microservices

<aside class="notice">
    These services are only available to ADMIN users.
</aside>

## List all registered microservices

To obtain a list of all the registered microservices:

```shell
curl -X GET https://api.resourcewatch.org/api/v1/microservice \
-H "Authorization: Bearer <your-token>"
```

> Example response:

```json
[
    {
        "infoStatus": {
            "numRetries": 0,
            "error": null,
            "lastCheck": "2019-02-04T14:05:30.748Z"
        },
        "pathInfo": "/info",
        "pathLive": "/ping",
        "status": "active",
        "cache": [],
        "uncache": [],
        "tags": [
            "dataset"
          
        ],
        "_id": "id",
        "name": "Dataset",
        "url": "http://dataset.default.svc.cluster.local:3000",
        "version": 1,
        "endpoints": [
            {
                "redirect": {
                    "method": "GET",
                    "path": "/api/v1/dataset"
                },
                "path": "/v1/dataset",
                "method": "GET"
            },
            {
                "redirect": {
                    "method": "POST",
                    "path": "/api/v1/dataset/find-by-ids"
                },
                "path": "/v1/dataset/find-by-ids",
                "method": "POST"
            },
            ...
        ],
        "updatedAt": "2019-01-24T13:04:46.728Z",
        "swagger": "{}"
    },
    {
        "infoStatus": {
            "numRetries": 0,
            "error": null,
            "lastCheck": "2019-02-04T14:05:30.778Z"
        },
        "pathInfo": "/info",
        "pathLive": "/ping",
        "status": "active",
        "cache": [
            "layer"
        ],
        "uncache": [
            "layer",
            "dataset"
        ],
        "tags": [
            "layer"
        ],
        "_id": "5aa667d1aee7ae16fb419c23",
        "name": "Layer",
        "url": "http://layer.default.svc.cluster.local:6000",
        "version": 1,
        "endpoints": [
            {
                "redirect": {
                    "method": "GET",
                    "path": "/api/v1/layer"
                },
                "path": "/v1/layer",
                "method": "GET"
            },
            {
                "redirect": {
                    "method": "POST",
                    "path": "/api/v1/dataset/:dataset/layer"
                },
                "path": "/v1/dataset/:dataset/layer",
                "method": "POST"
            },
            {
                "redirect": {
                    "method": "GET",
                    "path": "/api/v1/dataset/:dataset/layer"
                },
                "path": "/v1/dataset/:dataset/layer",
                "method": "GET"
            },
            ...
        ],
        "updatedAt": "2018-11-08T12:07:38.014Z",
        "swagger": "{}"
    },
    ...
  }
}
```

## Delete microservice

To remove a microservice:

```shell
curl -X DELETE https://api.resourcewatch.org/api/v1/microservice/:id \
-H "Authorization: Bearer <your-token>"
```

#### Notes

Keep in mind that this does not actually delete the microservice, instead it schedules it for being removed. 
There's a cron task that does the actual deleting, so the process is async.