# DefaultApi

All URIs are relative to *https://integration.doslano.ru*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**onLetterStatusChanged**](DefaultApi.md#onLetterStatusChanged) | **POST** /letterStatusChanged | Колбек на финальный статус |


<a id="onLetterStatusChanged"></a>
# **onLetterStatusChanged**
> onLetterStatusChanged(webhookEvent)

Колбек на финальный статус

Если при отправке письма указан &#x60;callback_url&#x60;, мы шлём на него POST при достижении финального статуса — по каждому получателю (&#x60;recipient.sent&#x60; / &#x60;recipient.failed&#x60;) и агрегатно по письму (&#x60;letter.sent&#x60; / &#x60;letter.partial_failure&#x60; / &#x60;letter.failed&#x60; / &#x60;letter.cancelled&#x60;).  Отдельный случай &#x60;letter.cancelled&#x60; — когда адрес/ФИО не прошли проверку Почты России **уже после** ответа &#x60;201&#x60; (поздний preflight: проверка не успела завершиться в окне синхронного ответа). Письмо отменяется автоматически, в &#x60;data.error&#x60; — перечень полей с ошибками; исправьте данные и создайте письмо заново. Если же ошибка адреса выявлена **сразу** при создании — вы получаете её синхронно (HTTP 422 &#x60;address_validation_failed&#x60;), и колбек по такому письму НЕ шлётся. То есть на одно письмо приходит ровно один сигнал об адресной ошибке: либо синхронный 422, либо асинхронный &#x60;letter.cancelled&#x60;.  **Подпись.** Заголовок &#x60;X-Doslano-Signature: t&#x3D;&lt;unix&gt;,v1&#x3D;&lt;hex&gt;&#x60; — где &#x60;v1 &#x3D; HMAC_SHA256(secret, \&quot;&lt;t&gt;.\&quot; + raw_body)&#x60;, &#x60;secret&#x60; — секрет аккаунта из ЛК (раздел «API»). Проверьте подпись и свежесть &#x60;t&#x60; (±5 мин).  **Доставка.** At-least-once: ждём ответ &#x60;2xx&#x60;; иначе ретраим по нарастающему графику (несколько попыток в течение ~24 ч), затем помечаем как недоставленный (видно в ЛК, можно переотправить). Дедуп — по &#x60;id&#x60; события. Порядок не гарантируется — сверяйтесь со &#x60;status&#x60; в теле. 

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.DefaultApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");

    DefaultApi apiInstance = new DefaultApi(defaultClient);
    WebhookEvent webhookEvent = new WebhookEvent(); // WebhookEvent | 
    try {
      apiInstance.onLetterStatusChanged(webhookEvent);
    } catch (ApiException e) {
      System.err.println("Exception when calling DefaultApi#onLetterStatusChanged");
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
| **webhookEvent** | [**WebhookEvent**](WebhookEvent.md)|  | |

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Принято (любой 2xx останавливает ретраи). |  -  |

