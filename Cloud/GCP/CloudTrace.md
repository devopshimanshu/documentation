# Cloud Trace
Cloud Trace is a distributed tracing system for Google Cloud.

It helps you understand how long it takes your application to handle incoming requests from users or other applications, and how long it takes to complete operations like RPC calls performed when handling the requests.

Cloud Trace collects latency data from :
App Engine
HTTP(S) load Balancers
Application instrumented with the CLoud Trace API.

It helps in answering the following questions:
- How long does it take my application to handle a given request?
- Why is it taking my application so long to handle a request?
- Why do some of my requests take longer than others?
- What is the overall latency of requests to my applications?
- Has latency for my application increased or decreased over time?
- What can I do to reduce application latency?
- What are my application's dependencies?

## Environment Support: 
Cloud Tarce e=runs on Linux in the following environments:
- Compute Engine
- Google Kubernetes Engine
- App Engine Flexible environment
- App Engine standard envioenment
- CLoud Run
- Non Google cloud Environments

Cloud Trace provides client libraries for instrumenting your applciation to capture trace infromantion. For per-language setup instructions.

## Components:
Cloud trace consist of a tracing client, which collects traces and sends them to your google cloud Project.

A trace describe the time it takes an application to complete a single operation.
Each trace consist of one or more ***spans*** 

A span describe how long it takes to perform a complete sub-operation.

## Tracing interface
After the agent or tracing client collect trace data, you can view and analyze that data in near real-time in the CLoud Trace Interface.

Interface consist of three pages:
- Overview:  Summary information about your application
    - Insights
    - Recent traces
    - Most frequent URIs
    - Most Frequent RPCs
    - Chargeable Trace Spans
    - Daily analysis reports
- Trace list: Lets you examine an individual traces in detail
- Analysis reports: Let you create custom reports

# Reference
[GCP Documentation for CLoud Trace](https://cloud.google.com/trace/docs/overview)
