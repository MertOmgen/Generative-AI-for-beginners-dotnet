# Ollama ile Lokal Geliştirme Kurulumu

Bulut yerine yerel model çalıştırmak istiyorsanız bu rehber başlangıç için yeterlidir. Özellikle maliyeti düşük tutmak, offline çalışmak veya veriyi makinenizde tutmak istiyorsanız Ollama iyi bir seçenektir.

## 1. Ollama'yı kurun

Önce Ollama'yı resmi sitesinden kurun:
- [https://ollama.com/download](https://ollama.com/download)

Kurulumdan sonra servisin çalıştığını doğrulayın.

## 2. Gerekli modelleri indirin

Kursun temel akışı için en az bir sohbet modeli gerekir. Daha sonra RAG örnekleri için embedding modeli de işin içine girer.

```bash
# Ana sohbet modeli
ollama pull phi4-mini

# Embedding modeli
ollama pull all-minilm
```

## 3. Projeyi yerel modele göre hazırlayın

Ollama varsayılan olarak şu adreste çalışır:

```text
http://localhost:11434
```

Örnek projelerde genellikle bu endpoint doğrudan kullanılır. Bu sayede Azure konfigürasyonu olmadan hızlı başlangıç yapabilirsiniz.

## 4. Örnek çalıştırın

```bash
cd samples/CoreSamples/BasicChat-03Ollama
dotnet run
```

Yanıt alıyorsanız ortam hazır demektir.

## Ne zaman Ollama seçilmeli?

- Lokal deney yapmak istiyorsanız
- API maliyeti olmadan ilerlemek istiyorsanız
- Veriyi kendi makinenizde tutmak istiyorsanız
- Ağ bağlantısına bağlı kalmak istemiyorsanız

## Sınırlamalar

- Model kalitesi bulut modellerine göre değişebilir
- Büyük modeller daha yüksek donanım ihtiyacı doğurur
- Bazı ileri örneklerde ek ayar gerekebilir

## Medium notu

Bu rehber, ilk dersin “başlangıç bariyerini düşürme” hedefi için kritiktir. Türkçe seri içinde özellikle “Azure mecburi değil” mesajını güçlendiren tamamlayıcı bir içerik olarak kullanılmalıdır.
