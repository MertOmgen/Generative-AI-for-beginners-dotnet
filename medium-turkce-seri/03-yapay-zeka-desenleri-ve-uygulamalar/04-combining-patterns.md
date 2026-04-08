# Pattern'leri Birleştirmek

Gerçek ürünler tek bir AI tekniğiyle nadiren ayakta kalır. Bu bölüm, öğrendiğimiz parçaların nasıl birleştiğini anlatır.

## Neden kombinasyon gerekir?

Örneğin iyi bir kurumsal asistan genellikle şunları aynı anda kullanır:
- chat arayüzü
- RAG ile veri getirme
- structured output
- function calling
- bazen görsel veya belge analizi

Yani değer, tek bir yetenekte değil; bu yeteneklerin birlikte nasıl çalıştırıldığında ortaya çıkar.

## Tipik kombinasyonlar

### Chat + RAG
Kullanıcı doğal dilde sorar, sistem ilgili belge parçalarını getirir, model kaynaklı cevap üretir.

### Chat + Function Calling
Model gerekirse uygulama içindeki araçları kullanır; fiyat hesaplar, veri çeker, aksiyon başlatır.

### Vision + Structured Output
Resim ya da belge yorumlanır, ama sonuç serbest metin değil; uygulama tarafından tüketilebilecek bir veri modeli olur.

### RAG + Agents
Bilgi getirme ve karar verme aşamaları ajan iş akışlarına entegre edilir.

## Tasarım yaklaşımı

Pattern birleştirirken üç soruya cevap vermek gerekir:
1. Kullanıcı ne istiyor?
2. Cevap için hangi veri gerekli?
3. Model hangi araçları veya ara katmanları kullanmalı?

## Sonuç

Bu bölümün ana mesajı şu: AI mimarisi, tek bir model çağrısından çok daha fazlasıdır. En iyi çözümler, doğru pattern kombinasyonundan çıkar.
