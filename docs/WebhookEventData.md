

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
|**receiptPdf** | **URI** | Ссылка на скачивание PDF фискального чека (54-ФЗ) через наш API. Колбэк &#x60;recipient.sent&#x60; уходит ПОСЛЕ готовности чека, поэтому поле в нём присутствует (вместе с &#x60;receipt_url&#x60;). |  [optional] |
|**receiptUrl** | **URI** | Ссылка на фискальный чек на сайте ОФД (1-ОФД). Может присутствовать и без &#x60;receipt_pdf&#x60; (link_only — наш PDF недоступен). |  [optional] |
|**inventoryPdf** | **URI** | Ссылка на скачивание PDF описи вложения (форма 107, версия отправителя) через наш API. Присутствует в &#x60;recipient.sent&#x60; и &#x60;recipient.delivered&#x60;, когда опись сформирована. |  [optional] |



