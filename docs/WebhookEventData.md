

# WebhookEventData


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**letterId** | **String** |  |  |
|**recipientId** | **String** |  |  [optional] |
|**status** | **String** |  |  |
|**shipmentNumber** | **String** |  |  [optional] |
|**trackingNumber** | **String** |  |  [optional] |
|**error** | **String** |  |  [optional] |
|**amountMinor** | **Integer** | Фактически списанная стоимость отправления ЭТОМУ получателю, в копейках (доля дисконтированного тотала письма с учётом промокода). Присутствует только в &#x60;recipient.sent&#x60; — отправление реально ушло и оплачено. В &#x60;recipient.failed&#x60; отсутствует: при провале сумма возвращается на баланс. |  [optional] |



