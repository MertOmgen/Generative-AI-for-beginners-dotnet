# Streaming ve Structured Output

Bu bölümde iki kritik üretim tekniği bir araya geliyor: kullanıcıya yanıtı parça parça göstermek ve model çıktısını doğrudan kullanılabilir veri yapıları halinde almak.

## Neden streaming önemli?

Uzun bir AI yanıtında kullanıcı birkaç saniye boş ekran görmek istemez. Streaming ile token'lar geldikçe çıktı ekrana yansır. Böylece deneyim daha canlı ve daha profesyonel görünür.

```csharp
await foreach (var update in client.GetStreamingResponseAsync(
    "Kuantum bilgisayarı basitçe açıkla"))
{
    Console.Write(update.Text);
}
```

Bu yaklaşım özellikle chat arayüzlerinde, uzun özetlerde ve ajan tabanlı açıklamalarda güçlüdür.

## 1. Kısım: Streaming response akışı

`GetResponseAsync` tüm cevabı bir kerede döndürür.
`GetStreamingResponseAsync` ise parçalar halinde bir `IAsyncEnumerable` verir.

Pratik sonuç:
- bekleme hissi azalır
- kullanıcı süreç içinde kalır
- aynı anda hem ekrana yazdırma hem geçmişe ekleme yapılabilir

Toplanan güncellemeler daha sonra tek bir tam cevaba dönüştürülebilir.

## 2. Kısım: Structured output nedir?

Metin esnektir ama her zaman ideal değildir. Bazen modelden doğrudan enum, record ya da liste dönmesini istersiniz.

Örnek:

```csharp
var response = await chatClient.GetResponseAsync<Sentiment>(
    $"Bu yorumun duygusu nedir? {review}");
```

Bu sayede yanıtı tekrar parse etmek zorunda kalmadan uygulama kodunuzda kullanabilirsiniz.

## Nerelerde işe yarar?

- duygu analizi
- bilgi çıkarımı
- JSON benzeri cevaplar
- toplantı notlarından aksiyon listesi çıkarma
- iletişim bilgisi yakalama

## Record ve koleksiyon desteği

Structured output yalnızca basit tiplerle sınırlı değildir. `record` yapıları, listeler ve daha zengin veri modelleri de doğrudan istenebilir. Bu da AI katmanını klasik backend işleme akışlarına bağlamayı kolaylaştırır.

## 3. Kısım: Streaming ile structured output birlikte

Bazı senaryolarda yanıtın gelirken görünmesini istersiniz ama işlem sonunda tek bir nesneye de ihtiyaç duyarsınız. İşte bu durumda önce streaming ile güncellemeleri toplar, sonra tekil yanıta dönüştürürsünüz.

Bu yaklaşım kullanıcı deneyimi ile makine tüketilebilir veri ihtiyacını aynı akışta buluşturur.

## ChatOptions ile ince ayar

Temperature, max tokens ya da ek istek ayarları `ChatOptions` üzerinden şekillendirilebilir. Özellikle structured output senaryolarında cevap formatını daha kontrollü tutmak için bu ayarlar değerlidir.

## Kısa özet

Bu bölümün ana kazanımları:
- streaming, kullanıcı deneyimini güçlendirir
- structured output, AI çıktısını uygulama verisine dönüştürür
- ikisinin birlikte kullanımı, prototipten ürüne geçişte önemli avantaj sağlar

## İlgili örnekler

- `samples/CoreSamples/BasicChat-01MEAI/`
- `samples/CoreSamples/BasicChat-10ConversationHistory/`
- yapılandırılmış çıktı kullanan MEAI örnekleri
