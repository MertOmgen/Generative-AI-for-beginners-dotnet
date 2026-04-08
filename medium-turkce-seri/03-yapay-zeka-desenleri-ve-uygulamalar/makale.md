# 3. Ders — .NET ile Yapay Zekâ Desenleri ve Gerçek Uygulamalar

## Giriş

Teknikleri bilmek tek başına yeterli değil. Chat, function calling ya da streaming birer araçtır; asıl farkı yaratan şey, bunların hangi problem için hangi desende bir araya getirildiğidir. Üçüncü ders tam olarak bunu anlatıyor.

## Bu derste hangi desenler var?

- embeddings ve semantic search
- retrieval-augmented generation (RAG)
- vision ve document understanding
- pattern birleştirme
- local model runners

## Semantic search neden klasik aramadan farklı?

Anahtar kelime araması, metindeki birebir eşleşmeleri bulur. Semantic search ise anlam yakınlığını kullanır. Bu yaklaşım özellikle doküman arama, bilgi tabanı tarama ve öneri sistemlerinde çok güçlüdür.

Kaynak: `samples/CoreSamples/RAGSimple-02MEAIVectorsMemory/Program.cs`

```csharp
var query = "A family friendly movie that includes ogres and dragons";
var queryEmbedding = await generator.GenerateVectorAsync(query);

var results = movieData
    .Select(movie => (Movie: movie, Score: CosineSimilarity(queryEmbedding.Span, movie.Vector.Span)))
    .OrderByDescending(x => x.Score)
    .Take(2);
```

Bu birkaç satır, “anlam ile arama” yaklaşımını çok iyi özetliyor.

## RAG neden bu kadar popüler?

Çünkü modelin genel bilgisini, sizin özel verinizle birleştirir. Böylece AI daha güncel, daha kuruma özel ve daha kontrol edilebilir yanıtlar üretir. Medium okuyucusu için bunu “LLM + şirket dokümanları = daha işe yarar cevaplar” şeklinde sadeleştirmek etkili olur.

## Görüntü ve belge anlama

Repo yalnızca metin odaklı değil. Görselleri yorumlama ve dokümanlardan bilgi çıkarma örnekleri de içeriyor.

Kaynak: `samples/CoreSamples/Vision-01MEAI-AzureOpenAI/Program.cs`

```csharp
AIContent aic = new DataContent(File.ReadAllBytes(image), "image/jpeg");
var message = new ChatMessage(Microsoft.Extensions.AI.ChatRole.User, [aic]);
messages.Add(message);

var response = await chatClient.GetResponseAsync(messages);
Console.WriteLine($"Response: {response.Text}");
```

Bu örnek, multimodal yaklaşımın .NET içinde ne kadar doğal kullanılabildiğini gösteriyor.

## Yerel model koşucuları neden stratejik?

AI Toolkit, Docker Model Runner ve Foundry Local gibi seçenekler; gizlilik, maliyet ve offline geliştirme açısından ciddi avantaj sağlar. Üçüncü makale için iyi bir kapanış, okuyucuya “AI yalnızca bulutta yapılmaz” mesajını vermektir.

## Sonuç

Bu dersle birlikte okuyucu artık sadece model çağıran biri olmaktan çıkar; hangi problemi hangi AI deseniyle çözeceğini düşünmeye başlar. Sonraki adımda bu desenlerin daha otonom hale geldiği ajan dünyasına geçiyoruz.
