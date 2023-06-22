# About

Dev container for Python azure functions 

## Get started
Run `func init  --source-control  --worker-runtime python --docker --model V2` to initiate the project, and then `func new` to add functions.

## Workshop 1
Send message to service bus queue.

1. Add `AzureWebJobsMyServiceBus` setting to `local.settings.json` with connection string to service bus.
2. Modify http trigger function by adding output binding decorator
```python
@app.service_bus_queue_output(arg_name="message",
                              connection="MyServiceBus",
                              queue_name="fun-demo-queue")
def HttpTrigger(req: func.HttpRequest, message: func.Out[str]) -> func.HttpResponse:
```
3. Set output message `message.set(f"Function called by {name}")`