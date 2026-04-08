# 1. Ders İçin Kod Örnekleri

## Yeni repoya alınması önerilen örnekler

| Orijinal yol | Önerilen yeni yol | Amaç |
|---|---|---|
| `samples/CoreSamples/BasicChat-01MEAI/` | `01-uretken-yapay-zekaya-giris/ornekler/BasicChat-01MEAI/` | `IChatClient` ile temel sohbet akışı |
| `samples/CoreSamples/BasicChat-03Ollama/` | `01-uretken-yapay-zekaya-giris/ornekler/BasicChat-03Ollama/` | Lokal model ile ilk çalışma |
| `01-IntroductionToGenerativeAI/setup-azure-openai.md` | `01-uretken-yapay-zekaya-giris/referanslar/setup-azure-openai.md` | Azure kurulumu |
| `01-IntroductionToGenerativeAI/setup-local-ollama.md` | `01-uretken-yapay-zekaya-giris/referanslar/setup-local-ollama.md` | Ollama kurulumu |

## Makalede kullanılabilecek kod bölümleri

### 1. Temel sohbet çağrısı
- Dosya: `samples/CoreSamples/BasicChat-01MEAI/app.cs`
- Vurgu: Prompt gönder, cevap al, ekrana yazdır.

### 2. Sağlayıcı bağımsızlığı
- Dosya: `samples/CoreSamples/BasicChat-03Ollama/`
- Vurgu: Aynı akışın yerel modelle de çalışabilmesi.

## Editoryal not

Bu ders için kod örneklerini tam taşımak yerine en az bir Azure ve bir Ollama örneği almak yeterlidir. Böylece makale, kurulum karmaşasına boğulmadan iki farklı çalışma modelini gösterebilir.
