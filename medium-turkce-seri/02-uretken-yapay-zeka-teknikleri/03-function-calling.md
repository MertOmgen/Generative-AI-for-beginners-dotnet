# Function Calling

Function calling, bu dersin en önemli kırılma noktalarından biridir. Çünkü burada model yalnızca metin üretmez; uygulamanın sunduğu araçları ne zaman kullanacağına da karar verir.

## Neden function calling?

Gerçek dünyada kullanıcı yalnızca “cevap” istemez. Hava durumu öğrenmek, veri çekmek, bir iş akışı başlatmak, fiyat hesaplamak ya da bir API çağırmak isteyebilir. Model bunları kendi başına yapamaz; ama sizin açtığınız fonksiyonları doğru anda çağırabilir.

## 1. Kısım: Mantık nasıl çalışır?

Akış kabaca şöyledir:
1. Geliştirici uygun tool/fonksiyonları tanımlar.
2. Bu fonksiyonlar modele açıklamalarıyla birlikte sunulur.
3. Model, isteğe göre hangi fonksiyonun çağrılması gerektiğine karar verir.
4. Uygulama fonksiyonu çalıştırır ve sonucu modele geri verir.
5. Model son kullanıcıya anlamlı bir cevap üretir.

Buradaki sihir, modelin “fonksiyon çağırma kararını” doğal dil üzerinden verebilmesidir.

## 2. Kısım: İlk fonksiyon çağrısı

```csharp
ChatOptions options = new ChatOptions
{
    Tools = [ AIFunctionFactory.Create(GetTheWeather) ]
};

IChatClient client = new AzureOpenAIClient(new Uri(endpoint), new AzureCliCredential())
    .GetChatClient(deploymentName)
    .AsIChatClient()
    .AsBuilder()
    .UseFunctionInvocation()
    .Build();
```

Bu örnekte model, “Bugün şemsiye gerekli mi?” gibi bir soruda uygun gördüğünde `GetTheWeather` fonksiyonunu çağırır.

## 3. Kısım: Parametreli fonksiyonlar

Fonksiyonlar yalnızca sabit cevaplar vermek zorunda değildir. Şehir adı, tarih, ürün kodu gibi parametreler alabilir. Açıklamalar ne kadar net olursa model doğru fonksiyonu o kadar güvenilir kullanır.

## 4. Kısım: Birden fazla fonksiyon

Gerçek uygulamalarda birden fazla araç aynı anda sunulur. Örneğin:
- hava durumu
- kur çevirme
- toplantı planlama
- müşteri kaydı sorgulama

Burada önemli olan, her tool'un tek bir sorumluluğa sahip olmasıdır.

## 5. Kısım: Sohbet içinde function calling

Function calling tek atımlık çağrılarla sınırlı değildir. Konuşma geçmişi olan bir chat uygulamasında da araçlar devreye girer. Böylece kullanıcı doğal dilde ilerlerken uygulama arka planda birden fazla operasyon yapabilir.

## 6. Kısım: Async fonksiyonlar ve streaming

Dış API çağrıları veya I/O işlemleri asenkron olduğunda fonksiyonların async tasarlanması gerekir. Bu da özellikle ajanlar ve daha uzun iş akışları için önemlidir.

Streaming ile birlikte kullanıldığında kullanıcı, araç kullanan bir modelin cevabını daha akıcı şekilde takip edebilir.

## En iyi pratikler

- Tool açıklamalarını açık yazın
- Parametre adlarını anlaşılır seçin
- Hata durumlarını zarif yönetin
- Büyük, her şeyi yapan fonksiyonlardan kaçının
- Tool'ları işlevsel olarak dar tutun

## Sonuç

Function calling, AI uygulamasını pasif cevap üreten bir sistemden aktif iş yapan bir sisteme taşır. Bu yüzden agent mimarilerinin de temel taşlarından biridir.

## İlgili örnekler

- `samples/CoreSamples/MEAIFunctions/`
- `samples/CoreSamples/MEAIFunctionsAzureOpenAI/`
- `samples/CoreSamples/MEAIFunctionsOllama/`
