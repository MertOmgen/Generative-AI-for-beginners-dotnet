# Multi-Agent Workflow'lar

Birden fazla ajan birlikte çalıştığında, tek modelle çözmesi zor olan işleri daha temiz şekilde bölebilirsiniz. Bu bölüm, ajan orkestrasyonunun temel desenlerini anlatır.

## Neden birden fazla ajan?

Tek bir modelden her rolü aynı kalitede beklemek zor olabilir. Bunun yerine görevleri uzmanlaşmış rollere ayırabilirsiniz:
- araştırmacı
- yazar
- editör
- denetleyici

Bu yaklaşım özellikle içerik üretimi, karar destek ve daha uzun iş akışlarında güçlüdür.

## 1. Kısım: Workflow desenleri

Multi-agent sistemlerde temel orkestrasyon biçimleri şunlardır:
- sequential
- concurrent
- handoff
- conditional handoff

Her biri farklı problem türü için uygundur.

## 2. Kısım: Sequential workflow

En anlaşılır başlangıç desenidir. Bir ajan çıktıyı üretir, diğeri bunu geliştirir.

```csharp
Workflow workflow =
    AgentWorkflowBuilder.BuildSequential(writer, editor);
```

Bu yapı yazı üretme, rapor özetleme veya taslak → revizyon akışlarında çok işe yarar.

## 3. Kısım: Concurrent workflow

Bazı görevler paralel ilerletilebilir. Örneğin bir konu için aynı anda pazar analizi, teknik analiz ve risk analizi çıkarılabilir. Daha sonra sonuçlar birleştirilir.

## 4. Kısım: Handoff ve conditional handoff

Bir ajan, işi uygun gördüğü başka bir ajana devredebilir. Daha gelişmiş sürümde ise bu devir, belli kurallara veya koşullara bağlı olarak yapılır.

## 5. Kısım: Multi-model orkestrasyon

Aynı workflow içinde farklı model sağlayıcıları kullanılabilir. Örneğin biri Azure OpenAI, biri Ollama, biri Foundry Agents olabilir. Bu esneklik kurumsal mimariler için güçlü bir avantajdır.

## En iyi pratikler

- her ajana net sorumluluk verin
- hata durumlarını düşünün
- workflow derinliğini gereksiz büyütmeyin
- ara çıktıları gözlemlenebilir hale getirin

## Sonuç

Multi-agent yaklaşımı, üretken yapay zekâyı tek cevap üretiminden çok adımlı iş çözümüne taşır.

## İlgili örnekler

- `samples/MAF/MAF02/`
- `samples/MAF/MAF-MultiAgents/`
