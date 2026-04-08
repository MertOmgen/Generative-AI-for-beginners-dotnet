# 1. Ders — .NET Geliştiricileri İçin Üretken Yapay Zekâya Giriş

## Giriş

Üretken yapay zekâ, çoğu .NET geliştiricisinin düşündüğünden daha yakında duruyor. Aslında bir REST API çağırmayı biliyorsanız, AI destekli uygulama geliştirmeye de çok uzakta değilsiniz. Bu dersin ana fikri tam olarak bu: Yeni bir dünya öğrenmek yerine, elinizdeki .NET reflekslerini yeni bir probleme uyguluyorsunuz.

## Neden önemli?

Klasik yazılım geliştirmede kuralları siz tanımlarsınız. Üretken yapay zekâ tarafında ise modele amacı tarif edersiniz. Kodun tamamı ortadan kalkmaz; sadece uygulamanın bir bölümünde deterministik kuralların yerini olasılıksal yanıtlar alır.

## Bu dersten çıkarılacak ana fikirler

- Üretken yapay zekâ yeni içerik üretir.
- LLM'ler girdiği “anlayarak” değil, örüntü tahmini yaparak çalışır.
- Token, context window ve temperature gibi kavramlar pratikte doğrudan sonucu etkiler.
- .NET geliştiricileri için en büyük avantaj, `IChatClient` gibi soyutlamalar sayesinde sağlayıcı bağımsız kalabilmektir.

## .NET tarafındaki kırılma noktası: `IChatClient`

Bu repodaki derslerin omurgası `Microsoft.Extensions.AI` yaklaşımıdır. Aynı uygulama kodu ile Azure OpenAI, OpenAI ya da Ollama arasında geçiş yapabilmek, öğrenme maliyetini ciddi biçimde düşürür.

### Öne çıkan örnek

Kaynak: `samples/CoreSamples/BasicChat-01MEAI/app.cs`

```csharp
IChatClient client = new AzureOpenAIClient(new Uri(endpoint), new AzureCliCredential())
        .GetChatClient(deploymentName)
        .AsIChatClient();

var response = await client.GetResponseAsync(prompt.ToString());
Console.WriteLine(response.Text);
```

Bu kısa örnek şunu gösteriyor: AI entegrasyonu, çoğu zaman yeni bir uygulama türü değil; var olan uygulamanın yeni bir servisle konuşmasıdır.

## Azure mı, Ollama mı?

Bu dersin güzel tarafı, tek bir sağlayıcıya kilitlenmiyor oluşu.

- **Azure OpenAI / Microsoft Foundry**: Kurumsal senaryolar ve bulut tabanlı kullanım için güçlü.
- **Ollama**: Lokal çalışma, düşük maliyet ve hızlı deney yapmak için ideal.

Makale serisinde bunu özellikle vurgulamak önemli; çünkü okuyucuya yalnızca kavramı değil, giriş bariyeri düşük bir başlangıç yolu da sunmuş olursunuz.

## Medium okuyucusu için mesaj

Bu ders Medium formatında şu iddiayla yayınlanabilir: “AI geliştirme, .NET geliştiricileri için sıfırdan başlanan bir alan değil.” Bu açı, teoriyi sadeleştirir ve okuyucuyu ikinci makaleye taşır.

## Sonuç

İlk dersin sonunda okuyucunun şunu net biçimde anlaması gerekir: Üretken yapay zekâ, .NET geliştiricisinin teknik kimliğini değiştirmez; sadece ona yeni bir çözüm alanı açar. Sonraki makalede artık sohbet, streaming, structured output ve function calling gibi daha somut tekniklere geçebiliriz.
