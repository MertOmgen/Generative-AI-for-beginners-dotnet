# Middleware Pipeline

Bu bölüm, AI istemci katmanını daha üretim hazır hale getiren yapı taşlarını ele alır. Amaç yalnızca modelden cevap almak değil; bunu gözlemlenebilir, önbelleklenebilir ve sürdürülebilir bir mimari ile yapmaktır.

## Neden middleware?

Bir AI uygulaması büyüdükçe aşağıdaki ihtiyaçlar ortaya çıkar:
- tekrar eden istekleri önbellekleme
- loglama ve telemetry
- ortak varsayılan ayarlar
- istek/yanıt akışına özel davranışlar ekleme

`ChatClientBuilder` yaklaşımı tam bu noktada devreye girer.

## 1. Kısım: Builder deseni

İstemciyi zincir halinde şekillendirirsiniz. Böylece tek bir chat client etrafında katmanlı davranışlar tanımlanabilir.

## 2. Kısım: Caching

Özellikle aynı prompt'ların sık tekrar ettiği senaryolarda caching maliyeti ve gecikmeyi düşürür.

- küçük uygulamalarda in-memory cache yeterli olabilir
- dağıtık yapılarda Redis gibi paylaşımlı çözümler tercih edilir

Bu katman, AI kullanım maliyetini kontrol altında tutmak için de önemlidir.

## 3. Kısım: Telemetry ve logging

AI çağrıları görünmez kaldığında hata ayıklamak zorlaşır. OpenTelemetry ve benzeri araçlarla:
- hangi isteklerin ne kadar sürdüğü
- hangi sağlayıcının nasıl davrandığı
- hata oranlarının ne olduğu

izlenebilir hale gelir.

## 4. Kısım: Çoklu middleware zinciri

Birden fazla middleware birlikte kullanıldığında çalıştırma sırası önemlidir. Örneğin önce cache kontrolü, sonra loglama ya da tam tersi farklı sonuçlar doğurabilir. Bu yüzden zincirin sırası bilinçli tasarlanmalıdır.

## 5. Kısım: Varsayılan ayarlar

`ChatOptions` gibi ortak ayarları istemci seviyesinde sabitlemek, uygulama boyunca daha tutarlı çıktı alınmasını sağlar.

## 6. Kısım: Custom middleware

Kendi ara katmanlarınızı yazarak:
- prompt ön işleme
- güvenlik filtreleme
- kurum içi kurallar
- özel başlık ve izleme mantığı

ekleyebilirsiniz.

Bu sayede AI katmanı, uygulamanın geri kalan mimarisiyle daha iyi hizalanır.

## 7. Kısım: Dependency injection

.NET projelerinde middleware zincirinin DI ile kurulması, özellikle web ve servis uygulamalarında sürdürülebilirlik sağlar. Böylece farklı ortamlarda farklı istemci yapılandırmaları tanımlamak kolaylaşır.

## 8. Kısım: Üretim bakışı

Bu bölümün asıl mesajı şudur: AI entegrasyonu yalnızca prompt yazmak değildir. Sağlam uygulamalarda gözlemlenebilirlik, performans ve bakım kolaylığı da en az prompt kadar önemlidir.

## İlgili örnekler

- `samples/CoreSamples/BasicChat-01MEAI/`
- `samples/CoreSamples/MEAIFunctions/`
- `samples/CoreSamples/BasicChat-10ConversationHistory/`
