# LettersApi

All URIs are relative to *https://integration.doslano.ru*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createLetter**](LettersApi.md#createLetter) | **POST** /v1/letters | Отправить письмо |
| [**getLetter**](LettersApi.md#getLetter) | **GET** /v1/letters/{id} | Статус письма |
| [**getRecipientTracking**](LettersApi.md#getRecipientTracking) | **GET** /v1/letters/{id}/recipients/{recipient_id}/tracking | Трек-события получателя |
| [**listLetters**](LettersApi.md#listLetters) | **GET** /v1/letters | Список писем |


<a id="createLetter"></a>
# **createLetter**
> DryRunResult createLetter(createLetterRequest, idempotencyKey)

Отправить письмо

Создаёт и (по умолчанию) сразу оплачивает с баланса одно заказное письмо одним запросом. Опись формируется автоматически на нашей стороне.  Требуется scope &#x60;letters:write&#x60;. 

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.auth.*;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.LettersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");
    
    // Configure HTTP bearer authorization: apiKey
    HttpBearerAuth apiKey = (HttpBearerAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setBearerToken("BEARER TOKEN");

    LettersApi apiInstance = new LettersApi(defaultClient);
    CreateLetterRequest createLetterRequest = new CreateLetterRequest(); // CreateLetterRequest | 
    String idempotencyKey = "idempotencyKey_example"; // String | Ключ идемпотентности. Повтор с тем же ключом в течение TTL вернёт исходный результат, не создавая письмо повторно.
    try {
      DryRunResult result = apiInstance.createLetter(createLetterRequest, idempotencyKey);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LettersApi#createLetter");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **createLetterRequest** | [**CreateLetterRequest**](CreateLetterRequest.md)|  | |
| **idempotencyKey** | **String**| Ключ идемпотентности. Повтор с тем же ключом в течение TTL вернёт исходный результат, не создавая письмо повторно. | [optional] |

### Return type

[**DryRunResult**](DryRunResult.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Письмо принято. Тело — состояние письма (включая цену и результат промокода). |  -  |
| **200** | Пробный прогон (&#x60;dry_run: true&#x60;) успешен: запрос валиден, показан расчёт. Письмо не создано, средства не списаны. |  -  |
| **400** | Некорректный запрос. |  -  |
| **401** | Нет/неверный API-ключ, либо IP не в allowlist ключа. |  -  |
| **403** | У ключа нет нужного scope. |  -  |
| **402** | Недостаточно средств на балансе (при &#x60;on_insufficient_funds&#x3D;reject&#x60;). |  -  |
| **422** | Ошибка валидации данных письма (адрес, файл, получатели и т.п.). В частности &#x60;code: address_validation_failed&#x60; — адрес/ФИО не прошли preflight-проверку Почты России: письмо отменено, в &#x60;detail&#x60; перечислены стороны и поля; исправьте данные и создайте письмо заново. Коды &#x60;recipient_address_unresolved&#x60; и &#x60;recipient_resolve_requires_inn&#x60; относятся к опции &#x60;resolve_address_by_inn&#x60; (см. RecipientInput). |  -  |

<a id="getLetter"></a>
# **getLetter**
> Letter getLetter(id)

Статус письма

Полное состояние письма с разбивкой по получателям и трек-номерами. Требуется scope &#x60;letters:read&#x60;.

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.auth.*;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.LettersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");
    
    // Configure HTTP bearer authorization: apiKey
    HttpBearerAuth apiKey = (HttpBearerAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setBearerToken("BEARER TOKEN");

    LettersApi apiInstance = new LettersApi(defaultClient);
    String id = "id_example"; // String | Идентификатор письма.
    try {
      Letter result = apiInstance.getLetter(id);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LettersApi#getLetter");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | **String**| Идентификатор письма. | |

### Return type

[**Letter**](Letter.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Состояние письма. |  -  |
| **401** | Нет/неверный API-ключ, либо IP не в allowlist ключа. |  -  |
| **403** | У ключа нет нужного scope. |  -  |
| **404** | Ресурс не найден (или не принадлежит аккаунту). |  -  |

<a id="getRecipientTracking"></a>
# **getRecipientTracking**
> TrackingInfo getRecipientTracking(id, recipientId)

Трек-события получателя

События трекинга Почты России по конкретному получателю (если трек-номер присвоен). Требуется scope &#x60;letters:read&#x60;.

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.auth.*;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.LettersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");
    
    // Configure HTTP bearer authorization: apiKey
    HttpBearerAuth apiKey = (HttpBearerAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setBearerToken("BEARER TOKEN");

    LettersApi apiInstance = new LettersApi(defaultClient);
    String id = "id_example"; // String | Идентификатор письма.
    String recipientId = "recipientId_example"; // String | 
    try {
      TrackingInfo result = apiInstance.getRecipientTracking(id, recipientId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LettersApi#getRecipientTracking");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **id** | **String**| Идентификатор письма. | |
| **recipientId** | **String**|  | |

### Return type

[**TrackingInfo**](TrackingInfo.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | События трекинга. |  -  |
| **401** | Нет/неверный API-ключ, либо IP не в allowlist ключа. |  -  |
| **403** | У ключа нет нужного scope. |  -  |
| **404** | Ресурс не найден (или не принадлежит аккаунту). |  -  |

<a id="listLetters"></a>
# **listLetters**
> ListLetters200Response listLetters(limit, offset, status, createdFrom, createdTo)

Список писем

Письма аккаунта (все каналы — и API, и личный кабинет; канал указан в поле &#x60;channel&#x60;). Требуется scope &#x60;letters:read&#x60;.

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.auth.*;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.LettersApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");
    
    // Configure HTTP bearer authorization: apiKey
    HttpBearerAuth apiKey = (HttpBearerAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setBearerToken("BEARER TOKEN");

    LettersApi apiInstance = new LettersApi(defaultClient);
    Integer limit = 20; // Integer | 
    Integer offset = 0; // Integer | 
    LetterStatus status = LetterStatus.fromValue("forming"); // LetterStatus | 
    OffsetDateTime createdFrom = OffsetDateTime.now(); // OffsetDateTime | 
    OffsetDateTime createdTo = OffsetDateTime.now(); // OffsetDateTime | 
    try {
      ListLetters200Response result = apiInstance.listLetters(limit, offset, status, createdFrom, createdTo);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling LettersApi#listLetters");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **limit** | **Integer**|  | [optional] [default to 20] |
| **offset** | **Integer**|  | [optional] [default to 0] |
| **status** | [**LetterStatus**](.md)|  | [optional] [enum: forming, awaiting_payment, paid, sending, sent, partial_failure, error, cancelled] |
| **createdFrom** | **OffsetDateTime**|  | [optional] |
| **createdTo** | **OffsetDateTime**|  | [optional] |

### Return type

[**ListLetters200Response**](ListLetters200Response.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Страница писем. |  -  |
| **401** | Нет/неверный API-ключ, либо IP не в allowlist ключа. |  -  |
| **403** | У ключа нет нужного scope. |  -  |

