# 2. Ders İçin Kod Örnekleri

## Yeni repoya alınması önerilen örnekler

| Orijinal yol | Önerilen yeni yol | Amaç |
|---|---|---|
| `samples/CoreSamples/BasicChat-01MEAI/` | `02-uretken-yapay-zeka-teknikleri/ornekler/BasicChat-01MEAI/` | Temel chat akışı |
| `samples/CoreSamples/BasicChat-10ConversationHistory/` | `02-uretken-yapay-zeka-teknikleri/ornekler/BasicChat-10ConversationHistory/` | Konuşma geçmişi yönetimi |
| `samples/CoreSamples/MEAIFunctions/` | `02-uretken-yapay-zeka-teknikleri/ornekler/MEAIFunctions/` | Function calling |
| `samples/CoreSamples/MEAIFunctionsAzureOpenAI/` | `02-uretken-yapay-zeka-teknikleri/ornekler/MEAIFunctionsAzureOpenAI/` | Azure varyantı |
| `samples/CoreSamples/MEAIFunctionsOllama/` | `02-uretken-yapay-zeka-teknikleri/ornekler/MEAIFunctionsOllama/` | Ollama varyantı |

## Makalede özellikle gösterilecek akışlar

1. Kullanıcı mesajını `conversation` listesine ekleme
2. Model yanıtını yeniden geçmişe yazma
3. Bir .NET metodunu tool olarak kaydetme
4. `UseFunctionInvocation()` ile tool zincirini etkinleştirme

## Editoryal not

Bu ders için örnekleri tam taşımak mantıklı; çünkü makale okuyucusu en çok buradaki kodları çalıştırmak isteyecektir.
