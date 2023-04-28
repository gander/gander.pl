---
title: "IFTTT: Maker Webhooks"
tags: [IFTTT, Maker, Webhooks, JSON, payload, value1, value2, value3, JsonPayload]
---
# {{ $frontmatter.title }}

How to configure [IFTTT Maker Webhooks](https://ifttt.com/maker_webhooks) service?

## Working configuration:

::: warning Attention
Note the **`/json/`** part in the webhook address.<br/>
This specifies whether the request contains arbitrary JSON or with required keys.
:::

### Ingredients

+ Send: "Event with 3 JSON values" (JSON payload containing value1, value2, value3)
+ Trigger: "Receive a web request" (Value1, Value2, Value3 ingredients)

```http
POST /trigger/web_request/with/key/MyUniqApiKey HTTP/2
Host: maker.ifttt.com
content-type: application/json
content-length: 68
```
```json
{
	"example": ["lorem","ipsum"],
	"value1":"foo",
	"value2":"bar"
}
```

Ingredients:
```text
Value1: foo
Value2: bar
Value3: none
```

### JSON Payload

+ Send: "Event with an arbitrary JSON payload" (arbitrary JSON payload)
+ Trigger: "Receive a web request with a JSON payload" (JsonPayload ingredient)

```http
POST /trigger/web_request_json/json/with/key/MyUniqApiKey HTTP/2
Host: maker.ifttt.com
content-type: application/json
content-length: 68
```
```json
{
	"example": ["lorem","ipsum"],
	"value1":"foo",
	"value2":"bar"
}
```

Ingredients:
```text
JsonPayload: {"example": ["lorem","ipsum"], "value1": "foo", "value2": "bar"}
```

## Not working configurations:

### JSON Payload &rarr; Ingredients

+ Send: "Event with an arbitrary JSON payload" (arbitrary JSON payload)
+ Trigger: "Receive a web request" (Value1, Value2, Value3 ingredients)

```http
POST /trigger/web_request/json/with/key/MyUniqApiKey HTTP/2
Host: maker.ifttt.com
content-type: application/json
content-length: 68
```
```json
{
	"example": ["lorem","ipsum"],
	"value1":"foo",
	"value2":"bar"
}
```

Ingredients:
```text
Value1: none
Value2: none
Value3: none
```

### Ingredients &rarr; JSON Payload

+ Send: "Event with 3 JSON values" (JSON payload containing value1, value2, value3)
+ Trigger: "Receive a web request with a JSON payload" (JsonPayload ingredient)

```http
POST /trigger/web_request_json/with/key/MyUniqApiKey HTTP/2
Host: maker.ifttt.com
content-type: application/json
content-length: 68
```
```json
{
	"example": ["lorem","ipsum"],
	"value1":"foo",
	"value2":"bar"
}
```

Ingredients:
```text
JsonPayload: none
```

-----