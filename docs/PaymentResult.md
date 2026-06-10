

# PaymentResult


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**charged** | **Boolean** | Списаны ли средства с баланса. |  |
|**status** | [**StatusEnum**](#StatusEnum) | &#x60;awaiting_payment&#x60; — при &#x60;on_insufficient_funds&#x3D;hold&#x60; до пополнения. |  [optional] |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| PAID | &quot;paid&quot; |
| AWAITING_PAYMENT | &quot;awaiting_payment&quot; |



