# 5. Ders İçin Kod Örnekleri

## Bu ders için yaklaşım

Beşinci ders, diğer bölümlere kıyasla daha çok ilke, risk ve uygulama tasarımı odaklıdır. Bu nedenle yeni repoda doğrudan “çalıştırılacak” örneklerden çok, önceki derslerdeki örneklerin sorumlu AI filtresiyle yeniden konumlandırılması önerilir.

## Yeni repoda referans verilecek örnekler

| Orijinal yol | Önerilen yeni yol | Neden burada? |
|---|---|---|
| `05-ResponsibleAI/readme.md` | `05-sorumlu-yapay-zeka/referanslar/orijinal-ders.md` | Ana içerik kaynağı |
| `samples/MAF/MAF-MultiAgents/` | `05-sorumlu-yapay-zeka/ornekler/MAF-MultiAgents/` | Ajan riskleri ve onay ihtiyacı |
| `samples/PracticalSamples/` | `05-sorumlu-yapay-zeka/ornekler/PracticalSamples/` | Dış araçlar ve entegrasyon güvenliği |
| `samples/CoreSamples/RAGSimple-02MEAIVectorsMemory/` | `05-sorumlu-yapay-zeka/ornekler/RAGSimple-02MEAIVectorsMemory/` | Kaynak gösterimi ve groundedness |

## Makalede kullanılacak pratik kontrol listesi

- Kullanıcıya AI disclosure gösteriliyor mu?
- Hassas aksiyonlar için insan onayı var mı?
- İçerik filtreleme ve hata yönetimi tanımlı mı?
- Kaynak gösterimi ve karar izi tutuluyor mu?
- Gizlilik ve veri sınırları açık mı?

## Editoryal not

Bu ders için ayrı kod klasörlerinden çok, “sorumlu kullanım rehberi” yaklaşımı daha güçlüdür. Kod örnekleri destekleyici unsur olarak kullanılmalı, merkezde risk analizi olmalıdır.
