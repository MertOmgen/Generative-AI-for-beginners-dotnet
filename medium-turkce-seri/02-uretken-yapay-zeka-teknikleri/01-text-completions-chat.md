# Text Completions ve Chat Konuşmaları

Bu bölümün amacı, en temel AI etkileşiminden tam sohbet deneyimine kadar ilerleyen yolu göstermektir. Medium okuyucusu için ana fikir şudur: üretken yapay zekâ çoğu zaman tek satırlık bir prompt ile başlar, ama gerçek uygulamalar konuşma bağlamını yönetmeyi gerektirir.

## "Hello World"dan gerçek sohbete

Tek atımlık bir AI çağrısı şu kadar basit olabilir:

```csharp
var response = await client.GetResponseAsync(
    "Bulut bilişimin avantajlarını tek cümlede özetle.");
Console.WriteLine(response.Text);
```

Bu yapı, özetleme, sınıflandırma, duygu analizi ve tek seferlik dönüşüm senaryoları için yeterlidir.

## 1. Kısım: Text completion nedir?

Text completion, tek prompt → tek cevap ilişkisidir. Model sizinle geçmiş bir konuşma taşımaz. Bu nedenle:
- kısa görevlerde hızlıdır
- anlaşılması kolaydır
- ancak bağlam gerektiren uygulamalarda sınırlıdır

Örneğin müşteri yorumlarının duygu analizini yapmak için uzun kurallar yazmak yerine doğrudan modeli yönlendirebilirsiniz.

## 2. Kısım: Completion'dan conversation'a geçiş

Modelin doğal bir hafızası yoktur. İkinci soruda ilk soruyu hatırlaması için konuşma geçmişini sizin taşımanız gerekir.

```csharp
List<ChatMessage> conversation = new();
conversation.Add(new ChatMessage(ChatRole.User, "Benim adım Bruno."));

var response1 = await client.GetResponseAsync(conversation);
conversation.Add(new ChatMessage(ChatRole.Assistant, response1.Text));
conversation.Add(new ChatMessage(ChatRole.User, "Adım neydi?"));
```

Buradaki kırılma noktası şudur: hafıza modelde değil, uygulamanın yönettiği mesaj listesinde yaşar.

## 3. Kısım: Üç chat rolü

Etkili sohbet uygulamalarında üç rol vardır:

- **System**: geliştiricinin koyduğu çerçeve
- **User**: son kullanıcının isteği
- **Assistant**: modelin verdiği yanıt

Özellikle system mesajı çok değerlidir. Çünkü modelin uzmanlığını, tonunu, sınırlarını ve görevini burada belirlersiniz.

Örnek bir system mesajı:

```csharp
new ChatMessage(ChatRole.System,
    "Sen kıdemli bir .NET geliştiricisisin. C# ve .NET sorularına kısa ve net cevap ver.")
```

Bu sayede model yalnızca cevap veren bir motor değil, belli bir rol içinde davranan bir yardımcı haline gelir.

## 4. Kısım: Tam bir chat uygulaması

Pratikte chat uygulaması kurarken tipik akış şöyledir:
1. System mesajını ekle
2. Kullanıcı mesajını geçmişe yaz
3. `GetResponseAsync` ile cevap al
4. Model yanıtını tekrar geçmişe ekle
5. Döngüyü sürdür

Bu desen, konsol uygulamasından web tabanlı chat arayüzüne kadar hemen her yerde kullanılabilir.

## Sağlayıcı değiştirmek neden kolay?

Bu dersin önemli avantajlarından biri, `IChatClient` sayesinde sağlayıcı değişiminin uygulama mantığını bozmamasıdır. Azure OpenAI kullanırken kurduğunuz sohbet akışı, Ollama ile de büyük ölçüde aynı kalır.

## Kısa özet

Bu bölümün sonunda okuyucu şunu anlamalı:
- text completion hızlı başlangıçtır
- gerçek chat uygulamaları mesaj geçmişi ister
- system/user/assistant rolleri iyi tasarlanmalıdır
- .NET tarafında bu mimari şaşırtıcı derecede yalındır

## İlgili örnekler

- `samples/CoreSamples/BasicChat-01MEAI/`
- `samples/CoreSamples/BasicChat-10ConversationHistory/`
- `samples/CoreSamples/BasicChat-03Ollama/`
