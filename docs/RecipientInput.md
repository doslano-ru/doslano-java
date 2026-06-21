

# RecipientInput


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**name** | **String** | ФИО или название получателя. При resolve_address_by_inn&#x3D;true ПЕРЕЗАПИСЫВАЕТСЯ наименованием из ЕГРЮЛ. |  |
|**address** | **String** | Адрес получателя (строкой; нормализуется на нашей стороне). Можно опустить при resolve_address_by_inn&#x3D;true. |  [optional] |
|**partyType** | **PartyType** |  |  [optional] |
|**inn** | **String** | ИНН (10 цифр). |  [optional] |
|**email** | **String** | Email получателя для уведомления-копии (опционально). После отправки письма получателю на этот адрес приходит письмо со ссылкой на электронную версию (страница /receive). Пустой/опущен — уведомление не шлётся; адрес указывает отправитель и отвечает за корректность. |  [optional] |
|**resolveAddressByInn** | **Boolean** | Авто-резолв адреса по ИНН из ЕГРЮЛ. Работает только для party_type&#x3D;organization с заданным inn: адрес и наименование берутся из реестра (DaData findById/party, головная организация), address можно не передавать. Если резолв не удался и address не передан — 422 recipient_address_unresolved; флаг без inn или не для organization — 422 recipient_resolve_requires_inn. Если передан и address — он fallback при неудаче резолва. |  [optional] |



