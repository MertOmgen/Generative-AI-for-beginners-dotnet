# İlk Ajanınızı Oluşturmak

Bu bölümde amaç, düz chat completion ile agent yaklaşımı arasındaki farkı görünür hale getirmektir.

## Chat mi, agent mı?

İlk bakışta ikisi benzer görünür. İkisinde de modele bir istek verip cevap alırsınız. Ama agent yaklaşımı şu farkları getirir:
- konuşma thread'ini kendi yönetir
- araç çağrılarını daha doğal ele alır
- çok adımlı akışlar için daha uygundur
- bağlamı daha sistematik taşır

## 1. Kısım: İlk agent örneği

```csharp
AIAgent writer = chatClient.CreateAIAgent(
    name: "Writer",
    instructions: "Write stories that are engaging and creative.");

AgentRunResponse response = await writer.RunAsync(
    "Lucia adında bir karakter içeren kısa bir hayaletli ev hikâyesi yaz.");
```

Bu örnek, `IChatClient` üstünden agent davranışı inşa etmenin ne kadar yalın olduğunu gösterir.

## 2. Kısım: `AIAgent` soyutlaması

`AIAgent`, agent dünyasının temel yapı taşıdır. İsmi vardır, talimatları vardır ve `RunAsync` üzerinden çalışır. Böylece model çağrısı daha görev odaklı bir forma dönüşür.

## 3. Kısım: Thread ile bağlam sürdürmek

Agent thread kullanıldığında konuşma sürekliliği daha temiz yönetilir. Kullanıcının adını, önceki isteğini veya önceki yanıtın bağlamını uygulama her seferinde elle taşımak zorunda kalmazsınız.

## 4. Kısım: Farklı sağlayıcılarla aynı desen

Azure OpenAI, API key tabanlı kullanım veya Ollama gibi yerel çözümlerle aynı agent kalıbı sürdürülebilir. Bu da Agent Framework'ün pratik gücünü artırır.

## 5. Kısım: Builder pattern

Telemetry, middleware ve özel davranışlar eklemek için builder zinciri kullanılabilir. Bu, ajanları daha gözlemlenebilir ve genişletilebilir hale getirir.

## Ne zaman agent kullanmalı?

Aşağıdaki durumlarda agent mantıklı hale gelir:
- çok adımlı işler
- tool çağrıları
- bağlamlı uzun diyaloglar
- planlama ve karar verme gerektiren akışlar

## İlgili örnekler

- `samples/MAF/MAF01/`
- `samples/MAF/MAF-Ollama-01/`
