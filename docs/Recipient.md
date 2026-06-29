

# Recipient


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**name** | **String** |  |  |
|**address** | **String** |  |  [optional] |
|**status** | **RecipientStatus** |  |  |
|**shipmentNumber** | **String** | Наш трек-номер (РПО), присваивается сразу при создании. |  [optional] |
|**trackingNumber** | **String** | Трек-номер Почты России (ШПИ). Появляется после регистрации отправления. |  [optional] |
|**priceMinor** | **Long** | Стоимость отправления этому получателю, в копейках. |  [optional] |
|**error** | **String** | Причина ошибки (для &#x60;failed&#x60;). |  [optional] |
|**receiptPdf** | **URI** | Ссылка на скачивание PDF фискального чека (54-ФЗ) этому получателю через наш API (см. &#x60;GET /v1/letters/{id}/recipients/{recipient_id}/receipt.pdf&#x60;). Присутствует, только когда чек пробит и его PDF сохранён у нас (получатель в статусе &#x60;sent&#x60;/&#x60;delivered&#x60;). |  [optional] |
|**receiptUrl** | **URI** | Ссылка на фискальный чек на сайте ОФД (1-ОФД). Присутствует, когда чек пробит (получатель &#x60;sent&#x60;/&#x60;delivered&#x60;). Может присутствовать и без &#x60;receipt_pdf&#x60; — когда наш PDF недоступен (link_only). |  [optional] |
|**inventoryPdf** | **URI** | Ссылка на скачивание PDF описи вложения (форма 107, версия отправителя) через наш API (см. &#x60;GET /v1/letters/{id}/recipients/{recipient_id}/inventory.pdf&#x60;). Присутствует, когда опись сформирована и отправление передано в Почту (получатель в статусе &#x60;sent&#x60;/&#x60;delivered&#x60;). |  [optional] |



