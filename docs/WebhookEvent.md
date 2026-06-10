

# WebhookEvent


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** | Уникальный идентификатор события (для дедупа). |  |
|**type** | [**TypeEnum**](#TypeEnum) |  |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**data** | [**WebhookEventData**](WebhookEventData.md) |  |  |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| LETTER_SENT | &quot;letter.sent&quot; |
| LETTER_PARTIAL_FAILURE | &quot;letter.partial_failure&quot; |
| LETTER_FAILED | &quot;letter.failed&quot; |
| LETTER_CANCELLED | &quot;letter.cancelled&quot; |
| RECIPIENT_SENT | &quot;recipient.sent&quot; |
| RECIPIENT_FAILED | &quot;recipient.failed&quot; |
| RECIPIENT_DELIVERED | &quot;recipient.delivered&quot; |



