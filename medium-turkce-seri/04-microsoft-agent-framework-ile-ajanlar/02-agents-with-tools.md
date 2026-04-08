# Tool Kullanan Ajanlar

Ajanların gerçek değeri, yalnızca konuşmalarından değil; bir şey yapabilmelerinden gelir. Bu bölümde tool kullanan agent tasarımını ele alıyoruz.

## Neden tool'lar önemli?

Bir ajanın sadece metin üretmesi çoğu gerçek senaryoda yetmez. Araçlar sayesinde ajan:
- veri çekebilir
- hesaplama yapabilir
- dış API'lerle konuşabilir
- işlem başlatabilir

Bu da agent'ı pasif danışmandan aktif yardımcıya dönüştürür.

## 1. Kısım: Agent tool nedir?

Tool, ajanın kullanabileceği kontrollü bir yetenektir. Geliştirici aracı tanımlar; ajan ne zaman kullanacağına karar verir.

## 2. Kısım: Tool tanımlamak

Bir .NET metodu uygun açıklama ve parametrelerle agent'a bağlanabilir. Burada asıl önemli nokta, tool açıklamasının modelin doğru karar vermesine yardımcı olmasıdır.

## 3. Kısım: Birden fazla tool

Gerçek uygulamalarda aynı ajan birden fazla araca erişebilir. Örneğin:
- hava durumu alma
- rezervasyon sorgulama
- takvim oluşturma
- müşteri kaydı arama

Bu noktada araçların görevleri net ayrılmalıdır.

## 4. Kısım: Karmaşık parametreler

Tool'lar şehir, tarih aralığı, ürün kodu veya kullanıcı tipi gibi daha karmaşık parametreler alabilir. Açıklamalar ve türler iyi tanımlandığında modelin doğru eşleme yapması kolaylaşır.

## 5. Kısım: Async tool'lar ve dış API'ler

Gerçek dünya tool'ları çoğu zaman ağ çağrısı veya veri erişimi içerir. Bu nedenle async tasarım kritik hale gelir. Aynı zamanda hata yönetimi de tool tarafında ciddi önem taşır.

## En iyi pratikler

- açıklamaları açık yazın
- tool'ları dar sorumluluklu tutun
- hata mesajlarını temiz yönetin
- güvenlik ve yetki sınırlarını düşünün
- her istekte her tool'u açmayın; gerekiyorsa per-run kullanın

## Sonuç

Tool kullanan agent, artık yalnızca konuşan değil, işlem yapan bir sistemdir. Bu yüzden sorumluluk, gözlemleme ve sınır koyma burada daha da kritik hale gelir.

## İlgili örnekler

- `samples/MAF/MAF-BackgroundResponses-02-Tools/`
- `samples/MAF/MAF01/`
