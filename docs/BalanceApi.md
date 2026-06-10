# BalanceApi

All URIs are relative to *https://integration.doslano.ru*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getBalance**](BalanceApi.md#getBalance) | **GET** /v1/balance | Баланс аккаунта |


<a id="getBalance"></a>
# **getBalance**
> Balance getBalance()

Баланс аккаунта

Текущий баланс в копейках. Требуется scope &#x60;balance:read&#x60;.

### Example
```java
// Import classes:
import ru.doslano.sdk.ApiClient;
import ru.doslano.sdk.ApiException;
import ru.doslano.sdk.Configuration;
import ru.doslano.sdk.auth.*;
import ru.doslano.sdk.models.*;
import org.openapitools.client.api.BalanceApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://integration.doslano.ru");
    
    // Configure HTTP bearer authorization: apiKey
    HttpBearerAuth apiKey = (HttpBearerAuth) defaultClient.getAuthentication("apiKey");
    apiKey.setBearerToken("BEARER TOKEN");

    BalanceApi apiInstance = new BalanceApi(defaultClient);
    try {
      Balance result = apiInstance.getBalance();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BalanceApi#getBalance");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**Balance**](Balance.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Баланс. |  -  |
| **401** | Нет/неверный API-ключ, либо IP не в allowlist ключа. |  -  |
| **403** | У ключа нет нужного scope. |  -  |

