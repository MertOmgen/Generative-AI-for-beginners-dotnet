# 4. Ders — Microsoft Agent Framework ile Ajanlar

## Giriş

Dördüncü derste oyun alanı genişliyor. Artık yalnızca soru-cevap üreten bir chat uygulaması değil, hedefe yönelik hareket eden ajanlardan söz ediyoruz. Bu fark küçük değil: chatbot cevap verir, ajan iş yapar.

## Ajan ile chatbot arasındaki fark

Bu repoda anlatılan çerçeve çok net:

- chatbot: etkileşime yanıt verir
- ajan: plan kurar, araç kullanır, adım adım ilerler

Bu farkı Türkçe Medium makalesinde özellikle sade bir dille kurmak önemli. Çünkü birçok okuyucu “ajan” kavramını gereğinden fazla soyut görüyor.

## İlk ajan örneği

Kaynak: `samples/MAF/MAF01/Program.cs`

```csharp
AIAgent writer = chatClient.CreateAIAgent(
    name: "Writer",
    instructions: "Write stories that are engaging and creative.");

AgentRunResponse response = await writer.RunAsync(
    "Write a short story about a haunted house with a character named Lucia.");
```

Buradaki temel mesaj şu: Agent Framework, düz model çağrısını amaç odaklı bir çalışma biçimine dönüştürüyor.

## Workflow tarafı

Kaynak: `samples/MAF/MAF02/Program.cs`

```csharp
Workflow workflow =
    AgentWorkflowBuilder
        .BuildSequential(writer, editor);

AIAgent workflowAgent = workflow.AsAgent();
AgentRunResponse workflowResponse =
    await workflowAgent.RunAsync("Write a short story about a haunted house.");
```

Bu örnek, çok ajanlı düşünmenin giriş seviyesi. Tek bir model her şeyi yapmak zorunda değil; görevler ajanlara bölünebilir.

## Gerçek güç: çok ajanlı orkestrasyon

Kaynak: `samples/MAF/MAF-MultiAgents/Program.cs`

Bu örnekte araştırmacı, yazar ve gözden geçiren rollerini üstlenen üç ayrı ajan birlikte çalışıyor. Üstelik farklı sağlayıcılar aynı iş akışında yer alabiliyor. Bu, kurumsal dünyada çok önemli bir avantaj: aynı mimaride farklı model sağlayıcılarını birleştirebilirsiniz.

## MCP neden önemli?

Model Context Protocol, ajanlara standart bir araç erişim katmanı sunar. Yani ajanlar yalnızca prompt ile değil; dış sistemlerle, tool server'larla ve başka servislerle daha düzenli biçimde konuşabilir. Medium makalesinde bunu “ajan ekosisteminin ortak bağlantı standardı” gibi sade bir çerçevede anlatmak etkili olur.

## Sonuç

Bu ders, okuyucuya modern AI uygulamalarının nereye evrildiğini gösterir. Chat uygulamalarından görev icra eden sistemlere geçiş, serinin en güçlü kırılma noktasıdır. Son makalede ise bu gücün sorumluluk tarafına bakacağız.
