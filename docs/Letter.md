

# Letter


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**id** | **String** |  |  |
|**channel** | [**ChannelEnum**](#ChannelEnum) | Канал создания письма — &#x60;api&#x60; (этот API) или &#x60;web&#x60; (личный кабинет). |  |
|**status** | **LetterStatus** |  |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**sender** | [**Party**](Party.md) |  |  [optional] |
|**recipients** | [**List&lt;Recipient&gt;**](Recipient.md) |  |  |
|**pricing** | [**Pricing**](Pricing.md) |  |  |
|**payment** | [**PaymentResult**](PaymentResult.md) |  |  [optional] |
|**callbackUrl** | **URI** |  |  [optional] |



## Enum: ChannelEnum

| Name | Value |
|---- | -----|
| WEB | &quot;web&quot; |
| API | &quot;api&quot; |



