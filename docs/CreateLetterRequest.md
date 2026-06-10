

# CreateLetterRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**sender** | [**SenderInput**](SenderInput.md) | Отправитель. Если не указан — берётся отправитель по умолчанию из профиля аккаунта. |  [optional] |
|**recipients** | [**List&lt;RecipientInput&gt;**](RecipientInput.md) |  |  |
|**content** | [**LetterContent**](LetterContent.md) |  |  |
|**letterClass** | **LetterClass** |  |  [optional] |
|**promoCode** | **String** | Промокод (опционально). |  [optional] |
|**onPromoInvalid** | [**OnPromoInvalidEnum**](#OnPromoInvalidEnum) | Что делать, если промокод не применился: &#x60;ignore&#x60; — отправить без скидки и вернуть пометку в &#x60;pricing.promo&#x60;; &#x60;reject&#x60; — отклонить (422).  |  [optional] |
|**onInsufficientFunds** | [**OnInsufficientFundsEnum**](#OnInsufficientFundsEnum) | Что делать при нехватке средств: &#x60;reject&#x60; — отклонить (402), письмо не создаётся; &#x60;hold&#x60; — создать письмо в статусе &#x60;awaiting_payment&#x60;, оно оплатится автоматически при пополнении баланса.  |  [optional] |
|**callbackUrl** | **URI** | HTTPS-URL для колбеков по этому письму. Если не указан — используйте поллинг. |  [optional] |



## Enum: OnPromoInvalidEnum

| Name | Value |
|---- | -----|
| IGNORE | &quot;ignore&quot; |
| REJECT | &quot;reject&quot; |



## Enum: OnInsufficientFundsEnum

| Name | Value |
|---- | -----|
| REJECT | &quot;reject&quot; |
| HOLD | &quot;hold&quot; |



