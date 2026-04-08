# Retrieval-Augmented Generation (RAG)

RAG, modelin genel bilgisi ile sizin verinizi birleştiren en popüler uygulama desenlerinden biridir. Kullanıcıya verilen cevaplar, yalnızca modelin eğitim verisine değil; sizin dokümanlarınıza, notlarınıza veya şirket içi bilgi tabanınıza da dayanır.

## Neden RAG?

Saf LLM kullanımı bazı durumlarda yetersiz kalır:
- kurumunuza özel bilgiyi bilmez
- güncel belgeye erişemez
- halüsinasyon üretme riski taşır

RAG bu problemi iki aşamada çözer:
1. İlgili bilgiyi bulur
2. Bulduğu bilgiyle cevabı üretir

## Temel akış

RAG tipik olarak şu zincirden oluşur:
- dokümanları parçalara ayır
- embedding üret
- vector store içine yaz
- kullanıcı sorgusu için embedding üret
- en ilgili parçaları getir
- modeli bu bağlamla birlikte çalıştır

## .NET bakışı

Bu repo içindeki örnekler, bellek içi yaklaşım, Azure AI Search ve Qdrant gibi farklı altyapılarla aynı deseni gösterir. Bu da okuyucuya, RAG'in tek bir ürün değil bir mimari yaklaşım olduğunu anlatır.

## RAG ne zaman kullanılır?

- kurum içi bilgi tabanı üzerinde soru-cevap
- destek dökümanlarıyla çalışan asistanlar
- mevzuat, prosedür, katalog veya sözleşme arama
- kullanıcıya kaynaklı, izlenebilir cevap verme ihtiyacı

## Dikkat edilmesi gerekenler

- chunk boyutu iyi ayarlanmalıdır
- veri güncellenince embedding tarafı da güncellenmelidir
- getirilen bağlamın kalitesi, son cevabın kalitesini doğrudan etkiler
- kaynak gösterimi güven açısından önemlidir

## İlgili örnekler

- `samples/CoreSamples/RAGSimple-02MEAIVectorsMemory/`
- `samples/CoreSamples/RAGSimple-03MEAIVectorsAISearch/`
- `samples/CoreSamples/RAGSimple-04MEAIVectorsQdrant/`
