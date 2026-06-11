

# DryRunResult

Результат пробного прогона (`dry_run: true`): запрос полностью валиден. Письмо НЕ создано, средства НЕ списаны. 

## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**dryRun** | **Boolean** | Всегда &#x60;true&#x60; (маркер ответа пробного прогона). |  |
|**valid** | **Boolean** | Всегда &#x60;true&#x60; — невалидные запросы получают 400/422. |  |
|**recipientsCount** | **Integer** | Количество получателей (&#x3D; отправлений) в запросе. |  |
|**pricing** | [**DryRunResultPricing**](DryRunResultPricing.md) |  |  |



