# 2. Ders — .NET ile Üretken Yapay Zekâ Teknikleri

## Giriş

İlk derste üretken yapay zekânın mantığını konuştuk. Bu derste ise işin günlük geliştirme tarafına iniyoruz: sohbet geçmişi nasıl tutulur, yanıtlar akış halinde nasıl alınır, modelden nasıl yapılandırılmış veri istenir ve kendi fonksiyonlarımız modele nasıl açılır?

## Bu dersin omurgası

Bu repo ikinci dersi dört başlıkta ele alıyor:

- text completions ve chat
- streaming ve structured output
- function calling
- middleware pipeline

Bu yapı Medium için de çok uygun; çünkü tek makale içinde ilerleyen ama bölümler halinde okunabilen bir anlatı kuruyor.

## Konuşma geçmişi neden önemli?

AI uygulamalarında “hafıza” çoğu zaman sihirli bir özellik gibi anlatılır. Oysa pratikte çoğu senaryoda yapılan şey, önceki mesajları modele yeniden vermektir.

Kaynak: `samples/CoreSamples/BasicChat-10ConversationHistory/app.cs`

```csharp
List<ChatMessage> conversation = new()
{
    new ChatMessage(ChatRole.System, "You are a good assistance with short and smart answers")
};

conversation.Add(new ChatMessage(ChatRole.User, question));
var response = await client.GetResponseAsync(conversation);
conversation.Add(new ChatMessage(ChatRole.Assistant, response.Text));
```

Bu örnek, chat uygulamalarının temelini çok net anlatır: geçmişi siz yönetirsiniz, model yalnızca kendisine verilen bağlam kadar “hatırlar”.

## Function calling neden kritik?

Gerçek ürünlerde modelin yalnızca metin üretmesi yetmez. Hava durumu sormak, veritabanından veri almak, bir API çağrısı yapmak gibi şeyler gerekir. İşte burada function calling devreye girer.

Kaynak: `samples/CoreSamples/MEAIFunctions/app.cs`

```csharp
ChatOptions options = new ChatOptions
{
    Tools = [
        AIFunctionFactory.Create(GetTheWeather)
    ]
};

IChatClient client = new AzureOpenAIClient(new Uri(endpoint), new AzureCliCredential())
    .GetChatClient(deploymentName)
    .AsIChatClient()
    .AsBuilder()
    .UseFunctionInvocation()
    .Build();
```

Buradaki önemli mesaj şu: Modelin yeteneği, uygulamanın sunduğu araçlarla genişler.

## Structured output ve middleware ne kazandırır?

Structured output, model cevabını doğrudan kullanılabilir veri haline getirir. Middleware ise loglama, telemetry, caching ve yeniden deneme gibi üretim senaryolarını temiz biçimde eklemenizi sağlar.

Bu noktada ikinci makalenin ana iddiası şu olabilir: “Prompt yazmak başlangıçtır; güvenilir AI uygulaması kurmak için teknik mimari gerekir.”

## Sonuç

Bu ders, okuyucuyu prototipten ürünleşmeye taşır. Bir sonraki aşamada artık tekniklerin tek başına yeterli olmadığını, problem çözmek için desenlere ihtiyaç duyduğumuzu göreceğiz.
