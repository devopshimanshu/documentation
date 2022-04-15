# API Gateway
API Gateway is an abstraction layer which helps traffic to interact with your backend services.
API Gateway also provides:
 - Authenticate access to the service
 - Secure data transport between client and the services
 - Protect the service from malicious attacks
 - Scale the service as usage increase or decrease
 - Provide the backend operations team with a way to monitor and track service usage
 - Track usage to provide accurate billing information

# Requirments to Create an API Gateway
 1. OpenAPI 2.0 spec
    - Update endpoint 
    - Access key
 2. Google Service account through whihc it communicate internal services.
 3. 

API Gateway is an API management system hat provides management, monitoring, and authentication or your APIs.

The Components are :
- **API Gateway:** for managing all aspects of a deployed API
- **Service Control:** for applying management rules
- **Service Management:** for managing API configuration
- **gCloud CLI:** or deploying and managing your APIs
- **Google Cloud Console:** for logging, monitoring and sharing

## Request Routing in API Gateway:
When a request is recieved:

1. API Gateway creates a trace token for Cloud Trace.
2. API Gateway matches the path of the incoming requests with the target API. After finding a matching route, API Gateway performs any authentication steps for the specified API.
3. If JWT validation is necessary, API Gateway validates the authentication using the appropriate public key for the signer, and validates the audience field in the JWT. If an API key is required, API Gateway calls the Service Control API to validate the key.
4. Service Control looks up the key to vaildate it, and ensures that the project associated with the key has enabled the API. If the key isn't valid or the project hasn't enabled the API, the call is rejected and it is logged via the Service Control API.
5. If Service Control successfully vaildates the key, the request along with all original headers, plus a JWT validation header, if appropriate, is forwarded to the backend.
6. When a response is received from the backend, API Gateway returns the response to the caller and sends the final timing information to Trace.
The call points are logged by the Service COntrol API, which then writes metrics and logs to their appropriate destinations.

## API Gateway Deployment Model
### API components:
Two components
1. API Config
2. Gateway:

### API Config:
The API configuration created when you upload an API definition. 

You create the API definition as on OpenAPI spec.

IF your API manages gRPC services on CLoud Run, you can define your API with a gRPC service definition and configuration.

Each time you upload an API definition, API Gateway creates a new API config.

That is, you can create an API config but you cannot later modify it.

You always create a new config.

### Gateway:
An Envoy based, high-performance, scalable proxy that hosts the deployed API config. Deploying an API config to a gateway creates the external facing URL that your API clients use to access the API.

Gateway is a region resource.

We cna not create an empty gateway, meaning one without an API config.

We cannot deploy multiple API configs to the same gateway

But we can have multiple gateways in API Gateway.

For each Gateway we can:
- Start/Stop/Delete the gateway
- View logs and metrics
- View trace information

## Defining the endpoint of the deployed API config:
When we deploy an API config to a gateway, API Gateway creates a unique URL for the Gateway in the gateway.dev domain (default internal domain). Your API clients then use a URL to access the deployed API Config.
```
https://GATEWAY_ID-HASH.REGION_CODE.gateway.dev

GATEWAY_ID: is the name of the gateway
HASH: si the unique hash code generated when we deployed the API
REGION_CODE: is the code for the GCP region where we deployed the gateway.
```
## About scale to zero
there is no traffic, all gateway instance are deleted, as the traffic increases gateway instances are created.

Scale to zero is controlled automatically by GCP.

## Using a load balancer:
Each gateway has its own load balancer (as it is deployed in region), So if we have deployed the same gateway in two region then we need to configure the Load Balancer to redirect the traffic.


## Configuring SSL access to an API
Google creates and manages the SSL cert on the load balancer integrated with the gateway. You do not have to create or upload your own cert.

## Configuring a DOmain Name server:
TO customize the domain name, create a load balancer to use your custom domain name and then direct requests to the gateway.dev domain of your deployed API.

## Deploying multiple API config in the same API

We can only deploy one API config to a gateway.

But can deploy multiple gateways under a single API.

Use case is :
- Production environment
- Staging enviroment
- Dev Env

## Deploying an API config to multiple regions:
We cna deploy API to multiple GCP regions.

***Note: Before you can deploy an API to a region, you must first deploy the backend service to that region. Because an API in one region can not make call to another region backend service.
## Updating an API
API Gateway supports a zero-downtime update model, which means your API continues to handle requests during the deployment of the updated API config.


# Refence 
[API Gateway Documentaiton](https://cloud.google.com/api-gateway/docs/concepts)
