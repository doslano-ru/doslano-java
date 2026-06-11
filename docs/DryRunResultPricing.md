

# DryRunResultPricing

Расчёт к списанию при реальной отправке этого запроса.

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**subtotalMinor** | **Long** | Цена без скидки, в копейках. |  |
|**totalMinor** | **Long** | Итог к списанию (после промокода), в копейках. Non-binding — фиксируется при реальной оплате. |  |
|**currency** | [**CurrencyEnum**](#CurrencyEnum) |  |  |
|**promo** | [**PromoResult**](PromoResult.md) |  |  [optional] |



## Enum: CurrencyEnum

| Name | Value |
|---- | -----|
| RUB | &quot;RUB&quot; |



