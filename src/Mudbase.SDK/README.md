# Created with Openapi Generator

<a id="cli"></a>
## Creating the library
Create a config.yaml file similar to what is below, then run the following powershell command to generate the library `java -jar "<path>/openapi-generator/modules/openapi-generator-cli/target/openapi-generator-cli.jar" generate -c config.yaml`

```yaml
generatorName: csharp
inputSpec: /home/runner/work/mudbase-docs/mudbase-docs/openapi/openapi.yaml
outputDir: out

# https://openapi-generator.tech/docs/generators/csharp
additionalProperties:
  packageGuid: '{BF5900F8-770E-440E-9D30-86A34E6D786C}'

# https://openapi-generator.tech/docs/integrations/#github-integration
# gitHost:
# gitUserId:
# gitRepoId:

# https://openapi-generator.tech/docs/globals
# globalProperties:

# https://openapi-generator.tech/docs/customization/#inline-schema-naming
# inlineSchemaOptions:

# https://openapi-generator.tech/docs/customization/#name-mapping
# modelNameMappings:
# nameMappings:

# https://openapi-generator.tech/docs/customization/#openapi-normalizer
# openapiNormalizer:

# templateDir: https://openapi-generator.tech/docs/templating/#modifying-templates

# releaseNote:
```

<a id="usage"></a>
## Using the library in your project

```cs
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;
using Org.OpenAPITools.Extensions;

namespace YourProject
{
    public class Program
    {
        public static async Task Main(string[] args)
        {
            var host = CreateHostBuilder(args).Build();
            var api = host.Services.GetRequiredService<IAPIKeysApi>();
            ICreateApiKeyApiResponse apiResponse = await api.CreateApiKeyAsync("todo");
            CreateApiKey201Response? model = apiResponse.Ok();
        }

        public static IHostBuilder CreateHostBuilder(string[] args) => Host.CreateDefaultBuilder(args)
          .ConfigureApi((context, services, options) =>
          {
              // The type of token here depends on the api security specifications
              // Available token types are ApiKeyToken, BasicToken, BearerToken, HttpSigningToken, and OAuthToken.
              BearerToken token = new("<your token>");
              options.AddTokens(token);

              // optionally choose the method the tokens will be provided with, default is RateLimitProvider
              options.UseProvider<RateLimitProvider<BearerToken>, BearerToken>();

              options.ConfigureJsonOptions((jsonOptions) =>
              {
                  // your custom converters if any
              });

              options.AddApiHttpClients(client =>
              {
                  // client configuration
              }, builder =>
              {
                  builder
                      .AddRetryPolicy(2)
                      .AddTimeoutPolicy(TimeSpan.FromSeconds(5))
                      .AddCircuitBreakerPolicy(10, TimeSpan.FromSeconds(30));
                      // add whatever middleware you prefer
                  }
              );
          });
    }
}
```
<a id="questions"></a>
## Questions

- What about HttpRequest failures and retries?
  Configure Polly in the IHttpClientBuilder
- How are tokens used?
  Tokens are provided by a TokenProvider class. The default is RateLimitProvider which will perform client side rate limiting.
  Other providers can be used with the UseProvider method.
- Does an HttpRequest throw an error when the server response is not Ok?
  It depends how you made the request. If the return type is ApiResponse<T> no error will be thrown, though the Content property will be null.
  StatusCode and ReasonPhrase will contain information about the error.
  If the return type is T, then it will throw. If the return type is TOrDefault, it will return null.
- How do I validate requests and process responses?
  Use the provided On and After partial methods in the api classes.

## Api Information
- appName: MUDBASESDK
- appVersion: 1.3.3
- appDescription: MUDBASE is a scalable, real-time, and secure Backend-as-a-Service (BaaS) platform  designed for modern applications. Built with custom logic, it offers fine-grained  control, extensibility, and enterprise-grade security.  ## Features - 🔐 Multi-provider authentication (30+ OAuth providers) - 📊 Real-time database with collections - 📁 File storage and management - 🔑 API key management with permissions - 🔗 Webhook system with retry logic - ⚡ Serverless functions - 💬 Multi-channel messaging (Push, Email, SMS) - 📈 Usage analytics and monitoring - 🌐 Real-time WebSocket events - 🔍 Full-text search capabilities - 💳 Billing: fiat only for project subscriptions and org BaaS checkout (platform fee split). On-chain billing is not exposed on these APIs (optional &#x60;crypto-payment-module/&#x60; in repo, not mounted by default). - 📡 Block-based multi-chain wallet monitoring (ETH/UTXO scanners, GetBlock, scanner metrics API) - 🏢 Enterprise / Phase 4: custom domains on Growth, Scale, and Enterprise (TXT DNS at &#x60;_mudbase-verify.&lt;hostname&gt;&#x60;); &#x60;settings.customDomainAddon&#x60; is optional (billing/legacy); dedicated DB migration script, periodic DNS recheck job, optional &#x60;infrastructureEnvironments[]&#x60; and edge/metering fields on &#x60;dedicated&#x60;. 

## Build
This C# SDK is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project.

- SDK version: 1.3.3
- Generator version: 7.20.0
- Build package: org.openapitools.codegen.languages.CSharpClientCodegen
