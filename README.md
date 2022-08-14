# Microservices Implementation With Ocelot Gateway with Aggregate
Microservices Implementation with Ocelot Gateway

call multiple end-point by using keys in Ocelot package 


{

  "Routes": [
    {
      "UpstreamPathTemplate": "/gateway/product",
      "UpstreamHttpMethod": [ "Get" ],
      "DownstreamPathTemplate": "/api/product",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7233
        }
      ],
      "Key": "product-key"
    },
    {
      "UpstreamPathTemplate": "/gateway/product/{id}",
      "UpstreamHttpMethod": [ "Get", "Delete" ],
      "DownstreamPathTemplate": "/api/product/{id}",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7233
        }
      ]
    },
    {
      "UpstreamPathTemplate": "/gateway/product",
      "UpstreamHttpMethod": [ "Post", "Put" ],
      "DownstreamPathTemplate": "/api/product",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7233
        }
      ]
    },
    {
      "UpstreamPathTemplate": "/gateway/user",
      "UpstreamHttpMethod": [ "Get" ],
      "DownstreamPathTemplate": "/api/user",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7285
        }
      ],
      "Key": "user-key"
    },
    {
      "UpstreamPathTemplate": "/gateway/user/{id}",
      "UpstreamHttpMethod": [ "Get", "Delete" ],
      "DownstreamPathTemplate": "/api/user/{id}",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7285
        }
      ]
    },
    {
      "UpstreamPathTemplate": "/gateway/user",
      "UpstreamHttpMethod": [ "Post", "Put" ],
      "DownstreamPathTemplate": "/api/user",
      "DownstreamScheme": "https",
      "DownstreamHostAndPorts": [
        {
          "Host": "localhost",
          "Port": 7285
        }
      ]
    }
  ],
  "Aggregates": [
    {
      "RouteKeys": [
        "user-key",
        "product-key"
      ],
      "UpstreamPathTemplate": "/api/user-product"

    }
  ],
  "GlobalConfiguration": {
    "BaseUrl": "https://localhost:7283"
  }
}
