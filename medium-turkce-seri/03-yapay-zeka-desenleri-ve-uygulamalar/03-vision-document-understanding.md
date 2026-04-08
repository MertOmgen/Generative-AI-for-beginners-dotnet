# Vision ve Document Understanding

AI uygulamaları yalnızca metinle sınırlı değildir. Bu bölümde görselleri yorumlama, dokümanlardan bilgi çıkarma ve çok modlu içerikle çalışma yaklaşımı anlatılır.

## Neden önemli?

Gerçek iş senaryolarında giriş verisi çoğu zaman şunlardan biri olur:
- fiş veya fatura
- ürün görseli
- lisans veya kimlik fotoğrafı
- PDF doküman
- ekran görüntüsü

Bu yüzden modern AI uygulaması, metin dışı içerikle de çalışabilmelidir.

## 1. Kısım: Görsel yorumlama

Bir resmi modele yalnızca eklemek bile güçlü sonuçlar verebilir:
- sahne açıklama
- nesne sayma
- OCR benzeri metin çıkarımı
- ürün veya belge inceleme

## 2. Kısım: Belge anlama

PDF ve benzeri dokümanlar için amaç genelde serbest metin üretmek değil, faydalı bilgi çıkarmaktır. Örneğin bir fişte toplam tutar, tarih veya kategori yakalanabilir.

## 3. Kısım: Multimodal düşünme

Bu alandaki asıl fark, prompt ile içeriğin birlikte çalışmasıdır. Yani modele yalnızca “Bu resimde ne var?” demek değil, “Bu faturada yalnızca kahve ve sosis için ne kadar öderim?” gibi hedefli sorular sorarsınız.

## Kullanım alanları

- belge işleme
- saha fotoğrafı analizi
- satış ve e-ticaret görsel incelemeleri
- kurumsal OCR senaryoları

## İlgili örnekler

- `samples/CoreSamples/Vision-01MEAI-AzureOpenAI/`
- `samples/CoreSamples/Vision-02MEAI-Ollama/`
- `samples/CoreSamples/Vision-03MEAI-AOAI/`
- `samples/CoreSamples/OpenAI-FileProcessing-Pdf-01/`
