# Embeddings ve Semantic Search

Bu bölümde klasik anahtar kelime aramasından anlam tabanlı aramaya geçiyoruz. Medium okuyucusu için temel mesaj basit: AI, kelimeleri yalnızca metin olarak değil, anlam taşıyan vektörler olarak da ele alabilir.

## Anahtar kelime aramasının problemi

“running shoes” arayan biri aslında “sneakers for jogging” ile de ilgileniyor olabilir. Klasik arama bunu çoğu zaman kaçırır. Semantic search ise metinlerin anlamsal yakınlığına bakar.

## 1. Kısım: Embedding nedir?

Embedding, metnin sayısal bir vektör temsilidir.

```text
"I love pizza" → [0.12, -0.45, 0.89, ...]
```

Benzer anlamlar, benzer vektörler üretir. Bu da “anlamla arama”yı mümkün kılar.

## 2. Kısım: .NET içinde embedding üretmek

`IEmbeddingGenerator` arayüzü, bu iş için standart kapıdır. Uygulama metni embedding modeline gönderir ve karşılığında bir vektör alır.

Bu yapı:
- doküman benzerliği
- öneri sistemleri
- semantic search
- RAG

senaryolarının temelidir.

## 3. Kısım: Similarity ölçmek

Vektörler üretildikten sonra genellikle cosine similarity ile karşılaştırılır. Skor ne kadar yüksekse anlamsal yakınlık o kadar fazladır.

Buradaki kritik içgörü şudur: aynı kelimeleri kullanmayan iki ifade yine de benzer sonuç verebilir.

## 4. Kısım: Vector store kullanımı

Gerçek sistemlerde her sorguda tüm embedding'leri yeniden üretmek ve sırayla dolaşmak doğru yaklaşım değildir. Bu yüzden vector store veya vector database kullanılır.

Bu katman:
- embedding'leri kalıcı saklar
- hızlı similarity search sağlar
- ölçeklenebilirlik kazandırır

## Neden önemli?

Semantic search, RAG'in ve anlam tabanlı bilgi erişiminin temelidir. Bu yüzden bu bölüm, sonraki konuların altyapısını kurar.

## İlgili örnekler

- `samples/CoreSamples/RAGSimple-02MEAIVectorsMemory/`
- `samples/CoreSamples/RAGSimple-03MEAIVectorsAISearch/`
- `samples/CoreSamples/RAGSimple-04MEAIVectorsQdrant/`
