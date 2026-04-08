# Local Model Runners

Yerel model koşucuları, AI geliştirmede yalnızca “alternatif” değil, bazen doğrudan stratejik tercihtir. Bu bölüm, lokal çalışma ekosistemini anlamaya odaklanır.

## Neden lokal model?

- veri gizliliği
- düşük maliyet
- çevrimdışı çalışma
- hızlı prototipleme
- sağlayıcı bağımsızlığı

## Bu repo hangi seçenekleri gösteriyor?

- AI Toolkit
- Docker Model Runner
- Foundry Local
- Ollama tabanlı yaklaşımlar

Bu araçların ortak noktası, .NET geliştiricisinin bulut zorunluluğu olmadan deney yapabilmesini sağlamalarıdır.

## Nerede avantajlı?

- demo ve eğitim ortamları
- iç ağda çalışan uygulamalar
- hassas verinin dışarı çıkmaması gereken senaryolar
- küçük ekiplerin maliyeti kontrol etme ihtiyacı

## Dikkat edilmesi gerekenler

- model kalitesi ve kapasitesi sağlayıcıya göre değişir
- büyük modeller daha güçlü donanım ister
- bazı multimodal senaryolarda bulut kadar rahat olmayabilir

## Sonuç

Bu bölümün mesajı açık: üretken yapay zekâ geliştirmek için her zaman bulut gerekmiyor. Doğru senaryoda lokal model çalıştırma, hız ve gizlilik açısından çok güçlü bir tercih olabilir.

## İlgili örnekler

- `samples/CoreSamples/AIToolkit-02-MEAI-Chat/`
- `samples/CoreSamples/DockerModels-02-MEAI-Chat/`
- `samples/CoreSamples/AIFoundryLocal-01-MEAI-Chat/`
